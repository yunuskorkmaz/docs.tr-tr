---
title: Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
description: Azure bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirin | Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
ms.date: 05/04/2018
ms.openlocfilehash: 54c5945326fb8a50a39c50552a413580926da2c7
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71331971"
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

Şekil 1 ' de, farklı türde uygulamalar ve bunlara yönelik ideal Azure barındırma senaryolarına ait bir döküm görebilirsiniz.

![Şekil 1](./media/image8.5.png)

> [!div class="step-by-step"]
> [Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [İleri](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
