---
title: Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
ms.date: 05/04/2018
ms.openlocfilehash: 079c9c5ca02b6dc75214d63cb59afdead03d3190
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/08/2019
ms.locfileid: "73737008"
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

Şekil 1 ' de, farklı türde uygulamalar ve bunlara yönelik ideal Azure barındırma senaryolarına ait bir döküm görebilirsiniz.

![Azure barındırma senaryolarının farklı uygulamalar için en iyisi tablosu.](./media/choosing-azure-compute-options-for-container-based-applications/azure-hosting-scenarios-for-apps.png)

> [!div class="step-by-step"]
> [Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [İleri](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
