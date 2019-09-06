---
title: Mikro hizmet uygulama katmanı ve Web API’sini tasarlama
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Uygulama katmanını tasarlamaya yönelik katı ilkelere ilişkin kısa bir açıklama.
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296740"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a>Mikro hizmet uygulama katmanını ve Web API 'sini tasarlama

## <a name="use-solid-principles-and-dependency-injection"></a>KATı ilkeler ve bağımlılık ekleme kullanma

KATı ilkeler, DDD desenleriyle mikro hizmet geliştirme gibi tüm modern ve görev açısından kritik bir uygulamada kullanılması için kritik tekniklerdir. SOLID, beş temel ilkeden oluşan bir kısaltmakta:

- Tek sorumluluk ilkesi

- Açık/kapalı ilke

- Lizkov değiştirme ilkesi

- Arabirim ayırma ilkesi

- Bağımlılık Inversion ilkesi

SOLID, uygulamanızı veya mikro hizmet iç Katmanlarınızı tasarlama ve bunlar arasındaki bağımlılıkları çözme hakkında daha fazla bilgi. Bu, etki alanı ile ilgili değil, uygulamanın teknik tasarımına yönelik değildir. Son ilke olan bağımlılık sürümü prensibi, altyapı katmanını katmanların geri kalanından ayırarak, DDD katmanlarının daha iyi ayrılmış bir uygulamasına olanak tanır.

Bağımlılık ekleme (dı), bağımlılık Inversion ilkesini uygulamak için bir yoldur. Nesneler ve bunların bağımlılıkları arasında gevşek bir bağlantısı elde etmek için bir tekniktir. Ortak çalışanların doğrudan örneklendiği veya statik başvuruların (yani, New...) kullanılması yerine, bir sınıfın eylemlerini gerçekleştirmek için ihtiyaç duyacağı nesneler sınıfına (veya "eklenen") sunulur. Çoğu zaman, sınıflar kendi bağımlılıklarıyla kendi bağımlılıklarını bildirir ve bu kullanıcıların açık bağımlılıklar ilkesini izlemesini sağlar. Bağımlılık ekleme, genellikle Denetim (IOC) kapsayıcılarının belirli bir INVERSION tabanlıdır. ASP.NET Core basit bir yerleşik IOC kapsayıcısı sağlar, ancak Autofac veya Neklemesine benzer şekilde, en sevdiğiniz IOC kapsayıcısını de kullanabilirsiniz.

DÜZ ilkeleri izleyerek, sınıflarınız doğal olarak küçük, iyi bir şekilde ve kolayca test edilir. Ancak sınıflarınıza çok fazla bağımlılık eklediyseniz nasıl emin olabilirsiniz? Oluşturucuyu Oluşturucu aracılığıyla kullanırsanız, yalnızca kurucularınızın parametre sayısına bakarak bunu tespit etmek kolay olur. Çok fazla bağımlılık varsa, bu genellikle sınıfınızın çok fazla yapmaya çalıştığı ve muhtemelen tek sorumluluk ilkesini ihlal eden bir imzadır ( [kod kokusu](https://deviq.com/code-smells/)).

Ayrıntılı bir şekilde ele almak için başka bir kılavuz alır. Bu nedenle bu kılavuzda, bu konularda yalnızca en az bilgiye sahip olmanız gerekir.

#### <a name="additional-resources"></a>Ek kaynaklar

- **SAĞLAM Temel OOP Ilkeleri** \
  <https://deviq.com/solid/>

- **Denetim kapsayıcıları ve bağımlılık ekleme deseninin Inversion 'ı** \
  <https://martinfowler.com/articles/injection.html>

- **Steve Smith. Yeni bir tutkalla** \
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> [Önceki](nosql-database-persistence-infrastructure.md)İleri
> [](microservice-application-layer-implementation-web-api.md)
