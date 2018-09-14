---
title: İzlenecek yollar ve teknik başlangıca genel bakış
description: Azure Bulutu ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | İzlenecek yollar ve teknik başlangıca genel bakış
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 41fbeb3abc201ef03cf0c237a069e7687c98dd18
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519792"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>İzlenecek yollar ve teknik başlangıca genel bakış

Bu e-kitabı boyutunu sınırlamak için ek teknik belgeler ve tam yönergeler bir GitHub deposunda kullanılabilir yapıldı. Bu bölümde açıklanan yönergeler çevrimiçi bir dizi adım adım kurulumu Windows kapsayıcıları ve Azure'a dağıtılacak temel alan birden çok ortamın kapsar.

Aşağıdaki bölümlerde hangi her izlenecek yol, hedefler ve üst düzey işleme hakkında ve söz konusu olan görevler bir diyagramını sunar açıklamaktadır. İzlenecek alabilirsiniz, *eShopModernizing* uygulamaları GitHub deposu wiki adresindeki [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).

## <a name="technical-walkthrough-list"></a>Teknik kılavuz listesi

Get-started aşağıdaki izlenecek kaldırın ve kapsayıcıları kullanarak shift ve Azure'da birden fazla dağıtım seçeneği kullanılarak ettirin örnek uygulamalar için tutarlı ve kapsamlı teknik rehberlik sağlar.

Her biri aşağıdaki izlenecek yollar github'da kullanılabilir olan yeni örnek eShopLegacy ve eShopModernizing uygulamaları kullanan [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).

- **Elektronik Mağaza eski uygulamaları (modernize etme temel uygulamaları) turu**

- **Windows kapsayıcıları ile mevcut ASP.NET web uygulamalarınızı (WebForms ve MVC) kapsayıcılı hale getirme**

- **Windows kapsayıcıları ile mevcut, WCF hizmetlerinizi (N katmanlı uygulamalar) kapsayıcılı hale getirme**

- **Windows kapsayıcıları tabanlı uygulamanız Azure Vm'lerine dağıtma**

- **Azure Container Service'te Kubernetes için Windows kapsayıcı tabanlı uygulamalarınızı dağıtın**

- **Azure Service Fabric'e Windows kapsayıcıları tabanlı uygulamalarınızı dağıtın**


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>İzlenecek yol: 1: Elektronik Mağaza eski uygulamaları turu

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirlik

Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir:

[eShopModernizing wiki izlenecek yollar](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a>Genel Bakış

Bu kılavuzda, üç örnek eski uygulamaları ilk uygulamasını keşfedebilirsiniz. İlk iki örnek web uygulaması, tek parçalı mimariye sahip ve klasik ASP.NET kullanılarak oluşturulmuş. Bir uygulama üzerinde ASP.NET tabanlı 4.x MVC; İkinci uygulama ASP.NET 4.x Web formları üzerinde temel alır. Sunucu tarafı ve istemci WinForms uygulaması ile oluşan bir 3 katmanlı uygulama üçüncü uygulamadır [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) hizmeti.

Bu uygulamalar kullanılabilir [eShopModernizing GitHub deposunu](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Hedefleri

Bu uygulamalarla ve kod ve yapılandırma hakkında bilgi edinmek için bu kılavuzun ana hedef teknolojidir. Oluşturma ve test amacıyla SQL veritabanı kullanmadan sahte veriler kullanın. böylece, uygulamaları yapılandırabilirsiniz. Bu isteğe bağlı yapılandırma üzerinde bağımlılık ekleme, ayrılmış bir şekilde bağlıdır.

### <a name="scenario-1-aspnet-web-apps"></a>Senaryo 1: ASP.NET Web uygulamaları

Aşağıdaki şekilde, özgün eski ASP.NET web uygulamaları basit bir senaryo gösterilmektedir.

> ![Basit mimari senaryo özgün eski ASP.NET web uygulamaları](./media/image5-1.png)
>

Bir iş etki alanı açısından bakıldığında, her iki uygulama aynı katalog yönetimi özellikleri sunar. Elektronik Mağaza Kurumsal ekibi üyelerinin, uygulamayı görüntülemek ve ürün kataloğunu düzenlemek için kullanırsınız. 

Sonraki şekilde, ilk uygulama ekran görüntüleri gösterilmektedir.

![ASP.NET MVC ve ASP.NET Web Forms uygulamaları (mevcut/bilinen teknolojileri)](./media/image5-2.png)

Bağımlılıkları ASP.NET 4.x veya önceki sürümleri (ya da Web Forms veya MVC için) anlamına gelir kodu tam olarak ASP.NET Core MVC kullanarak yeniden sürece bu uygulamalar üzerinde .NET Core çalışmadığından. 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Senaryo 2: WCF hizmeti ve WinForms istemci uygulaması (3 katmanlı uygulama)

Aşağıdaki şekilde, özgün 3 katmanlı eski uygulamayı basit bir senaryo gösterilmektedir.

> ![Bir WCF Hizmeti ile özgün eski 3 katmanlı uygulama ve bir WinForms istemci uygulamasının basit mimari senaryosu](./media/image5-1.5.png)
>

### <a name="benefits"></a>Yararları

Bu izlenecek yolda avantajlarını basittir: yalnızca ilk uygulamaları ve kod ile hakkında bilgi edinin.

### <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:

  - [Tur taban ASP.NET MVC ve Web Forms "eski" uygulamaları](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [Temel WCF hizmeti ve WinForms (Katman 3) "eski" uygulama turu](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>İzlenecek yol: 2: Windows kapsayıcıları ile mevcut .NET uygulamalarınızı kapsayıcılı hale getirme

### <a name="overview"></a>Genel Bakış

Windows kapsayıcıları, MVC, Web Forms veya WCF, üretim, geliştirme ve test ortamları için tabanlı olanlar gibi mevcut .NET uygulamalarının dağıtımını iyileştirmek için kullanın.

### <a name="goals"></a>Hedefleri

Bu kılavuzun amacı, size var olan bir .NET Framework uygulamasını kapsayıcılı hale getirmek için birkaç seçenek göstermektir. Şunları yapabilirsiniz:

- Kullanarak uygulamanızı kapsayıcılı hale getirme [Docker için Visual Studio 2017 Araçları](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 veya sonraki sürümler).

- El ile ekleyerek uygulamanızı kapsayıcılı hale getirme bir [Dockerfile](https://docs.docker.com/engine/reference/builder/)ve ardından kullanarak [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).

- Kullanarak uygulamanızı kapsayıcılı hale getirme [Img2Docker](https://github.com/docker/communitytools-image2docker-win) Aracı (Docker açık kaynaklı aracından).

Bu izlenecek yol, Docker yaklaşım için Visual Studio 2017 araçları odaklanır, ancak diğer iki yaklaşım dockerfile'ları kullanarak in regard to oldukça benzerdir.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Senaryo 1: Kapsayıcılı ASP.NET web uygulamaları

Aşağıdaki şekilde, kapsayıcılı Elektronik Mağaza eski web apps uygulamaları için bir senaryo gösterilmektedir.

> ![Basitleştirilmiş bir mimari diyagramını bir geliştirme ortamında ASP.NET uygulamaları kapsayıcıya alınmış](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a>Senaryo 2: Kapsayıcılı WCF Hizmeti

Aşağıdaki şekilde kapsayıcı bir WCF Hizmeti ile bir 3 katmanlı uygulama için bir senaryo gösterilmektedir. 

> ![Basitleştirilmiş bir geliştirme ortamında kapsayıcı WCF hizmeti mimarisi diyagramı](./media/image5-3.5.png)
>

### <a name="benefits"></a>Yararları

Tek parça, uygulamanızın bir kapsayıcıda çalışan avantajları vardır. İlk olarak, uygulama için bir görüntü oluşturun. Bu noktadan itibaren her dağıtımda aynı ortamda çalışır. Her kapsayıcı aynı işletim sistemi sürümünü kullanır, aynı sürümü yüklü bağımlılıkları, aynı .NET framework sürümünü kullanır ve aynı işlemi kullanılarak oluşturulmuş. Temel olarak, bir Docker görüntüsü kullanarak uygulamanızın bağımlılıkları denetleyin. Kapsayıcıları dağıtırken uygulama ile bağımlılıkları seyahat.

Ek bir avantaj, geliştiricilerin uygulama Windows kapsayıcıları tarafından sağlanan tutarlı ortamında çalıştırabilirsiniz ' dir. Yalnızca belirli sürümler ile görünen sorunları hemen bir hazırlık veya üretim ortamında görünmesini yerine anlaþýlmaz. Kapsayıcı uygulamaları çalıştırdığınızda, geliştirme ekibi üyeleri tarafından kullanılan geliştirme ortamlarında farkları daha az önemli.

Kapsayıcılı uygulamaları, ayrıca düzleştiren bir ölçek genişletme eğri vardır. Kapsayıcılı uygulamaları, daha fazla uygulama ve hizmet örnekleri (kapsayıcılarında dayanarak) sahip bir VM veya fiziksel makine normal uygulama dağıtım makine sayısı ile karşılaştırıldığında sağlar. Bu daha yüksek yoğunluklu ve daha az gerekli dönüşür özellikle Kubernetes veya Service Fabric gibi düzenleyicilerle kullandığınızda kaynakları.

İdeal durumda, kapsayıcı uygulama koduna herhangi bir değişiklik yapmadan gerektirmez (C\#). Çoğu senaryoda, Docker dağıtım meta veri dosyaları (dockerfile'ları ve Docker Compose dosyaları) yeterlidir.

### <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:

  - [Nasıl Windows kapsayıcıları ve Docker ile .NET Framework web uygulamaları kapsayıcıya alın](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [Bir WCF hizmeti için Docker desteği ekleme](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>İzlenecek yol: 3: Windows kapsayıcıları tabanlı uygulamanız Azure Vm'lerine dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirlik

Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a>Genel Bakış

Azure'da Windows Server 2016 sanal makine (VM) üzerinde bir Docker konağı için geliştirme/test/hazırlama ortamlarını hızlıca oluşturmasına olanak tanır. Ayrıca, test uzmanı veya iş kullanıcılarının uygulamayı doğrulamak için ortak bir yerde tanır. VM'ler, bir hizmet (Iaas) üretim ortamlarında geçerli alt yapı de olabilir.

### <a name="goals"></a>Hedefleri

Bu kılavuzun amacı, Windows Server 2016 veya sonraki sürümler göre Azure Vm'leri için Windows kapsayıcıları dağıtma sahip birden çok çok\r\nalternatif göstermektir.

### <a name="scenarios"></a>Senaryolar

Çeşitli senaryolar bu kılavuzda ele alınmaktadır.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Senaryo A: Docker altyapısı bağlantısı üzerinden bir geliştirme bilgisayarı'ndan Azure VM'ye Dağıt

![Bir Azure sanal makinesi için bir Docker altyapısının bağlantısı üzerinden bir geliştirme bilgisayarı dağıtan](./media/image5-4.png)

> **Şekil 5-4.** Bir Azure sanal makinesi için bir Docker altyapısının bağlantısı üzerinden bir geliştirme bilgisayarı dağıtan

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Senaryo B: bir Docker kayıt defteri aracılığıyla Azure VM dağıtma

![Bir Docker kayıt defteri aracılığıyla Azure VM dağıtma](./media/image5-5.png)

> **Şekil 5-5.** Bir Docker kayıt defteri aracılığıyla Azure VM dağıtma

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Azure DevOps Hizmetleri'nde senaryo C: dağıtma Azure VM'ye gelen CI/CD işlem hatları

![Azure DevOps Hizmetleri'nde CI/CD işlem hatları bir Azure VM'ye dağıtan](./media/image5-6.png)

> **Şekil 5-6.** Azure DevOps Hizmetleri'nde CI/CD işlem hatları bir Azure VM'ye dağıtan

### <a name="azure-vms-for-windows-containers"></a>Windows kapsayıcıları için Azure sanal makineleri

Windows Server 2016, Windows 10 veya sonraki sürümler üzerinde alan VM'ler Azure Vm'leri için Windows kapsayıcıları, Docker altyapısı ile her ikisini birden ayarlayın. Çoğu durumda, Azure Vm'lerinde Windows Server 2016 kullanılır.

Azure, şu anda adlı bir VM sağlayan **kapsayıcılar ile Windows Server 2016**. Bu VM, Windows Server Core veya Windows Nano sunucu ile yeni Windows Server kapsayıcı özelliğini denemek için kullanabilirsiniz. Kapsayıcı işletim sistemi görüntüleri yüklenir ve sonra VM ile Docker kullanıma hazırdır.

### <a name="benefits"></a>Yararları

Windows kapsayıcıları, Azure'a dağıtırken şirket içi Windows Server 2016 sanal makinelerine dağıtılabilir olsa da, daha kolay bir yolu, kullanıma hazır Windows Server kapsayıcı sanal makinelerini kullanmaya başlama alın. Ayrıca test uzmanlarına ve Azure sanal makine ölçek kümeleri aracılığıyla otomatik ölçeklenebilirlik erişilebilir genel, çevrimiçi bir konuma sahip olursunuz.

### <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>İzlenecek yol: 4: Windows kapsayıcı tabanlı uygulamalarınızı Azure Container Instances'a (ACI) dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirlik

Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir:

[ACI (Azure Container Instances) için uygulama dağıtma](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Genel Bakış

[Azure Container Instances'a (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) kapsayıcılar'ın tek örneklerine dağıtabileceğiniz bir kapsayıcı geliştirme/test/hazırlama ortamına sahip olmak için en hızlı yoludur.

### <a name="goals"></a>Hedefleri

Bu izlenecek yol, Windows kapsayıcıları için Azure Container Instances'a (ACI) ve eShopModernizing uygulamaları ACI nasıl dağıtabileceğiniz dağıtırken ana senaryoları gösterir.

### <a name="scenarios"></a>Senaryolar

Tek veya tüm uygulamaları (MVC uygulaması, WebForms uygulaması veya WCF Hizmeti) dağıtma gibi ACI eShopModernizing uygulamaları dağıtma hakkında daha fazla çeşitleme olabilir. Aşağıda gösterilen aşağıdaki senaryoda, ASP.NET MVC uygulaması yanı sıra bunların her ikisi de dağıtılan SQL Server kapsayıcı kapsayıcıları olarak ACI (Azure Container Instances) görebilirsiniz.

![Bir geliştirme ortamından ACI'ya dağıtma](./media/image5-3.5.6.png)

### <a name="benefits"></a>Yararları

Azure Container Instances, oluşturmak ve sanal makine sağlamak veya daha yüksek düzeyde bir hizmeti benimsemek zorunda kalmadan azure'da Docker kapsayıcıları yönetmek kolaylaştırır. ACI ile doğrudan azure'da bir Windows kapsayıcı dağıtabilir ve (Windows kapsayıcı görüntüsünü hazır bir Docker kayıt defterinde Docker Hub veya Azure Container gibi olması koşuluyla, bir tam etki alanı adı (FQDN) ile İnternet'e birkaç saniye içinde kullanıma sunma Kayıt defteri).

### <a name="considerations"></a>Dikkat Edilecekler

Ya da tam .NET Framework ile Windows kapsayıcıları dağıtma / ASP.NET veya SQL Server ile Azure Container Instances'a (ACI) Docker görüntüsünü olması gerektiğinden (örneğin, bir Windows Server 2016 ile Windows kapsayıcıları) normal bir Docker konağı dağıtma olarak oldukça hızlı değil her seferinde (Docker kayıt defterinden çekilen) indirilir ve kendi docker Konağı (kalıcı olarak çevrimiçi tutmaktan daha ucuz ancak SQL kapsayıcı görüntüsü (15.1 GB) ve ASP.NET kapsayıcı görüntüsü (13.9 GB) boyutunu önemli ölçüde büyük Azure'da Windows kapsayıcılarını VM ile Windows Server 2016) değil, diğer taraftan, üretim dağıtımları için harika bir seçenek olan Kubernetes Azure (AKS/ACS) veya Azure Service Fabric gibi tam bir orchestrator bahsedebilirsiniz.

Ana sonuç, Azure Container Instances kullanılarak bir çok ilgi çekici CI/CD işlem hatları ve geliştirme/Test senaryoları için seçeneğidir.

## <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha derinlemesine GitHub Wiki'de keşfedin: 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>İzlenecek yol: 5: Azure Container Service'te Kubernetes için Windows kapsayıcı tabanlı uygulamalarınızı dağıtın.

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirlik

Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a>Genel Bakış

Windows kapsayıcılarında alan bir uygulamayı hızla platformlar Iaas sanal makinelerinden hemen daha da ileri taşıma, kullanmanız gerekir. Bu kolayca yüksek ölçeklenebilirlik elde etmek için gereklidir ve daha iyi ölçeklenebilirlik otomatik ve dağıtımları ve sürüm oluşturma için önemli bir iyileştirme otomatik. Orchestrator'ı kullanarak bu hedeflere ulaşabilirsiniz [Kubernetes](https://kubernetes.io/)sunulan [Azure Container Services](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Hedefleri

Kubernetes için Windows kapsayıcı tabanlı bir uygulama dağıtma hakkında bilgi edinmek için bu kılavuzun amacı olan (olarak da adlandırılan *K8s*) Azure Container Service. Kubernetes için sıfırdan dağıtma iki adımlı bir işlemdir:

1.  Azure Container Service'te bir Kubernetes kümesi dağıtın.

2.  Uygulama ve ilgili kaynakları Kubernetes kümesine dağıtın.

### <a name="scenarios"></a>Senaryolar

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Senaryo A: bir geliştirme ortamından bir Kubernetes kümesi için doğrudan Dağıt

![Bir geliştirme ortamından doğrudan bir Kubernetes kümesi dağıtma](./media/image5-7.png)

> **Şekil 5-7.** Bir geliştirme ortamından doğrudan bir Kubernetes kümesi dağıtma

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Azure DevOps Hizmetleri'nde senaryo B: dağıtma bir Kubernetes kümesine gelen CI/CD işlem hatları

![Azure DevOps Hizmetleri'nde CI/CD işlem hatları gelen bir Kubernetes kümesine dağıtın](./media/image5-8.png)

> **Şekil 5-8.** Azure DevOps Hizmetleri'nde CI/CD işlem hatları gelen bir Kubernetes kümesine dağıtın

### <a name="benefits"></a>Yararları

Bir Kubernetes kümesine dağıtmak için birçok faydası vardır. En büyük avantaj (var olan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısını düğümler ve sanal makineleri küme (temel kapsayıcı örneği sayısını göre uygulamanın içinde ölçeklendirebilirsiniz üretime hazır bir ortamın alma olduğu Genel ölçeklenebilirlik kümenin).

Azure Container Service, popüler açık kaynak Araçlar ve teknolojiler için özellikle Azure iyileştirir. Hem kapsayıcılarınız için hem de uygulama yapılandırmanız için taşınabilirlik sunan bir açık çözümü sahip olursunuz. Boyutu, konak sayısını seçin ve diğer her şey orchestrator araçları-kapsayıcı hizmeti işler.

Kubernetes ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmeye gelen Diğerlerinin yanında aşağıdaki özellikleri kolaylaştıran bir kapsayıcı merkezli Altyapı planlama ilerleme:

- Birden çok kapsayıcılara göre uygulamalar

- Container Instances ve yatay ölçeklendirme çoğaltılıyor

- Adlandırma ve (örneğin, iç DNS) bulma

- Yükünü dengeleme

- Güncelleştirmeleri alma

- Gizli dizileri dağıtma

- Uygulama sistem durumu denetimleri

## <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha derinlemesine GitHub Wiki'de keşfedin: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a>İzlenecek yol: 6: Azure Service Fabric'e Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirlik

Tam Teknik Gözden geçirme eShopModernizing GitHub deposuna wikide kullanılabilir:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a>Genel Bakış

Windows kapsayıcılarında kolayca tabanlı bir uygulama platformları, Iaas sanal makinelerinden hemen daha da ileri taşıma kullanılmalıdır. Bu kolayca yüksek ölçeklenebilirlik elde etmek için gereklidir ve daha iyi ölçeklenebilirlik otomatik ve dağıtımları ve sürüm oluşturma için önemli bir iyileştirme otomatik. Azure bulut ortamında kullanılabilir, ancak şirket içinde de kullanılabilir olan, Azure Service Fabric, orchestrator'ı kullanarak veya hatta farklı bir genel bulut bu hedeflere elde edebilirsiniz.

### <a name="goals"></a>Hedefleri

Windows kapsayıcı tabanlı bir uygulamayı azure'da bir Service Fabric kümesine dağıtma hakkında bilgi edinmek için bu kılavuzun amacı olan. Sıfırdan Service Fabric'e dağıtma iki adımlı bir işlemdir:

1.  Service Fabric kümesi, Azure (veya farklı bir ortam) dağıtın.

2.  Uygulama ve ilgili kaynakları, Service Fabric kümesine dağıtın.

### <a name="scenarios"></a>Senaryolar

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a>Senaryo A: bir geliştirme ortamından bir Service Fabric kümesine doğrudan Dağıt

![Bir geliştirme ortamından doğrudan bir Service Fabric kümesine dağıtma](./media/image5-9.png)

> **Şekil 5-9.** Bir geliştirme ortamından doğrudan bir Service Fabric kümesine dağıtma

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Senaryo B: dağıtma bir Service Fabric kümesine CI/CD gelen Azure DevOps Hizmetleri'nde işlem hatları

![Bir Service Fabric kümesine CI/CD işlem hatları Azure DevOps Hizmetleri'nde dağıtan](./media/image5-10.png)

> **Şekil 5-10.** Bir Service Fabric kümesine CI/CD işlem hatları Azure DevOps Hizmetleri'nde dağıtan

## <a name="benefits"></a>Yararları

Bir Service Fabric kümesine dağıtma avantajları, Kubernetes kullanmanın avantajları için benzerdir. Tek fark, yine de olan Service Fabric Windows uygulamaları, beta aşamasında Kubernetes sürümü 1.9 Windows kapsayıcıları için Kubernetes ile karşılaştırıldığında daha olgun bir üretim ortamında olduğunu (aralık 2017). Kubernetes Linux fazla olgun bir ortamdır.

Azure Service Fabric kullanmanın ana Avantajı (var olan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısına göre kapsayıcı örneği sayısını göre uygulamanın içinde ölçeklendirebilirsiniz üretime hazır bir ortamın alma olduğu düğümleri veya Vm'leri kümede (genel ölçeklenebilirlik kümenin).

Azure Service Fabric, kapsayıcılar için hem de uygulama yapılandırmanız için taşınabilirlik sunar. Azure'da küme ya da şirket içindeki kendi veri merkezinizde yüklemeyi Service Fabric olabilir. Hatta bir Service Fabric kümesi farklı bir buluta gibi yükleyebilirsiniz [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).

Service Fabric sayesinde geliştiriciler fiziksel ve sanal makineler hakkında düşünmeye gelen Diğerlerinin yanında aşağıdaki özellikleri kolaylaştıran bir kapsayıcı merkezli Altyapı planlama ilerleme:

- Birden çok kapsayıcılara göre uygulamaları.

- Container Instances ve yatay ölçeklendirme çoğaltılıyor.

- Adlandırma ve (örneğin, iç DNS) bulunuyor.

- Yükü Dengeleme.

- Güncelleştirmeleri alınıyor.

- Gizli dizileri dağıtma.

- Uygulama durumunu denetler.

Aşağıdaki özellikleri (diğer düzenleyiciler için karşılaştırıldığında) Service fabric'te özel şunlardır:

- Reliable Services uygulaması modeliyle durum bilgisi olan hizmetler yeteneği.

- Reliable Actors uygulama modeli aracılığıyla aktörler deseni.

- Çıplak bone süreçlerinin, Windows veya Linux kapsayıcıları dağıtın.

- Gelişmiş sıralı güncelleştirme ve sistem durumu denetimleri.

### <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha derinlemesine GitHub Wiki'de keşfedin:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
[Önceki](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[İleri](conclusions.md)
