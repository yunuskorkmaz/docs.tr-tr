---
title: Mantıksal mimari ile fiziksel mimari karşılaştırması
description: Mantıksal ve fiziksel mimarileri arasındaki farkları.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: e8ed375899637d06db8eb9b12a0e1cb0c05591f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756848"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Mantıksal mimari ile fiziksel mimari karşılaştırması

Bu noktada durdurmak ve mantıksal mimari ile fiziksel mimari ve nasıl Bu mikro hizmet tabanlı uygulama tasarımı için geçerlidir arasında ayrım tartışmak kullanışlıdır.

Başlamak için mikro hizmetler oluşturma herhangi belirli bir teknoloji kullanımı gerektirmez. Örneğin, Docker kapsayıcılar mikro hizmet tabanlı bir mimari oluşturmak için zorunlu değildir. Bu mikro hizmetler ayrıca düz işlemleri olarak çalıştırabilir. Mikro hizmetler mantıksal bir mimaridir.

Ayrıca, bile bir mikro hizmet, fiziksel bir tek hizmet, işlem veya kapsayıcı uygulanabilir (Basitlik'ın çok için olan ilk sürümünde uygulanan yaklaşıma [hizmetine](https://aka.ms/MicroservicesArchitecture)), bu arasındaki eşlik mutlaka birçok düzinelerce veya hatta yüzlerce hizmeti oluşan büyük ve karmaşık bir uygulama oluşturduğunuzda iş mikro hizmet ve fiziksel hizmet veya kapsayıcı her durumda gerekli değildir.

Burada bir uygulamanın mantıksal mimari ile fiziksel mimari arasında bir fark yoktur. Bir sistemin mantıksal sınırları ve mantıksal mimariyi mutlaka bire bir fiziksel veya dağıtım mimarisinin eşlemeyin. Olabilir, ancak genellikle değil.

Belirli iş mikro hizmetler ve sınırlanmış Bağlamlar belirlemiş ancak, bir tek hizmet (örneğin, ASP.NET Web API'si) ya da her iş mikro hizmet için tek bir Docker kapsayıcısı oluşturarak bunları uygulamak için en iyi yolu her zaman olduğu anlamına gelmez. Her iş mikro hizmet söyleyen bir kural sahip tek bir hizmet kullanılarak uygulanabilir veya kapsayıcı çok katı.

Bu nedenle, bir iş mikro hizmet içerik sınırlanmış (veya etkinleştirmezsiniz) çakıştığı bir mantıksal mimari mi ile fiziksel mimari. Önemli olan nokta bir iş mikro hizmet veya içerik sınırlanmış kod birbirinden bağımsız sürümlere olması durumuna dağıtılan ve ölçeklendirilmiş vererek otonom olmasıdır.

Şekil 4-8 gösterildiği gibi çeşitli hizmetler ve işlemlerin Kataloğu iş mikro hizmet oluşan. Bunlar, birden çok ASP.NET Web API Hizmetleri veya herhangi bir HTTP veya başka bir protokol kullanarak hizmetler türden olabilir. Daha da önemlisi, bu hizmetler aynı iş etki alanına göre birbirine bağlı olduğu sürece Hizmetleri aynı veri paylaşabilir.

![Diyagramı içeren bir API Kataloğu iş mikro hizmet, bir arama hizmeti ile SQL Server veritabanı hizmeti.](./media/image8.png)

**Şekil 4-8**. Birden fazla fiziksel Hizmetleri ile iş mikro hizmet

Web API'si hizmeti arama hizmetinin aynı verilere hedeflediğinden örnekte Hizmetleri aynı veri modeli paylaşın. Fiziksel iş mikro hizmet uygulamasında, iç bu hizmetlerin her birini yukarı veya aşağı gerektiği şekilde ölçeklendirebilirsiniz şekilde işlevselliği bölme şekilde. Belki de Web API'si hizmeti genellikle ihtiyaçlarını daha fazla arama hizmeti veya tam tersi örnekleri.

Kısacası, mantıksal mikro hizmetler mimarisi her zaman fiziksel dağıtım mimarisi ile çakıştığı yok. Her bir mikro hizmet bahsetmek Biz bu kılavuzda, bir işletmeyi ya da bir veya daha fazla (fiziksel) Hizmetleri eşleyebilirsiniz mantıksal mikro hizmet demek isteriz. Çoğu durumda, bu tek bir hizmet olacaktır, ancak daha fazla olabilir.

>[!div class="step-by-step"]
>[Önceki](data-sovereignty-per-microservice.md)
>[İleri](distributed-data-management.md)