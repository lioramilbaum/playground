Vagrant.configure("2") do |config|
    config.vm.define "vb" do |vb|
        vb.vm.box = "hashicorp/bionic64"
    end

    config.vm.define "aws" do |aws|

        aws.vm.box = "dummy"
        aws.vm.box_url = "https://github.com/mitchellh/vagrant-aws/raw/master/dummy.box"

        aws.vm.provider :aws do |aws,override|
        override.nfs.functional = false
        aws.aws_profile = ENV['PROFILE_aws']
        aws.keypair_name = ENV['KEY_NAME_aws']
        aws.ami = ENV['AMI_aws']
        aws.instance_type = ENV['INSTANCE_TYPE_aws']
        aws.region = ENV['REGION_aws']
        aws.subnet_id = ENV['SUBNET_ID_aws']
        aws.security_groups = ENV['SECURITY_GROUPS_aws']
        aws.associate_public_ip = true
        override.ssh.username = ENV['USERNAME_aws']
        override.ssh.private_key_path = ENV['PRIVATE_KEY_PATH_aws']
        end
    end

end
