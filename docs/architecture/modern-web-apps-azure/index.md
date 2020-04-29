---
title: ASP.NET Core ve Azure ile modern web uygulamaları tasarlama
description: ASP.NET Core ve Azure kullanarak tek parçalı Web uygulamaları oluşturmaya yönelik uçtan uca rehberlik sağlayan bir kılavuz.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: 936a068507116033ad178f26e77945f30f70387e
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507199"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>ASP.NET Core ve Microsoft Azure ile Modern Web Uygulamaları Tasarlama

![Mimarel Modern Web uygulamaları kılavuzu 'nun kitap kapağı resmi.](./media/index/web-application-guide-cover-image.png)

**Sürüm v 3.1** -ASP.NET Core 3,1 ' ye güncelleştirildi

YAYIMLAYAN

Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı © 2020 Microsoft Corporation

Tüm hakları saklıdır. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve "ticari markalar" https://www.microsoft.com Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. ' in ticari markalarıdır.

Docker balina logosu,, izin tarafından kullanılan Docker, Inc. ' in tescilli ticari markasıdır.

Diğer tüm işaretler ve amblemler kendi sahiplerinin mülkiyetindedir.

Yazar:

> **Steve "ardalış" Smith** -yazılım mimarı ve trainer- [Ardalis.com](https://ardalis.com)

Edit

> **Maira Wenzel**

## <a name="action-links"></a>Eylem bağlantıları

- Bu e-kitap ayrıca bir PDF biçiminde (Yalnızca Ingilizce sürüm) [indirilebilir](https://aka.ms/webappebook)

- [GitHub 'da başvuru uygulaması Eshoponweb 'i](https://github.com/dotnet-architecture/eShopOnWeb) kopyalama/çatal

## <a name="introduction"></a>Giriş

.NET Core ve ASP.NET Core geleneksel .NET geliştirme konusunda çeşitli avantajlar sunar. Aşağıdakilerden bazıları veya tümü uygulamanızın başarısı için önemliyse, sunucu uygulamalarınız için .NET Core ' u kullanmanız gerekir:

- Platformlar arası destek.

- Mikro hizmetlerin kullanımı.

- Docker Kapsayıcıları kullanımı.

- Yüksek performans ve ölçeklenebilirlik gereksinimleri.

- Aynı sunucuda .NET sürümlerinin uygulamaya göre yan yana sürümü oluşturma.

Geleneksel .NET uygulamaları, bu gereksinimlerin birçoğunu destekler ve ASP.NET Core ve .NET Core, yukarıdaki senaryolar için geliştirilmiş destek sunacak şekilde iyileştirildi.

Daha fazla kuruluş, Microsoft Azure gibi hizmetleri kullanarak Web uygulamalarını bulutta barındırmak üzere tercih ediyor. Uygulamanız veya kuruluşunuz için önemli bir öneme sahipseniz, uygulamanızı bulutta barındırmayı göz önünde bulundurmanız gerekir:

- Veri merkezi maliyetlerinde daha az yatırım (donanım, yazılım, boşluk, yardımcı programlar, sunucu yönetimi vb.)

- Esnek fiyatlandırma (boşta kapasite için değil, kullanıma göre ödeme yapın).

- Aşırı güvenilirlik.

- Geliştirilmiş uygulama Mobility; Uygulamanızın nerede ve nasıl dağıtıldığını kolayca değiştirin.

- Esnek kapasite; gerçek ihtiyaçlarına göre ölçeği artırma veya azaltma.

Azure 'da barındırılan ASP.NET Core ile Web uygulamaları oluşturmak, geleneksel alternatifler üzerinde birçok rekabet avantajı sunar. ASP.NET Core Modern Web uygulaması geliştirme uygulamaları ve bulut barındırma senaryoları için iyileştirilmiştir. Bu kılavuzda, bu özelliklerden en iyi şekilde yararlanmak için ASP.NET Core uygulamalarınızı nasıl mimareceğinizi öğreneceksiniz.

## <a name="purpose"></a>Amaç

Bu kılavuz, ASP.NET Core ve Azure kullanarak *tek parçalı* Web uygulamaları oluşturmaya yönelik uçtan uca yönergeler sağlar. Bu bağlamda, "monoparçalı", bu uygulamaların bir etkileşim Hizmetleri ve uygulamaları koleksiyonu olarak değil, tek bir birim olarak dağıtılmasının gerçeğini ifade eder.

Bu kılavuz, ["_.net mikro hizmetleri" için tamamlayıcı bir kılavuzdur. _](../microservices/index.md)Docker, mikro hizmetler ve kapsayıcı dağıtımında kurumsal uygulamaları barındırmak için daha fazla odaklanan, Kapsayıcılı .NET uygulamaları için mimari.

### <a name="net-microservices-architecture-for-containerized-net-applications"></a>.NET mikro hizmetleri. Kapsayıcılı .NET Uygulamaları Mimarisi

- **e-kitap**  
  <https://aka.ms/MicroservicesEbook>
- **Örnek uygulama**  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalıdır?

Bu kılavuzun hedef kitlesi, bulutta Microsoft teknolojilerini ve hizmetlerini kullanarak modern web uygulamaları oluşturmaya ilgilenen temel geliştiriciler, geliştirme müşteri adayları ve mimarilerdir.

İkincil hedef kitle, zaten ASP.NET veya Azure 'u bildiğiniz ve yeni veya mevcut projeler için ASP.NET Core yükseltme konusunda anlamlı olup olmadığı hakkında bilgi arayan teknik karar mekanizmalarıdır.

## <a name="how-you-can-use-this-guide"></a>Bu Kılavuzu nasıl kullanabileceğiniz

Bu kılavuz, modern .NET teknolojileri ve Azure ile Web uygulamaları oluşturmaya odaklanan görece küçük bir belgeye yoğunlaştırılmıştır. Bu nedenle, bu tür uygulamaları ve teknik konuları anlama temelini sağlamak için tamamen okunabilir. Kılavuz, örnek uygulamayla birlikte bir başlangıç noktası veya başvuru işlevi de sunabilir. İlişkili örnek uygulamayı kendi uygulamalarınız için bir şablon olarak veya uygulamanızın bileşen parçalarını nasıl düzenleyebileceğini görmek için kullanın. Kendi uygulamanız için bu seçenekleri katdığınızda, kılavuzun ilkelerine ve mimari ve teknoloji seçeneklerinin kapsamına ve kararına dikkat edin.

Bu noktaların ve fırsatların yaygın olarak anlaşılmasına yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin. Her bir gövdenin ortak bir terminoloji kümesinden ve temel ilkelerin üzerinde çalışmasını sağlamak, mimari desenlerinin ve uygulamaların tutarlı olmasını sağlamaya yardımcı olur.

## <a name="references"></a>Başvurular

- **Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma**  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[Sonraki](modern-web-applications-characteristics.md)
