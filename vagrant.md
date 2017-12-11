# vagrant

vagrant를 설치해 봅시다.



## version

- VirtualBox : 5.1.30
- vagrant_1.9.5
- git for windows



## setting

```ruby
# 기존 설정파일에 있습니다.

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest: 3000, host: 3000 
end
```

- Ruby on Rails 설치 - Go Rails 따라서 GoGo

- Ruby on Rails 서버 실행

  ```shell
  rails s -b 0.0.0.0
  ```



## 가이드

```markdown
1. windows에서 폴더하나를 만든다.
2. 폴더에 들어가서 vagrant init ubuntu/xenial64
	-> Vagrantfile 생성
	-> port, host:3000, guest:3000 수정
3. vagrant up
4. vagrant ssh
5. 가상머신 접속 상태에서 cd /vagrant
	-> 공유폴더로 접속 가능
6. 기본 프로그램 설치
	- gorails.com ->guides -> setup ruby on rails
	- 필수 프로그램 : 진짜 많음

** gem install bundler 까지
```

