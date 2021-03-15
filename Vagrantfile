class Hash
    def slice(*keep_keys)
      h = {}
      keep_keys.each { |key| h[key] = fetch(key) if has_key?(key) }
      h
    end unless Hash.method_defined?(:slice)
    def except(*less_keys)
      slice(*keys - less_keys)
    end unless Hash.method_defined?(:except)
end

Vagrant.configure("2") do |config|
    config.vm.define "vb" do |vb|
        vb.vm.box = "hashicorp/bionic64"
    end

    config.vm.define "aws" do |aws|

        aws.vm.box = "dummy"
        aws.vm.box_url = "https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box"

        aws.vm.provider :aws do |aws,override|
            override.nfs.functional = false
            aws.keypair_name = "id_rsa"
            aws.ami = "ami-08bac620dc84221eb"
            aws.instance_type = "t3.micro"
            aws.region = "eu-west-1"
            aws.subnet_id = "subnet-9bf73cc1"
            aws.security_groups = ["sg-7b78fe07"]
            aws.associate_public_ip = true
            override.ssh.username = "ec2-user"
            override.ssh.private_key_path = "~/.ssh/id_rsa_aws_air.pem"
        end
    end

end
