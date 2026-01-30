require 'fileutils'
include FileUtils

def home
  @home ||= ENV['HOME'] || abort('Error. Set env `HOME`')
end

def claude_home
  "#{home}/.claude"
end

def repo_root
  File.expand_path(__dir__)
end

def red_puts(string)
  print "\e[31m"
  puts string
  print "\e[0m"
end

def green_puts(string)
  print "\e[32m"
  puts string
  print "\e[0m"
end

# rm_rf with backup
def rm_with_backup!(target_path)
  return unless File.exist?(target_path) || File.symlink?(target_path)

  backup_base = "/tmp/cc_backup/"
  mkdir_p backup_base
  backup_path = File.join(backup_base, File.basename(target_path) + ".#{Time.now.to_i}.#{Process.pid}")

  if File.symlink?(target_path)
    # just remove symlink
    rm_f target_path
  else
    # backup if real file/directory
    cp_r target_path, backup_path
    rm_rf target_path
  end
end

desc "default task"
task default: :link_skills

desc "Link all skills from repo to ~/.claude/skills/"
task :link_skills do
  skills_src = "#{repo_root}/.claude/skills"
  skills_dest = "#{claude_home}/skills"

  unless Dir.exist?(skills_src)
    red_puts "Error: #{skills_src} does not exist"
    abort
  end

  mkdir_p skills_dest

  Dir.children(skills_src).each do |skill_name|
    src = "#{skills_src}/#{skill_name}"
    dest = "#{skills_dest}/#{skill_name}"

    next unless File.directory?(src)

    if File.symlink?(dest)
      current_target = File.readlink(dest)
      if current_target == src
        puts "✓ #{skill_name} (already linked)"
        next
      else
        puts "⚠ #{skill_name}: updating symlink"
      end
    elsif File.exist?(dest)
      puts "⚠ #{skill_name}: replacing existing directory"
    else
      puts "➕ #{skill_name}: creating symlink"
    end

    rm_with_backup!(dest)
    ln_sf src, dest
    green_puts "  → #{dest} -> #{src}"
  end

  puts
  green_puts "✅ Done!"
end

desc "List current skill symlinks"
task :status do
  skills_dest = "#{claude_home}/skills"

  puts "=== ~/.claude/skills/ status ==="
  puts

  unless Dir.exist?(skills_dest)
    puts "(directory does not exist)"
    next
  end

  Dir.children(skills_dest).sort.each do |name|
    path = "#{skills_dest}/#{name}"
    if File.symlink?(path)
      target = File.readlink(path)
      if target.start_with?(repo_root)
        green_puts "✓ #{name} -> #{target}"
      else
        puts "? #{name} -> #{target} (external)"
      end
    else
      red_puts "✗ #{name} (not a symlink)"
    end
  end
end

desc "Unlink all skills managed by this repo"
task :unlink_skills do
  skills_src = "#{repo_root}/.claude/skills"
  skills_dest = "#{claude_home}/skills"

  unless Dir.exist?(skills_src)
    red_puts "Error: #{skills_src} does not exist"
    abort
  end

  Dir.children(skills_src).each do |skill_name|
    src = "#{skills_src}/#{skill_name}"
    dest = "#{skills_dest}/#{skill_name}"

    next unless File.symlink?(dest)
    next unless File.readlink(dest) == src

    rm_f dest
    puts "✗ Unlinked #{skill_name}"
  end

  green_puts "✅ Done!"
end
