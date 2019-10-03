---
title: Mantıksal Mimari ve fiziksel mimariye karşı
description: Mantıksal ve fiziksel mimarilerin farklarını anlayın.
ms.date: 09/20/2018
ms.openlocfilehash: 8d1bfca190eb9b18d46625fa4afdec963eb07054
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834397"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Mantıksal Mimari ve fiziksel mimariye karşı

Bu noktada, mantıksal mimari ve fiziksel mimari arasındaki farkın durdurulması ve ele alındığı ve bu durumun mikro hizmet tabanlı uygulamaların tasarımına nasıl uygulandığı açıklanmaktadır.

Başlamak için, mikro hizmetlerin oluşturulması belirli bir teknolojinin kullanılmasını gerektirmez. Örneğin, Docker kapsayıcıları, mikro hizmet tabanlı bir mimari oluşturmak için zorunlu değildir. Bu mikro hizmetler düz işlem olarak da çalıştırılabilir. Mikro hizmetler bir mantıksal mimaridir.

Üstelik, bir mikro hizmet fiziksel olarak tek bir hizmet, işlem veya kapsayıcı olarak uygulansa bile (basitlik için [Eshoponcontainers](https://aka.ms/MicroservicesArchitecture)'un ilk sürümünde gerçekleştirilen yaklaşım), iş mikro hizmeti arasında bu eşlik ve çoğu düzinelerce veya hatta yüzlerce hizmetten oluşan büyük ve karmaşık bir uygulama oluşturduğunuzda tüm durumlarda fiziksel hizmet veya kapsayıcı gerekli değildir.

Bu, bir uygulamanın mantıksal mimarisi ve fiziksel mimarisi arasında bir farklılık olduğu yerdir. Bir sistemin mantıksal mimarisi ve mantıksal sınırları, bire bir-bir ' i fiziksel veya dağıtım mimarisine eşlemenize gerek yoktur. Bu durum gerçekleşebilir, ancak genellikle değildir.

Belirli iş mikro hizmetlerini veya sınırlı bağlamlarını belirlemiş olsanız da, bunları uygulamak için en iyi yol her zaman tek bir hizmet (örneğin, bir ASP.NET Web API 'SI) veya her bir iş mikro hizmeti için tek bir Docker kapsayıcısı oluşturmaktır. Her bir iş mikro hizmetinin tek bir hizmet kullanılarak veya kapsayıcı tarafından uygulanması gerektiğini söyleyen bir kurala sahip olmak çok rigıd.

Bu nedenle, bir iş mikro hizmeti veya sınırlı bağlam fiziksel mimariye sahip olabilecek (veya olmayan) bir mantıksal mimaridir. Önemli nokta, kod ve durumun bağımsız olarak sürümü oluşturulmuş, dağıtılmış ve ölçeklendirilmesine izin vererek bir iş mikro hizmetinin veya sınırlanmış bağlamın otonom olması gerekir.

Şekil 4-8 ' de gösterildiği gibi, katalog iş mikro hizmeti çeşitli hizmetlerden veya işlemlerden oluşabilir. Bunlar, HTTP veya diğer herhangi bir protokolü kullanarak birden çok ASP.NET Web API hizmeti veya başka türde bir hizmet olabilir. Daha da önemlisi, hizmetler aynı iş etki alanına göre aynı verileri paylaşabilir.

![Fiziksel sunucularla Katalog iş mikro hizmeti 'nin diyagramı.](./media/logical-versus-physical-architecture/multiple-physical-services.png)

**Şekil 4-8**. Çeşitli fiziksel hizmetlerle iş mikro hizmeti

Örnekteki hizmetler, Web API hizmeti arama hizmeti ile aynı verileri hedeflediğinden aynı veri modelini paylaşır. Bu nedenle, iş mikro hizmeti 'nin fiziksel uygulamasında bu işlevselliği böyorsunuz, böylece söz konusu iç hizmetlerin her birini gerektiği şekilde ölçeklendirebilirsiniz veya azaltabilirsiniz. Web API hizmeti genellikle arama hizmetinden daha fazla örneğe ihtiyaç duyuyor veya tam tersi olabilir.

Kısaca, mikro hizmetlerin mantıksal mimarisinin fiziksel dağıtım mimarisiyle her zaman uyması gerekmez. Bu kılavuzda, bir mikro hizmetten bahsettiğimiz zaman bir veya daha fazla (fiziksel) hizmetle eşlenecek bir iş veya mantıksal mikro hizmet demek sunuyoruz. Çoğu durumda bu tek bir hizmet olacaktır, ancak daha fazla olabilir.

>[!div class="step-by-step"]
>[Önceki](data-sovereignty-per-microservice.md)
>[İleri](distributed-data-management.md)
