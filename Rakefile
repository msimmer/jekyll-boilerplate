
require 'rake'
require 'yaml'

CONFIG = YAML.load_file("_rsync.yml")

LOCAL_PATH = CONFIG['local_path']
REMOTE_PATH = CONFIG['remote_path']
SSH_USER = CONFIG['ssh_user']
SSH_HOST = CONFIG['ssh_host']
SYNC_CMD = CONFIG['rsync_cmd']

def execute(command)
  system command.to_s
end

task default: :serve

desc 'Deploy website via rsync'
task :deploy do
  execute("#{SYNC_CMD} #{LOCAL_PATH} #{SSH_USER}@#{SSH_HOST}:#{REMOTE_PATH}")
end

desc 'Build the website'
task :build do
  execute('bundle exec jekyll build')
end

desc 'Start a development server'
task :serve do
  execute('bundle exec jekyll serve')
end
