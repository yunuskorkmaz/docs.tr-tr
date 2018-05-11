---
title: İzlenecek yollar ve teknik başlatılan özeti
description: Azure Bulut ve Windows kapsayıcıları varolan .NET uygulamaları modernize | İzlenecek yollar ve teknik başlatılan özeti
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 27de9d1c5475855a22f2d8a3518982605277f6d9
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>İzlenecek yollar ve teknik başlatılan özeti

Bu e-kitap boyutunu sınırlamak için ek teknik belgeler ve tam izlenecek yollar GitHub deposunda kullanılabilir yapılmıştır. Bu bölümde açıklanan izlenecek yollar çevrimiçi bir dizi adım adım kurulum Windows kapsayıcıları ve Azure dağıtımına dayalı birden çok ortamlarının kapsar.

Aşağıdaki bölümlerde ne her gözden geçirme, hedefler ve üst düzey görme hakkında ve ilgili olan görevleri diyagramı sağlar açıklanmıştır. İzlenecek yollar kendilerini alabilirsiniz içinde *eShopModernizing* uygulamaları GitHub deposuna wiki adresindeki [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).

## <a name="technical-walkthrough-list"></a>Teknik kılavuz listesi

Aşağıdaki get-started izlenecek kaldırın ve kapsayıcılar kullanarak kaydırma ve Azure içinde birden çok dağıtım seçenekleri kullanarak Taşı örnek uygulamaları için tutarlı ve kapsamlı teknik Kılavuzu sağlamak.

Her biri aşağıdaki izlenecek github'da kullanılabilir olan yeni örnek eShopLegacy ve eShopModernizing uygulamaları kullanır [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).

- **Elektronik Mağaza eski uygulamalara (modernize için temel) turu**

- **Mevcut ASP.NET web uygulamalarınızı (WebForms & MVC) ile Windows kapsayıcıları containerize**

- **Windows kapsayıcılarla mevcut WCF hizmetlerini (N katmanlı uygulamalar) containerize**

- **Azure VM'ler kapsayıcıları tabanlı Windows uygulamanızı dağıtma**

- **Azure kapsayıcı Hizmeti'nde Kubernetes Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma**

- **Azure Service Fabric Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma**


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Gözden geçirme 1: Elektronik Mağaza eski uygulamaları turu

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirliği

Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:

[eShopModernizing wiki izlenecek yollar](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a>Genel Bakış

Bu kılavuzda, üç örnek eski uygulamalar ilk uyarlamasını keşfedebilirsiniz. İlk iki örnek web uygulamaları tek yapılı bir mimariye sahip ve klasik ASP.NET kullanılarak oluşturulmuş. ASP.NET ile tabanlı bir uygulamayı 4.x MVC; İkinci uygulama ASP.NET 4.x Web Forms üzerinde temel alır. İstemci WinForms uygulama ve sunucu tarafı tarafından oluşturulan 3 katmanlı uygulama üçüncü uygulamadır [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) hizmet.

Bu uygulamalar kullanılabilir [eShopModernizing GitHub deposuna](https://github.com/dotnet-architecture/eShopModernizing).

### <a name="goals"></a>Hedefleri

Asıl amacı, bu kılavuzda yalnızca bu uygulamalarla ve kendi kod ve yapılandırma hakkında bilgi edinmek için ' dir. Böylece oluşturmak ve test amacıyla SQL veritabanı kullanmadan sahte veriler kullanmak uygulamaları yapılandırabilirsiniz. Bu isteğe bağlı yapılandırma bağımlılık ekleme, ayrılmış bir biçimde temel alır.

### <a name="scenario-1-aspnet-web-apps"></a>Senaryo 1: ASP.NET Web uygulamaları

Aşağıdaki şekilde özgün eski ASP.NET web uygulamaları basit bir senaryo gösterilmektedir.

> ![Özgün eski ASP.NET web uygulamalarının basit mimarisi senaryosu](./media/image5-1.png)
>

Bir iş etki alanı açısından bakıldığında, hem uygulamalar aynı katalog yönetimi özellikleri sunar. Elektronik Mağaza Kurumsal ekibi üyelerinin uygulamayı görüntülemek ve ürün kataloğu düzenlemek için kullanırsınız. 

Sonraki şekilde, ilk uygulama ekran görüntüleri gösterir.

![ASP.NET MVC ve ASP.NET Web Forms uygulamaları (varolan eski teknolojileri)](./media/image5-2.png)

Bağımlılıklar ASP.NET 4.x veya önceki sürümleri (veya MVC için Web formları için) anlamına gelir kodu tam olarak ASP.NET Core MVC kullanarak yeniden yazılmıştır sürece bu uygulamaları .NET Core üzerinde çalışmaz. 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Senaryo 2: WCF hizmeti ve WinForms istemci uygulaması (3 katmanlı uygulama)

Aşağıdaki şekilde özgün 3 katmanlı eski uygulamayı basit bir senaryo gösterilmektedir.

> ![Bir WCF Hizmeti özgün eski 3 katmanlı uygulama ve bir WinForms istemci uygulaması basit mimarisi senaryosu](./media/image5-1.5.png)
>

### <a name="benefits"></a>Yararları

Bu kılavuzda yararları basit: yalnızca ilk uygulamaları ve kod ile hakkında bilgi edinin.

### <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:

  - [ASP.NET MVC taban tur ve Web Forms "eski" uygulamalar](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [Temel WCF hizmeti ve WinForms (Katman 3) "eski" uygulama turu](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>İzlenecek yol: 2: var olan .NET uygulamalarınız Windows kapsayıcılarla Containerize

### <a name="overview"></a>Genel Bakış

MVC, Web Forms veya WCF, üretim, geliştirme ve test ortamları için temel gelenler varolan .NET uygulamalarının dağıtımını iyileştirmek için Windows kapsayıcıları kullanın.

### <a name="goals"></a>Hedefleri

Bu kılavuzun amacı, var olan bir .NET Framework uygulamasını containerizing için çeşitli seçenekler göstermektir. Şunları yapabilirsiniz:

- Uygulamanızı kullanarak containerize [Docker için Visual Studio 2017 Araçları](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 veya sonraki sürümler).

- El ile ekleyerek uygulamanızı containerize bir [Dockerfile](https://docs.docker.com/engine/reference/builder/)ve ardından kullanarak [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).

- Uygulamanızı kullanarak containerize [Img2Docker](https://github.com/docker/communitytools-image2docker-win) Aracı (Docker açık kaynak aracından).

Bu kılavuz Docker yaklaşım için Visual Studio 2017 araçları odaklanır, ancak diğer iki yaklaşım Dockerfiles kullanarak in regard to oldukça benzer.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Senaryo 1: Kapsayıcılı ASP.NET web uygulamaları

Aşağıdaki şekilde kapsayıcılı Elektronik Mağaza eski web apps uygulamaları senaryosu gösterilmektedir.

> ![ASP.NET uygulamaları geliştirme ortamında kapsayıcılı Basitleştirilmiş mimarisi diyagramı](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a>Senaryo 2: Kapsayıcılı WCF Hizmeti

Aşağıdaki şekilde kapsayıcılı WCF Hizmeti ile 3 katmanlı uygulama senaryosu gösterilmektedir. 

> ![Basitleştirilmiş bir geliştirme ortamı kapsayıcılı WCF hizmeti mimarisi diyagramı](./media/image5-3.5.png)
>

### <a name="benefits"></a>Yararları

Bir kapsayıcıda tek yapılı uygulamanızı çalıştırmanın avantajı vardır. İlk olarak, uygulama için bir görüntü oluşturun. Bu noktadan itibaren her dağıtım aynı ortamda çalışır. Her kapsayıcı aynı işletim sistemi sürümünü kullanır, yüklü bağımlılıkları aynı sürümü, aynı .NET framework sürümünü kullanır ve aynı işlemi kullanılarak oluşturulmuş. Temel olarak, uygulamanızın bağımlılıkları Docker görüntüsünü kullanarak denetler. Kapsayıcılar dağıttığınızda bağımlılıkları uygulamayla ilerler.

Ek bir faydası, geliştiricilerin uygulama Windows kapsayıcıları tarafından sağlanan tutarlı ortamında çalıştırabilirsiniz ' dir. Yalnızca belirli sürümler ile görünür sorunları bir hazırlık veya üretim ortamında görünmesini yerine hemen anlaþýlmaz. Kapsayıcı uygulamaları çalıştırdığınızda, geliştirme ortamları ve geliştirme ekibi üyeleri tarafından kullanılan farklılıkları daha az önemli.

Kapsayıcılı uygulamaları daha düz genişleme eğri de vardır. Kapsayıcılı uygulamaları, daha fazla uygulama ve hizmet örnekleri (kapsayıcılarında dayanarak) sahip bir VM veya fiziksel makine makine başına normal uygulama dağıtımı ile karşılaştırıldığında olanak verir. Bu daha yüksek yoğunluk ve daha az gerekli dönüşür özellikle orchestrators Kubernetes veya Service Fabric gibi kullandığınızda kaynakları.

İdeal durumlarda verilerin kapsayıcıyla taşınmasını uygulama kodu herhangi bir değişiklik yapmadan gerektirmez (C\#). Çoğu senaryoda, Docker dağıtım meta veri dosyaları (Dockerfiles ve Docker Compose) yeterlidir.

### <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:

  - [.NET Framework web uygulamalarını Windows kapsayıcıları ve Docker ile containerize nasıl](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [Bir WCF hizmetine Docker desteği ekleme](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>İzlenecek yol: 3: kapsayıcıları tabanlı Windows uygulamanızı Azure VM'ler için dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirliği

Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a>Genel Bakış

Docker ana bilgisayar üzerinde bir Windows Server 2016 sanal makine (VM) azure'a dağıtma hızlı geliştirme/test/hazırlama ortamlarını ayarlama ayarlamanıza olanak tanır. Bu ayrıca sınayıcılar veya iş kullanıcıları uygulama doğrulamak ortak bir yer sağlar. VM'ler, bir hizmet (Iaas) üretim ortamlarında geçerli alt yapı de olabilir.

### <a name="goals"></a>Hedefleri

Bu kılavuz, Windows Server 2016 veya sonraki sürümler göre Azure vm'lerine Windows kapsayıcıları dağıtırken sahip birden çok alternatifleri göstermek için hedefidir.

### <a name="scenarios"></a>Senaryolar

Bazı senaryolarda bu kılavuzda ele alınmıştır.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Senaryo A: bir Azure VM geliştirme PC Docker altyapısına bağlantısı üzerinden gelen Dağıt

![Docker altyapısına bağlantısı üzerinden geliştirme bilgisayarınıza bir Azure VM Dağıtım](./media/image5-4.png)

> **Şekil 5-4.** Docker altyapısına bağlantısı üzerinden geliştirme bilgisayarınıza bir Azure VM Dağıtım

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Senaryo B: Docker kayıt defteri aracılığıyla bir Azure VM dağıtma

![Bir Azure VM Docker kayıt defteri aracılığıyla dağıtma](./media/image5-5.png)

> **Şekil 5-5.** Bir Azure VM Docker kayıt defteri aracılığıyla dağıtma

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a>Visual Studio Team Services içinde senaryo C: dağıtımı için bir Azure VM CI/CD'sinden ardışık düzenleri

![Visual Studio Team Services CI/CD ardışık düzen bir Azure VM Dağıtım](./media/image5-6.png)

> **Şekil 5-6.** Visual Studio Team Services CI/CD ardışık düzen bir Azure VM Dağıtım

### <a name="azure-vms-for-windows-containers"></a>Azure VM'ler Windows kapsayıcıları için

Azure VM'ler için Windows Windows Server 2016, Windows 10 veya sonraki sürümler göre VM'ler kapsayıcılardır, Docker altyapısına her ikisi de ayarlayın. Çoğu durumda, Windows Server 2016 Azure Vm'lerde kullanılır.

Azure şu anda sağlar adlı bir VM'den **Windows Server 2016 kapsayıcılarla**. Bu VM, Windows Server Core veya Windows Nano Server ile yeni Windows Server kapsayıcı özelliği denemek için kullanabilirsiniz. Kapsayıcı işletim sistemi görüntüleri yüklenir ve ardından VM ile Docker kullanıma hazırdır.

### <a name="benefits"></a>Yararları

Azure'a dağıtırken, şirket içi Windows Server 2016 VM'ler için Windows kapsayıcıları dağıtılabilir rağmen kullanıma hazır Windows Server kapsayıcı VM'ler ile çalışmaya başlamak için daha kolay bir yolu alın. Ayrıca Sınayıcılar ve Azure sanal makine ölçek kümeleri aracılığıyla otomatik ölçeklenebilirlik erişebileceği ortak bir çevrimiçi konumu elde edersiniz.

### <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>İzlenecek yol: 4: Azure kapsayıcı örnekleri (ACI) Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirliği

Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:

[Uygulamaları dağıtma ACI (Azure kapsayıcı örnekleri)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Genel Bakış

[Azure kapsayıcı örnekleri (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) kapsayıcıları tek tek örneklerini dağıtabileceğiniz kapsayıcıları dev/test/hazırlama ortamına sahip olmak için en hızlı yoludur.

### <a name="goals"></a>Hedefleri

Bu kılavuzda Windows kapsayıcıları Azure kapsayıcı örnekleri (ACI) ve ACI eShopModernizing uygulamalarını nasıl dağıtabileceğini dağıtırken ana senaryo gösterir.

### <a name="scenarios"></a>Senaryolar

Tek veya tüm uygulamaların (MVC uygulama, WebForms uygulaması veya WCF Hizmeti) dağıtmak gibi ACI eShopModernizing uygulamaları dağıtma hakkında Çeşitlemeler olabilir. Aşağıda gösterilen aşağıdaki senaryoda, ASP.NET MVC uygulaması artı ikisinin dağıtılan SQL Server kapsayıcı kapsayıcıları (Azure kapsayıcı örnekleri) ACI görebilirsiniz.

![Geliştirme ortamından ACI için dağıtma](./media/image5-3.5.6.png)

### <a name="benefits"></a>Yararları

Azure kapsayıcı örnekleri oluşturmak ve sanal makineler sağlamak veya bir üst düzey hizmet benimsemeyi zorunda kalmadan, azure'da Docker kapsayıcıları yönetmek kolay hale getirir. ACI ile doğrudan Azure Windows kapsayıcısında dağıtabilir ve (Windows kapsayıcı görüntünün hazır Docker hub'a veya Azure kapsayıcı gibi Docker defterinde olması koşuluyla, bir tam etki alanı adı (FQDN) ile Internet'e birkaç saniye içinde kullanıma sunma Kayıt defteri).

### <a name="considerations"></a>Dikkat Edilecekler

Tam ya da .NET Framework ile Windows kapsayıcıları dağıtma / ASP.NET veya SQL Server Azure kapsayıcı örnekleri (ACI) içine Docker görüntü olduğu normal bir Docker ana bilgisayar (örneğin, Windows Server 2016 Windows kapsayıcılarla) dağıtma olarak oldukça hızlı değil her zaman (Docker kayıt defterinden çekilen) indirilir ve kendi docker ana (kalıcı olarak çevrimiçi koruma daha ucuz ancak SQL kapsayıcı görüntüsünü (15.1 GB) ve ASP.NET kapsayıcı görüntüsünü (13.9 GB) boyutunu önemli ölçüde büyük Windows Server 2016 ile azure'da Windows kapsayıcıları VM), diğer yandan, üretim dağıtımları için harika seçenekleri olan Kubernetes Azure (AKS/ACS) veya Azure Service Fabric gibi tüm orchestrator gerekeceğinden buraya değil.

Ana sonuç, Azure kapsayıcı örnekleri CI/CD ardışık düzen ve geliştirme ve Test senaryoları için çok ilgi çekici bir seçenek kullanmaktır.

## <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha kapsamlı GitHub Wiki'de keşfedin: 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>5 izlenecek yol: Kubernetes Azure kapsayıcı hizmetinde kapsayıcıları tabanlı Windows uygulamalarınızı dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirliği

Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a>Genel Bakış

Windows kapsayıcılarında tabanlı bir uygulama hızlı bir şekilde daha uzakta Iaas Vm'lerden taşıma platformlarda kullanmaları gerekir. Bu kolayca yüksek ölçeklenebilirlik elde etmek için gereklidir ve daha iyi ölçeklenebilirlik otomatik ve önemli bir iyileştirme için dağıtımları ve sürüm oluşturma otomatik. Orchestrator'ı kullanarak bu hedefleri elde edebilirsiniz [Kubernetes](https://kubernetes.io/), kullanılabilir [Azure kapsayıcı hizmetlerini](https://azure.microsoft.com/services/container-service/).

### <a name="goals"></a>Hedefleri

Kubernetes Windows kapsayıcı tabanlı bir uygulamaya dağıtma hakkında bilgi edinmek için bu kılavuzu belirtilir (olarak da bilinir *K8s*) Azure kapsayıcı Hizmeti'nde. Kubernetes için baştan dağıtma iki adımlı bir işlemdir:

1.  Kubernetes küme Azure kapsayıcı hizmeti dağıtın.

2.  İlgili kaynaklar ve uygulama Kubernetes kümeye dağıtın.

### <a name="scenarios"></a>Senaryolar

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Senaryo A: bir geliştirme ortamı'ndan doğrudan Kubernetes kümeye dağıtma

![Geliştirme ortamından doğrudan Kubernetes kümeye dağıtma](./media/image5-7.png)

> **Şekil 5-7.** Geliştirme ortamından doğrudan Kubernetes kümeye dağıtma

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a>Senaryo B: dağıtmak Kubernetes kümeye CI/CD'sinden Team Services içinde ardışık düzenleri

![CI/CD ardışık düzen Team Services Kubernetes kümeye dağıtım](./media/image5-8.png)

> **Şekil 5-8.** CI/CD ardışık düzen Team Services Kubernetes kümeye dağıtım

### <a name="benefits"></a>Yararları

Kubernetes bir kümede dağıtılması için birçok avantaj vardır. En büyük (varolan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısını düğümlerinin veya sanal makineleri küme (temel kapsayıcı örnek sayısına göre uygulamanın içinde ölçeklenebilen bir üretime hazır ortamı alma avantajdır Genel ölçeklenebilirlik kümenin).

Azure kapsayıcı hizmeti popüler açık kaynak Araçlar ve teknolojiler özellikle Azure için en iyi duruma getirir. Taşınabilirlik, kapsayıcılarınızı hem uygulama yapılandırmanızı sağlayan açık olan çözüm alın. Boyutu, ana bilgisayar sayısını seçin ve orchestrator araçları-kapsayıcı hizmeti şey işler.

Kubernetes ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmekten aşağıdaki özellikleri, diğerlerinin yanı sıra kolaylaştıran kapsayıcı merkezli bir altyapı planlama için ilerleme:

- Birden çok kapsayıcılara göre uygulamaları

- Kapsayıcı örnekleri ve yatay otomatik ölçeklendirmeyi çoğaltma

- Adlandırma ve (örneğin, iç DNS) bulma

- Yükünü dengeleme

- Güncelleştirmeleri alınıyor

- Gizli dağıtma

- Uygulama durumu denetimleri

## <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha kapsamlı GitHub Wiki'de keşfedin: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a>İzlenecek yol: 6: Azure Service Fabric Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirliği

Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a>Genel Bakış

Windows kapsayıcılarında hızla tabanlı bir uygulama daha uzakta Iaas Vm'lerden taşıma platformları kullanması gerekir. Bu kolayca yüksek ölçeklenebilirlik elde etmek için gereklidir ve daha iyi ölçeklenebilirlik otomatik ve önemli bir iyileştirme için dağıtımları ve sürüm oluşturma otomatik. Azure bulutta kullanılabilir, ancak şirket içi kullanmak de kullanılabilir olan, Azure Service Fabric orchestrator kullanarak veya farklı bir genel bulut bile, bu hedefleri elde edebilirsiniz.

### <a name="goals"></a>Hedefleri

Bu kılavuzda Windows kapsayıcı tabanlı bir uygulama için Azure Service Fabric kümesi dağıtma hakkında bilgi edinmek için hedefidir. Service Fabric sıfırdan dağıtma iki adımlı bir işlemdir:

1.  Service Fabric kümesi Azure (veya farklı bir ortam) dağıtın.

2.  İlgili kaynaklar ve uygulama için Service Fabric kümesi dağıtın.

### <a name="scenarios"></a>Senaryolar

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a>Senaryo A: Dağıt doğrudan bir Service Fabric kümesi bir geliştirme ortamı'ndan

![Geliştirme ortamından doğrudan bir Service Fabric kümesi dağıtma](./media/image5-9.png)

> **Şekil 5-9.** Geliştirme ortamından doğrudan bir Service Fabric kümesi dağıtma

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a>Senaryo B: dağıtmak için Service Fabric kümesi CI/CD'sinden Team Services içinde ardışık düzenleri

![Service Fabric kümesi için Visual Studio Team Services CI/CD ardışık düzen dağıtım](./media/image5-10.png)

> **Şekil 5-10.** Service Fabric kümesi için Visual Studio Team Services CI/CD ardışık düzen dağıtım

## <a name="benefits"></a>Yararları

Service Fabric, kümeye dağıtma avantajlarını Kubernetes kullanmanın avantajları için benzerdir. Tek fark, yine de olan Service Fabric Kubernetes sürüm 1.9 Windows kapsayıcı için bir beta aşamasında olan Kubernetes karşılaştırıldığında Windows uygulamaları için daha da olgun bir üretim ortamında olduğunu (aralık 2017). Kubernetes Linux daha da olgun bir ortamdır.

Azure Service Fabric kullanmanın ana Avantajı (varolan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısına göre kapsayıcı örnek sayısına göre uygulamanın içinde ölçeklenebilen bir üretime hazır ortamı alma olduğu düğümler ve (genel ölçeklenebilirlik kümenin) kümedeki sanal makineleri.

Azure Service Fabric taşınabilirlik kapsayıcılarınızı hem uygulama yapılandırmanızı sağlar. Azure'da küme ya da şirket içi, kendi veri merkezinizde yüklemeyi Service Fabric olabilir. Bile bir Service Fabric kümesi farklı bir buluta gibi yükleyebilirsiniz [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).

Service Fabric ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmekten aşağıdaki özellikleri, diğerlerinin yanı sıra kolaylaştıran kapsayıcı merkezli bir altyapı planlama için ilerleme:

- Birden çok kapsayıcılara göre uygulamalar.

- Kapsayıcı örnekleri ve yatay otomatik ölçeklendirmeyi çoğaltılıyor.

- Adlandırma ve (örneğin, iç DNS) bulma.

- Yükü Dengeleme.

- Güncelleştirmeleri alınıyor.

- Gizli dağıtma.

- Uygulama durumunu denetler.

Aşağıdaki özellikleri Service Fabric (diğer orchestrators karşılaştırıldığında) de özeldir:

- Güvenilir hizmetler uygulama modeli üzerinden durum bilgisi olan hizmetler yeteneği.

- Reliable Actors uygulama modeli üzerinden aktörler deseni.

- Windows veya Linux kapsayıcıları yanı sıra tam kemik işlemleri dağıtın.

- Gelişmiş çalışırken güncelleştirmeleri ve sistem durumu denetimleri.

### <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
[Önceki](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[sonraki](conclusions.md)
