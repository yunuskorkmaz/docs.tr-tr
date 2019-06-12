---
title: Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Kapsayıcı tabanlı uygulamalar için Azure işlem platformlarını seçme
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833850"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme

Önceki bölümlerde okuduktan sonra fark etmiş gibi birden çok seçenek sunan bir açık bulut azure'dur. İhtiyaçlarınıza en uygun kullanabilirsiniz, ancak bunu ayrıca kapsayıcılı uygulamalarınız için kullanması gereken hangi ürün/teknoloji hakkında sorular ortaya çıkarır.

Olarak bir *varsayılan olarak* öneri, bu kılavuzda önerilen ana ölçüt aşağıdaki gibidir:

- **Tek tek parçalı uygulama:** Azure uygulama hizmeti seçin
- **N katmanlı uygulama:** Tek bir veya birkaç arka uç Hizmetleri varsa, Azure Kubernetes Service (AKS) veya App Service gibi düzenleyiciler arasından seçim yapın
- **Mikro hizmetler:** AKS veya Azure Web uygulaması için kapsayıcı seçin
- **& Olay işleyicileri sunucusuz İşlevler:** Azure işlevleri'ni seçin
- **Büyük ölçekli Batch:** Azure Batch seçin

Ancak, ürünün seçimi belirli uygulamanızın gereksinimlerini ve özelliklerini bağlı olarak bu öneriyi güvenlik değeri,'bir tabletinizde ile dikkat edilmelidir. Hatta Başlangıçta bunlar benzer türler görünebilir, tüm uygulamalar aynı olur.

Uygulama gereksinimleri hakkında daha ayrıntılı çözümleme sonrasında, seçili ürün farklı olabilir. Ancak, bir başlangıç noktası olarak değerlendiriliyor başlayabileceğiniz gelen başlangıç düzeyi bir kılavuz olmanız faydalı olacaktır ve belirli önceliğine bağlı olarak test etme.

Sonraki şekilde, farklı türde uygulamaları ve bunların ideal Azure barındırma senaryolarında dökümünü görebilirsiniz.

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [İleri](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
