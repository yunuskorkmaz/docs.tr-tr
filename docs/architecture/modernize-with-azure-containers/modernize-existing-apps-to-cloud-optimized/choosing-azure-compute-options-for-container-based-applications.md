---
title: Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
ms.date: 05/04/2018
ms.openlocfilehash: 2262d2cf4e69e19e8b78c07c239602dd5dccc3cd
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318672"
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

![Şekil 1](./media/image8.5.png)

> [!div class="step-by-step"]
> [Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [İleri](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
