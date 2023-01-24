# AzureIaaSVMWin2016SQL2016FCI

안녕하세요…

저는 이제 거의 60대를 달려가는 이동철 이라는 사람입니다.
예전 한참 테크넷 블로그(https://learn.microsoft.com/ko-kr/archive/blogs/dongclee/)에 Microsoft 기술을 스크린샷 위주의 step by step 가이드로 저의 얕은 지식을 공유한 적이 있었습니다.
모니터를 1시간 이상 쳐다보기에도 힘든 육체적 나이지만, 최근 몇 가지 프로젝트를 수행하면서, Azure IaaS VM 기반의 Microsoft SQL Server High Availability 를 구현하게 되었습니다. 이에 혹시나 도움이 될까해서 github 에 제 문서를 공유해 보고자 합니다.
대단한 개발자들의 코드가 공유되는 플랫폼에 너무 쉬운 그림책을 공유하는게 맞나 싶어서, 포스팅을 고민하였지만, 혹시나 제 문서가 도움이 될 수도 있는 분이 있을까 해서 공유합니다.
문서가 주로 스크린샷 위주이므로, 부족한 설명은 제 문서의 참조자료에 있는 URL을 참조하셨으면 합니다.

Microsoft SQL Server의 High Availability 구현 방법은 크게 Failover Cluster Instance (이하 FCI) 와 AlwaysOn 2가지가 있습니다.
제가 Azure Shared Disk를 사용하는 IaaS VM 기반의 SQL Server FCI 를 구현하는 방법을 step by step 가이드로 만들어 보았습니다. FCI를 구현하기 위한 Azure Storage Option 은 크게 아래와 같이 3가지 정도로 구분될 수 있습니다. 제 문서는 Azure Shared Disk 기반으로 작성되어 있습니다. FCI를 구현할 때 Azure Storage Option의 선택은 고객의 상황에 따라 달라질 것입니다. Azure Storage Option 은 아래 링크를 참조하셨으면 합니다.

https://learn.microsoft.com/en-us/azure/azure-sql/virtual-machines/windows/failover-cluster-instance-overview?view=azuresql#storage

<img width="434" alt="image" src="https://user-images.githubusercontent.com/42400574/214303908-c9ae4b26-92fe-4204-8810-592d3be1f2ba.png">

또한, Azure IaaS VM 기반의 SQL Server FCI를 생성할 때, Window Server 버전 별로 Azure Load Balancer가 필요할 수도 있고, 필요 없을 수도 있습니다.

ALB 사용 여부도 고객사의 상황에 맞게 고려되어져야 합니다.

<img width="455" alt="image" src="https://user-images.githubusercontent.com/42400574/214304098-0048e2ed-e565-48c8-b44c-3b41421c953a.png">

본 문서는 아래와 같은 데모 환경으로 구성되어 있습니다.

	OS : Windows Server 2016 Datacenter

	SQL : SQL Server 2016 Enterprise with SP2

	FCI Network Name : Virtual Network Name

	ALB : 사용

실제 간략한 구성도는 아래와 같습니다.

 ![image](https://user-images.githubusercontent.com/42400574/214303597-1ff7ad8f-8920-454a-aab1-ea52577bd460.png)


추후, ALB를 사용하지 않는 Windows Server 2019 & SQL Server 2019 & AlwaysOn & Distributed Network Name 조합의 step by step 가이드를 만들어 볼 예정입니다.

감사합니다.
[MigrationSQLTest.pdf](https://github.com/dongclee/AzureIaaSVMWin2016SQL2016FCI/files/10490319/MigrationSQLTest.pdf)
