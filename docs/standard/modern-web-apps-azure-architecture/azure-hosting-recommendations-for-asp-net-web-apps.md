---
title: ASP.NET Core web uygulamaları için öneriler barındırma azure
description: ASP.NET Core ve Azure ile modern Web uygulamaları mimari | ASP.NET web uygulamaları için öneriler barındırma azure
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eccb57e5ccf9162a6e6ce11434e644682881debc
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>ASP.NET Core Web uygulamaları için öneriler barındırma azure

> "İş kılavuzları her yerde bulut (diğer adıyla SaaS) uygulamaları almak için BT departmanları atlayarak ve Dergi aboneliğinin gibi bunlar için ödeme. Ve hizmet artık gerekli olmadığında abonelik sol üst köşedeki kullanılmayan hiçbir donanım ile iptal."  
> _\- Daryl Plummer, Gartner analisti_

## <a name="summary"></a>Özet

Ne olursa olsun, uygulamanızın gereksinimlerine ve mimari, Windows Azure bunu destekleyebilir. Barındırma gereksinimlerinize Hizmetleri düzinelerce oluşan bir son derece Gelişmiş uygulama statik web sitesine kadar basit olabilir. ASP.NET Core tek yapılı web uygulamaları ve destekleyici hizmetler için önerilen çeşitli iyi bilinen yapılandırmaları vardır. Aşağıdaki öneriler barındırılması, uygulamalar, tek tek işlemler veya veri olup tam kaynak türüne göre gruplandırılır.

## <a name="web-applications"></a>Web Uygulamaları

Web uygulamaları ile barındırılabilir:

-   App Service Web Apps

-   Kapsayıcılar

-   Azure Service Fabric

-   Sanal makineler (VM'ler)

Bu, App Service Web Apps çoğu senaryo için önerilen yaklaşım şunlardır. Mikro hizmet mimarisi için bir kapsayıcı dayalı yaklaşım veya service fabric göz önünde bulundurun. Uygulamanızı çalıştıran makineler hakkında daha fazla denetime ihtiyacınız varsa, Azure sanal makineleri göz önünde bulundurun.

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps web uygulamalarını barındırmak için en iyi duruma getirilmiş tam olarak yönetilen bir platform sağlar. Azure alır altyapınızla ilgilenirken, iş mantığına odaklanmanıza olanak tanır çalıştırın ve uygulama ölçeklendirme için gereken sunan bir platform-as-a-service(PaaS) olur. Önemli özelliklerinden bazıları App Service Web Apps:

-   DevOps iyileştirmesi (sürekli tümleştirme ve teslimat, birden çok ortamları A / B testi, komut dosyası oluşturma desteği)

-   Genel ölçeği ve yüksek kullanılabilirlik

-   SaaS platformları ve şirket içi verilerinizi bağlantılar

-   Güvenlik ve uyumluluk

-   Visual Studio tümleştirmesi

Azure uygulama hizmeti, çoğu web uygulamaları için en iyi seçimdir. Dağıtım ve yönetim platformuyla doğrudan tümleşik, siteleri hızlı bir şekilde yüksek trafik yükleri işlemek için ölçeklendirilebilir ve yerleşik Yük Dengeleme ve trafik Yöneticisi yüksek kullanılabilirlik sağlar. Azure uygulama hizmeti var olan sitelere bir çevrimiçi geçiş aracı ile kolayca Web uygulama Galeriden bir açık kaynak uygulama kullanın ya da framework ve tercih ettiğiniz Araçları'nı kullanarak yeni bir site oluşturun taşıyabilirsiniz. WebJobs özelliğini arka plan işi uygulama hizmeti web uygulamanızı işleme eklemek kolaylaştırır.

### <a name="containers-and-azure-container-service"></a>Kapsayıcılar ve Azure kapsayıcı hizmeti

Azure kapsayıcı hizmeti oluşturmak, yapılandırmak ve sanal makinelerin kapsayıcılı uygulamaları çalıştırmak için yapılandırılmış bir kümeyi yönetmek için daha basit hale getirir. En iyi duruma getirilmiş bir popüler açık kaynak planlama ve düzenleme araçları yapılandırmasını kullanır. Bu, varolan yeteneklerinizi kullanın veya Microsoft Azure üzerinde kapsayıcı tabanlı uygulamaları dağıtmak ve yönetmek için topluluk uzmanlığı büyük ve artan bir gövdesi üzerine çizmek sağlar.

Azure kapsayıcı hizmeti oluşturmak, yapılandırmak ve sanal makinelerin kapsayıcılı uygulamaları çalıştırmak için yapılandırılmış bir kümeyi yönetmek için daha basit hale getirir. En iyi duruma getirilmiş bir popüler açık kaynak planlama ve düzenleme araçları yapılandırmasını kullanır. Bu, varolan yeteneklerinizi kullanın veya Microsoft Azure üzerinde kapsayıcı tabanlı uygulamaları dağıtmak ve yönetmek için topluluk uzmanlığı büyük ve artan bir gövdesi üzerine çizmek sağlar.

Azure kapsayıcı hizmeti tek amacı, açık kaynaklı araçları ve bugün Microsoft'un müşterileri arasında popüler teknolojileri kullanarak bir kapsayıcı barındırma ortamı sağlamaktır. Bu amaçla, Azure kapsayıcı hizmeti standart API uç noktaları için seçilen orchestrator (DC/OS, Docker Swarm veya Kubernetes) kullanıma sunar. Bu uç noktalar kullanarak, bu Uç noktalara Konuşmayı yeteneğine sahip herhangi bir yazılım yararlanabilirsiniz. Örneğin, Docker Swarm uç nokta söz konusu olduğunda, Docker komut satırı arabirimi (CLI) kullanmayı seçebilirsiniz. DC/OS için DCOS CLI seçebilirsiniz. Kubernetes için kubectl seçebilirsiniz. Şekil 11-1, kapsayıcı kümelerinizi yönetmek için bu uç noktaları nasıl kullanacağınız gösterir.

![](./media/image11-1.png)

**Şekil 11-1.** Docker, Kubernetes veya DC/OS uç noktaları ile Azure kapsayıcı Hizmeti Yönetimi.

### <a name="azure-service-fabric"></a>Azure Service Fabric

Yeni bir uygulama oluşturma ya da mevcut bir uygulamayı mikro hizmet mimarisi kullanmak üzere yeniden yazmadan Service Fabric iyi bir seçimdir. Paylaşılan bir havuzunda makineleri çalıştırmak, uygulamaları küçük başlayın ve büyük ölçekli yüzlerce veya binlerce gerektiğinde makinelerin büyüyebileceği. Durum bilgisi olan hizmetler tutarlı ve güvenilir bir şekilde uygulama durumunu depolamak kolaylaştırır ve Service Fabric otomatik olarak hizmet bölümlendirme, ölçeklendirme ve kullanılabilirlik tarafından yönetilir. Service Fabric Webapı açık Web arabirimi ile .NET (OWIN) ve ASP.NET Core için de destekler. Uygulama hizmeti ile karşılaştırıldığında, Service Fabric ayrıca daha fazla denetime ya da doğrudan erişim, altyapının sağlar. Sunucu başlangıç görevleri yapılandırmak veya sunucularınızı uzaktan kullanabilirsiniz.

### <a name="azure-virtual-machines"></a>Azure sanal makineler

Uygulama hizmeti veya Service Fabric çalıştırmak için önemli değişiklikler gerektiren var olan bir uygulamanız varsa, buluta geçiş basitleştirmek için sanal makineleri seçebilir. Ancak, doğru şekilde güvenli hale getirme, yapılandırma ve bakımını yapmak VM'ler gerektirir çok daha fazla zaman ve Azure App Service ve Service Fabric karşılaştırıldığında BT uzmanlık. Azure sanal makineleri düşünüyorsanız, düzeltme eki, güncelleştirme ve VM ortamınızı yönetmek için gerekli devam eden bakım çaba dikkate emin olun. Azure sanal makinelerin App Service ve Service Fabric Platform olarak-hizmet (Paas) durumdayken-olarak-hizmet altyapı (Iaas) şeklindedir.

#### <a name="feature-comparison"></a>Özellik karşılaştırması

| Uygulama hizmeti özelliği | Service Fabric | Sanal makine |
|---------|----------|----------|
| Neredeyse anında dağıtım | X | X | |
| Daha büyük makinelere dağıtın olmadan ölçeği | X | X | |
| İçerik ve yapılandırma örnekleri paylaşır; gereksiz yeniden dağıtın veya ölçeklendirdiğinizde yeniden yapılandırın | X | X | |
| Birden çok dağıtım ortamı (üretim, hazırlama) | X | X | |
| Otomatik işletim sistemi güncelleştirme yönetimi | X | | |
| Sorunsuz 32/64 bit platformlarda arasında geçiş yapma | X | | |
| Git, FTP ile kod dağıtma | X | | X |
| WebDeploy koduyla dağıtma | X | | X |
| Kod TFS ile Dağıt | X | X | X |
| Ana bilgisayar web veya web hizmeti katmanı çok katmanlı mimarisi | X | X | X |
| Hizmet veri yolu, depolama, SQL veritabanı gibi Azure hizmetlerine erişim | X | X | X |
| Tüm özel MSI yükleme | | X | X |

## <a name="logical-processes"></a>Mantıksal işlemleri

Uygulama geri kalanından ayrılmış ayrı mantıksal işlemlerin, "sunucusuz" bir şekilde Azure işlevleri için bağımsız olarak dağıtılabilir. Azure işlevleri yalnızca çalıştırmak için uygulamayı veya altyapı hakkında endişelenmeden belirli bir sorun için gereken kod yazmanıza izin verir. Programlama dilleri, C dahil olmak üzere çeşitli arasından seçim yapabilirsiniz\#, F\#, Node.js, Python ve PHP, görev için en verimli dil elinizdeki çekme olanak sağlar. Bulut tabanlı çoğu çözümleri gibi kullanımınız yalnızca zaman miktarı için ödeme ve gerektiğinde ölçeği Azure işlevleri güvenebilir.

## <a name="data"></a>Veri

Uygulamanız için uygun veri sağlayıcısı için söz konusu verileri kullanabilmesi için azure çok çeşitli veri depolama seçenekleri sunar.

İşlem, ilişkisel veri için en iyi seçenek Azure SQL veritabanlarıdır. Yüksek performans okuma çoğunlukla verileri için bir Azure SQL veritabanı tarafından yedeklenen bir Redis önbelleği iyi bir çözümdür.

Yapılandırılmamış JSON verilerini çeşitli şekillerde, BLOB'ları veya Azure Storage tablolarda SQL veritabanı sütunlarından documentdb'ye depolanabilir. Bu, DocumentDB işlevselliği sorgulama en iyi sunar ve çok sayıda sorgulama desteklemelidir JSON tabanlı belgeler için önerilen bir seçenektir.

Uygulama davranışına düzenlemek için kullanılan geçici komut veya olay tabanlı verileri Azure hizmet veri yolu veya Azure depolama kuyrukları kullanabilirsiniz. Azure depolama veri Yolu'nun daha fazla esneklik sunar ve önemsiz olmayan ileti içinde ve uygulamalar arasında için önerilen hizmetidir.

## <a name="architecture-recommendations"></a>Mimari önerileri

Uygulamanızın gereksinimlerine mimarisinin dikte. Birçok farklı Azure Hizmetleri doğru olanı önemli bir karardır seçme kullanılabilir. Microsoft ortak senaryolar için iyileştirilen tipik mimarileri tanımlamaya yardımcı olmak için başvuru mimarileri Galerisi sunar. Maps yakından için uygulamanızın gereksinimlerine ya da en az sunduğu bir başlangıç noktası bir referans mimarisi bağlayabilirsiniz.

Şekil 11-2 bir örnek referans mimarisi gösterilir. Bu diyagramda, pazarlama için en iyi hale getirilmiş bir Sitecore içerik yönetim sistemi Web sitesi için önerilen mimarisi yaklaşımı açıklanmaktadır.

![](./media/image11-2.png)

**Şekil 11-2.** Web sitesi referans mimarisi pazarlama Sitecore.

**Başvuruları – Azure önerileri barındırma**

-   Azure çözüm Architectures\
    <https://azure.microsoft.com/solutions/architecture/>

-   Azure Geliştirici Guide\
    <https://azure.microsoft.com/campaigns/developer-guide/>

-   Azure uygulama hizmeti nedir? \
    <https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is>

-   Azure uygulama hizmeti, sanal makineleri, Service Fabric ve Cloud Services Comparison\
    <https://docs.microsoft.com/azure/app-service-web/choose-web-site-cloud-service-vm>

>[!div class="step-by-step"]
[Önceki] (geliştirme-işlem-için-azure.md)
