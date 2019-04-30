---
title: Mikro hizmet uygulama katmanı ve Web API’sini tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Uygulama katmanı tasarlamaya yönelik KATI ilkeler, kısa bir Bahsetme.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 9177ac9a79afaea01f0ec21b0a64bad5a94e9966
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760902"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a>Mikro hizmet uygulama katmanı ve Web API'sini tasarlama

## <a name="use-solid-principles-and-dependency-injection"></a>KATI ilkeler ve bağımlılık ekleme

KATI ilkeler DDD deseni ile bir mikro hizmet geliştirme gibi modern ve görev açısından kritik bir uygulamada, kullanılacak kritik tekniklerle aynıdır. DÜZ bir kısaltma bu grupları beş temel ilkeler verilmiştir:

- Tek sorumluluk İlkesi

- İlke açık/kapalı

- Liskov değiştirme İlkesi

- Ayırma ilkesini arabirimi

- Bağımlılık tersine çevirme ilkesi

DÜZ, uygulamanızın veya iç mikro hizmet katmanları nasıl tasarlayacağınızı ve aralarındaki bağımlılıkları ayırma hakkında daha fazla. Bu etki alanı, ancak uygulamanın teknik tasarım ilişkili değil. Son ilke, bağımlılık tersine çevirme ilkesine DDD katmanların bir daha iyi ayrılmış uygulama sağlayan diğer katmanların altyapı katmanını ayırmak sağlar.

Bağımlılık ekleme (dı) bağımlılık tersine çevirme ilkesini uygulamak için bir yoludur. Bu nesneleri ve bunların bağımlılıklarını arasındaki bu sıkı bağ elde etmek için kullanabileceğiniz bir tekniktir. Doğrudan ortak çalışanlar örnekleme veya (kullanan yeni...) statik başvuruları kullanma yerine, bir sınıf eylemlerini gerçekleştirmek için gereken nesneleri için sağlanan (veya "içine eklenen") sınıfı. Çoğunlukla sınıfları, bunları özel bağımlılıklar ilkesini izlemek izin verme oluşturucularına aracılığıyla bunların bağımlılıklarını bildirir. Bağımlılık ekleme, genellikle belirli bir denetimi tersine çevirme (IOC) kapsayıcı üzerinde temel alır. Basit bir yerleşik IOC kapsayıcısında ASP.NET Core sağlar, ancak Autofac veya Ninject gibi sık kullanılan, IOC kapsayıcı de kullanabilirsiniz.

KATI ilkeler uygulayarak, sınıflarınızı doğal olarak küçük, katsayıları iyi belirlenmiş ve kolayca test edilmiş olma eğilimindedir. Ancak çok fazla bağımlılıkları, sınıflara eklenmiş olmadığını nasıl bilebilirsiniz? Oluşturucusu DI kullanırsanız, yalnızca güvenlik denetimini atladığından için parametre sayısı bakarak algılayan kolay olacaktır. Çok fazla bağımlılıkları varsa, bu, genellikle bir oturum. (bir [kod kokusu](https://deviq.com/code-smells/)) sınıfınıza çok yapmak çalışıyor ve büyük olasılıkla tek sorumluluk ilkesini ihlal.

Bunu başka bir kılavuz DÜZ ayrıntılı olarak ele alır. Bu nedenle, bu kılavuzda Bu konu için en az bir bilgiye sahip gerektirir.

#### <a name="additional-resources"></a>Ek kaynaklar

- **DÜZ: Temel OOP ilkeleri** \
  <https://deviq.com/solid/>

- **Tersine çevirme denetimi kapsayıcıları ve bağımlılık ekleme deseni** \
  <https://martinfowler.com/articles/injection.html>

- **Steve Smith. Birleştirici yenilikler** \
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> [Önceki](nosql-database-persistence-infrastructure.md)
> [İleri](microservice-application-layer-implementation-web-api.md)
