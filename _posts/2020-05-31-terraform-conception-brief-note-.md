---
title: "[Terraform] 기본 개념 간략한 정리"
layout: post
date: '2020-05-31 18:47:00 +0000'
categories:
- Blog
tags:
- devops
- terraform
---

해당 페이지에 기재된 내용이 어느 블로그 내용에서 나온거 같다면 알려주세용.

제가 공부할 때 노트에 적고 묵히고 묵혀두다가 블로그에 정리하는 편이라

~~출처가 어딘지 자세히 기억이 나지 않을 때가..~~



1. 기본개념 정리

- Providers: 테라폼으로 정의할 인프라 제공자를 의미한다.

- Resource : 실제로 생성할 인프라 자원을 의미한다.

- Output: 인프라를 provision한 후, 생성된 자원의 특정 값을 output으로 출력 지정 가능하다.

- Backend: Terraform의 상태를 저장할 공간을 지정할 수 있다.

	 ( * BeNX는 S3를 기본적으로 사용 - 송주영님의 온라인  meetup에서 - )

- Module: 공통적으로 활용할 수 있는 인프라 코드를 한 곳으로 모아 정의.  module 사용시, 변수만 바꾸어 동일한 리소스를 쉽게 생성이 가능하다.

- Remote state: VPC, IAM과 같이 여러 서비스가 공통적으로 사용중인 리소스들을 공유하여 provisioning이 가능하다. tfstate파일이 저장되어 있는 backend 정보를 명시하면, terraform이 해당 backend에서   output 정보들을 가져온다.

2. Terraform 실행 순서

- IAM에서 aws-cli 실행가능한 권한이 주어진 사용자 생성해야 한다.

- terraform init: 해당 디렉토리에서 terraform initialization하면 terraform은 프로젝트에 적합한 providers plugin을 설치한다.

- terraform plan: .tf 파일에 명시된 리소스 추가 및 변경사항 프로세스 리뷰가능하다.

- terraform apply: 실제 리소스들을 생성하는 과정으로 실제 배포환경과 비교된 변경내용을 반영한다

  변경된 내용은 state파일에 작성되며, apply 실행 전에 실행계획을 보여준다.

	이 때 출력형식은 git diff와 같이 +, -로 추가/수정 및 삭제 여부를 확인할 수 있다.

-  terraform show: 해당 프로젝트에서 관리중인 provisioned 인프라 상태를 확인할 수 있다.



다음글에서는 tfstate파일이 무엇인지, 어떻게 관리를 해야하는지 알아보자
