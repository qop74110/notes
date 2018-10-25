# centOS使用yuman安装node、npm

### 1

```
curl --silent --location https://rpm.nodesource.com/setup_8.x | sudo bash -

// 或者

curl --silent --location https://rpm.nodesource.com/setup_10.x | sudo bash -
```

### 2
```
sudo yum -y install nodejs
```

> 可选：： 安装构建工具
```
sudo yum install gcc-c++ make
# or: sudo yum groupinstall 'Development Tools'
```