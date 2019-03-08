---
title: Docker uygulamaları tasarlama
description: Mikro hizmet mimarisi için kapsamlı bir kılavuz başvuru, bir konu olduğu için burada bulabilirsiniz, bu kılavuzda ayrıntılı değil.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 858147883b3b4a5a5f487856028fdbfa84f6cca9
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675192"
---
# <a name="design-docker-applications"></a>Docker uygulamaları tasarlama

Bölüm 1 kapsayıcıları ve Docker ile ilgili temel kavramları sundu. Bu bilgileri kullanmaya başlamak gereken bilgileri temel düzeyidir. Ancak, Kurumsal uygulamaları, karmaşık ve oluştuğundan, birden çok hizmet yerine tek bir hizmet veya kapsayıcı olabilir. Bu isteğe bağlı kullanım durumları için ek yaklaşımları Service-Oriented mimari (SOA) gibi tasarım ve daha gelişmiş mikro hizmetler kavramları ve kapsayıcı düzenleme kavramlarını bilmeniz gerekir. Bu belgenin kapsamı mikro hizmetler için sınırlı değildir, ancak ayrıca kapsayıcıları ve Docker ile normal SOA, arka plan görevleri veya işleri kullanın, veya hatta çünkü tüm Docker uygulaması yaşam döngüsü için bu nedenle, mikro hizmetler mimarisi derinlemesine keşfedin değil tek parçalı bir uygulama dağıtım yaklaşımları ile.

**Daha fazla bilgi** kurumsal uygulamalar ve mikro hizmet mimarisi derinlemesine hakkında daha fazla bilgi edinmek için Kılavuzu okuyun [NET mikro hizmetler: Kapsayıcılı .NET uygulamaları mimarisi](https://docs.microsoft.com/dotnet/standard/microservices-architecture) dan indirebileceğiniz <https://aka.ms/MicroservicesEbook>.

Ancak, DevOps ve uygulama yaşam döngüsü içinde aldığımız önce tasarım nasıl duyacağınızı biliyorsanız ve uygulamanız ve tasarım seçimlerinizi nelerdir oluşturmak önem taşır.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](common-container-design-principles.md)
