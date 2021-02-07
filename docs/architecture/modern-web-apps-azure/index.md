---
title: ASP.NET Core ve Azure ile modern web uygulamaları tasarlama
description: ASP.NET Core ve Azure kullanarak tek parçalı Web uygulamaları oluşturmaya yönelik uçtan uca rehberlik sağlayan bir kılavuz.
author: ardalis
ms.author: wiwagn
ms.date: 02/02/2021
ms.openlocfilehash: 37aec94625071fdc07f2b8433f6e9ef200d92099
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754595"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>ASP.NET Core ve Microsoft Azure ile Modern Web Uygulamaları Tasarlama

![Mimarel Modern Web uygulamaları kılavuzu 'nun kitap kapağı resmi.](./media/index/web-application-guide-cover-image.png)

**Sürüm v 5.0** -ASP.NET Core 5,0 ' ye güncelleştirildi

Kitap güncelleştirmeleri ve topluluk katkılarına yönelik [changelog](https://aka.ms/aspnet-ebook-changelog) 'u inceleyin.

YAYIMLAYAN

Microsoft Geliştirici bölümü, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation 'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı © 2021 Microsoft Corporation

All rights reserved. Bu kitabın içeriğinin herhangi bir bölümü herhangi bir biçimde veya herhangi bir şekilde veya başka bir şekilde herhangi bir şekilde çoğaltılamaz veya herhangi bir şekilde gönderilebilir.

Bu kitap, "olduğu gibi" verilmiştir ve yazarın görünümlerini ve opnons 'yi ifade eder. URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu kitapta ifade edilen görünümler, eklentiler ve bilgiler bildirimde bulunmadan değiştirilebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve <https://www.microsoft.com> "ticari markalar" Web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

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

.NET 5 ve ASP.NET Core geleneksel .NET geliştirme konusunda çeşitli avantajlar sunar. Aşağıdakilerden bazıları veya tümü uygulamanızın başarısı için önemliyse, sunucu uygulamalarınız için .NET 5 ' i kullanmanız gerekir:

- Platformlar arası destek.

- Mikro hizmetlerin kullanımı.

- Docker Kapsayıcıları kullanımı.

- Yüksek performans ve ölçeklenebilirlik gereksinimleri.

- Aynı sunucuda .NET sürümlerinin uygulamaya göre yan yana sürümü oluşturma.

Geleneksel .NET uygulamaları bu gereksinimlerin birçoğunu destekler ve ASP.NET Core ve .NET 5, yukarıdaki senaryolar için geliştirilmiş destek sunacak şekilde iyileştirilmiştir.

Daha fazla kuruluş, Microsoft Azure gibi hizmetleri kullanarak Web uygulamalarını bulutta barındırmak üzere tercih ediyor. Uygulamanız veya kuruluşunuz için önemli bir öneme sahipseniz, uygulamanızı bulutta barındırmayı göz önünde bulundurmanız gerekir:

- Veri merkezi maliyetlerinde daha az yatırım (donanım, yazılım, boşluk, yardımcı programlar, sunucu yönetimi vb.)

- Esnek fiyatlandırma (boşta kapasite için değil, kullanıma göre ödeme yapın).

- Aşırı güvenilirlik.

- Geliştirilmiş uygulama Mobility; Uygulamanızın nerede ve nasıl dağıtıldığını kolayca değiştirin.

- Esnek kapasite; gerçek ihtiyaçlarına göre ölçeği artırma veya azaltma.

Azure 'da barındırılan ASP.NET Core ile Web uygulamaları oluşturmak, geleneksel alternatifler üzerinde birçok rekabet avantajı sunar. ASP.NET Core Modern Web uygulaması geliştirme uygulamaları ve bulut barındırma senaryoları için iyileştirilmiştir. Bu kılavuzda, bu özelliklerden en iyi şekilde yararlanmak için ASP.NET Core uygulamalarınızı nasıl mimareceğinizi öğreneceksiniz.

## <a name="version"></a>Sürüm

Bu kılavuz, .NET 5,0 sürümüyle aynı "Wave" teknolojileri (Azure ve ek üçüncü taraf teknolojileri) coinciding ile ilgili birçok ek güncelleştirme ile birlikte **.net 5,0** sürümünü kapsayacak şekilde değiştirilmiştir. Kitap sürümü de **5,0** sürümüne güncelleştirilmiştir.

## <a name="purpose"></a>Amaç

Bu kılavuz, ASP.NET Core ve Azure kullanarak *tek parçalı* Web uygulamaları oluşturmaya yönelik uçtan uca yönergeler sağlar. Bu bağlamda, "monoparçalı", bu uygulamaların bir etkileşim Hizmetleri ve uygulamaları koleksiyonu olarak değil, tek bir birim olarak dağıtılmasının gerçeğini ifade eder.

Bu kılavuz, ["_.net mikro hizmetleri" için tamamlayıcı bir kılavuzdur._](../microservices/index.md)Docker, mikro hizmetler ve kapsayıcı dağıtımında kurumsal uygulamaları barındırmak için daha fazla odaklanan, Kapsayıcılı .NET uygulamaları için mimari.

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

- **Sunucu uygulamaları için .NET 5 ve .NET Framework arasında seçim yapma**  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[Sonraki](modern-web-applications-characteristics.md)
