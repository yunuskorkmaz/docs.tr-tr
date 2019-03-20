---
title: Kapsayıcı tabanlı uygulamalar için Azure işlem platformlarını seçme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Kapsayıcı tabanlı uygulamalar için Azure işlem platformlarını seçme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: f251aecfeaf2421a5cecf218577369963bc736fb
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186110"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Kapsayıcı tabanlı uygulamalar için Azure işlem platformlarını seçme

Önceki bölümlerde okuduktan sonra fark etmiş gibi birden çok seçenek sunan bir açık bulut azure'dur. İhtiyaçlarınıza en uygun kullanabilirsiniz, ancak bunu ayrıca kapsayıcılı uygulamalarınız için kullanması gereken hangi ürün/teknoloji hakkında sorular ortaya çıkarır.

Olarak bir *varsayılan olarak* öneri, bu kılavuzda önerilen ana ölçüt aşağıdaki gibidir:

- **Tek tek parçalı uygulama:** Azure uygulama hizmeti seçin
- **N katmanlı uygulama:** Tek bir veya birkaç arka uç Hizmetleri varsa, Azure Kubernetes Service (AKS), Service Fabric (BT) veya App Service gibi düzenleyiciler arasından seçim yapın
- **Linux mikro hizmetler:** AKS/Kubernetes seçin
- **Windows mikro hizmetler:** Service Fabric seçin
- **& Olay işleyicileri sunucusuz İşlevler:** Azure işlevleri'ni seçin
- **Büyük ölçekli Batch:** Azure Batch seçin

Ancak, ürünün seçimi belirli uygulamanızın gereksinimlerini ve özelliklerini bağlı olarak bu öneriyi güvenlik değeri,'bir tabletinizde ile dikkat edilmelidir. Hatta Başlangıçta bunlar benzer türler görünebilir, tüm uygulamalar aynı olur.

Uygulama gereksinimleri hakkında daha ayrıntılı çözümleme sonrasında, seçili ürün farklı olabilir. Ancak, bir başlangıç noktası olarak değerlendiriliyor başlayabileceğiniz gelen başlangıç düzeyi bir kılavuz olmanız faydalı olacaktır ve belirli önceliğine bağlı olarak test etme.

Sonraki şekilde, daha genel bir ayrıntılı karar tablosu sırasında çözümleyebilirsiniz.

![](./media/image8.5.png)

Bildirim nasıl temel işletim sistemi (Windows vs. Linux) bir karar faktör daha olgun Linux kapsayıcıları üzerinde ve Windows kapsayıcılarına diğer bazı düzenleyiciler da olabilir. Örneğin, Linux kapsayıcıları Service Fabric üzerinde daha az olgun ancak (AKS azure'da) Kubernetes içinde çok olgun. Diğer taraftan, Windows kapsayıcıları Service Fabric (Mayıs 2017'de yayımlanan) daha olgun ve daha az AKS olgun.

Ancak, bu işletim sistemi olgunluk farklılıkları gelecekte kaybolacaktır ve birden çok platform karşılaştırılabilir işletim sistemi olgunluk olduğundan ve kararı uygulamanız gerekebilir veya üzerinde her platformun ekosistemi dayalı belirli özelliklere bağlı olarak tercihleri üzerinde daha fazla düzenleme nedenleri.

> [!div class="step-by-step"]
> [Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [İleri](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
