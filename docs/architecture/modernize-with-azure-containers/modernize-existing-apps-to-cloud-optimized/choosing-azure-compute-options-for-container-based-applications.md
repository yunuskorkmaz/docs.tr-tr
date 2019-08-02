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
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="fc81d-103">Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme</span><span class="sxs-lookup"><span data-stu-id="fc81d-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="fc81d-104">Önceki bölümleri okuduktan sonra fark etmişsinizdir, Azure birden çok seçenek sunan açık bir bulutdır.</span><span class="sxs-lookup"><span data-stu-id="fc81d-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="fc81d-105">Gereksinimlerinize en uygun olanı kullanabilirsiniz, ancak Kapsayıcılı uygulamalarınız için hangi ürün/teknolojinin kullanılması gerektiğine dair soruları de yüzeyler.</span><span class="sxs-lookup"><span data-stu-id="fc81d-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="fc81d-106">*Varsayılan* olarak, bu kılavuzda önerilen ana ölçütler aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fc81d-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="fc81d-107">**Tek monoparçalı uygulama:** Azure App Service seçin</span><span class="sxs-lookup"><span data-stu-id="fc81d-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="fc81d-108">**N katmanlı uygulama:** Azure Kubernetes hizmeti (AKS) veya tek veya birkaç adet arka uç hizmetiniz varsa App Service düzenleyiciler seçin</span><span class="sxs-lookup"><span data-stu-id="fc81d-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="fc81d-109">**Mikro hizmetler** Kapsayıcılar için AKS veya Azure Web Apps seçin</span><span class="sxs-lookup"><span data-stu-id="fc81d-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="fc81d-110">**Sunucusuz işlevler olay işleyicilerini &:** Azure Işlevleri 'ni seçin</span><span class="sxs-lookup"><span data-stu-id="fc81d-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="fc81d-111">**Büyük ölçekli toplu Işlem:** Azure Batch seçin</span><span class="sxs-lookup"><span data-stu-id="fc81d-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="fc81d-112">Ancak, ürünün seçimi belirli uygulamanızın ihtiyaçlarına ve özelliklerine bağlı olacağı için bu önerinin pinç bir güvenlik ile alınması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc81d-112">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="fc81d-113">Başlangıçta benzer türleri görünseler bile, tüm uygulamalar aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="fc81d-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="fc81d-114">Uygulamanın ihtiyaçlarına daha derin bir çözümledikten sonra, seçilen ürün farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc81d-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="fc81d-115">Ancak, başlangıç noktası olarak, belirli önceliğe göre değerlendirme ve test etmeye başlayabileceğiniz ilk kılavuzluk olması iyi bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="fc81d-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="fc81d-116">Bir sonraki şekilde, farklı türde uygulamalar ve bunlara yönelik ideal Azure barındırma senaryolarına ait bir döküm görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc81d-116">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="fc81d-117">[Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)İleri
> [](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="fc81d-117">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
