require 'rake/clean'
require 'rake/rdoctask'
require 'rake/packagetask'

task :default => :web

task :web => [:doc, :package] do
  sh 'rsync', '--rsh=ssh', '-av', '--delete', *(FileList['pkg/*'] << "#{ENV['UC']}:web/pub/wmii")
end

CLOBBER.include 'doc', 'pkg'

Rake::RDocTask.new(:doc) do |rd|
  rd.rdoc_files.include('wmiirc', '*.rb')
  rd.rdoc_dir = 'doc'
end

Rake::PackageTask.new('snk_wmiirc', :noversion) do |p|
  p.need_tar_gz = true
  p.package_files.include('doc', 'wmiirc', '*.rb', 'ruby-ixp')
end
