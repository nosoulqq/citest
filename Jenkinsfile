node("docker-node-1") {
	stage 'Checkout'
		git url: "https://github.com/nosoulqq/citest.git"
        stage 'build'
	        checkout scm
		sh "docker info"
		sh "docker build -t nginx-lj:${BUILD_NUMBER} ."
        stage 'Tag&push'
		sh "docker tag nginx-lj:${BUILD_NUMBER} cnwbzp1187.cn.dst.ibm.com/library/nginx-lj:${BUILD_NUMBER}"
		sh "docker images"
		sh "docker login -u admin -p Harbor12345 cnwbzp1187.cn.dst.ibm.com"
		sh "docker push cnwbzp1187.cn.dst.ibm.com/library/nginx-lj:${BUILD_NUMBER}"
	stage 'delopy'
                sh "docker run --name nginx-lj -d -p 8085:80 nginx-lj:${BUILD_NUMBER}"
                sh "docker rm -f `docker ps -a |grep 'nginx-lj' |awk '{print \$1}'`"
		sh "docker run --name nginx-lj -d -p 8084:80 cnwbzp1187.cn.dst.ibm.com/library/nginx-lj:${BUILD_NUMBER}"
}
