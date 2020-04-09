---
title: Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernize edin | Kapsayıcı tabanlı uygulamalar için Azure bilgi işlem platformlarını seçme
ms.date: 02/18/2020
ms.openlocfilehash: 4bc72fb5a5be30d47cffe73d53a82b3237a959a6
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987822"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme

Önceki bölümleri okuduktan sonra fark ettiğiniz gibi Azure, birden çok seçenek sunan açık bir buluttür. İhtiyaçlarınıza en uygun olanı kullanabilirsiniz, ancak konteyner uygulamalarınız için hangi ürünü/teknolojiyi kullanmanız gerektiği yle ilgili soruları da ortaya çıkar.

Varsayılan *bir* öneri olarak, bu kılavuzda önerilen temel ölçütler şunlardır:

- **Tek monolitik uygulama:** Azure Uygulama Hizmeti'ni seçin
- **N-Tier uygulaması:** Tek veya birkaç arka uç hizmetiniz varsa Azure Kubernetes Hizmeti (AKS) veya Uygulama Hizmeti gibi orkestratörleri seçin
- **Mikro hizmetler:** Kapsayıcılar için AKS veya Azure Web Uygulamaları'nı seçin
- **Olay işleyicileri & sunucusuz işlevler:** Azure İşlevlerini Seçin
- **Büyük Ölçekli Toplu İş:** Azure Toplu İş'i Seçin

Ancak, ürünün seçimi özel uygulamanızın ihtiyaçlarına ve özelliklerine bağlı olacağından, bu öneri bir tutam tuzla birlikte alınmalıdır. Başlangıçta benzer türlerde görünseler bile tüm uygulamalar aynı değildir.

Uygulamanın gereksinimlerinin daha derin bir analizinden sonra, seçilen ürün farklı olabilir. Ancak, bir başlangıç noktası olarak, belirli bir önceliğe göre değerlendirmeye ve test etmeye başlabildiğiniz ilk kılavuza sahip olmak iyidir.

Aşağıdaki tabloda, farklı türde uygulamaların ve bunların olası ve önerilen Azure barındırma senaryolarının dökümünü görebilirsiniz.

| Uygulama Mimarisi | Sanal Makineler - Azure Sanal Makineler | ACI - Azure Kapsayıcı Örnekleri | Azure Uygulama Hizmeti (w-w/o kapsayıcıları) | AKS - Azure Kubernetes Hizmetleri | Azure İşlevleri | Azure Batch |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Web uygulamaları (Monolitik)**         | ![VM'lerle mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![ACI ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Uygulama Hizmeti ile önerilir](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![AKS ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **N-Tier uygulamaları (Hizmetler)**        | ![VM'lerle mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![ACI ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Uygulama Hizmeti ile önerilir](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![AKS ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Azure Fuctions ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **Bulut-Yerli (Microservices)**  | | ![ACI ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | ![AKS ile önerilir](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Linux&nbsp;konteynerleri)| ![Azure İşlevleriyle Önerilir](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Olay&#x2011;tahrik) | |
| **Toplu İşlemler/İşler (Arka plan görevleri)** | ![VM'lerle mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![ACI ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Uygulama Hizmeti ile Mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![AKS ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Azure İşlevleriyle Önerilir](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Arka&nbsp;plan görevleri) | ![Azure Toplu İşile Önerilir](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Büyük&#x2011;ölçeği) |

**Efsane**

![Önerilen simge](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) Önerilen \
![Olası simge](media/choosing-azure-compute-options-for-container-based-applications/possible.png) Mümkün

> [!div class="step-by-step"]
> [Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Sonraki](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
