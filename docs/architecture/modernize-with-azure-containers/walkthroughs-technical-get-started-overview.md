---
title: İzlenecek yollar ve teknik başlangıca genel bakış
description: Azure bulut ve Windows kapsayıcıları Ile mevcut .NET uygulamalarını modernleştirin | İzlenecek yollar ve teknik Başlarken Genel Bakış
ms.date: 04/28/2018
ms.openlocfilehash: 98d33b13d2b28bfe1c35894df45e525cff0520c1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172150"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>İzlenecek yollar ve teknik başlangıca genel bakış

Bu e-kitabın boyutunu sınırlamak için, ek teknik belgeler ve bir GitHub deposunda sunulan tam izlenecek yollar. Bu bölümde açıklanan çevrimiçi izlenecek yollar serisi, Windows kapsayıcılarına dayalı birden çok ortamın adım adım kurulumunu ve Azure 'a dağıtımını ele almaktadır.

Aşağıdaki bölümlerde her bir izlenecek yolun ne olduğu, amaçları ve üst düzey Vizyonumuz açıklanmakta ve dahil olan görevlerin bir diyagramı sağlanmıştır. İzlenecek *yolları, ' de bulunan uygulama GitHub* deposu wiki ' de yer alır <https://github.com/dotnet-architecture/eShopModernizing/wiki> .

## <a name="technical-walkthrough-list"></a>Teknik izlenecek yol listesi

Aşağıdaki Başlarken izlenecek yollar, kapsayıcıları kullanarak kaldırıp kaydıracağınız örnek uygulamalar için tutarlı ve kapsamlı teknik rehberlik sağlar ve ardından Azure 'da birden çok dağıtım seçeneği kullanarak hareket edebilir.

Aşağıdaki izlenecek yolların her biri, GitHub 'da bulunan yeni örnek eShopLegacy ve Eshopmodernize uygulamalarını kullanır <https://github.com/dotnet-architecture/eShopModernizing> .

- **EShop eski uygulamalar turu (temel uygulamalar modernleştirin)**

- **Mevcut ASP.NET Web uygulamalarınızı (WebForms & MVC) Windows kapsayıcılarıyla kapsayıcıyla**

- **Mevcut WCF hizmetlerinizi (N katmanlı uygulamalar) Windows kapsayıcılarıyla Kapsayıçleştirme**

- **Windows kapsayıcıları tabanlı uygulamanızı Azure VM 'lerine dağıtma**

- **Windows kapsayıcıları tabanlı uygulamalarınızı Azure Container Service 'de Kubernetes 'e dağıtma**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>İzlenecek yol 1: eShop eski uygulamalar turu

### <a name="technical-walkthrough-availability"></a>Teknik izlenecek yol kullanılabilirliği

Tam teknik izlenecek yol, GitHub deposu wiki ' de kullanılabilir:

[wiki gözden geçirmeleri için Eshopmodernize](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Genel Bakış

Bu kılavuzda, üç örnek eski uygulamanın ilk uygulamasını inceleyebilirsiniz. İlk iki örnek Web uygulaması tek parçalı bir mimariye sahiptir ve klasik ASP.NET kullanılarak oluşturulmuştur. Bir uygulama ASP.NET 4. x MVC 'yi temel alır. ikinci uygulama, ASP.NET 4. x Web Forms temel alır.
Üçüncü uygulama, bir istemci WinForms uygulaması ve sunucu tarafı [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) hizmeti tarafından oluşturulan 3 katmanlı bir uygulamadır.

Tüm bu uygulamalar [GitHub](https://github.com/dotnet-architecture/eShopModernizing)deposunda mevcuttur.

### <a name="goals"></a>Hedefler

Bu izlenecek yolun ana amacı, bu uygulamaları ve bunların kod ve yapılandırmasıyla ilgili bilgi almak için yeterlidir. Uygulamaları, test amacıyla SQL veritabanını kullanmadan, sahte verileri oluşturup kullanacak şekilde yapılandırabilirsiniz. Bu isteğe bağlı yapılandırma, bağımlılık ekleme işlemini ayrılmış bir şekilde temel alır.

### <a name="scenario-1-aspnet-web-apps"></a>Senaryo 1: ASP.NET Web Apps

Aşağıdaki şekilde, özgün eski ASP.NET Web uygulamalarının basit senaryosu gösterilmektedir.

![Özgün eski ASP.NET Web uygulamalarının basit mimari senaryosu](./media/image5-1.png)

Bir iş etki alanı perspektifinden, her iki uygulama da aynı katalog yönetimi özelliklerini sunmaktadır. EShop Enterprise ekibinin üyeleri, ürün kataloğunu görüntülemek ve düzenlemek için uygulamayı kullanır.

Sonraki şekilde, ilk uygulama ekran görüntüleri gösterilmektedir.

![ASP.NET MVC ve ASP.NET Web Forms uygulamaları (mevcut/eski teknolojiler)](./media/image5-2.png)

ASP.NET 4. x veya önceki sürümlerindeki bağımlılıklar (MVC veya Web Forms için), kodun ASP.NET Core MVC kullanılarak tam olarak yeniden yazılması durumunda .NET Core üzerinde çalıştırılmayacağı anlamına gelir.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Senaryo 2: WCF hizmeti ve WinForms istemci uygulaması (3 katmanlı uygulama)

Aşağıdaki şekilde, özgün 3 katmanlı eski uygulamanın basit senaryosu gösterilmektedir.

![Bir WCF hizmeti ve bir WinForms istemci uygulaması ile, eski, 3 katmanlı ilk uygulamanın basit mimari senaryosu](./media/image5-1.5.png)

### <a name="benefits"></a>Yararları

Bu izlenecek yolun avantajları basittir: yalnızca kod ve ilk uygulamalar hakkında bilgi edinin.

### <a name="next-steps"></a>Sonraki adımlar

GitHub wiki üzerinde bu içeriği daha ayrıntılı bir şekilde gezin:

- [Temel ASP.NET MVC ve "eski" uygulamalar Web Forms turuna katılın](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Taban çizgisi WCF hizmeti ve WinForms (3 katmanlı) "eski" uygulama turu](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>İzlenecek yol 2: mevcut .NET uygulamalarınızı Windows kapsayıcılarıyla Kapsayıyleştirme

### <a name="overview"></a>Genel Bakış

MVC, Web Forms veya WCF tabanlı uygulamalar, üretim, geliştirme ve test ortamları gibi mevcut .NET uygulamalarının dağıtımını geliştirmek için Windows kapsayıcıları kullanın.

### <a name="goals"></a>Hedefler

Bu izlenecek yolun amacı, mevcut bir .NET Framework uygulamasını kapsayıdırma için size çeşitli seçenekler göstermektir. Seçenekleriniz şunlardır:

- [Visual studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (visual Studio 2017 veya üzeri sürümler) kullanarak uygulamanızı kapsayıkatın.

- El ile bir [Dockerfile](https://docs.docker.com/engine/reference/builder/)ekleyerek ve sonra [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/)kullanarak uygulamanızı kapsayıcın.

- [Img2Docker](https://github.com/docker/communitytools-image2docker-win) aracını kullanarak (Docker 'daki açık kaynaklı bir araç) uygulamanızı kapsayıkatın.

Bu izlenecek yol, Docker yaklaşımına yönelik Visual Studio 2017 araçlarına odaklanır, ancak diğer iki yaklaşım Dockerfiles kullanımına benzer şekilde oldukça benzerdir.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Senaryo 1: Kapsayıcılı ASP.NET Web uygulamaları

Aşağıdaki şekilde Kapsayıcılı, eski Web Apps uygulamalarına yönelik senaryo gösterilmektedir.

![Geliştirme ortamında Kapsayıcılı ASP.NET uygulamalarının Basitleştirilmiş mimari diyagramı](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Senaryo 2: Kapsayıcılı WCF hizmeti

Aşağıdaki şekilde kapsayıcılı bir WCF hizmeti olan 3 katmanlı bir uygulamanın senaryosu gösterilmektedir.

![Bir geliştirme ortamında Kapsayıcılı WCF hizmetinin Basitleştirilmiş mimari diyagramı](./media/image5-3.5.png)

### <a name="benefits"></a>Yararları

Tek parçalı uygulamanızı bir kapsayıcıda çalıştırmanın avantajları vardır. İlk olarak, uygulama için bir görüntü oluşturursunuz. Bu noktadan itibaren, her dağıtım aynı ortamda çalışır. Her kapsayıcı aynı işletim sistemi sürümünü kullanır, aynı bağımlılıklar sürümü yüklü, aynı .NET Framework sürümünü kullanır ve aynı işlem kullanılarak oluşturulmuştur. Temel olarak, bir Docker görüntüsü kullanarak uygulamanızın bağımlılıklarını kontrol edersiniz. Kapsayıcılar, kapsayıcıları dağıtırken uygulamayla birlikte seyahat ediyor.

Ek bir avantaj, geliştiricilerin uygulamayı Windows kapsayıcıları tarafından sunulan tutarlı bir ortamda çalıştırabildiği bir avantajdır. Yalnızca belirli sürümlerle görüntülenen sorunlar, hazırlama veya üretim ortamında kullanıma sunulacak şekilde hemen bağlanabilir. Geliştirme ortamlarının üyeleri tarafından kullanılan geliştirme ortamlarındaki farklar, uygulamalar kapsayıcılar içinde çalıştırıldığında daha az önemlidir.

Kapsayıcılı uygulamalar için de eğri ölçeği genişletme eğrisi vardır. Kapsayıcılı uygulamalar, makine başına normal uygulama dağıtımlarıyla karşılaştırıldığında bir VM 'de veya fiziksel makinede daha fazla uygulama ve hizmet örneği (kapsayıcılara göre) sağlar. Bu, özellikle Kubernetes gibi düzenleyiciler kullandığınızda daha yüksek yoğunluklu ve daha az gereken kaynağa çevrilir.

Kapsayıcılama, ideal durumlarda uygulama kodunda herhangi bir değişiklik yapılmasını gerektirmez (C \# ). Çoğu senaryoda yalnızca Docker dağıtım meta verileri dosyalarına (Dockerfiles ve Docker Compose dosyaları) ihtiyacınız vardır.

### <a name="next-steps"></a>Sonraki adımlar

GitHub wiki üzerinde bu içeriği daha ayrıntılı bir şekilde gezin:

- [Windows kapsayıcıları ve Docker ile .NET Framework Web uygulamalarını kapsayıcıyla](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [WCF hizmetine Docker desteği ekleme](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>İzlenecek yol 3: Windows kapsayıcıları tabanlı uygulamanızı Azure VM 'lerine dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik izlenecek yol kullanılabilirliği

Tam teknik izlenecek yol, GitHub deposu wiki ' de kullanılabilir: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Genel Bakış

Azure 'da bir Windows Server 2016 sanal makinesi (VM) üzerindeki bir Docker konağına dağıtım, geliştirme/test/hazırlık ortamlarını hızla ayarlamanıza olanak sağlar. Ayrıca, Sınayıcılar veya iş kullanıcılarının uygulamayı doğrulaması için ortak bir yer sağlar. VM 'Ler ayrıca geçerli bir hizmet olarak altyapı (IaaS) üretim ortamları olabilir.

### <a name="goals"></a>Hedefler

Bu izlenecek yolun amacı, Windows Server 2016 veya sonraki sürümlerini temel alan Azure VM 'lerine Windows kapsayıcıları dağıtırken size sahip olduğunuz birden çok alternatifi göstermektir.

### <a name="scenarios"></a>Senaryolar

Bu izlenecek yolda çeşitli senaryolar ele alınmıştır.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Senaryo A: Azure VM 'ye Docker altyapısı bağlantısı aracılığıyla bir geliştirme PC 'den dağıtma

![Bir Azure sanal makinesine Docker altyapısı bağlantısı aracılığıyla bir geliştirme BILGISAYARDAN dağıtma](./media/image5-4.png)

**Şekil 5-4.** Bir Azure sanal makinesine Docker altyapısı bağlantısı aracılığıyla bir geliştirme BILGISAYARDAN dağıtma

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Senaryo B: bir Docker kayıt defteri aracılığıyla bir Azure VM 'ye dağıtma

![Docker kayıt defteri aracılığıyla bir Azure VM 'ye dağıtma](./media/image5-5.png)

**Şekil 5-5.** Docker kayıt defteri aracılığıyla bir Azure VM 'ye dağıtma

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Senaryo C: Azure DevOps Services içindeki CI/CD işlem hatlarından bir Azure VM 'sine dağıtım

![Azure DevOps Services ' deki CI/CD işlem hatlarından bir Azure VM 'sine dağıtım](./media/image5-6.png)

**Şekil 5-6.** Azure DevOps Services ' deki CI/CD işlem hatlarından bir Azure VM 'sine dağıtım

### <a name="azure-vms-for-windows-containers"></a>Windows kapsayıcıları için Azure VM 'Leri

Windows kapsayıcıları için Azure VM 'Leri, hem Docker Engine 'in ayarlandığı Windows Server 2016, Windows 10 veya sonraki sürümleri temel alır. Çoğu durumda, Azure VM 'lerinde Windows Server 2016 kullanılır.

Azure Şu anda **kapsayıcılarla Windows Server 2016**ADLı bir VM sağlıyor. Windows Server Core veya Windows nano Server ile yeni Windows Server kapsayıcısı özelliğini denemek için bu VM 'yi kullanabilirsiniz. Kapsayıcı işletim sistemi görüntüleri yüklenir ve ardından sanal makine Docker ile kullanıma hazırdır.

### <a name="benefits"></a>Yararları

Windows kapsayıcıları, şirket içi Windows Server 2016 VM 'lerine dağıtılabilse de, Azure 'a dağıtırken, kullanıma hazırlama öncesi Windows Server kapsayıcısı VM 'Leri ile kullanmaya başlamak için daha kolay bir yol alırsınız. Ayrıca, Test edicilerin erişebileceği ve Azure sanal makine ölçek kümeleri aracılığıyla otomatik ölçeklenebilirlik sağlayan ortak bir çevrimiçi konum alırsınız.

### <a name="next-steps"></a>Sonraki adımlar

GitHub wiki üzerinde bu içeriği daha ayrıntılı bir şekilde gezin:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Adım 4: Windows kapsayıcıları tabanlı uygulamalarınızı Azure Container Instances (ACI) uygulamasına dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik izlenecek yol kullanılabilirliği

Tam teknik izlenecek yol, GitHub deposu wiki ' de kullanılabilir:

[Uygulamaları ACI 'ye dağıtma (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Genel Bakış

[Azure Container Instances (ACI)](/azure/container-instances/) , kapsayıcılar geliştirme/test/hazırlama ortamının tek tek örneklerini dağıtabileceğiniz en hızlı yoldur.

### <a name="goals"></a>Hedefler

Bu izlenecek yol, Windows kapsayıcılarını Azure Container Instances (ACI) ile dağıtırken ve ACI 'de Eshopmodernize uygulamaları nasıl dağıtabileceğiniz ana senaryoları gösterir.

### <a name="scenarios"></a>Senaryolar

Uygulamaların yalnızca birini veya tümünü (MVC uygulaması, WebForms uygulaması veya WCF hizmeti) dağıtmak gibi, Eshopmodernize uygulamalarını dağıtmaya yönelik Çeşitlemeler bulunabilir. Aşağıda gösterilen aşağıdaki senaryoda, ASP.NET MVC uygulamasını ve her ikisi de bir kapsayıcı olarak dağıtılan SQL Server kapsayıcısını ACI 'ye (Azure Container Instances) görebilirsiniz.

![Geliştirme ortamından acı 'ye dağıtma](./media/image5-3.5.6.png)

### <a name="benefits"></a>Yararları

Azure Container Instances, sanal makine sağlamak veya daha yüksek düzey bir hizmet benimsemek zorunda kalmadan Azure’da Docker kapsayıcıları oluşturmayı ve yönetmeyi kolaylaştırır. ACI ile, bir Windows kapsayıcısını doğrudan Azure 'da dağıtabilir ve saniyeler içinde tam etki alanı adı (FQDN) ile internet 'te kullanıma sunabilirsiniz (Windows kapsayıcı görüntünüzü Docker Hub veya Azure Container Registry gibi bir Docker kayıt defterine hazırlayın).

### <a name="considerations"></a>Dikkat edilmesi gerekenler

Windows kapsayıcılarını tam .NET Framework/ASP.NET veya SQL Server ile Azure Container Instances (ACI) ile dağıtmak, Docker görüntüsünün her seferinde ve SQL Container Image 'ın boyutlarını (Docker kayıt defteri 'nden çekildiğinden), düzenli bir Docker ana bilgisayarına (Windows kapsayıcıları ile Windows Server 2016 gibi) dağıtım kadar hızlı değildir. (15,1 GB) ve ASP.NET kapsayıcı görüntüsü (13,9 GB) önemli ölçüde büyüktür, ancak Azure 'da (AKS) bulunan Kubernetes gibi bir düzenleyicinin tamamını değil, kendi Docker ana bilgisayarınızı (Azure 'daki Windows kapsayıcıları sanal makinesi ile kalıcı olarak çevrimiçi Windows Server 2016) kullanmaktan çok daha ucuz. öte yandan, üretim dağıtımları için harika bir seçimdir.

Ana sonuç olarak, Azure Container Instances kullanımı geliştirme/test senaryoları ve CI/CD işlem hatları için çok etkileyici bir seçenektir.

### <a name="next-steps"></a>Sonraki adımlar

GitHub wiki üzerinde bu içeriği daha ayrıntılı bir şekilde gezin:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>İzlenecek yol 5: Windows kapsayıcıları tabanlı uygulamalarınızı Azure Container Service Kubernetes 'e dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik izlenecek yol kullanılabilirliği

Tam teknik izlenecek yol, GitHub deposu wiki ' de kullanılabilir:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>Genel Bakış

Windows kapsayıcılarına dayalı bir uygulamanın, IaaS VM 'lerinden daha da fazla hareket eden platformları kullanması hızla gerekecektir. Bu, kolayca yüksek ölçeklenebilirlik ve daha iyi otomatik ölçeklenebilirlik elde etmek ve otomatikleştirilmiş dağıtımlar ve sürüm oluşturma konusunda önemli bir geliştirme sağlamak için gereklidir. [Azure Container Services](https://azure.microsoft.com/services/container-service/)'de bulunan Orchestrator [Kubernetes](https://kubernetes.io/)'i kullanarak bu hedeflere ulaşabilirsiniz.

### <a name="goals"></a>Hedefler

Bu izlenecek yol, Azure Container Service ' de bir Windows kapsayıcı tabanlı uygulamayı Kubernetes 'e dağıtmayı öğrenmektir ( *K8s*olarak da bilinir). Sıfırdan Kubernetes 'e dağıtım iki adımlı bir işlemdir:

1. Azure Container Service için bir Kubernetes kümesi dağıtın.

2. Uygulamayı ve ilgili kaynakları Kubernetes kümesine dağıtın.

### <a name="scenarios"></a>Senaryolar

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Senaryo A: bir geliştirme ortamından bir Kubernetes kümesine doğrudan dağıtım

![Geliştirme ortamından bir Kubernetes kümesine doğrudan dağıtım](./media/image5-7.png)

**Şekil 5-7.** Geliştirme ortamından bir Kubernetes kümesine doğrudan dağıtım

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Senaryo B: Azure DevOps Services içindeki CI/CD işlem hatlarından bir Kubernetes kümesine dağıtım

![Azure DevOps Services ' deki CI/CD işlem hatlarından bir Kubernetes kümesine dağıtın](./media/image5-8.png)

**Şekil 5-8.** Azure DevOps Services ' deki CI/CD işlem hatlarından bir Kubernetes kümesine dağıtın

### <a name="benefits"></a>Yararları

Kubernetes içindeki bir kümeye dağıtmanın birçok avantajı vardır. En büyük avantaj, kullanmak istediğiniz kapsayıcı örneği sayısına (mevcut düğümlerde iç ölçeklenebilirlik) göre ve kümedeki düğüm veya VM sayısına (kümenin genel ölçeklenebilirliği) göre, uygulamayı ölçeklendirebilmeniz için üretime hazır bir ortam elde edersiniz.

Azure Container Service, popüler açık kaynaklı araçları ve teknolojileri özel olarak Azure için iyileştirir. Kapsayıcılar ve uygulama yapılandırmanız için taşınabilirlik sağlayan açık bir çözüm alırsınız. Boyut, ana bilgisayar sayısı ve Orchestrator Araçları-kapsayıcı hizmeti, diğer her şeyi de gerçekleştirir.

Kubernetes sayesinde, geliştiriciler fiziksel ve sanal makineler hakkında düşünmekten ilerlemeye devam edebilir ve diğer kullanıcıların yanı sıra aşağıdaki özellikleri kolaylaştıran kapsayıcı merkezli bir altyapı planlıyor:

- Birden çok kapsayıcıyı temel alan uygulamalar

- Kapsayıcı örnekleri ve yatay otomatik ölçeklendirmeyi çoğaltma

- Adlandırma ve bulma (örneğin, iç DNS)

- Yük Dengelemesi

- Güncelleştirmeler alınıyor

- Gizli dizileri dağıtma

- Uygulama durumu denetimleri

### <a name="next-steps"></a>Sonraki adımlar

GitHub wiki üzerinde bu içeriği daha ayrıntılı bir şekilde gezin: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>İzlenecek yol 6: Windows kapsayıcıları tabanlı uygulamalarınızı kapsayıcılar için Azure App Service dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik izlenecek yol kullanılabilirliği

Tam teknik izlenecek yol, GitHub deposu wiki ' de kullanılabilir:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>Genel Bakış

Windows kapsayıcıları kullanılarak basit kapsayıcılı bir uygulama, kapsayıcılar için Azure App Service kolayca dağıtılabilir. Bu, Windows kapsayıcı tabanlı çoğu uygulama için önerilen yaklaşımdır.

### <a name="goals"></a>Hedefler

Bu izlenecek yol, bir kayıt defterinden (Docker Hub veya Azure Container Registry) kapsayıcılar için Azure App Service Windows kapsayıcı tabanlı bir uygulamanın nasıl dağıtılacağını öğrenmektir.

### <a name="scenario"></a>Senaryo

![Kapsayıcılar için Windows kapsayıcı tabanlı uygulamayı Azure App Service dağıtma](./media/image5-11.png)

### <a name="benefits"></a>Yararları

Kapsayıcılar için Azure App Service dağıtım, Azure App Service PaaS avantajları ile eşleştirilmiş kapsayıcıların avantajlarını sunmaktadır. App Service kolayca dikey ve yatay olarak ölçeklendirilebilir ve değişen talepleri karşılamak üzere otomatik olarak ölçeklendirilebilen şekilde yapılandırılabilir. Güncelleştirmeler sıfır kapalı kalma süresiyle gerçekleştirilebilir ve bir kayıt defterinden sürekli dağıtımın yapılandırılması de kolay bir şekilde yapılandırılabilir.

### <a name="next-steps"></a>Sonraki adımlar

GitHub wiki üzerinde bu içeriği daha ayrıntılı bir şekilde gezin: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [Önceki](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md) 
>  [Sonraki](conclusions.md) <!-- Next Chapter -->
