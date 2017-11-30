---
title: "Genel yönergeler"
description: "Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Genel yönergeler"
keywords: "Docker, mikro, ASP.NET, kapsayıcı"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 22dea926e77079e4f543934613ced13a28b2dae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="general-guidance"></a>Genel yönergeler

Bu bölümde, .NET Core veya .NET Framework seçmek ne zaman bir özetini sunar. Aşağıdaki bölümlerde bu seçenekler hakkında daha fazla ayrıntı sunuyoruz.

.NET Core, Linux veya Windows kapsayıcıları kapsayıcılı Docker server uygulamanız için kullanmanız gerekir zaman:

-   Platformlar arası gereksinimleri vardır. Örneğin, Linux ve Windows kapsayıcılar kullanmak istediğiniz.

-   Uygulama Mimarinizi mikro üzerinde temel alır.

-   Kapsayıcıları Hızlı Başlat ve, maliyetleri azaltmak için daha iyi yoğunluğu elde etmek için kapsayıcı ya da daha fazla kapsayıcı donanım birim başına başına küçük bir yer istediğiniz gerekir.

Kısacası, yeni kapsayıcılı .NET uygulamaları oluşturduğunuzda varsayılan seçenek olarak .NET Core düşünmelisiniz. Birçok avantaj vardır ve kapsayıcıları felsefesi ve çalışma stilini en uygun.

.NET Core kullanmanın ek bir faydası aynı makinedeki uygulamaları için yan yana .NET sürümleri çalıştırabilirsiniz ' dir. Uygulamanın gerekir .NET sürümlerinin kapsayıcıları yalıtmak için bu avantajı sunucuları veya kapsayıcıları, kullanmayın VM'ler için daha önemlidir. (Temel işletim sistemiyle uyumlu olduklarını sürece.)

İle Windows kapsayıcıları, .NET Framework kapsayıcılı Docker server uygulamanız için kullanması gereken zaman:

-   Uygulamanız şu anda .NET Framework kullanır ve Windows'da güçlü bağımlılıklara sahiptir.

-   .NET Core tarafından desteklenmeyen Windows API'leri kullanmanız gerekir.

-   Üçüncü taraf .NET kitaplıklarına veya .NET Core için kullanılabilir değil NuGet paketlerini kullanmanız gerekir.

.NET Framework üzerinde Docker kullanarak dağıtım deneyimlerinizi dağıtım sorunlarını en aza indirerek artırabilir. Bu [ *"kaldırın ve shift" senaryo* ](https://aka.ms/liftandshiftwithcontainersebook) ASP.NET WebForms, MVC web uygulamaları veya WCF (gibi geleneksel .NET Framework ile ilk olarak geliştirilen eski uygulamaları containerizing için önemlidir Windows Communication Foundation) Hizmetleri.

### <a name="additional-resources"></a>Ek kaynaklar

-   **e-kitap: Azure ve Windows kapsayıcıları ile var olan .NET Framework uygulamaları Modernize**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)

-   **Örnek uygulamalar: Windows kapsayıcıları kullanarak eski ASP.NET web uygulamalarının Modernization**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)


>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (net-core-kapsayıcı-scenarios.md)
