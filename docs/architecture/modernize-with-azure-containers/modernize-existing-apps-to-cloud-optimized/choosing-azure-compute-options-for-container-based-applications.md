---
title: Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68677038"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme

Önceki bölümleri okuduktan sonra fark etmişsinizdir, Azure birden çok seçenek sunan açık bir bulutdır. Gereksinimlerinize en uygun olanı kullanabilirsiniz, ancak Kapsayıcılı uygulamalarınız için hangi ürün/teknolojinin kullanılması gerektiğine dair soruları de yüzeyler.

*Varsayılan* olarak, bu kılavuzda önerilen ana ölçütler aşağıda verilmiştir:

- **Tek monoparçalı uygulama:** Azure App Service seçin
- **N katmanlı uygulama:** Azure Kubernetes hizmeti (AKS) veya tek veya birkaç adet arka uç hizmetiniz varsa App Service düzenleyiciler seçin
- **Mikro hizmetler** Kapsayıcılar için AKS veya Azure Web Apps seçin
- **Sunucusuz işlevler olay işleyicilerini &:** Azure Işlevleri 'ni seçin
- **Büyük ölçekli toplu Işlem:** Azure Batch seçin

Ancak, ürünün seçimi belirli uygulamanızın ihtiyaçlarına ve özelliklerine bağlı olacağı için bu önerinin pinç bir güvenlik ile alınması gerekir. Başlangıçta benzer türleri görünseler bile, tüm uygulamalar aynı değildir.

Uygulamanın ihtiyaçlarına daha derin bir çözümledikten sonra, seçilen ürün farklı olabilir. Ancak, başlangıç noktası olarak, belirli önceliğe göre değerlendirme ve test etmeye başlayabileceğiniz ilk kılavuzluk olması iyi bir yoldur.

Bir sonraki şekilde, farklı türde uygulamalar ve bunlara yönelik ideal Azure barındırma senaryolarına ait bir döküm görebilirsiniz.

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)İleri
> [](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
