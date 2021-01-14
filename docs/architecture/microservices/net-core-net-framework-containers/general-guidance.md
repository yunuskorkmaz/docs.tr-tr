---
title: Genel kılavuz
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Genel rehberlik
ms.date: 01/13/2021
ms.openlocfilehash: 4fd2d936c524cb3e5ae463038eaffe88b459d2bd
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187957"
---
# <a name="general-guidance"></a>Genel kılavuz

Bu bölümde, .NET 5 veya .NET Framework ne zaman seçeceğiniz hakkında bir Özet sağlanmaktadır. İzleyen bölümlerde bu seçimler hakkında daha fazla ayrıntı sağlıyoruz.

Şu durumlarda Kapsayıcılı Docker sunucu uygulamanızda .NET 5 ' i Linux veya Windows kapsayıcılarıyla birlikte kullanın:

- Platformlar arası gereksinimleriniz var. Örneğin, hem Linux hem de Windows kapsayıcılarını kullanmak istiyorsunuz.

- Uygulama mimariniz mikro hizmetleri temel alır.

- Kapsayıcıları hızlı bir şekilde başlatmanız ve bir kapsayıcı başına küçük bir ayak izi, maliyetlerinizi düşürmek için donanım birimi başına daha iyi yoğunluk veya daha fazla kapsayıcı elde etmeniz gerekir.

Kısacası, yeni Kapsayıcılı .NET uygulamaları oluşturduğunuzda, .NET 5 ' i varsayılan seçenek olarak düşünmeniz gerekir. Birçok avantajı vardır ve kapsayıcıların FI ve çalışma tarzıyla en iyi şekilde uyum sağlar.

.NET 5 kullanmanın bir avantajı, aynı makine içindeki uygulamalar için yan yana .NET sürümlerini çalıştırabilmeniz. Bu avantaj, kapsayıcılar kullanmayan sunucular veya VM 'Ler için daha önemlidir çünkü kapsayıcılar, uygulamanın ihtiyaç duyacağı .NET sürümlerini yalıtır. (Temel alınan IŞLETIM sistemiyle uyumlu oldukları sürece.)

Kapsayıcılı Docker sunucu uygulamanız için .NET Framework şu durumlarda kullanın:

- Uygulamanız Şu anda .NET Framework kullanıyor ve Windows üzerinde güçlü bağımlılıklara sahip.

- .NET 5 tarafından desteklenmeyen Windows API 'Lerini kullanmanız gerekir.

- .NET 5 için kullanılamayan üçüncü taraf .NET kitaplıklarını veya NuGet paketlerini kullanmanız gerekir.

Docker üzerinde .NET Framework kullanmak, dağıtım sorunlarını en aza indirerek dağıtım deneyimlerinizi iyileştirebilir. Bu ["yükseltme ve kaydırma" senaryosu](https://aka.ms/liftandshiftwithcontainersebook) , ASP.net WEBFORMS, MVC Web Apps veya WCF (Windows Communication Foundation) Hizmetleri gibi geleneksel .NET Framework geliştirilmiş eski uygulamaları kapsayımak için önemlidir.

### <a name="additional-resources"></a>Ek kaynaklar

- **E-kitap: Azure ve Windows kapsayıcıları ile mevcut .NET Framework uygulamaları modernleştirin**  
    <https://aka.ms/liftandshiftwithcontainersebook>

- **Örnek uygulamalar: Windows kapsayıcıları kullanarak eski ASP.NET Web uygulamalarını modernleştirme**  
    <https://aka.ms/eshopmodernizing>

>[!div class="step-by-step"]
>[Önceki](index.md) 
> [Sonraki](net-core-container-scenarios.md)
