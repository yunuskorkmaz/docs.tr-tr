---
title: İzlenecek yollar ve teknik başlangıca genel bakış
description: Azure Bulutu ve Windows Kapsayıcıları ile Mevcut .NET Uygulamalarını Modernize Edin | Walkthroughs ve teknik genel bakış başlar
ms.date: 04/28/2018
ms.openlocfilehash: 190b33c4307b09bab0543d481e66ac9328074a0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69660891"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a>İzlenecek yollar ve teknik başlangıca genel bakış

Bu e-kitabın boyutunu sınırlamak için, ek teknik belgeler ve tam izlikler GitHub deposunda kullanıma sunuldu. Bu bölümde açıklanan çevrimiçi gözden geçirme ler serisi, Windows Kapsayıcılarını temel alan birden çok ortamın adım adım kurulumünü ve Azure'a dağıtımını kapsar.

Aşağıdaki bölümler, her gözden geçirmenin ne yle ilgili olduğunu, hedeflerini ve üst düzey vizyonunu açıklar ve ilgili görevlerin diyagramını sağlar. *EShopModernizing* uygulamaları GitHub repo wiki de <https://github.com/dotnet-architecture/eShopModernizing/wiki>izlenebilir.

## <a name="technical-walkthrough-list"></a>Teknik gözden geçirme listesi

Aşağıdaki başlangıç walkthroughs kapsayıcıları kullanarak kaldırabilir ve kaydırabilirsiniz örnek uygulamalar için tutarlı ve kapsamlı teknik yönergeler sağlar ve ardından Azure'da birden fazla dağıtım seçeneği kullanarak hareket ettirebilirsiniz.

Aşağıdaki izbinlerin her biri, GitHub'da <https://github.com/dotnet-architecture/eShopModernizing>bulunan yeni örnek eShopLegacy ve eShopModernizing uygulamalarını kullanmaktadır.

- **eShop eski uygulamaları turu (modernize etmek için temel uygulamalar)**

- **Mevcut ASP.NET web uygulamalarınızı (WebForm'lar & MVC) Windows Kapsayıcıları ile kaplayın**

- **Mevcut WCF hizmetlerinizi (N Katmanlı uygulamalar) Windows Kapsayıcıları ile konteynerleştirin**

- **Windows Kapsayıcılar tabanlı uygulamanızı Azure VM'lerine dağıtma**

- **Azure Kapsayıcı Hizmeti'nde Windows Kapsayıcı tabanlı uygulamalarınızı Kubernetes'e dağıtın**

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a>Walkthrough 1: eShop eski uygulamaları turu

### <a name="technical-walkthrough-availability"></a>Teknik yol kullanılabilirliği

Tam teknik izbile edinebilirsiniz eShopModernizing GitHub repo wiki:

[eShopModernizing wiki walkthroughs](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a>Genel Bakış

Bu izne, üç örnek eski uygulamanın ilk uygulamasını keşfedebilirsiniz. İlk iki örnek web uygulaması yekpare bir mimariye sahiptir ve klasik ASP.NET kullanılarak oluşturulmuştur. Bir uygulama ASP.NET 4.x MVC dayanmaktadır; ikinci uygulama ASP.NET 4.x Web Formları dayanmaktadır.
Üçüncü uygulama, istemci WinForms uygulaması ve sunucu tarafı [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) hizmeti tarafından oluşturulan 3 Katmanlı bir uygulamadır.

Tüm bu uygulamalar [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing)mevcuttur.

### <a name="goals"></a>Hedefler

Bu gözden geçirmenin temel amacı, bu uygulamalara ve onların kod ve yapılandırmasına aşina olmaktır. Uygulamaları, SQL veritabanını kullanmadan, test amacıyla sahte veri oluşturacak ve kullanacak şekilde yapılandırabilirsiniz. Bu isteğe bağlı config bağımlılık enjeksiyonu dayanmaktadır, bir decoupled şekilde.

### <a name="scenario-1-aspnet-web-apps"></a>Senaryo 1: ASP.NET Web uygulamaları

Aşağıdaki şekil, web uygulamaları ASP.NET orijinal eski basit senaryo gösterir.

![Web uygulamaları ASP.NET orijinal mirasın basit mimari senaryosu](./media/image5-1.png)

İş alanı açısından bakıldığında, her iki uygulama da aynı katalog yönetimi özelliklerini sunar. eShop kurumsal ekibinin üyeleri, ürün kataloğunu görüntülemek ve bunları görüntülemek için uygulamayı kullanır.

Bir sonraki şekil, ilk uygulama ekran görüntülerini gösterir.

![ASP.NET MVC ve ASP.NET Web Formları uygulamaları (mevcut/eski teknolojiler)](./media/image5-2.png)

ASP.NET 4.x veya önceki sürümlerde (MVC veya Web Formları için) bağımlılıklar, kod ASP.NET Core MVC kullanılarak tamamen yeniden yazılmadıkça bu uygulamaların .NET Core'da çalışmayamayacağı anlamına gelir.

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a>Senaryo 2: WCF hizmeti ve WinForms istemci uygulaması (3 Katmanlı uygulama)

Aşağıdaki şekil, orijinal 3 Katmanlı eski uygulamanın basit senaryosunu gösterir.

![WCF hizmeti ve WinForms istemci uygulaması ile orijinal eski 3 Katmanlı uygulamanın basit mimari senaryosu](./media/image5-1.5.png)

### <a name="benefits"></a>Avantajlar

Bu gözden geçirmenin avantajları basittir: Kodu ve ilk uygulamaları tanımanın yeterlidir.

### <a name="next-steps"></a>Sonraki adımlar

Bu içeriği GitHub wiki'de daha ayrıntılı olarak keşfedin:

- [MVC ve Web Formları "eski" uygulamalar ASP.NET temel üzerinde Tur](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [Temel WCF hizmeti nde tur ve WinForms (3 Katmanlı) "eski" uygulaması](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a>Walkthrough 2: Mevcut .NET uygulamalarınızı Windows Kapsayıcıları ile konteynerleştirin

### <a name="overview"></a>Genel Bakış

MVC, Web Formları veya WCF'ye dayalı uygulamalar gibi varolan .NET uygulamalarının üretim, geliştirme ve test ortamlarına dağıtımını iyileştirmek için Windows Kapsayıcıları'nı kullanın.

### <a name="goals"></a>Hedefler

Bu gözden geçirmenin amacı, varolan bir .NET Framework uygulamasını kapsayıcı hale getirmek için çeşitli seçenekler göstermektir. Şunları yapabilirsiniz:

- [Visual Studio 2017 Docker Araçları](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 veya sonraki sürümleri) kullanarak başvurunuzu konteynerize edin.

- Bir [Dockerfile'ı](https://docs.docker.com/engine/reference/builder/)el ile ekleyerek ve docker [CLI'yi](https://docs.docker.com/engine/reference/commandline/cli/)kullanarak uygulamanızı konteynerleştirin.

- [Img2Docker](https://github.com/docker/communitytools-image2docker-win) aracını (Docker'dan gelen açık kaynak bir araç) kullanarak uygulamanızı konteynerleştirin.

Bu izim, Visual Studio 2017 Docker için Araçlar yaklaşımına odaklanır, ancak diğer iki yaklaşım Dockerfiles'ı kullanma konusunda oldukça benzerdir.

### <a name="scenario-1-containerized-aspnet-web-apps"></a>Senaryo 1: Web uygulamaları ASP.NET kaplanmış

Aşağıdaki şekil konteynere eShop eski web uygulamaları uygulamaları için senaryo gösterir.

![Geliştirme ortamında kapsayıcı ASP.NET uygulamalarının basitleştirilmiş mimari diyagramı](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a>Senaryo 2: Konteynerleştirilmiş WCF hizmeti

Aşağıdaki şekil, konteynerleştirilmiş bir WCF hizmetine sahip 3 Katmanlı bir uygulama senaryosunu gösterir.

![Geliştirme ortamında kapsayıcı WCF hizmetinin basitleştirilmiş mimari diyagramı](./media/image5-3.5.png)

### <a name="benefits"></a>Avantajlar

Yekpare uygulamanızı bir kapta çalıştırmanın avantajları vardır. İlk olarak, uygulama için bir görüntü oluşturursunuz. Bu noktadan itibaren, her dağıtım aynı ortamda çalışır. Her kapsayıcı aynı işletim sistemi sürümünü kullanır, bağımlılıkların aynı sürümü yüklü, aynı .NET çerçeve sürümünü kullanır ve aynı işlem kullanılarak oluşturulur. Temel olarak, docker görüntüsü kullanarak uygulamanızın bağımlılıklarını kontrol eleştirirsiniz. Kapsayıcıları dağıttığınızda bağımlılıklar uygulamayla birlikte hareket emredilir.

Ek bir yararı geliştiriciler Windows Kapsayıcılar tarafından sağlanan tutarlı ortamda uygulama çalıştırabilirsiniz. Yalnızca belirli sürümlerle görünen sorunlar, bir evreleme veya üretim ortamında yüzeye çıkmak yerine hemen tespit edilebilir. Uygulamalar kapsayıcılarda çalıştırıldığında geliştirme ekibi üyeleri tarafından kullanılan geliştirme ortamlarında farklılıklar daha az önemlidir.

Konteyner uygulamaları da düz bir ölçek-out eğrisi var. Kapsayıcı uygulamalar, bir VM veya fiziksel makinede makine başına normal uygulama dağıtımlarına kıyasla daha fazla uygulama ve servis örneğine (kapsayıcılara göre) sahip olabilirsiniz. Bu, özellikle Kubernetes gibi orkestratörleri kullandığınızda, daha yüksek yoğunluk ve daha az gerekli kaynak anlamına gelir.

Konteynerleştirme, ideal durumlarda, uygulama kodu (C)\#herhangi bir değişiklik yapılmasını gerektirmez. Çoğu senaryoda, docker dağıtım meta veri dosyaları (Dockerfiles ve Docker Compose dosyaları) gerekir.

### <a name="next-steps"></a>Sonraki adımlar

Bu içeriği GitHub wiki'de daha ayrıntılı olarak keşfedin:

- [Windows Kapsayıcıları ve Docker ile .NET Framework web uygulamalarını nasıl kaplarlar?](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [Bir WCF hizmetine Docker Desteği Ekleme](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a>Walkthrough 3: Windows Kapsayıcıları tabanlı uygulamanızı Azure VM'lerine dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik yol kullanılabilirliği

Tam teknik izbile edinebilirsiniz eShopModernizing GitHub repo wiki:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

### <a name="overview"></a>Genel Bakış

Azure'daki Windows Server 2016 Sanal Makine'de (VM) Docker ana bilgisayara dağıtmak, geliştirme/test/evreleme ortamlarını hızla ayarlamanızı sağlar. Ayrıca, test edenlerin veya iş kullanıcılarının uygulamayı doğrulamaları için ortak bir yer sağlar. VM'ler, Hizmet Olarak Altyapı (IaaS) üretim ortamları da geçerli olabilir.

### <a name="goals"></a>Hedefler

Bu izbin amacı, Windows Kapsayıcılarını Windows Server 2016 veya sonraki sürümlerine dayalı Azure VM'lere dağıtırken sahip olduğunuz birden çok alternatifi size göstermektir.

### <a name="scenarios"></a>Senaryolar

Bu gözden geçirme de çeşitli senaryolar ele alınmıştır.

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a>Senaryo A: Docker Engine bağlantısı aracılığıyla dev bir bilgisayardan Azure VM'ye dağıtma

![Docker Engine bağlantısı aracılığıyla dev bir bilgisayardan Azure VM'ye dağıtma](./media/image5-4.png)

**Şekil 5-4.** Docker Engine bağlantısı aracılığıyla dev bir bilgisayardan Azure VM'ye dağıtma

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a>Senaryo B: Docker Kayıt Defteri aracılığıyla Azure VM'ye dağıtma

![Docker Kayıt Defteri aracılığıyla Azure VM'ye dağıtma](./media/image5-5.png)

**Şekil 5-5.** Docker Kayıt Defteri aracılığıyla Azure VM'ye dağıtma

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a>Senaryo C: Azure DevOps Hizmetlerinde CI/CD ardışık hatlarından bir Azure VM'sine dağıtma

![Azure DevOps Hizmetleri'ndeki CI/CD ardışık işlerinden Azure VM'ye dağıtma](./media/image5-6.png)

**Şekil 5-6.** Azure DevOps Hizmetleri'ndeki CI/CD ardışık işlerinden Azure VM'ye dağıtma

### <a name="azure-vms-for-windows-containers"></a>Windows Kapsayıcıları için Azure VM'ler

Windows Kapsayıcıları için Azure VM'ler, Docker Engine'in ayarlanmasıyla windows server 2016, Windows 10 veya sonraki sürümlere dayalı VM'lerdir. Çoğu durumda, Windows Server 2016 Azure VM'lerinde kullanılır.

Azure şu anda **Kapsayıcılarla Windows Server 2016**adında bir VM sağlar. Bu VM'yi, Windows Server Core veya Windows Nano Server ile yeni Windows Server Kapsayıcı özelliğini denemek için kullanabilirsiniz. Konteyner işletim sistemi görüntüleri yüklenir ve ardından VM Docker ile kullanıma hazırdır.

### <a name="benefits"></a>Avantajlar

Windows Kapsayıcıları şirket içi Windows Server 2016 VM'lerine dağıtılabilse de, Azure'a dağıttığınızda kullanıma hazır Windows Server Container VM'lerle başlamak için daha kolay bir yol elde edersiniz. Ayrıca, test edenler tarafından erişilebilen ortak bir çevrimiçi konum ve Azure sanal makine ölçek kümeleri aracılığıyla otomatik ölçeklenebilirlik de elde elabilirsiniz.

### <a name="next-steps"></a>Sonraki adımlar

Bu içeriği GitHub wiki'de daha ayrıntılı olarak keşfedin:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a>Walkthrough 4: Windows Kapsayıcıtabanlı uygulamalarınızı Azure Kapsayıcı Örneklerine (ACI) dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik yol kullanılabilirliği

Tam teknik izbile edinebilirsiniz eShopModernizing GitHub repo wiki:

[Uygulamaları ACI'ye Dağıtma (Azure Kapsayıcı Örnekleri)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

### <a name="overview"></a>Genel Bakış

[Azure Kapsayıcı Örnekleri (ACI),](https://docs.microsoft.com/azure/container-instances/) tek kapsayıcı örneklerini dağıtabileceğiniz kapsayıcı geliştirme/test/hazırlama ortamına sahip olmak için en hızlı yoldur.

### <a name="goals"></a>Hedefler

Bu izim, Windows Kapsayıcılarını Azure Kapsayıcı Örneklerine (ACI) dağıtırken ana senaryoları ve eShopModernizing Apps'ı ACI'ye nasıl dağıtabileceğinizi gösterir.

### <a name="scenarios"></a>Senaryolar

eShopModernizing uygulamalarını ACI'ye dağıtma konusunda, uygulamaların yalnızca birini veya tamamını dağıtma (MVC uygulaması, WebForms uygulaması veya WCF hizmeti) gibi varyasyonlar olabilir. Aşağıda gösterilen aşağıdaki senaryoda ASP.NET MVC uygulamasını ve SQL Server kapsayıcısını görebilirsiniz.

![Geliştirme ortamından ACI'ye dağıtın](./media/image5-3.5.6.png)

### <a name="benefits"></a>Avantajlar

Azure Container Instances, sanal makine sağlamak veya daha yüksek düzey bir hizmet benimsemek zorunda kalmadan Azure’da Docker kapsayıcıları oluşturmayı ve yönetmeyi kolaylaştırır. ACI ile, Azure'da doğrudan bir Windows kapsayıcısı dağıtabilir ve birkaç saniye içinde tam nitelikli bir etki alanı adı (FQDN) ile internete açabilirsiniz (Windows Konteyner görüntüsünü Docker Hub veya Azure Kapsayıcısı gibi docker kayıt defterinde hazır olması koşuluyla Kayıt Defteri).

### <a name="considerations"></a>Dikkat edilmesi gerekenler

Windows Kapsayıcılarını Azure Kapsayıcı Örneklerine (ACI) tam .NET Framework / ASP.NET veya SQL Server ile dağıtmak, normal bir Docker Hosts'a (Windows Containers ile Windows Server 2016 gibi) dağıtmak kadar hızlı değildir, çünkü Docker görüntüsünün her seferinde indirilmesi (Docker kayıt defterinden çekilmesi) ve SQL kapsayıcı görüntüsünün (15,1 GB) boyutları ve kapsayıcı ASP.NET görüntüsünün (13,9 GB) önemli ölçüde büyük olması gerekir, ancak kendi docker ana bilgisayar (kalıcı on-line Windows) korumak tan çok daha ucuzdur Sunucu 2016 Windows Containers VM ile Azure) Azure Kubernetes gibi bir bütün orkestratör söz değil (AKS) hangi, diğer taraftan, üretim dağıtımları için harika bir seçimdir.

Ana sonuç olarak, Azure Kapsayıcı Örnekleri'ni kullanmak, Geliştirme/Test senaryoları ve CI/CD ardışık hatları için çok cazip bir seçenektir.

## <a name="next-steps"></a>Sonraki adımlar

Bu içeriği GitHub wiki'de daha ayrıntılı olarak keşfedin:

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a>Walkthrough 5: Windows Kapsayıcı tabanlı uygulamalarınızı Azure Kapsayıcı Hizmeti'nde Kubernetes'e dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik yol kullanılabilirliği

Tam teknik izbile edinebilirsiniz eShopModernizing GitHub repo wiki:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a>Genel Bakış

Windows Kapsayıcıları'nı temel alan bir uygulamanın, IaaS VM'lerden daha da uzağa hareket eden platformları hızlı bir şekilde kullanması gerekir. Bu, yüksek ölçeklenebilirlik ve daha iyi otomatik ölçeklenebilirlik elde etmek ve otomatik dağıtımlar ve sürümlerde önemli bir iyileşme sağlamak için gereklidir. [Azure Konteyner Hizmetleri'nde](https://azure.microsoft.com/services/container-service/)bulunan orkestratör [Kubernetes'i](https://kubernetes.io/)kullanarak bu hedeflere ulaşabilirsiniz.

### <a name="goals"></a>Hedefler

Bu gözden geçirmenin amacı, Azure Kapsayıcı Hizmeti'nde Windows Kapsayıcı tabanlı bir uygulamayı Kubernetes'e *(K8*olarak da adlandırılır) nasıl dağıtılamayı öğrenmektir. Kubernetes'e sıfırdan dağıtmak iki aşamalı bir işlemdir:

1. Azure Kapsayıcı Hizmetine bir Kubernetes kümesi dağıtın.

2. Uygulamayı ve ilgili kaynakları Kubernetes kümesine dağıtın.

### <a name="scenarios"></a>Senaryolar

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a>Senaryo A: Bir dev ortamdan doğrudan bir Kubernetes kümesine dağıtma

![Geliştirme ortamından doğrudan bir Kubernetes kümesine dağıtın](./media/image5-7.png)

**Şekil 5-7.** Geliştirme ortamından doğrudan bir Kubernetes kümesine dağıtın

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a>Senaryo B: Azure DevOps Hizmetlerinde CI/CD ardışık hatlarından bir Kubernetes kümesine dağıtın

![Azure DevOps Hizmetleri'ndeki CI/CD ardışık hatlarından Bir Kubernetes kümesine dağıtın](./media/image5-8.png)

**Şekil 5-8.** Azure DevOps Hizmetleri'ndeki CI/CD ardışık hatlarından Bir Kubernetes kümesine dağıtın

### <a name="benefits"></a>Avantajlar

Kubernetes'teki bir kümeye dağıtımın birçok faydası vardır. En büyük yararı, kullanmak istediğiniz kapsayıcı örneklerinin sayısına (varolan düğümlerde iç ölçeklenebilirlik) ve kümedeki düğüm veya VM sayısına göre uygulamayı ölçeklendirebileceğiniz üretime hazır bir ortam elde edebilmenizdir ( kümenin küresel ölçeklenebilirliği).

Azure Kapsayıcı Hizmeti, azure için özel olarak popüler açık kaynak araçlarını ve teknolojilerini optimize eder. Hem kapsayıcılarınız hem de uygulama yapılandırmanız için taşınabilirlik sunan açık bir çözüm elde elabilirsiniz. Boyutu, ana bilgisayar sayısını ve orkestratör araçları-Konteyner Hizmeti diğer her şeyi işler seçin.

Kubernetes ile geliştiriciler fiziksel ve sanal makineler hakkında düşünmekten, aşağıdaki yetenekleri kolaylaştıran konteyner merkezli bir altyapı planlamaya kadar ilerleyebilirler:

- Birden fazla kapsayıcıya dayalı uygulamalar

- Kapsayıcı örneklerini çoğaltma ve yatay otomatik ölçeklendirme

- Adlandırma ve keşfetme (örneğin, dahili DNS)

- Dengeleme yükleri

- Güncele kaydetme

- Sırları dağıtma

- Uygulama sağlık kontrolleri

## <a name="next-steps"></a>Sonraki adımlar

Bu içeriği GitHub wiki'de daha ayrıntılı olarak keşfedin:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a>Walkthrough 6: Windows Kapsayıcılar tabanlı uygulamalarınızı Kapsayıcılar için Azure Uygulama Hizmetine dağıtma

### <a name="technical-walkthrough-availability"></a>Teknik yol kullanılabilirliği

Tam teknik izbile edinebilirsiniz eShopModernizing GitHub repo wiki:

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a>Genel Bakış

Windows Kapsayıcıları'nı kullanan basit bir kapsayıcı uygulaması, Kapsayıcılar için Azure Uygulama Hizmeti'ne kolayca dağıtılabilir. Bu, çoğu Windows Kapsayıcı tabanlı uygulamalar için önerilen yaklaşımdır.

### <a name="goals"></a>Hedefler

Bu gözden geçirmenin amacı, bir kayıt defterinden (Docker Hub veya Azure Kapsayıcı Kayıt Defteri) Kapsayıcılar için Azure Uygulama Hizmetine Windows Kapsayıcı tabanlı bir uygulamayı nasıl dağıtılamayı öğrenmektir.

### <a name="scenario"></a>Senaryo

![Kapsayıcılar için Azure Uygulama Hizmetine Windows Kapsayıcı tabanlı uygulamayı dağıtma](./media/image5-11.png)

### <a name="benefits"></a>Avantajlar

Kapsayıcılar için Azure Uygulama Hizmetine dağıtmak, Azure Uygulama Hizmeti'nin PaaS avantajlarıyla eşleştirilmiş kapsayıcıların avantajlarını sunar. Uygulama hizmeti hem dikey hem de yatay olarak kolayca ölçeklenebilir ve değişen talepleri karşılamak üzere otomatik ölçeklendirilecek şekilde yapılandırılabilir. Güncelleştirmeler sıfır kapalı kalma süresi yle gerçekleştirilebilir ve bir kayıt defterinden sürekli dağıtım yapılandırması da kolayca yapılandırılabilir.

## <a name="next-steps"></a>Sonraki adımlar

Bu içeriği GitHub wiki'de daha ayrıntılı olarak keşfedin:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

> [!div class="step-by-step"]
> [Önceki](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [Sonraki](conclusions.md) <!-- Next Chapter -->
