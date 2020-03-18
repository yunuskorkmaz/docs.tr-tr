---
title: ASP.NET Core ve Azure ile modern web uygulamalarını mimar
description: ASP.NET Core ve Azure kullanarak yekpare web uygulamaları oluşturma konusunda uçlardan uca kılavuz sağlayan bir kılavuz.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: c19e5e90cfb96463f744cfb064abe72ee5db2e9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77449340"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>ASP.NET Core ve Microsoft Azure ile Modern Web Uygulamaları Tasarlama

![Mimar Modern Web Uygulamaları kılavuzunun kitap kapağı görüntüsü.](./media/index/web-application-guide-cover-image.png)

**EDITION v3.1** - Core 3.1 ASP.NET güncellendi

YAYIMLAYAN

Microsoft Developer Division, .NET ve Visual Studio ürün ekipleri

Microsoft Corporation'ın bir bölümü

One Microsoft Way

Redmond, Washington 98052-6399

Telif hakkı © 2020 Microsoft Corporation tarafından

Tüm hakları saklıdır. Bu kitabın içeriğinin hiçbir bölümü, yayımcının yazılı izni olmadan herhangi bir biçimde veya herhangi bir şekilde çoğaltılamaz veya aktarılamaz.

Bu kitap "olduğu gibi" sağlanır ve yazarın görüş ve görüşlerini ifade eder. URL ve diğer Internet web sitesi referansları da dahil olmak üzere bu kitapta ifade edilen görüşler, görüşler ve bilgiler önceden haber verilmeden değişebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve "Ticari https://www.microsoft.com Markalar" web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS, Apple Inc. şirketinin ticari markalarıdır.

Docker balina logosu, Docker, Inc. şirketinin izni yle kullanılan tescilli ticari markasıdır.

Diğer tüm işaretler ve logolar ilgili sahiplerinin mülkiyetindedir.

Yazar:

> **Steve "ardalis" Smith** - Yazılım Mimarı ve Eğitmen - [Ardalis.com](https://ardalis.com)

Editörler:

> **Maira Wenzel**

## <a name="introduction"></a>Giriş

.NET Core ve ASP.NET Core, geleneksel .NET geliştirmeye göre çeşitli avantajlar sunar. Aşağıdakilerden bazıları veya tümü uygulamanızın başarısı için önemliyse sunucu uygulamalarınız için .NET Core'u kullanmalısınız:

- Platform ötesi destek.

- Mikro hizmetlerin kullanımı.

- Docker konteynerlerinin kullanımı.

- Yüksek performans ve ölçeklenebilirlik gereksinimleri.

- .NET sürümlerinin aynı sunucudaki uygulamalara göre yan yana sürüklüyor.

Geleneksel .NET uygulamaları bu gereksinimlerin çoğunu destekleyebilir ve destekleyebilir, ancak ASP.NET Core ve .NET Core yukarıdaki senaryolar için geliştirilmiş destek sunmak üzere optimize edilmiştir.

Giderek daha fazla kuruluş, Microsoft Azure gibi hizmetleri kullanarak web uygulamalarını bulutta barındırmayı tercih ediyor. Aşağıdakiler uygulamanız veya kuruluşunuz için önemliyse, uygulamanızı bulutta barındırmayı düşünmelisiniz:

- Veri merkezi maliyetlerine daha az yatırım (donanım, yazılım, alan, yardımcı programlar, sunucu yönetimi, vb.)

- Esnek fiyatlandırma (boşta kapasite için değil, kullanıma göre ödeme).

- Aşırı güvenilirlik.

- Geliştirilmiş uygulama hareketliliği; uygulamanızın nerede ve nasıl dağıtılandığını kolayca değiştirin.

- Esnek kapasite; gerçek ihtiyaçlar temel alınabında yukarı veya aşağı ölçeklendirin.

Azure'da barındırılan ASP.NET Core ile web uygulamaları oluşturmak, geleneksel alternatiflere göre birçok rekabet avantajı sunar. ASP.NET Core modern web uygulama geliştirme uygulamaları ve bulut barındırma senaryoları için optimize edin. Bu kılavuzda, bu özelliklerden en iyi şekilde yararlanmak için ASP.NET Core uygulamalarınızı nasıl tasarlayacağımızı öğreneceksiniz.

## <a name="purpose"></a>Amaç

Bu kılavuz, ASP.NET Core ve Azure kullanarak *yekpare* web uygulamaları oluşturma konusunda uçlardan uca kılavuz sağlar. Bu bağlamda,"yekpare", bu uygulamaların etkileşimli hizmetler ve uygulamalar topluluğu olarak değil, tek bir birim olarak dağıtılmasını ifade eder.

Bu kılavuz ["_.NET Microservices tamamlayıcıdır. _](../microservices/index.md) Kurumsal uygulamaları barındıracak şekilde Docker, Microservices ve Dağıtım Kapları'na odaklanan Containerized .NET Applications için Mimari.

### <a name="net-microservices-architecture-for-containerized-net-applications"></a>.NET MikroHizmetler. Kapsayıcılı .NET Uygulamaları Mimarisi

- **e-kitap**  
  <https://aka.ms/MicroservicesEbook>
- **Örnek Uygulama**  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalı?

Bu kılavuzun hedef kitlesi, bulutta Microsoft teknolojilerini ve hizmetlerini kullanarak modern web uygulamaları oluşturmak isteyen geliştiriciler, geliştirme yol gösterici ve mimarlardır.

İkinci bir hedef kitle, ASP.NET veya Azure'u zaten tanıdık olan ve yeni veya varolan projeler için ASP.NET Core'a yükseltmenin mantıklı olup olmadığı hakkında bilgi arayan teknik karar vericilerdir.

## <a name="how-you-can-use-this-guide"></a>Bu kılavuzu nasıl kullanabilirsiniz?

Bu kılavuz, modern .NET teknolojileri ve Windows Azure ile web uygulamaları oluşturmaya odaklanan nispeten küçük bir belgeye sıkıştırılmıştır. Bu nedenle, bu tür uygulamalar ve teknik hususlar anlayış bir temel sağlamak için bütünüyle okunabilir. Kılavuz, örnek uygulamasıyla birlikte, bir başlangıç noktası veya başvuru olarak da hizmet verebilir. İlişkili örnek uygulamayı kendi uygulamalarınız için şablon olarak veya uygulamanızın bileşen parçalarını nasıl düzenleyebileceğini görmek için kullanın. Kendi uygulamanız için bu seçenekleri değerlendirirken kılavuzun ilkelerine ve mimari ve teknoloji seçeneklerinin ve karar konularının kapsamına bakın.

Bu hususların ve fırsatların ortak bir şekilde anlaşılmasını sağlamaya yardımcı olmak için bu kılavuzu ekibinize iletmekten çekinmeyin. Herkesin ortak bir terminoloji ve temel ilkeler den çalışması mimari örüntü lerin ve uygulamaların tutarlı bir şekilde uygulanmasını sağlamaya yardımcı olur.

## <a name="references"></a>Başvurular

- **Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma**  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[Sonraki](modern-web-applications-characteristics.md)
