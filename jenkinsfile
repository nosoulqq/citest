node("docker-node-1") {
	stage 'Checkout'
		git url: "https://github.com/nosoulqq/citest.git"
        stage 'build'
                check scm
	        sh "docker info"
		sh "docker build -t nginx-lj01:${BUILD_NUMBER} ."
		sh "docker tag nginx-lj01:${BUILD_NUMBER} cnwbzp1187.cn.dst.ibm.com/library/nginx-lj01:${BUILD_NUMBER}"
		sh "docker images"
		sh "docker login -u admin -p Harbor12345 cnwbzp1187.cn.dst.ibm.com"
		sh "docker push cnwbzp1187.cn.dst.ibm.com/library/nginx-lj01:${BUILD_NUMBER}"
}
