---
title: Mantıksal mimari ile fiziksel mimari karşılaştırması
description: Mantıksal ve fiziksel mimarilerin farklarını anlayın.
ms.date: 09/20/2018
ms.openlocfilehash: c269369e9b5391e8d25ece46e6b08e34a82fbbba
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295495"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Mantıksal mimari ile fiziksel mimari karşılaştırması

Bu noktada, mantıksal mimari ve fiziksel mimari arasındaki farkın durdurulması ve ele alındığı ve bu durumun mikro hizmet tabanlı uygulamaların tasarımına nasıl uygulandığı açıklanmaktadır.

Başlamak için, mikro hizmetlerin oluşturulması belirli bir teknolojinin kullanılmasını gerektirmez. Örneğin, Docker kapsayıcıları, mikro hizmet tabanlı bir mimari oluşturmak için zorunlu değildir. Bu mikro hizmetler düz işlem olarak da çalıştırılabilir. Mikro hizmetler bir mantıksal mimaridir.

Üstelik, bir mikro hizmet fiziksel olarak tek bir hizmet, işlem veya kapsayıcı olarak uygulansa bile (basitlik için [Eshoponcontainers](https://aka.ms/MicroservicesArchitecture)'un ilk sürümünde gerçekleştirilen yaklaşım), iş mikro hizmeti arasında bu eşlik ve çoğu düzinelerce veya hatta yüzlerce hizmetten oluşan büyük ve karmaşık bir uygulama oluşturduğunuzda tüm durumlarda fiziksel hizmet veya kapsayıcı gerekli değildir.

Bu, bir uygulamanın mantıksal mimarisi ve fiziksel mimarisi arasında bir farklılık olduğu yerdir. Bir sistemin mantıksal mimarisi ve mantıksal sınırları, bire bir-bir ' i fiziksel veya dağıtım mimarisine eşlemenize gerek yoktur. Bu durum gerçekleşebilir, ancak genellikle değildir.

Belirli iş mikro hizmetlerini veya sınırlı bağlamlarını belirlemiş olsanız da, bunları uygulamak için en iyi yol her zaman tek bir hizmet (örneğin, bir ASP.NET Web API 'SI) veya her bir iş mikro hizmeti için tek bir Docker kapsayıcısı oluşturmaktır. Her bir iş mikro hizmetinin tek bir hizmet kullanılarak veya kapsayıcı tarafından uygulanması gerektiğini söyleyen bir kurala sahip olmak çok rigıd.

Bu nedenle, bir iş mikro hizmeti veya sınırlı bağlam fiziksel mimariye sahip olabilecek (veya olmayan) bir mantıksal mimaridir. Önemli nokta, kod ve durumun bağımsız olarak sürümü oluşturulmuş, dağıtılmış ve ölçeklendirilmesine izin vererek bir iş mikro hizmetinin veya sınırlanmış bağlamın otonom olması gerekir.

Şekil 4-8 ' de gösterildiği gibi, katalog iş mikro hizmeti çeşitli hizmetlerden veya işlemlerden oluşabilir. Bunlar, HTTP veya diğer herhangi bir protokolü kullanarak birden çok ASP.NET Web API hizmeti veya başka türde bir hizmet olabilir. Daha da önemlisi, hizmetler aynı iş etki alanına göre aynı verileri paylaşabilir.

![Bir API hizmeti olan bir arama hizmeti ve bir SQL Server veritabanı içeren katalog iş mikro hizmetinin diyagramı.](./media/image8.png)

**Şekil 4-8**. Çeşitli fiziksel hizmetlerle iş mikro hizmeti

Örnekteki hizmetler, Web API hizmeti arama hizmeti ile aynı verileri hedeflediğinden aynı veri modelini paylaşır. Bu nedenle, iş mikro hizmeti 'nin fiziksel uygulamasında bu işlevselliği böyorsunuz, böylece söz konusu iç hizmetlerin her birini gerektiği şekilde ölçeklendirebilirsiniz veya azaltabilirsiniz. Web API hizmeti genellikle arama hizmetinden daha fazla örneğe ihtiyaç duyuyor veya tam tersi olabilir.

Kısaca, mikro hizmetlerin mantıksal mimarisinin fiziksel dağıtım mimarisiyle her zaman uyması gerekmez. Bu kılavuzda, bir mikro hizmetten bahsettiğimiz zaman bir veya daha fazla (fiziksel) hizmetle eşlenecek bir iş veya mantıksal mikro hizmet demek sunuyoruz. Çoğu durumda bu tek bir hizmet olacaktır, ancak daha fazla olabilir.

>[!div class="step-by-step"]
>[Önceki](data-sovereignty-per-microservice.md)İleri
>[](distributed-data-management.md)
