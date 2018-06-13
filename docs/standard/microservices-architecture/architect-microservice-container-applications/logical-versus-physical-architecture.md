---
title: Fiziksel yapısı ve mantıksal mimarisi
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Fiziksel yapısı ve mantıksal mimarisi
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: f77123977a50c30150f5a64cc08c3c217b429ac4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574692"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Fiziksel yapısı ve mantıksal mimarisi

Bu noktada durdurmak ve mantıksal mimarisi ve fiziksel mimarisi ve bu mikro hizmet tabanlı uygulamalar tasarımını nasıl uygulandığı arasında ayrım tartışmak yararlıdır.

Başlamak için mikro hizmetler oluşturma herhangi belirli teknolojisinin kullanılmasına gerektirmez. Örneğin, Docker kapsayıcıları mikro hizmet tabanlı bir mimari oluşturmak için zorunlu değildir. Bu mikro düz işlemleri olarak da çalıştırılabilir. Mikro mantıksal bir mimaridir.

Ayrıca, bile bir mikro hizmet fiziksel olarak tek hizmet, işlem veya kapsayıcı olarak uygulanabilir (Basitlik'ın artırmak amacıyla için olan ilk sürümünde uygulanan yaklaşıma [eShopOnContainers](http://aka.ms/MicroservicesArchitecture)), bu eşlik arasında birçok düzinelerce veya hatta yüzlerce Hizmetleri oluşan büyük ve karmaşık bir uygulama oluşturduğunuzda iş mikro hizmet ve fiziksel hizmet veya kapsayıcı mutlaka her durumda gerekli değildir.

Bu yerdir bir uygulamanın mantıksal mimarisi ve fiziksel yapısı arasında fark yoktur. Mantıksal mimarisi ve bir sistem mantıksal sınırlarının mutlaka fiziksel veya dağıtım mimarisi için bire bir eşleme değil. Olabilir, ancak genellikle yok.

Belirli iş mikro veya sınırlanmış bağlamları belirlemiş ancak bir tek hizmet (örneğin, bir ASP.NET Web API) ya da her iş mikro hizmet için tek Docker kapsayıcısı oluşturarak bunları uygulamak için en iyi yolu her zaman olduğu gelmez. Her iş mikro hizmet belirten bir kural sahip tek bir hizmet kullanarak uygulanacak olan veya çok katı bir kapsayıcısıdır.

Bu nedenle, bir iş mikro ilişkisindeki bağlam (veya değil) çakıştığı mantıksal bir mimari mi fiziksel mimarisine sahip. Bir iş mikro hizmet veya sınırlanmış bağlam kodu ve bağımsız olarak sürümlü olması durumuna dağıtılan ve ölçeklendirilmiş vererek otonom olması gerektiğini önemli noktasıdır.

Şekil 4-8'de görüldüğü gibi katalog iş mikro birkaç Hizmetleri veya işlemleri oluşan. Bunlar, birden çok ASP.NET Web API Hizmetleri veya diğer her türlü HTTP veya diğer herhangi bir protokolünü kullanarak Hizmetleri olabilir. Daha da önemlisi, bu hizmetler aynı iş etki alanına göre bağlı olduğu sürece Hizmetleri aynı veri paylaşabilir.

![](./media/image8.png)

**Şekil 4-8**. Birden fazla fiziksel hizmetleriyle iş mikro hizmet

Web API hizmeti arama hizmeti olarak aynı veri hedeflediğinden örnek Hizmetleri'nde aynı veri modeli paylaşır. İş mikro hizmet fiziksel uygulamasında her iç hizmetlerin yukarı veya aşağı gerektiğinde ölçeklendirmek için bu işlevselliği bölme şekilde. Belki de Web API'si hizmeti genellikle ihtiyaçlarını daha arama hizmeti daha veya tersi örnekler.)

Kısacası, mikro mantıksal mimarisi fiziksel dağıtım mimarisi ile çakıştığı her zaman yok. Biz bir mikro Bahsediyor her bu kılavuzda, bir iş ya da bir veya daha fazla hizmet için eşleme mantıksal mikro hizmet demek isteriz. Çoğu durumda bu tek bir hizmeti olacaktır, ancak daha fazla olabilir.


>[!div class="step-by-step"]
[Önceki] (veri-Egemenlik-başına-microservice.md) [sonraki] (dağıtılmış-data-management.md)
