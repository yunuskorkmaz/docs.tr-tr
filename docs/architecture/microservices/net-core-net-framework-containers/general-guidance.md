---
title: Genel kılavuz
description: .NET Microservices Mimari Containerized .NET Uygulamaları için | Genel rehberlik
ms.date: 09/11/2018
ms.openlocfilehash: 2fa66d7593b764a8df4d9acc20f93d3f8fb26174
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73089643"
---
# <a name="general-guidance"></a>Genel kılavuz

Bu bölümde ,NET Core veya .NET Framework ne zaman seçileceklerinin bir özetini sağlar. Takip eden bölümlerde bu seçenekler hakkında daha fazla bilgi sağlarız.

Kapsayıcı Docker sunucu uygulamanız için Linux veya Windows Kapsayıcıları ile .NET Core'u şu zaman kullanmalısınız:

- Platform ötesi ihtiyaçların var. Örneğin, hem Linux hem de Windows Kapsayıcıları kullanmak istiyorsunuz.

- Uygulama mimariniz mikro hizmetlere dayanmaktadır.

- Maliyetlerinizi düşürmek için kapsayıcıları hızlı başlatmanız ve donanım birimi başına daha iyi yoğunluk veya daha fazla kapsayıcı elde etmek için konteyner başına küçük bir ayak izi istemeniz gerekir.

Kısacası, yeni kapsayıcı .NET uygulamaları oluşturduğunuzda, .NET Core'u varsayılan seçenek olarak düşünmelisiniz. Birçok faydası vardır ve konteyner felsefesi ve çalışma tarzı ile en iyi uyuyor.

.NET Core'u kullanmanın bir diğer avantajı da, aynı makinedeki uygulamalar için yan yana .NET sürümlerini çalıştırabiliyor olabilirsiniz. Kapsayıcılar .NET'in uygulamanın ihtiyaç duyduğu sürümleriya yalıttığından, bu avantaj kapsayıcıları kullanmayan sunucular veya VM'ler için daha önemlidir. (Temel işletim sistemi yle uyumlu oldukları sürece.)

Kapsayıcı Docker sunucu uygulamanız için .NET Framework'u şu zaman kullanmalısınız:

- Uygulamanız şu anda .NET Framework kullanır ve Windows üzerinde güçlü bağımlılıkları vardır.

- .NET Core tarafından desteklenmeyen Windows API'lerini kullanmanız gerekir.

- .NET Core için kullanılamayan üçüncü taraf .NET kitaplıklarını veya NuGet paketlerini kullanmanız gerekir.

Docker'da .NET Framework'ü kullanmak, dağıtım sorunlarını en aza indirerek dağıtım deneyimlerinizi artırabilir. Bu ["kaldırma ve kaydırma" senaryosu,](https://aka.ms/liftandshiftwithcontainersebook) web formları, MVC web uygulamaları veya WCF (Windows Communication Foundation) hizmetleri ASP.NET gibi geleneksel .NET Framework ile geliştirilen eski uygulamaları konteynerleştirmek için önemlidir.

### <a name="additional-resources"></a>Ek kaynaklar

- **E-kitap: Azure ve Windows Kapsayıcıları ile mevcut .NET Framework uygulamalarını modernize edin**  
    https://aka.ms/liftandshiftwithcontainersebook

- **Örnek uygulamalar: Windows Kapsayıcıları kullanılarak eski ASP.NET web uygulamalarının modernizasyonu**  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](net-core-container-scenarios.md)
