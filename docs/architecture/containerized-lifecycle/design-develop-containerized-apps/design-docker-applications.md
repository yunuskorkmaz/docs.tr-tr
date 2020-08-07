---
title: Docker uygulamaları tasarlama
description: Bu kılavuzda ayrıntılı olmadığından, mikro hizmetler mimarisine yönelik derinlemesine bir kılavuza yönelik bir başvuru bulabilirsiniz.
ms.date: 08/06/2020
ms.openlocfilehash: b63d4344abb358a393587bdacf91f6091b531af0
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915984"
---
# <a name="design-docker-applications"></a>Docker uygulamaları tasarlama

Bölüm 1, kapsayıcılar ve Docker ile ilgili temel kavramları sunmuştur. Bu bilgiler, başlamak için ihtiyacınız olan temel bilgi düzeyidir. Ancak kurumsal uygulamalar, tek bir hizmet veya kapsayıcı yerine karmaşık ve birden çok hizmetten oluşabilir. Bu isteğe bağlı kullanım örnekleri için, hizmet odaklı mimari (SOA) ve daha gelişmiş mikro hizmet kavramları ve kapsayıcı düzenleme kavramları gibi tasarıma yönelik ek yaklaşımlar bilmeniz gerekir. Bu belgenin kapsamı mikro hizmetlerle sınırlı değildir, ancak herhangi bir Docker uygulaması yaşam döngüsü ile, kapsayıcıları ve Docker 'ı normal SOA, arka plan görevleri veya işleriyle, hatta tek parçalı uygulama dağıtımı yaklaşımları ile de kullanabileceğiniz için, mikro hizmetler mimarisini derinlemesine bir şekilde araştırmaz.

**Daha fazla bilgi** Kurumsal uygulamalar ve mikro hizmetler mimarisi hakkında ayrıntılı bilgi edinmek için, ağ mikro hizmetleri: ' dan da indirebileceğiniz [Kapsayıcılı .NET uygulamaları Için mimari](../../microservices/index.md) makalesini okuyun <https://aka.ms/MicroservicesEbook> .

Ancak, uygulama yaşam döngüsü ve DevOps 'a girmeden önce, uygulamanızı nasıl tasarlayacağınızı ve tasarlayacağınızı ve tasarım seçimlerinizle karşılaşabileceğinizi bilmeniz önemlidir.

>[!div class="step-by-step"]
>[Önceki](index.md) 
> [Sonraki](common-container-design-principles.md)
