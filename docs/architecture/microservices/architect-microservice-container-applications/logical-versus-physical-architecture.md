---
title: Mantıksal mimari ile fiziksel mimari karşılaştırması
description: Mantıksal ve fiziksel mimariler arasındaki farkları anlayın.
ms.date: 09/20/2018
ms.openlocfilehash: 8d1bfca190eb9b18d46625fa4afdec963eb07054
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834397"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Mantıksal mimari ile fiziksel mimari karşılaştırması

Bu noktada, mantıksal mimari ve fiziksel mimari arasındaki ayrımı ve bunun mikro hizmet tabanlı uygulamaların tasarımı için nasıl geçerli olduğunu durdurmak ve tartışmak yararlıdır.

Başlamak için, mikro hizmetler oluşturmak için herhangi bir özel teknolojinin kullanılması gerekmez. Örneğin, Docker kapsayıcıları mikro hizmet tabanlı bir mimari oluşturmak için zorunlu değildir. Bu mikro hizmetler de düz süreçler olarak çalıştırılabilir. Microservices mantıksal bir mimaridir.

Ayrıca, bir microservice fiziksel olarak tek bir hizmet, süreç veya konteyner olarak uygulanabilir (basitlik aşkına, bu [yaklaşım eShopOnContainers](https://aka.ms/MicroservicesArchitecture)ilk sürümünde alınan ' s ), iş microservice ve fiziksel hizmet veya konteyner arasındaki bu parite mutlaka her durumda büyük ve karmaşık bir uygulama birçok düzinelerce hatta yüzlerce hizmet oluşan inşa gerekli değildir.

Uygulamanın mantıksal mimarisi ile fiziksel mimarisi arasında fark vardır. Bir sistemin mantıksal mimarisi ve mantıksal sınırları, fiziksel veya dağıtım mimarisiyle bire bir eşlemesi gerekmez. Olabilir, ama çoğu zaman olmaz.

Belirli iş mikro hizmetlerini veya Sınırlı Bağlamları tanımlamış olabilirsiniz, ancak bu, bunları uygulamanın en iyi yolunun her iş mikro hizmeti için tek bir hizmet (ASP.NET Web API gibi) veya tek docker kapsayıcısı oluşturmak olduğu anlamına gelmez. Her iş microservice tek bir hizmet veya konteyner kullanılarak uygulanması gerektiğini belirten bir kural olması çok katıdır.

Bu nedenle, bir iş microservice veya Sınırlı Bağlam fiziksel mimari ile çakışabilir (veya değil) mantıksal bir mimaridir. Önemli nokta, bir iş microservice veya Sınırlı Bağlam kod ve devlet bağımsız olarak sürümü, dağıtılan ve ölçeklendirilmelidir izin vererek özerk olması gerektiğidir.

Şekil 4-8'in gösterdiği gibi, katalog iş microservice çeşitli hizmet veya işlemlerden oluşabilir. Bunlar, HTTP veya başka bir protokolü kullanarak birden çok ASP.NET Web API hizmeti veya başka bir tür hizmet olabilir. Daha da önemlisi, bu hizmetler aynı iş alanı yla ilgili olarak uyumlu olduğu sürece, hizmetler aynı verileri paylaşabilir.

![Fiziksel sunucular ile Katalog iş microservice Diyagramı.](./media/logical-versus-physical-architecture/multiple-physical-services.png)

**Şekil 4-8**. Çeşitli fiziksel hizmetler ile iş microservice

Web API hizmeti Arama hizmetiyle aynı verileri hedeflediğinden, örnekteki hizmetler aynı veri modelini paylaşır. Yani, iş mikrohizmetinin fiziksel uygulamasında, bu işlevselliği bölerek bu dahili hizmetlerin her birini gerektiği gibi yukarı veya aşağı ölçeklendirebilirsiniz. Belki Web API hizmeti genellikle Arama hizmetidaha fazla örnek gerekir, ya da tam tersi.

Kısacası, mikro hizmetlerin mantıksal mimarisi her zaman fiziksel dağıtım mimarisiyle çakışmak zorunda değildir. Bu kılavuzda, ne zaman bir microservice söz, biz bir veya daha fazla (fiziksel) hizmetleri harita olabilir bir iş veya mantıksal microservice anlamına gelir. Çoğu durumda, bu tek bir hizmet olacaktır, ancak daha fazla olabilir.

>[!div class="step-by-step"]
>[Önceki](data-sovereignty-per-microservice.md)
>[Sonraki](distributed-data-management.md)
