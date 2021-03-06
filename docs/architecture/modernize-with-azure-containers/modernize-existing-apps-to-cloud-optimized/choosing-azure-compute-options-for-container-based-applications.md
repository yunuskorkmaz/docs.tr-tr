---
title: Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
ms.date: 02/18/2020
ms.openlocfilehash: 9246b8dfb4e1d68fbd965d25e2e9d3272563798c
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257999"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme

Önceki bölümleri okuduktan sonra fark etmişsinizdir, Azure birden çok seçenek sunan açık bir bulutdır. Gereksinimlerinize en uygun olanı kullanabilirsiniz, ancak Kapsayıcılı uygulamalarınız için hangi ürün/teknolojinin kullanılması gerektiğine dair soruları de yüzeyler.

*Varsayılan* olarak, bu kılavuzda önerilen ana ölçütler aşağıda verilmiştir:

- **Tek monoparçalı uygulama:** Azure App Service seçin
- **N katmanlı uygulama:** Azure Kubernetes hizmeti (AKS) veya bir veya birkaç adet arka uç hizmetiniz varsa App Service düzenleyiciler seçin
- **Mikro hizmetler:** Kapsayıcılar için AKS veya Azure Web Apps seçin
- **Sunucusuz işlevler olay işleyicilerini &:** Azure Işlevleri 'ni seçin
- **Büyük ölçekli toplu işlem:** Azure Batch seçin

Ancak, ürünün seçimi belirli uygulamanızın ihtiyaçlarına ve özelliklerine bağlı olacağı için bu önerinin pinç bir güvenlik ile alınması gerekir. Başlangıçta benzer türleri görünseler bile, tüm uygulamalar aynı değildir.

Uygulamanın ihtiyaçlarına daha derin bir çözümledikten sonra, seçilen ürün farklı olabilir. Ancak, başlangıç noktası olarak, belirli önceliğe göre değerlendirme ve test etmeye başlayabileceğiniz ilk kılavuzluk olması iyi bir yoldur.

Aşağıdaki tabloda, farklı türde uygulamalar ve bunların olası ve önerilen Azure barındırma senaryolarına ait bir dökümünü görebilirsiniz.

| Uygulama mimarisi | VM 'Ler-Azure sanal makineleri | ACI-Azure Container Instances | Azure App Service (w-w/o kapsayıcıları) | AKS-Azure Kubernetes Hizmetleri | Azure İşlevleri | Azure Batch |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Web uygulamaları (tek parçalı)**         | ![VM 'lerle mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![ACI ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![App Service önerilir](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![AKS ile mümkün olan](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **N katmanlı uygulamalar (Hizmetler)**        | ![VM 'lerle mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![ACI ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![App Service önerilir](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![AKS ile mümkün olan](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Azure 'daki olanaklar sayesinde](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **Bulutta yerel (mikro hizmetler)**  | | ![ACI ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![ACI ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) <br/> ( &nbsp; Kapsayıcılar ile) | ![AKS ile önerilen](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Linux &nbsp; kapsayıcıları)| ![Azure Işlevleri ile önerilir](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Olay&#x2011;temelli) | |
| **Toplu iş/Işler (arka plan görevleri)** | ![VM 'lerle mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![ACI ile mümkün](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![App Service ile mümkün olan](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![AKS ile mümkün olan](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Azure Işlevleri ile önerilir](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Arka plan &nbsp; görevleri) | ![Azure Batch önerilir](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Büyük&#x2011;ölçeği) |

**Gösterge**

![Önerilen simge](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) Önerilen
![Olası simge](media/choosing-azure-compute-options-for-container-based-applications/possible.png) Üç

> [!div class="step-by-step"]
> [Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md) 
>  [Sonraki](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
