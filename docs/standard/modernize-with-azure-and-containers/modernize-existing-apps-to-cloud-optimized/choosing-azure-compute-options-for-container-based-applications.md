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
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="770eb-103">Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme</span><span class="sxs-lookup"><span data-stu-id="770eb-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="770eb-104">Önceki bölümlerde okuduktan sonra fark etmiş gibi birden çok seçenek sunan bir açık bulut azure'dur.</span><span class="sxs-lookup"><span data-stu-id="770eb-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="770eb-105">İhtiyaçlarınıza en uygun kullanabilirsiniz, ancak bunu ayrıca kapsayıcılı uygulamalarınız için kullanması gereken hangi ürün/teknoloji hakkında sorular ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="770eb-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="770eb-106">Olarak bir *varsayılan olarak* öneri, bu kılavuzda önerilen ana ölçüt aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="770eb-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="770eb-107">**Tek tek parçalı uygulama:** Azure uygulama hizmeti seçin</span><span class="sxs-lookup"><span data-stu-id="770eb-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="770eb-108">**N katmanlı uygulama:** Tek bir veya birkaç arka uç Hizmetleri varsa, Azure Kubernetes Service (AKS) veya App Service gibi düzenleyiciler arasından seçim yapın</span><span class="sxs-lookup"><span data-stu-id="770eb-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="770eb-109">**Linux mikro hizmetler:** AKS/Kubernetes seçin</span><span class="sxs-lookup"><span data-stu-id="770eb-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
- <span data-ttu-id="770eb-110">**Windows mikro hizmetler:** Azure Web uygulaması için kapsayıcı Seç</span><span class="sxs-lookup"><span data-stu-id="770eb-110">**Windows microservices:** Choose Azure Web Apps for Containers</span></span>
- <span data-ttu-id="770eb-111">**& Olay işleyicileri sunucusuz İşlevler:** Azure işlevleri'ni seçin</span><span class="sxs-lookup"><span data-stu-id="770eb-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="770eb-112">**Büyük ölçekli Batch:** Azure Batch seçin</span><span class="sxs-lookup"><span data-stu-id="770eb-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="770eb-113">Ancak, ürünün seçimi belirli uygulamanızın gereksinimlerini ve özelliklerini bağlı olarak bu öneriyi güvenlik değeri,'bir tabletinizde ile dikkat edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="770eb-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="770eb-114">Hatta Başlangıçta bunlar benzer türler görünebilir, tüm uygulamalar aynı olur.</span><span class="sxs-lookup"><span data-stu-id="770eb-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="770eb-115">Uygulama gereksinimleri hakkında daha ayrıntılı çözümleme sonrasında, seçili ürün farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="770eb-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="770eb-116">Ancak, bir başlangıç noktası olarak değerlendiriliyor başlayabileceğiniz gelen başlangıç düzeyi bir kılavuz olmanız faydalı olacaktır ve belirli önceliğine bağlı olarak test etme.</span><span class="sxs-lookup"><span data-stu-id="770eb-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="770eb-117">Sonraki şekilde, farklı türde uygulamaları ve bunların ideal Azure barındırma senaryolarında dökümünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="770eb-117">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="770eb-118">[Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [İleri](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="770eb-118">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
