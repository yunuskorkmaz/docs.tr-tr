---
title: Docker uygulamaları tasarlama
description: Mikro hizmet mimarisi için kapsamlı bir kılavuz başvuru, bir konu olduğu için burada bulabilirsiniz, bu kılavuzda ayrıntılı değil.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 1d49f7509c0a12edfe375486429147e8fd240b2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799352"
---
# <a name="design-docker-applications"></a>Docker uygulamaları tasarlama

Bölüm 1 kapsayıcıları ve Docker ile ilgili temel kavramları sundu. Bu bilgileri kullanmaya başlamak gereken bilgileri temel düzeyidir. Ancak, Kurumsal uygulamaları, karmaşık ve oluştuğundan, birden çok hizmet yerine tek bir hizmet veya kapsayıcı olabilir. Bu isteğe bağlı kullanım durumları için ek yaklaşımları Service-Oriented mimari (SOA) gibi tasarım ve daha gelişmiş mikro hizmetler kavramları ve kapsayıcı düzenleme kavramlarını bilmeniz gerekir. Bu belgenin kapsamı mikro hizmetler için sınırlı değildir, ancak ayrıca kapsayıcıları ve Docker ile normal SOA, arka plan görevleri veya işleri kullanın, veya hatta çünkü tüm Docker uygulaması yaşam döngüsü için bu nedenle, mikro hizmetler mimarisi derinlemesine keşfedin değil tek parçalı bir uygulama dağıtım yaklaşımları ile.

**Daha fazla bilgi** kurumsal uygulamalar ve mikro hizmet mimarisi derinlemesine hakkında daha fazla bilgi edinmek için Kılavuzu okuyun [NET mikro hizmetler: Kapsayıcılı .NET uygulamaları mimarisi](../../microservices-architecture/index.md) dan indirebileceğiniz <https://aka.ms/MicroservicesEbook>.

Ancak, DevOps ve uygulama yaşam döngüsü içinde aldığımız önce tasarım nasıl duyacağınızı biliyorsanız ve uygulamanız ve tasarım seçimlerinizi nelerdir oluşturmak önem taşır.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](common-container-design-principles.md)