---
title: Mikro hizmet uygulama katmanı ve Web API'sini tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Mikro hizmet uygulama katmanı ve Web API'sini tasarlama
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: a8c03f99accf75f60fe6c21a0f09f304214b4a6c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194117"
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>Mikro hizmet uygulama katmanı ve Web API'sini tasarlama

## <a name="using-solid-principles-and-dependency-injection"></a>KATI ilkeler ve bağımlılık ekleme kullanılarak

KATI ilkeler DDD deseni ile bir mikro hizmet geliştirme gibi modern ve görev açısından kritik bir uygulamada, kullanılacak kritik tekniklerle aynıdır. DÜZ bir kısaltma bu grupları beş temel ilkeler verilmiştir:

-   Tek sorumluluk İlkesi

-   İlke açık/kapalı

-   Liskov değiştirme İlkesi

-   Ayırma ilkesini arabirimi

-   Bağımlılık tersine çevirme ilkesi

DÜZ, uygulamanızın veya iç mikro hizmet katmanları nasıl tasarlayacağınızı ve aralarındaki bağımlılıkları ayırma hakkında daha fazla. Bu etki alanı, ancak uygulamanın teknik tasarım ilişkili değil. Son ilke, bağımlılık tersine çevirme ilkesine DDD katmanların bir daha iyi ayrılmış uygulama sağlayan diğer katmanların altyapı katmanını ayırmak sağlar.

Bağımlılık ekleme (dı) bağımlılık tersine çevirme ilkesini uygulamak için bir yoludur. Bu nesneleri ve bunların bağımlılıklarını arasındaki bu sıkı bağ elde etmek için kullanabileceğiniz bir tekniktir. Ortak Çalışanlar doğrudan örnekleme veya statik başvurular yerine bir sınıf eylemlerini gerçekleştirmek için gereken nesneleri için sağlanan (veya "içine eklenen") sınıfı. Çoğunlukla sınıfları, bunları özel bağımlılıklar ilkesini izlemek izin verme oluşturucularına aracılığıyla bunların bağımlılıklarını bildirir. DI, genellikle belirli bir denetimi tersine çevirme (IOC) kapsayıcı üzerinde temel alır. Basit bir yerleşik IOC kapsayıcısında ASP.NET Core sağlar, ancak Autofac veya Ninject gibi sık kullanılan, IOC kapsayıcı de kullanabilirsiniz.

KATI ilkeler uygulayarak, sınıflarınızı doğal olarak küçük, katsayıları iyi belirlenmiş ve kolayca test edilmiş olma eğilimindedir. Ancak çok fazla bağımlılıkları, sınıflara eklenmiş olmadığını nasıl bilebilirsiniz? Oluşturucusu DI kullanırsanız, yalnızca güvenlik denetimini atladığından için parametre sayısı bakarak algılayan kolay olacaktır. Çok fazla bağımlılıkları varsa, bu, genellikle bir oturum. (bir [kod kokusu](https://deviq.com/code-smells/)) sınıfınıza çok yapmak çalışıyor ve büyük olasılıkla tek sorumluluk ilkesini ihlal.

Bunu başka bir kılavuz DÜZ ayrıntılı olarak ele alır. Bu nedenle, bu kılavuzda Bu konu için en az bir bilgiye sahip gerektirir.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **KATI: Temel OOP ilkeleri**
    [*https://deviq.com/solid/*](https://deviq.com/solid/%20)

-   **Tersine çevirme denetimi kapsayıcıları ve bağımlılık ekleme deseni**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)

-   **Steve Smith. Birleştirici yenilikler**
    [*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue)


>[!div class="step-by-step"]
[Önceki](nosql-database-persistence-infrastructure.md)
[İleri](microservice-application-layer-implementation-web-api.md)
