# vagrant

vagrant를 설치해 봅시다.

## version

- VirtualBox : 5.1.30
- vagrant_1.9.5
- git for windows

## setting

1. Windows에서 폴더 하나를 만든다. (현재 작업 중인 폴더가 있다면 해당 폴더로 들어간다.)
2. 폴더에 들어가서(예, `cd ~/proejct`)
```console
vagrant init
```
3. Vagrantfile 수정
```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest: 3000, host: 3000  # Rails를 위한 port 설정
  config.vm.network "forwarded_port", guest: 4567, host: 4567  # Sinatra를 위한 port 설정
end
```
3. 가상환경 만들기 : vagrant up
```console
vagrant up
```
4. 가상환경 접속하기 : vagrant ssh
```console
vagrant ssh
```
5. 가상머신 접속 상태에서 공유폴더 접근하기
```console
cd /vagrant
```
- 공유폴더(Vagrantfile이 만들어진 폴더)로 접근 가능

6. 필수 프로그램 설치
- 아래의 코드를 한땀 한땀 옮겨 쓰기
```
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

sudo apt-get update
sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev nodejs yarn
```

7. Ruby 설치
- 아래의 코드를 한땀 한땀 옮겨 쓰기
```
cd
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL

git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
exec $SHELL

rbenv install 2.3.5
rbenv global 2.3.5
ruby -v
```

