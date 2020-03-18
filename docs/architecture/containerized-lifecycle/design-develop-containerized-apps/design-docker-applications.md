---
title: Docker uygulamaları tasarlama
description: Burada mikro hizmetler mimarisi için ayrıntılı bir kılavuza bir başvuru bulabilirsiniz, çünkü bu kılavuzda ayrıntılı olarak belirtilmeyecek bir konudur.
ms.date: 02/15/2019
ms.openlocfilehash: b9539ff4edf405ab890d83be59a248ffa2360c99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295865"
---
# <a name="design-docker-applications"></a>Docker uygulamaları tasarlama

Bölüm 1 konteyner ve Docker ile ilgili temel kavramları tanıttı. Bu bilgiler, başlamak için gereken temel bilgi düzeyidir. Ancak, kurumsal uygulamalar karmaşık olabilir ve tek bir hizmet veya kapsayıcı yerine birden çok hizmetten oluşabilir. İsteğe bağlı kullanım örnekleri için, Hizmet Odaklı Mimari (SOA) ve daha gelişmiş microservices kavramları ve konteyner orkestrasyon kavramları gibi tasarıma ek yaklaşımları bilmeniz gerekir. Bu belgenin kapsamı mikro hizmetlerle sınırlı değildir, ancak docker uygulama yaşam döngüsü ile sınırlı değildir, bu nedenle, mikrohizmetler mimarisini derinlemesine keşfetmez, çünkü düzenli SOA, arka plan görevleri veya işleri ve hatta yekpare uygulama dağıtım yaklaşımları ile.

**Daha fazla bilgi** Kurumsal uygulamalar ve mikrohizmetler mimarisi hakkında daha fazla bilgi edinmek [için NET Microservices: Architecture for Containerized .NET Applications](../../microservices/index.md) adlı rehberi ni <https://aka.ms/MicroservicesEbook>okuyabilirsiniz.

Ancak, uygulama yaşam döngüsüne ve DevOps'lere girmeden önce, uygulamanızı nasıl tasarlayıp oluşturacağınız ve tasarım seçenekleriniz nelerdir bilmek önemlidir.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[Sonraki](common-container-design-principles.md)
