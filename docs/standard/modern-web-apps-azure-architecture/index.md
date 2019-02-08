---
title: ASP.NET Core ve Azure ile modern web uygulamaları tasarlama
description: ASP.NET Core ve Azure kullanarak tek parça web uygulamaları oluşturmaya uçtan uca yönergeler sağlar. bir kılavuz.
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 5e85126cbec23bdebd510b103478b3c362ef71fa
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55827870"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama

![kapak resmi](./media/cover.png)

TARAFINDAN YAYIMLANAN

Microsoft Geliştirici bölme, .NET ve Visual Studio ürün takımları

Microsoft Corporation'ın bir bölme

One Microsoft Way

Redmond, Washington 98052-6399

Telif Hakkı © Microsoft Corporation 2019

Tüm hakları saklıdır. Bu kitap içeriğini bir parçası çoğaltılamaz veya herhangi bir araçla yayımcı yazılı izni olmadan herhangi bir biçimdeki aktarılamaz.

Bu kitap sağlanan "olarak-olduğunu" ve yazarın görünümleri ve düşünceleri son derece ifade eder. Görünümleri ve düşünceleri son derece bilgi URL ve diğer Internet Web sitesi referansları da dahil olmak üzere bu kitap, ifade verilmeksizin değiştirilebilir.

Burada açıklanan bazı örnekler yalnızca çizim için sağlanmıştır ve bu kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya çıkarılmamalıdır.

Microsoft ve adresinde listelenmiş ticari https://www.microsoft.com "Ticari" Web sayfasında Microsoft şirketler grubunun ticari markalarıdır.

Mac ve macOS Apple Inc.'in ticari markalarıdır.

Docker whale logosu, Docker, Inc.'in kayıtlı ticari markasıdır. İzni tarafından kullanılır.

Diğer tüm işaretleri ve logoları sahiplerinin özelliği var.

Yazar:

> **Steve "ardalis" Smith** - yazılım mühendisi ve Eğitmen - [Ardalis.com](https://ardalis.com)

Düzenleyiciler:

> **Maira Wenzel**

## <a name="introduction"></a>Giriş

.NET core ve ASP.NET Core geleneksel .NET geliştirme kıyasla çeşitli avantajlar sunar. Aşağıdakilerin tümü veya uygulamanızın başarısı için önemli ise, sunucu uygulamaları için .NET Core kullanmanız gerekir:

- Platformlar arası desteği.

- Mikro hizmetler kullanın.

- Docker kapsayıcılarını kullanın.

- Yüksek performans ve ölçeklenebilirlik gereksinimleri.

- Uygulama ile aynı sunucuya .NET sürümlerinin yan yana sürüm oluşturma.

Geleneksel .NET uygulamalar yapın ve bu gereksinimlerin çoğu destekler, ancak yukarıdaki senaryoları için geliştirilmiş destek sunmak için ASP.NET Core ve .NET Core getirilmiştir.

Microsoft Azure gibi hizmetleri kullanarak bulutta web uygulamalarını barındırmak giderek daha fazla kuruluşların seçim. Aşağıda, uygulama veya kuruluşunuz için önemliyse, uygulamanızı bulutta barındırma dikkate almanız gerekir:

- Daha az yatırım veri merkezi maliyetlerini (donanım, yazılım, boşluk, yardımcı programlar, sunucu yönetimi, vb.)

- Esnek fiyatlandırma (boş kapasite için değil, kullanıma bağlı olarak ödeme).

- Extreme güvenilirlik.

- Gelişmiş uygulama taşınabilirliği; kolayca uygulamanızı nerede ve nasıl dağıtılır.

- Esnek Kapasite; ölçeği artırın veya göre gerçek ihtiyaçları azaltın.

ASP.NET Core, Azure üzerinde barındırılan Web uygulamalarıyla geleneksel alternatifleri rekabetçi birçok avantaj sunar. ASP.NET Core, modern bir web uygulaması geliştirme uygulamaları ve bulut barındırma senaryoları için optimize edilmiştir. Bu kılavuzda, bu özellikler en iyi şekilde yararlanmak için ASP.NET Core uygulamalarınızı tasarlama öğreneceksiniz.

## <a name="purpose"></a>Amaç

Bu kılavuz, uygulama oluşturmaya uçtan uca yönergeler sağlar *tek parça* web uygulamaları ASP.NET Core ve Azure kullanarak. Bu bağlamda, bu uygulamaların etkileşim kuran hizmetler ve uygulamalar koleksiyonu olarak değil, tek bir birim olarak dağıtıldığını olgu "tek parça" ifade eder.

Bu kılavuz için tamamlayıcı ["_.NET mikro Hizmetleri. Kapsayıcılı .NET uygulamaları mimarisi_"](../microservices-architecture/index.md) hangi odaklanır daha fazla üzerinde Docker, mikro hizmetler ve kapsayıcılar dağıtımının Kurumsal uygulamalarını barındırmak için.

### <a name="net-microservices-architecture-for-containerized-net-applications"></a>.NET mikro Hizmetleri. Kapsayıcılı .NET uygulamaları mimarisi

- **e-kitabı**  
  <https://aka.ms/MicroservicesEbook>
- **Örnek uygulama**  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Bu kılavuzda kullanan

Bu kılavuz için İzleyici ağırlıklı olarak geliştiriciler, geliştirme Liderleri ve bulutta Microsoft teknolojileri ve Hizmetleri kullanarak modern web uygulamaları oluşturmak istiyorsanız mimarları olduğu.

İkincil bir dinleyici zaten bilinen ASP.NET veya Azure ve ASP.NET Core için yeni veya mevcut projeleri için yükseltme mantıklı olup olmadığı hakkında bilgi arıyorsanız, teknik karar verenler ' dir.

## <a name="how-you-can-use-this-guide"></a>Nasıl bu kılavuzu kullanabilirsiniz.

Bu kılavuz, modern .NET teknolojileri ve Windows Azure ile web uygulamaları oluşturmaya odaklanan görece küçük bir belgenin içine sıkıştırılmış. Bu nedenle, bu tür uygulamalar ve bunların teknik konuları anlamanın sağlamasıdır için tamamen okunabilir. Birlikte, örnek uygulama Kılavuzu, ayrıca bir başlangıç noktası veya başvuru hizmet verebilir. İlişkili örnek uygulama için kendi uygulamalarınızı ya da uygulamanızın bileşen parçalarına nasıl düzenleyebileceğini görmek için bir şablon olarak kullanın. Kendi uygulamanız için bu seçenekleri ağırlığıyla olduğunda geri kılavuz ilkeleri ve mimarisi ve teknolojisi seçeneklerini ve karar konuları kapsamını bakın.

Bu noktalar ve fırsatlar genel olarak anladığından emin olmak için bu kılavuzu takımınıza iletmek çekinmeyin. Herkesin sahip ortak bir dizi terminolojisi çalışma ve ilkeler temel mimari desenleri ve uygulamaları tutarlı uygulama sağlamaya yardımcı olur.

## <a name="references"></a>Referanslar

- **Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma**  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Next](modern-web-applications-characteristics.md)