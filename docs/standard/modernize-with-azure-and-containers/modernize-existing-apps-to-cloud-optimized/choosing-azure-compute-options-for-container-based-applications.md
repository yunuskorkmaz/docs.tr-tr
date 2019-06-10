---
title: Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Kapsayıcı tabanlı uygulamalar için Azure işlem platformlarını seçme
ms.date: 05/04/2018
ms.openlocfilehash: d91cd279402dc24beb5f766c06cb85ac8d74f482
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758808"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme

Önceki bölümlerde okuduktan sonra fark etmiş gibi birden çok seçenek sunan bir açık bulut azure'dur. İhtiyaçlarınıza en uygun kullanabilirsiniz, ancak bunu ayrıca kapsayıcılı uygulamalarınız için kullanması gereken hangi ürün/teknoloji hakkında sorular ortaya çıkarır.

Olarak bir *varsayılan olarak* öneri, bu kılavuzda önerilen ana ölçüt aşağıdaki gibidir:

- **Tek tek parçalı uygulama:** Azure uygulama hizmeti seçin
- **N katmanlı uygulama:** Tek bir veya birkaç arka uç Hizmetleri varsa, Azure Kubernetes Service (AKS) veya App Service gibi düzenleyiciler arasından seçim yapın
- **Linux mikro hizmetler:** AKS/Kubernetes seçin
- **Windows mikro hizmetler:** Azure Web uygulaması için kapsayıcı Seç
- **& Olay işleyicileri sunucusuz İşlevler:** Azure işlevleri'ni seçin
- **Büyük ölçekli Batch:** Azure Batch seçin

Ancak, ürünün seçimi belirli uygulamanızın gereksinimlerini ve özelliklerini bağlı olarak bu öneriyi güvenlik değeri,'bir tabletinizde ile dikkat edilmelidir. Hatta Başlangıçta bunlar benzer türler görünebilir, tüm uygulamalar aynı olur.

Uygulama gereksinimleri hakkında daha ayrıntılı çözümleme sonrasında, seçili ürün farklı olabilir. Ancak, bir başlangıç noktası olarak değerlendiriliyor başlayabileceğiniz gelen başlangıç düzeyi bir kılavuz olmanız faydalı olacaktır ve belirli önceliğine bağlı olarak test etme.

Sonraki şekilde, farklı türde uygulamaları ve bunların ideal Azure barındırma senaryolarında dökümünü görebilirsiniz.

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [İleri](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
