---
title: Docker uygulamaları tasarlama
description: Burada mikro hizmetler mimarisi için ayrıntılı bir kılavuza bir başvuru bulabilirsiniz, çünkü bu kılavuzda ayrıntılı olarak belirtilmeyecek bir konudur.
ms.date: 02/15/2019
ms.openlocfilehash: b8a08658ec6c3df3e1aed596a0240223768dd647
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738458"
---
# <a name="design-docker-applications"></a>Docker uygulamaları tasarlama

Bölüm 1 konteyner ve Docker ile ilgili temel kavramları tanıttı. Bu bilgiler, başlamak için gereken temel bilgi düzeyidir. Ancak, kurumsal uygulamalar karmaşık olabilir ve tek bir hizmet veya kapsayıcı yerine birden çok hizmetten oluşabilir. İsteğe bağlı kullanım örnekleri için, Hizmet Odaklı Mimari (SOA) ve daha gelişmiş microservices kavramları ve konteyner orkestrasyon kavramları gibi tasarıma ek yaklaşımları bilmeniz gerekir. Bu belgenin kapsamı mikro hizmetlerle sınırlı değildir, ancak herhangi bir Docker uygulama yaşam döngüsüyle sınırlı değildir, bu nedenle, düzenli SOA, arka plan görevleri veya işleri, hatta yekpare uygulama dağıtım yaklaşımları ile kaplar ve Docker kullanabilirsiniz, çünkü derinlemesine mikrohizmetler mimarisi keşfetmek değildir.

**Daha fazla bilgi** Kurumsal uygulamalar ve mikrohizmetler mimarisi hakkında daha fazla bilgi edinmek [için NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) adlı rehberi ni <https://aka.ms/MicroservicesEbook>okuyabilirsiniz.

Ancak, uygulama yaşam döngüsüne ve DevOps'lere girmeden önce, uygulamanızı nasıl tasarlayıp oluşturacağınız ve tasarım seçenekleriniz nelerdir bilmek önemlidir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](common-container-design-principles.md)
