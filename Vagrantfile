Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2204"
  config.vm.box_version = "4.0.28"
  config.vm.hostname = "postgres-8.4"
  config.vm.network "forwarded_port", guest: 5432, host: 5432 # Для PostgreSQL
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = 1
  end
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get install -y wget lsb-release gnupg
    echo "deb https://apt-archive.postgresql.org/pub/repos/apt precise-pgdg main" > /etc/apt/sources.list.d/pgdg.list
    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
    apt-get update
    apt-get install -y postgresql-8.4
  SHELL
end
