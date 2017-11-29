---
title: "ASP.NET Core ve Azure ile Mimarı modern web uygulamaları"
description: "ASP.NET Core ve Azure ile modern Web uygulamaları mimari | Giriş"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 93a74bb7ba537d3c7c0291f7903112dc470133a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a>ASP.NET Core ve Azure ile Mimarı Modern Web uygulamaları

.NET core ve ASP.NET Core geleneksel .NET geliştirme birkaç avantaj sunar. Aşağıdaki tümünün veya uygulamanızın başarısı için önemli olan ise, sunucu uygulamaları için .NET Core kullanmanız gerekir:

-   Platformlar arası desteği

-   Mikro kullanımı

-   Docker kapsayıcıları kullanma

-   Yüksek performans ve ölçeklenebilirlik gereksinimleri

-   Aynı sunucuda bir uygulama tarafından .NET sürümlerinin yan yana sürüm oluşturma

Geleneksel .NET uygulamaları yapın ve bu gereksinimleri desteklemesi ancak yukarıdaki senaryoları için geliştirilmiş destek sunmak için ASP.NET Core ve .NET Core getirilmiştir.

Microsoft Azure gibi hizmetler kullanarak bulutta web uygulamalarını barındırmak daha da fazla kuruluşlar seçim. Aşağıdakiler, uygulama veya kuruluşunuz için önemliyse, uygulamanızda bulut barındırma dikkate almanız gerekir:

-   Azaltılmış yatırım veri merkezi maliyetlerini (donanım, yazılım, boşluk, yardımcı programlar, vb.)

-   (Kullanım için boşta kapasite göre ödeme) fiyatlandırma esnek

-   Extreme güvenilirlik

-   Geliştirilmiş uygulama mobility; kolayca değiştirmek, uygulamanızın nerede ve nasıl dağıtılır

-   Esnek Kapasite; Yukarı veya aşağı göre gerçek gereksinimlerini ölçeklendirme

Microsoft Azure üzerinde barındırılan ASP.NET Core ile Web uygulamaları oluşturmak, geleneksel alternatifleri çok sayıda rekabet avantaj sunar. ASP.NET Core modern web uygulaması geliştirme uygulamaları ve bulut barındırma senaryolarında için optimize edilmiştir. Bu kılavuzda, bu özellikler en iyi şekilde yararlanmak için ASP.NET Core uygulamaları mimari öğreneceksiniz.

## <a name="purpose"></a>Amaç

Bu kılavuz, ASP.NET Core ve Azure kullanarak tek yapılı web uygulamaları geliştirmek uçtan uca yönergeler sağlar.

Bu kılavuz için tamamlayıcı "*Architecting ve geliştirme kapsayıcılı ve .NET mikro hizmet tabanlı uygulamalarla*" hangi odaklanır daha fazla üzerinde Docker, mikro ve dağıtım, kapsayıcıları konak kuruluş uygulamalar.

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a>Mimariden ve kapsayıcılı mikro hizmet geliştirirken .NET uygulamalarında dayalı
> - **e-kitap**  
> <http://aka.MS/MicroservicesEbook>
> - **Örnek uygulama**  
> <http://aka.MS/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a>Bu kılavuz kullanan

Bu kılavuzda kitlesi çoğunlukla geliştiriciler, geliştirme müşteri adayları ve bulutta Microsoft teknolojileri ve hizmetleri kullanan modern web uygulamaları oluşturmaya ilgi duyan mimarlar içindir.

İkincil bir dinleyici zaten bilinen ASP.NET ve/veya Azure ve yeni veya mevcut projeleri için ASP.NET Core yükseltmek için anlam olup olmadığı hakkında bilgi mi arıyorsunuz teknik karar alıcılar ' dir.

## <a name="how-you-can-use-this-guide"></a>Bu kılavuz nasıl kullanabileceğiniz

Bu kılavuz, modern .NET teknolojileri ve Windows Azure ile web uygulamaları oluşturmaya odaklanan görece küçük bir belgeye sıkıştırılmış. Bu nedenle, bu tür uygulamalar ve bunların teknik konular anlamanın bir temel tamamının okunabilir. Kendi örnek uygulama ile birlikte kılavuzu ayrıca bir başlangıç noktası veya başvuru hizmet verebilir. İlişkili örnek uygulaması, kendi uygulamalar için veya uygulamanızın bileşen parçalarını nasıl düzenleyebileceğini görmek için bir şablon olarak kullanın. Geri kılavuz ilkeleri ve kapsamı mimarisi ve teknoloji seçenekleri ve karar dikkat edilecek noktalar, kendi uygulama için bu seçeneklerin başvuracaklarını zaman bakın.

Bu konuları ve fırsatlar genel olarak anlaşılmasını sağlamak için bu kılavuzu ekibinize iletmek çekinmeyin. Herkes ortak bir dizi terminolojisi çalışma ve ilkeleri temelindeki sahip mimari desenleri ve uygulamalar tutarlı uygulama sağlamaya yardımcı olur.

## <a name="references"></a>Referanslar
- **Sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim yapma**  
<https://docs.microsoft.com/dotnet/articles/Standard/choosing-Core-Framework-Server>

>[!div class="step-by-step"]
[Sonraki] (modern-web-uygulamalar-characteristics.md)
