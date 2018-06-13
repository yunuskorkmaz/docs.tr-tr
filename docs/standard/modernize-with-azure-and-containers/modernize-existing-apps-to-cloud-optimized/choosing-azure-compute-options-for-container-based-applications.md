---
title: Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
description: Azure Bulut ve Windows kapsayıcılarla varolan .NET uygulamaları modernize | Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: ebf022a52aaaf95ae335976f5e097921b0ac8006
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958244"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme

Önceki bölümlerde okuduktan sonra fark etmiş, Azure birden çok seçenek sunar açık bir bulut aynıdır. Gereksinimleriniz için en uygun şekilde kullanabilirsiniz, ancak, bu aynı zamanda kapsayıcılı uygulamalarınız için kullanması gereken hangi ürün ve teknoloji hakkında sorular ortaya çıkarır.

Farklı bir *varsayılan olarak* öneri, bu kılavuzunda önerilen ana ölçütleri aşağıdaki gibidir:

  - **Tek tek yapılı uygulama:** Azure uygulama hizmeti seçin
  - **N katmanlı uygulama:** tek bir veya birkaç arka uç hizmetlerini varsa Azure Kubernetes hizmet (AKS), Service Fabric (BT) veya uygulama hizmeti gibi orchestrators seçin
  - **Linux mikro:** AKS/Kubernetes seçin
  - **Windows mikro:** Service Fabric seçin
  - **Sunucusuz işlevleri & olay işleyicileri:** Azure işlevleri seçin
  - **Büyük ölçekli Batch:** Azure toplu işlem seçin

Ancak, ürünün seçimi belirli uygulamanızın gereksinimlerine ve özelliklere bağlıdır gibi Bu öneri bir salt, tutarak ile yapılması gerekir. Hatta Başlangıçta bunlar benzer türler görünebilir, tüm uygulamalar aynı değildir.

Uygulamanın gereksinimlerini daha derin çözümleme sonrasında, seçilen ürün farklı olabilir. Ancak, bir başlangıç noktası olarak değerlendiriliyor başlayabileceğiniz gelen ilk kılavuz yararlı olan ve belirli önceliği temelinde test etme.

Sonraki şekilde, ayrıntılı karar tablosu çalışırken daha genel analiz edebilirsiniz.

![](./media/image8.5.png)

Bildirim nasıl temel işletim sistemi (Windows vs. Linux) karar faktörü daha Linux kapsayıcılarında olgun ve Windows kapsayıcılarında diğer bazı orchestrators de olabilir. Örneğin, Linux Service Fabric üzerinde daha az olgun ancak Kubernetes (azure'da AKS) içinde çok olgun kapsayıcılardır. Diğer taraftan, Windows Service Fabric (Mayıs 2017 serbest) daha olgun ve AKS daha az olgun kapsayıcılardır.

Ancak, bu işletim sistemi olgunluk farklılıkları gelecekte kaybolacaktır ve birden çok platform karşılaştırılabilir OS olgunluk sahip olur ve kararı, tercihlerine uygulamanız gerekebilir veya üzerinde her platformun ekosistemi dayalı belirli özelliklere bağlı olarak daha fazla düzenleme nedenleri.


>[!div class="step-by-step"]
[Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[sonraki](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
