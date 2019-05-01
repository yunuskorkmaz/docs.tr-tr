---
title: Azure barındırma önerileri için ASP.NET Core web uygulamaları
description: ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama | Azure barındırma önerileri ASP.NET web uygulamaları için
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: cda4c002c73e2dd0db1b2d5d1fa8bc76903c5c62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019496"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Azure barındırma önerileri için ASP.NET Core web uygulamaları

> "Satır iş liderleri her yerde buluttan (diğer adıyla SaaS) uygulamaları almak için BT departmanları atlayarak ve magazine aboneliği yaptıkları gibi bunlar için ödeme yapma. Ve hizmet artık gerekli olmadığında, abonelik sol üst köşedeki kullanılmayan hiçbir donanım ile iptal edebilirsiniz. "  
> _\- Daryl Plummer, Gartner analisti_

İnovasyonunuz ne olursa olsun, uygulamanızın ihtiyaçlarına ve mimarisi, Windows Azure, destekleyebilir. Barındırma gereksinimlerinize statik bir Web sitesi Hizmetleri onlarca oluşan karmaşık bir uygulama olarak basit olabilir. ASP.NET Core tek parça web uygulamaları ve destekleyici hizmetler için önerilen çeşitli iyi bilinen yapılandırmaları vardır. Bu makalede bulunan önerileri barındırılması, uygulamalar, tek tek işlemleri veya veri olup tam kaynak türüne göre gruplandırılır.

## <a name="web-applications"></a>Web uygulamaları

Web uygulamaları ile barındırılabilir:

- App Service Web Apps

- Kapsayıcılar

- Azure Service Fabric

- Sanal makineler (VM)

Bu App Service Web Apps için önerilen çoğu senaryo için yaklaşımdır. Mikro hizmet mimarileri için bir kapsayıcı tabanlı bir yaklaşım veya Service Fabric göz önünde bulundurun. Uygulamanızı çalıştıran makineler hakkında daha fazla denetime ihtiyacınız varsa, Azure sanal makineler göz önünde bulundurun.

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps, web uygulamalarını barındırmak için en iyi duruma getirilmiş tam olarak yönetilen bir platform sunar. Bu Azure altyapınızla ilgilenirken, sizin işlerinize odaklanmanızı odaklanmanıza olanak tanır, çalıştırmak ve uygulamayı ölçeklendirmek gereken sunan bir hizmet (PaaS) olarak platformudur. App Service Web Apps'in temel özelliklerinden bazıları:

- DevOps iyileştirmesi (sürekli tümleştirme ve teslim, birden çok ortama, A / B testi, komut dosyası oluşturma desteği).

- Küresel ölçekli ve yüksek kullanılabilirlik.

- SaaS platformları ve şirket içi verilerinizi bağlantılar.

- Güvenlik ve uyumluluk.

- Visual Studio tümleştirmesi.

Azure App Service, çoğu web uygulaması için en iyi seçenektir. Dağıtım ve yönetim süreçleri platform ile tümleştirilmiştir, siteler hızla yüksek trafik yüklerinin altından kalkacak şekilde ölçeklendirilebilir ve yerleşik Yük Dengeleme ve trafik Yöneticisi yüksek kullanılabilirlik sağlar. Bir çevrimiçi geçiş aracı ile kolayca Azure App Service için var olan siteler, Web uygulamaları Galerisi'nden açık kaynaklı uygulama kullanma veya çerçevesi ve tercih ettiğiniz araçları kullanarak yeni bir site oluşturmak taşıyabilirsiniz. WebJobs özelliği, App Service web uygulamanıza işleme arka plan işinin eklemenizi kolaylaştırır.

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Service (AKS), barındırılan Kubernetes ortamınızı hızla ve kolayca kapsayıcı düzenleme uzmanlığı gerektirmeden kapsayıcıya alınmış uygulamaları dağıtmayı ve yönetmeyi yönetir. Sağlama, yükseltme ve uygulamalarınızı çevrimdışı duruma getirmeden kaynakları isteğe bağlı olarak ölçeklendirme Süren işlemlerin ve bakımın yükünü de kaldırır.

AKS, karmaşıklığı ve azure'a SORUMLULUĞUN çoğunu devrederek bir Kubernetes kümesi yönetmenin işlemsel ek yükü azaltır. Barındırılan bir Kubernetes hizmeti, sistem durumu izleme ve sizin için bakım gibi kritik görevleri Azure tanıtıcıları. Ayrıca, yalnızca aracı düğümleri için yönetici değil, kümeleri içinde ödeme. Yönetilen bir Kubernetes hizmeti olarak Aks Aşağıdakileri sağlar:

- Otomatik Kubernetes sürüm yükseltmeleri ve düzeltme eki uygulama.
- Kolay küme ölçeklendirme.
- Kendi kendini onaran barındırılan denetim düzlemi (Yöneticiler).
- Maliyet tasarrufu - yalnızca çalışan aracı havuz düğümleri için ödeme yaparsınız.

AKS kümenizde düğümleri yönetimi işlemleri Azure ile artık birçok el ile Küme yükseltme gibi görevleri gerekir. Azure Bu kritik bakım görevlerini sizin için gerçekleştirdiğinden, AKS doğrudan erişim sağlamaz (gibi SSH ile) kümeye.

### <a name="azure-service-fabric"></a>Azure Service Fabric

Yeni bir uygulama oluşturuyor ya da bir mikro hizmet mimarisi kullanan mevcut bir uygulamayı yeniden yazma, Service Fabric iyi bir seçimdir. Paylaşılan makine havuzu üzerinde çalışan, uygulamalar küçükten başlayabilir ve yüzlerce veya binlerce makineye gerektiği gibi makineyle muazzam bir ölçeğe uygun şekilde büyütüldüğünü görürsünüz. Durum bilgisi olan hizmetler uygulama durumunu tutarlı ve güvenilir bir şekilde depolamak kolaylaştırır ve Service Fabric otomatik olarak hizmet bölümleme, ölçeklendirme ve kullanılabilirlik sizin yerinize yönetir. Service Fabric .NET (OWIN) ve ASP.NET Core Webapı açık Web arabirimine sahip de destekler. App Service ile karşılaştırıldığında Service Fabric ayrıca daha fazla denetime veya doğrudan erişim için temel alınan altyapı sağlar. Siz sunucularınıza uzaktan bağlanabilir veya sunucu başlatma görevleri yapılandırabilirsiniz.

### <a name="azure-virtual-machines"></a>Azure sanal makineleri

App Service veya Service Fabric çalıştırmak için önemli değişiklikler gerektirecek bir var olan bir uygulamanız varsa, buluta geçirme basitleştirmek için sanal makineleri seçebilirsiniz. Ancak, doğru yapılandırmak, güvenliğini sağlamak ve bakımını yapmak Vm'leri gerektirir çok daha fazla zaman ve IT uzmanlığı için Azure App Service ve Service Fabric karşılaştırması. Azure sanal makineleri düşünüyorsanız, düzeltme eki uygulama, güncelleştirme ve VM ortamınızı yönetmek için gereken sürekli bir bakım çabası dikkate emin olun. Azure sanal makineleri olan altyapı (Iaas), hizmet olarak App Service ve Service Fabric PaaS çalışırken.

#### <a name="feature-comparison"></a>Özellik karşılaştırması

| Özellik                                                                                    | App Service | Kapsayıcılar (AKS) | Service Fabric | Sanal makine |
| ------------------------------------------------------------------------------------------ | ----------- | ---------------- | -------------- | --------------- |
| Neredeyse anında dağıtım                                                                    | X           | X                | X              |                 |
| Yeniden dağıtmadan daha büyük makinelere ölçeklendirme                                               | X           | X                | X              |                 |
| Örnekleri içeriği ve yapılandırmayı paylaşır; yeniden dağıtın veya ölçeklendirme RECONFIGURE gerek | X           | X                | X              |                 |
| Birden çok dağıtım ortamı (üretim, hazırlama)                                     | X           | X                | X              |                 |
| Otomatik işletim sistemi güncelleştirme yönetimi                                                             | X           | X                |                |                 |
| Sorunsuz 32/64 bit platformlar arasında geçiş yapma                                             | X           | X                |                |                 |
| Git ve FTP ile kod dağıtma                                                                  | X           | X                |                | X               |
| WebDeploy ile kod dağıtma                                                                 | X           | X                |                | X               |
| TFS ile kod dağıtma                                                                       | X           | X                | X              | X               |
| Barındırma web veya çok katmanlı mimarinin web hizmet katmanı                                    | X           | X                | X              | X               |
| Service Bus, depolama, SQL veritabanı gibi Azure hizmetlerine erişim                              | X           | X                | X              | X               |
| Herhangi bir özel MSI'yi yükleme                                                                     |             | X                | X              | X               |

## <a name="logical-processes"></a>Mantıksal işlemleri

Uygulama geri kalanından birbirinden ayrı mantıksal işlemlerin "sunucusuz" bir şekilde Azure işlevleri için bağımsız olarak dağıtılabilir. Azure işlevleri yalnızca çalıştırmak için uygulama veya altyapı hakkında endişelenmeden belirli bir sorun için ihtiyacınız olan kod yazmanıza olanak sağlar. Programlama dilleri, C de dahil olmak üzere çeşitli arasından seçim yapabilirsiniz\#, F\#, Node.js, Python ve PHP, eldeki en verimli dil görev için çekme etmenize imkan sağlar. Çoğu bulut tabanlı çözümler gibi kullanımınız yalnızca zaman miktarı ödeme yapar ve Azure işlevleri'nin ölçeği gerektikçe güvenebilir.

## <a name="data"></a>Veri

Uygulamanızı uygun veri sağlayıcısı için söz konusu verileri kullanabilmesi için azure, çok çeşitli veri depolama seçenekleri sunar.

İşlem, ilişkisel veri, Azure SQL veritabanı en iyi seçenektir. Yüksek performanslı okuma çoğunlukla veriler için bir Azure SQL veritabanı tarafından desteklenen bir Redis önbelleği iyi bir çözümdür.

Yapılandırılmamış JSON verilerini çeşitli şekillerde, Blobları veya tabloları, Azure depolama, SQL veritabanı sütunlarından documentdb'ye depolanabilir. Bu, DocumentDB işlevi sorgulanırken en iyi sunar ve çok sayıda sorgulama desteklemelidir, JSON tabanlı belgeleri için önerilen seçenektir.

Uygulama davranışını düzenlemek için kullanılan geçici komutu veya olay tabanlı verileri, Azure Service Bus veya Azure depolama kuyruklarını kullanabilirsiniz. Azure depolama veri yolu, daha fazla esneklik sunar ve önemsiz içinde ve uygulamalar arasında ileti için önerilen hizmetidir.

## <a name="architecture-recommendations"></a>Mimari önerileri

Uygulamanızın gereksinimlerini mimarisinin belirleyen unsurlar olmalıdır. Birçok farklı Azure hizmetlerini kullanılabilir. Doğru olanı seçme önemli bir karardır. Microsoft, yaygın senaryolar için en iyi duruma getirilmiş tipik mimariler belirlemenize yardımcı olması için başvuru mimarileri Galerisi sunar. Bir başvuru mimarisi, haritalar, uygulamanızın gereksinimleri için yakından veya daha az sunar, başlangıç noktası bulabilirsiniz.

Şekil 11-2, bir örnek başvuru mimarisini gösterir. Bu diyagramda, pazarlama için en iyi duruma getirilmiş Sitecore içerik yönetim sistemi Web sitesi için önerilen mimari bir yaklaşım açıklanmaktadır.

![](./media/image11-2.png)

**Şekil 11-1.** Sitecore pazarlama Web sitesi başvuru mimarisi.

**Başvuruları – Azure barındırma önerileri**

- Azure çözüm Architectures\
  <https://azure.microsoft.com/solutions/architecture/>

- Azure Geliştirici Guide\
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Web Apps overview\
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Azure App Service, sanal makineler, Service Fabric ve Cloud Services comparison\
  <https://docs.microsoft.com/azure/app-service-web/choose-web-site-cloud-service-vm>

- Azure Kubernetes Service'i (AKS) giriş \
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Önceki](development-process-for-azure.md)