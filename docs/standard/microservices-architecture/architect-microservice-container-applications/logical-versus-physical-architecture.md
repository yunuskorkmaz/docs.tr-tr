---
title: Mantıksal mimari ile fiziksel mimari karşılaştırması
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Mantıksal mimari ile fiziksel mimari karşılaştırması
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: bb5f0daf0bcf824d72bb104914de03532bd3f9f7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44136394"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Mantıksal mimari ile fiziksel mimari karşılaştırması

Bu noktada durdurmak ve mantıksal mimari ile fiziksel mimari ve nasıl Bu mikro hizmet tabanlı uygulama tasarımı için geçerlidir arasında ayrım tartışmak kullanışlıdır.

Başlamak için mikro hizmetler oluşturma herhangi belirli bir teknoloji kullanımı gerektirmez. Örneğin, Docker kapsayıcıları, mikro hizmet tabanlı bir mimari oluşturmak için zorunlu değildir. Bu mikro hizmetler ayrıca düz işlemleri olarak çalıştırabilir. Mikro hizmetler mantıksal bir mimaridir.

Ayrıca, bile bir mikro hizmet, fiziksel bir tek hizmet, işlem veya kapsayıcı uygulanabilir (Basitlik'ın çok için olan ilk sürümünde uygulanan yaklaşıma [hizmetine](https://aka.ms/MicroservicesArchitecture)), bu arasındaki eşlik birçok düzinelerce veya hatta yüzlerce hizmeti oluşan büyük ve karmaşık bir uygulama oluşturduğunuzda iş mikro hizmet ve fiziksel hizmet veya kapsayıcı mutlaka her durumda gerekli değildir.

Burada bir uygulamanın mantıksal mimari ile fiziksel mimari arasında bir fark yoktur. Bir sistemin mantıksal sınırları ve mantıksal mimariyi mutlaka bire bir fiziksel veya dağıtım mimarisinin eşlemeyin. Olabilir, ancak genellikle yok.

Belirli iş mikro hizmetler ve sınırlanmış Bağlamlar belirlemiş ancak bir tek hizmet (örneğin, ASP.NET Web API'si) ya da her iş mikro hizmet için tek bir Docker kapsayıcısı oluşturarak bunları uygulamak için en iyi yolu her zaman olduğu gelmez. Her iş mikro hizmet söyleyen bir kural sahip tek bir hizmet kullanılarak uygulanabilir veya kapsayıcı çok katı.

Bu nedenle, bir iş mikro hizmet içerik sınırlanmış (veya etkinleştirmezsiniz) çakıştığı bir mantıksal mimari mi ile fiziksel mimari. Önemli olan nokta bir iş mikro hizmet veya içerik sınırlanmış kod birbirinden bağımsız sürümlere olması durumuna dağıtılan ve ölçeklendirilmiş vererek otonom olmasıdır.

Şekil 4-8 gösterildiği gibi çeşitli hizmetler ve işlemlerin Kataloğu iş mikro hizmet oluşan. Bunlar, birden çok ASP.NET Web API Hizmetleri veya herhangi bir HTTP veya başka bir protokol kullanarak hizmetler türden olabilir. Daha da önemlisi, bu hizmetler aynı iş etki alanına göre birbirine bağlı olduğu sürece Hizmetleri aynı veri paylaşabilir.

![](./media/image8.png)

**Şekil 4-8**. Birden fazla fiziksel Hizmetleri ile iş mikro hizmet

Web API'si hizmeti arama hizmetinin aynı verilere hedeflediğinden örnekte Hizmetleri aynı veri modeli paylaşın. Bu nedenle, iş mikro hizmet fiziksel uygulamasında, bu iç hizmetlerinin her biri yukarı veya aşağı gerektiği şekilde ölçeklendirebilirsiniz şekilde işlevselliği bölüyor. Belki de Web API'si hizmeti genellikle ihtiyaçlarını daha fazla arama hizmeti veya tam tersi örnekleri.

Kısacası, mikro hizmetler mantıksal mimarisini fiziksel dağıtım mimarisi ile çakıştığı her zaman yok. Her bir mikro hizmet bahsetmek Biz bu kılavuzda, bir işletmeyi ya da bir veya daha fazla hizmet için eşleyebilirsiniz mantıksal mikro hizmet demek isteriz. Çoğu durumda, bu tek bir hizmet olacaktır, ancak daha fazla olabilir.


>[!div class="step-by-step"]
[Önceki](data-sovereignty-per-microservice.md)
[İleri](distributed-data-management.md)
