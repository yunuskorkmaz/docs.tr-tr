---
title: Docker uygulamaları tasarlama
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: d02cec0595024eb7bd7c0ac46df093359680da74
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155385"
---
# <a name="design-docker-applications"></a>Docker uygulamaları tasarlama

Bölüm 1 kapsayıcıları ve Docker ile ilgili temel kavramları sundu. Bu bilgileri kullanmaya başlamak gereken bilgileri temel düzeyidir. Ancak, Kurumsal uygulamaları, karmaşık ve oluştuğundan, birden çok hizmet yerine tek bir hizmet veya kapsayıcı olabilir. Bu isteğe bağlı kullanım durumları için ek yaklaşımları Service-Oriented mimari (SOA) gibi tasarım ve daha gelişmiş mikro hizmetler kavramları ve kapsayıcı düzenleme kavramlarını bilmeniz gerekir. Bu belgenin kapsamı mikro hizmetler için sınırlı değildir, ancak ayrıca kapsayıcıları ve Docker ile normal SAO, arka plan görevleri veya işleri kullanın, veya hatta çünkü tüm Docker uygulaması yaşam döngüsü için bu nedenle, mikro hizmetler mimarisi derinlemesine keşfedin değil tek parçalı bir uygulama dağıtım yaklaşımları ile.

Ancak, DevOps ve uygulama yaşam döngüsü içinde aldığımız önce tasarım nasıl kalacaklarını bilmek ve uygulamanız ve tasarım seçimlerinizi nelerdir oluşturmak önem taşır.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](common-container-design-principles.md)