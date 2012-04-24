require 'rake'

namespace :install do
  desc 'Hook the dotfiles into $HOME/'
  task :hook do
    skip_all = overwrite_all = backup_all = false

    Dir.glob('**/**{.symlink}').each do |target|
      name = target.split('/').last.split('.symlink').last
      if name.include?('.no_dot')
        name = "#{ENV['HOME']}/#{name.split('no_dot').last}"
      else
        name = "#{ENV['HOME']}/.#{name}"
      end

      if File.exists?(name) || File.symlink?(name)
        puts "File exists! #{name}"
        case STDIN.gets.chomp
        when 'o' then overwrite = true
        when 'b' then backup = true
        when 's' then next
        end

        # File backup if backup (add .old)
        # File remove if overwrite
      end

      # Link here... `ln -s target name`
    end
  end

  desc 'Run special install commands for non standard files'
  task :special do
  end

  desc 'Hook and run special install'
  task :all => [ :hook, :special ]
end

desc 'alias for install:all'
task :install => :'install:all'

desc 'Makes an existing .file part of the .dotfiles folder'
task :mop do
end

desc 'Uninstalls whatever was installed during installation'
task :uninstall do
end
