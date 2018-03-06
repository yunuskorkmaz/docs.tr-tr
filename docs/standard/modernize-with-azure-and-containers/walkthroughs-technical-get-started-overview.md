---
title: "İzlenecek yollar ve teknik başlatılan özeti"
description: "Azure Bulut ve Windows kapsayıcıları varolan .NET uygulamaları modernize | izlenecek yollar ve teknik başlatılan özeti"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bced3bed84d138dbda4f322322213b47c0159016
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>İzlenecek yollar ve teknik başlatılan özeti 

Bu e-kitap boyutunu sınırlamak için ek teknik belgeler ve tam yönergeler bulunan bir GitHub deposuna yaptık. Bu bölümde açıklanan izlenecek yollar çevrimiçi bir dizi adım adım kurulum Windows kapsayıcıları ve Azure dağıtımına dayalı birden çok ortamlarının kapsar.

Aşağıdaki bölümlerde, her gözden geçirme hakkında-ITS nedir açıklanır hedefleri, kendi üst düzey görme- ve ilgili olan görevleri diyagramı sağlar. İzlenecek yollar kendilerini alabilirsiniz içinde *eShopModernizing* uygulamaları GitHub deposuna wiki adresindeki [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).

# <a name="technical-walkthrough-list"></a>Teknik kılavuz listesi

Aşağıdaki get-started izlenecek kaldırın ve kapsayıcılar kullanarak kaydırma ve Azure içinde birden çok dağıtım seçenekleri kullanarak Taşı örnek uygulamaları için tutarlı ve kapsamlı teknik Kılavuzu sağlamak.

Her biri aşağıdaki izlenecek github'da kullanılabilir olan yeni örnek eShopLegacy ve eShopModernizing uygulamaları kullanır [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).

-   **Elektronik Mağaza eski uygulamaları turu**

-   **Var olan .NET uygulamalarınız Windows kapsayıcılarla containerize**

-   **Azure VM'ler kapsayıcıları tabanlı Windows uygulamanızı dağıtma**

-   **Azure kapsayıcı Hizmeti'nde Kubernetes Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma**

-   **Azure Service Fabric Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Gözden geçirme 1: Elektronik Mağaza eski uygulamaları turu

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirliği

Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a>Genel Bakış

Bu kılavuzda, iki örnek eski uygulamalar ilk uyarlamasını keşfedebilirsiniz. Her iki örnek uygulamaları tek yapılı bir mimariye sahip ve klasik ASP.NET kullanılarak oluşturulmuş. ASP.NET ile tabanlı bir uygulamayı 4.x MVC; İkinci uygulama ASP.NET 4.x Web Forms üzerinde temel alır. Her iki uygulamada bulunan [eShopModernizing GitHub deposuna](https://github.com/dotnet-architecture/eShopModernizing).

Her iki örnek uygulamaları containerize, benzer şekilde, Klasik containerize [Windows Communication Foundation](../../framework/wcf/whats-wcf.md) bir masaüstü uygulaması olarak kullanılması (WCF) uygulama. Bir örnek için bkz: [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).

### <a name="goals"></a>Hedefleri

Asıl amacı, bu kılavuzda yalnızca bu uygulamalarla ve kendi kod ve yapılandırma hakkında bilgi edinmek için ' dir. Böylece oluşturmak ve test amacıyla SQL veritabanı kullanmadan sahte veriler kullanmak uygulamaları yapılandırabilirsiniz. Bu isteğe bağlı yapılandırma bağımlılık ekleme, ayrılmış bir biçimde temel alır.

### <a name="scenario"></a>Senaryo

Şekil 5-1 özgün eski uygulamaları basit bir senaryo gösterir.

> ![Basit mimarisi senaryo özgün eski uygulamalar](./media/image5-1.png)
>
> **Şekil 5-1.** Basit mimarisi senaryo özgün eski uygulamalar

Bir iş etki alanı açısından bakıldığında, hem uygulamalar aynı katalog yönetimi özellikleri sunar. Elektronik Mağaza Kurumsal ekibi üyelerinin uygulamayı görüntülemek ve ürün kataloğu düzenlemek için kullanırsınız. Şekil 5-2 ilk uygulama ekran görüntüleri gösterir.

![ASP.NET MVC ve ASP.NET Web Forms uygulamaları (varolan eski teknolojileri)](./media/image5-2.png)

> **Şekil 5-2.** ASP.NET MVC ve ASP.NET Web Forms uygulamaları (varolan eski teknolojileri)

Gözat ve Katalog girişleri değiştirmek için kullanılan web uygulamaları şunlardır. Her iki uygulamalar aynı iş/işlevsel özellikleri sunmak olgu yalnızca karşılaştırma amacıyla kullanılır. ASP.NET MVC ve ASP.NET Web Forms çerçeveler kullanılarak oluşturulmuş olan uygulamalar için benzer bir modernization işlem görebilirsiniz.

Bağımlılıklar ASP.NET 4.x veya önceki sürümleri (veya MVC için Web formları için) anlamına gelir kodu tam olarak ASP.NET Core MVC kullanarak yeniden yazılmıştır sürece bu uygulamaları .NET Core üzerinde çalışmaz. Bu yeniden düzenlenmesine veya kodu yeniden istemediğiniz yaparsanız, mevcut uygulamaları containerize ve hala aynı .NET teknolojileri ve aynı kodu kullan olduğunu noktası gösterir. Bu eski kod için herhangi bir değişiklik yapılmadan kapsayıcılarında gibi uygulamaları nasıl çalıştırabileceğiniz görebilirsiniz.

### <a name="benefits"></a>Yararları

Bu kılavuzda yararları basit: yalnızca bağımlılık ekleme temel kod ve uygulama yapılandırma hakkında bilgi edinin. Ardından, containerize ve birden çok ortamlar için gelecekte dağıtırken Bu yaklaşımda deneyebilirsiniz.

### <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>İzlenecek yol: 2: var olan .NET uygulamalarınız Windows kapsayıcılarla Containerize

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirliği

Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

### <a name="overview"></a>Genel Bakış

MVC, Web Forms veya WCF, üretim, geliştirme ve test ortamları için temel gelenler varolan .NET uygulamalarının dağıtımını iyileştirmek için Windows kapsayıcıları kullanın.

### <a name="goals"></a>Hedefleri

Bu kılavuzun amacı, var olan bir .NET Framework uygulamasını containerizing için çeşitli seçenekler göstermektir. Şunları yapabilirsiniz:

-   Uygulamanızı kullanarak containerize [Docker için Visual Studio 2017 Araçları](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 veya sonraki sürümler).

-   El ile ekleyerek uygulamanızı containerize bir [Dockerfile](https://docs.docker.com/engine/reference/builder/)ve ardından kullanarak [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).

-   Uygulamanızı kullanarak containerize [Img2Docker](https://github.com/docker/communitytools-image2docker-win) Aracı (Docker açık kaynak aracından).

Bu kılavuz Docker yaklaşım için Visual Studio 2017 araçları odaklanır, ancak diğer iki yaklaşım Dockerfiles kullanmanın bakımından oldukça benzer.

### <a name="scenario"></a>Senaryo

Şekil 5-3 kapsayıcılı Elektronik Mağaza eski uygulamaları senaryosu gösterilmektedir.

> ![Bir geliştirme ortamı kapsayıcılı uygulamalarda Basitleştirilmiş mimarisi diyagramı](./media/image5-3.png)
>
> **Şekil 5-3.** Bir geliştirme ortamı kapsayıcılı uygulamalarda Basitleştirilmiş mimarisi diyagramı

### <a name="benefits"></a>Yararları

Bir kapsayıcıda tek yapılı uygulamanızı çalıştırmanın avantajı vardır. İlk olarak, uygulama için bir görüntü oluşturun. Bu noktadan itibaren her dağıtım aynı ortamda çalışır. Her kapsayıcı aynı işletim sistemi sürümünü kullanır, yüklü bağımlılıkları aynı sürümü, aynı .NET framework sürümünü kullanır ve aynı işlemi kullanılarak oluşturulmuş. Temel olarak, uygulamanızın bağımlılıkları Docker görüntüsünü kullanarak denetler. Kapsayıcılar dağıttığınızda bağımlılıkları uygulamayla ilerler.

Ek bir faydası, geliştiricilerin uygulama Windows kapsayıcıları tarafından sağlanan tutarlı ortamında çalıştırabilirsiniz ' dir. Yalnızca belirli sürümler ile görünür sorunları bir hazırlık veya üretim ortamında görünmesini yerine hemen anlaþýlmaz. Kapsayıcı uygulamaları çalıştırdığınızda, geliştirme ortamları ve geliştirme ekibi üyeleri tarafından kullanılan farklılıkları daha az önemli.

Kapsayıcılı uygulamaları daha düz genişleme eğri de vardır. Kapsayıcılı uygulamaları, daha fazla uygulama ve hizmet örnekleri (kapsayıcılarında dayanarak) sahip bir VM veya fiziksel makine makine başına normal uygulama dağıtımı ile karşılaştırıldığında olanak verir. Bu daha yüksek yoğunluk ve daha az gerekli dönüşür özellikle orchestrators Kubernetes veya Service Fabric gibi kullandığınızda kaynakları.

İdeal durumlarda verilerin kapsayıcıyla taşınmasını uygulama kodu herhangi bir değişiklik yapmadan gerektirmez (C\#). Çoğu senaryoda, Docker dağıtım meta veri dosyaları (Dockerfiles ve Docker Compose) yeterlidir.

### <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha kapsamlı GitHub Wiki'de keşfedin: [https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>İzlenecek yol: 3: kapsayıcıları tabanlı Windows uygulamanızı Azure VM'ler için dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirliği

Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

### <a name="overview"></a>Genel Bakış

Bir Windows Server 2016 VM Azure Docker konakta dağıtma hızlı geliştirme/test/hazırlama ortamlarını ayarlama ayarlamanıza olanak tanır. Bu ayrıca sınayıcılar veya iş kullanıcıları uygulama doğrulamak ortak bir yer sağlar. Sanal makineleri aynı zamanda geçerli Iaas üretim ortamlarında olabilir.

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

Yalnızca Windows Server 2016, Windows 10 tabanlı VM'ler Azure VM'ler için Windows kapsayıcılar olan veya sonraki sürümleri, Docker altyapısına her ikisi de ayarlayın. Çoğu durumda, Windows Server 2016 Azure Vm'lerde kullanır.

Azure şu anda sağlar adlı bir VM'den **Windows Server 2016 kapsayıcılarla**. Bu VM, Windows Server Core veya Windows Nano Server ile yeni Windows Server kapsayıcı özelliği denemek için kullanabilirsiniz. Kapsayıcı işletim sistemi görüntüleri yüklenir ve ardından VM ile Docker kullanıma hazırdır.

### <a name="benefits"></a>Yararları

Azure'a dağıtırken, şirket içi Windows Server 2016 VM'ler için Windows kapsayıcıları dağıtılabilir rağmen kullanıma hazır Windows Server kapsayıcı VM'ler ile çalışmaya başlamak için daha kolay bir yolu alın. Ayrıca Sınayıcılar ve otomatik ölçeklenebilirlik Azure VM ölçek kümesi aracılığıyla erişilebilen ortak bir çevrimiçi konuma elde edersiniz.

### <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>İzlenecek yol: 4: Azure kapsayıcı Hizmeti'nde Kubernetes Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma

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

Kubernetes bir kümede dağıtılması için birçok avantaj vardır. İçinde (varolan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısını düğümlerinin veya sanal makineleri küme (temel kapsayıcı örnek sayısına göre uygulama genişleme üretime hazır ortamı alma büyük avantaj olmalıdır Genel ölçeklenebilirlik kümenin).

Azure kapsayıcı hizmeti popüler açık kaynak Araçlar ve teknolojiler özellikle Azure için en iyi duruma getirir. Taşınabilirlik, kapsayıcılarınızı hem uygulama yapılandırmanızı sağlayan açık olan çözüm alın. Boyutu, ana bilgisayar sayısını seçin ve orchestrator araçları-kapsayıcı hizmeti şey işler.

Kubernetes ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmekten aşağıdaki özellikleri, diğerlerinin yanı sıra kolaylaştıran kapsayıcı merkezli bir altyapı planlama için ilerleme:

-   Birden çok kapsayıcılara göre uygulamaları

-   Kapsayıcı örnekleri ve yatay otomatik ölçeklendirmeyi çoğaltma

-   Adlandırma ve (örneğin, iç DNS) bulma

-   Yükünü dengeleme

-   Güncelleştirmeleri alınıyor

-   Gizli dağıtma

-   Uygulama durumu denetimleri

## <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha kapsamlı GitHub Wiki'de keşfedin: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-() Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a>İzlenecek yol: 5: Azure Service Fabric Windows kapsayıcıları tabanlı uygulamalarınızı dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik kılavuz kullanılabilirliği

Tam teknik Kılavuzu eShopModernizing GitHub deposuna wiki kullanılabilir:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a>Genel Bakış

Windows kapsayıcılarında tabanlı bir uygulama hızlı bir şekilde daha uzakta Iaas Vm'lerden taşıma platformlarda kullanmaları gerekir. Bu kolayca yüksek ölçeklenebilirlik elde etmek için gereklidir ve daha iyi ölçeklenebilirlik otomatik ve önemli bir iyileştirme için dağıtımları ve sürüm oluşturma otomatik. Azure bulutta kullanılabilir, ancak şirket içi kullanmak de kullanılabilir olan, Azure Service Fabric orchestrator kullanarak veya farklı bir genel bulut bile, bu hedefleri elde edebilirsiniz.

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

Service Fabric, kümeye dağıtma avantajlarını Kubernetes kullanmanın avantajları için benzerdir. Tek fark, ancak Service Fabric erken kadar Windows kapsayıcıları için Önizleme'de 2017 kalan edildi Kubernetes karşılaştırıldığında Windows uygulamaları için çok olgun üretim ortamında olmasıdır. (Kubernetes daha da olgun için bir Linux ortamıdır). 

İçinde (varolan düğümleri iç ölçeklenebilirlik) kullanmak istiyorsanız ve sayısına göre kapsayıcı örnek sayısına göre uygulama genişleme üretime hazır ortamı alma Azure Service Fabric kullanmanın ana avantajı olduğu düğümler ve (genel ölçeklenebilirlik kümenin) kümedeki sanal makineleri.

Azure Service Fabric taşınabilirlik kapsayıcılarınızı hem uygulama yapılandırmanızı sağlar. Azure'da küme ya da şirket içi, kendi veri merkezinizde yüklemeyi Service Fabric olabilir. Bile bir Service Fabric kümesi farklı bir buluta gibi yükleyebilirsiniz [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).

Service Fabric ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmekten aşağıdaki özellikleri, diğerlerinin yanı sıra kolaylaştıran kapsayıcı merkezli bir altyapı planlama için ilerleme:

-   Birden çok kapsayıcılara göre uygulamalar.

-   Kapsayıcı örnekleri ve yatay otomatik ölçeklendirmeyi çoğaltılıyor.

-   Adlandırma ve (örneğin, iç DNS) bulma.

-   Yükü Dengeleme.

-   Güncelleştirmeleri alınıyor.

-   Gizli dağıtma.

-   Uygulama durumunu denetler.

Aşağıdaki özellikleri Service Fabric (diğer orchestrators karşılaştırıldığında) de özeldir:

-   Güvenilir hizmetler uygulama modeli üzerinden durum bilgisi olan hizmetler yeteneği.

-   Reliable Actors uygulama modeli üzerinden aktörler deseni.

-   Windows veya Linux kapsayıcıları yanı sıra tam kemik işlemleri dağıtın.

-   Gelişmiş çalışırken güncelleştirmeleri ve sistem durumu denetimleri.

### <a name="next-steps"></a>Sonraki adımlar

Bu içerik daha kapsamlı GitHub Wiki'de keşfedin:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
[Önceki](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[sonraki](conclusions.md)
