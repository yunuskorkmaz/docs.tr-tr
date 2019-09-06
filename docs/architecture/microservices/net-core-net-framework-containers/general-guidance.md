---
title: Genel rehber
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Genel rehberlik
ms.date: 09/11/2018
ms.openlocfilehash: 0981cb16d5aa2036391caba0cf6ad3ac5c44ed6f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296530"
---
# <a name="general-guidance"></a>Genel rehber

Bu bölüm, ne zaman .NET Core veya .NET Framework seçme hakkında bir Özet sağlar. İzleyen bölümlerde bu seçimler hakkında daha fazla ayrıntı sağlıyoruz.

Şu durumlarda Kapsayıcılı Docker sunucu uygulamanızda .NET Core 'u Linux veya Windows kapsayıcıları ile kullanmanız gerekir:

- Platformlar arası gereksinimleriniz var. Örneğin, hem Linux hem de Windows kapsayıcılarını kullanmak istiyorsunuz.

- Uygulama mimariniz mikro hizmetleri temel alır.

- Kapsayıcıları hızlı bir şekilde başlatmanız ve bir kapsayıcı başına küçük bir ayak izi, maliyetlerinizi düşürmek için donanım birimi başına daha iyi yoğunluk veya daha fazla kapsayıcı elde etmeniz gerekir.

Kısacası, yeni Kapsayıcılı .NET uygulamaları oluşturduğunuzda, .NET Core 'u varsayılan seçim olarak düşünmeniz gerekir. Birçok avantajı vardır ve kapsayıcıların FI ve çalışma tarzıyla en iyi şekilde uyum sağlar.

.NET Core kullanmanın ek avantajları, aynı makine içindeki uygulamalar için yan yana .NET sürümlerini çalıştırabilmeniz. Bu avantaj, kapsayıcılar kullanmayan sunucular veya VM 'Ler için daha önemlidir çünkü kapsayıcılar, uygulamanın ihtiyaç duyacağı .NET sürümlerini yalıtır. (Temel alınan IŞLETIM sistemiyle uyumlu oldukları sürece.)

Kapsayıcılı Docker sunucu uygulamanız için .NET Framework şu durumlarda kullanmanız gerekir:

- Uygulamanız Şu anda .NET Framework kullanıyor ve Windows üzerinde güçlü bağımlılıklara sahip.

- .NET Core tarafından desteklenmeyen Windows API 'Lerini kullanmanız gerekir.

- .NET Core için kullanılamayan üçüncü taraf .NET kitaplıklarını veya NuGet paketlerini kullanmanız gerekir.

Docker üzerinde .NET Framework kullanmak, dağıtım sorunlarını en aza indirerek dağıtım deneyimlerinizi iyileştirebilir. Bu ["yükseltme ve kaydırma" senaryosu](https://aka.ms/liftandshiftwithcontainersebook) , ASP.net WEBFORMS, MVC Web Apps veya WCF (Windows Communication Foundation) Hizmetleri gibi geleneksel .NET Framework geliştirilmiş eski uygulamaları kapsayımak için önemlidir.

### <a name="additional-resources"></a>Ek kaynaklar

- **E-kitap Azure ve Windows kapsayıcıları ile mevcut .NET Framework uygulamaları modernleştirin**  
    https://aka.ms/liftandshiftwithcontainersebook

- **Örnek uygulamalar: Windows kapsayıcıları kullanarak eski ASP.NET Web uygulamalarını modernleştirme**  
    https://aka.ms/eshopmodernizing

>[!div class="step-by-step"]
>[Önceki](index.md)İleri
>[](net-core-container-scenarios.md)
