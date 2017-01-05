<h1>使用說明</h1>
在build新的image時候把參數利用 --build-arg 參數必要參數代入<br />

<h2>必要參數</h2>
username 使用者帳號(default: user)<br />
userpassword 使用者密碼(default: 000000)

<h2>使用方式</h2>
在dockerfile所在位置利用docker build製作新的image
```
docker build \
  --build-arg username=[your name] \
  --build-arg userpassword=[your password] -t sshd:dockerfile .
```
這樣就可以在
```
docker images
```
中看到新做出來的影像擋，這個影像擋已經有剛剛塞進去的帳號密碼

```
docker run -d -p [your port]:22 sshd:dockerfile
```
啟動已經建設好的image，並且把port放對應到伺服器的[your port] port上

```
ssh [your name]:[server ip] -p [your port]
```
