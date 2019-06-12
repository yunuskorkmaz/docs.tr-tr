---
title: Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Kapsayıcı tabanlı uygulamalar için Azure işlem platformlarını seçme
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833850"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="eca66-103">Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme</span><span class="sxs-lookup"><span data-stu-id="eca66-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="eca66-104">Önceki bölümlerde okuduktan sonra fark etmiş gibi birden çok seçenek sunan bir açık bulut azure'dur.</span><span class="sxs-lookup"><span data-stu-id="eca66-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="eca66-105">İhtiyaçlarınıza en uygun kullanabilirsiniz, ancak bunu ayrıca kapsayıcılı uygulamalarınız için kullanması gereken hangi ürün/teknoloji hakkında sorular ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="eca66-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="eca66-106">Olarak bir *varsayılan olarak* öneri, bu kılavuzda önerilen ana ölçüt aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="eca66-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

- <span data-ttu-id="eca66-107">**Tek tek parçalı uygulama:** Azure uygulama hizmeti seçin</span><span class="sxs-lookup"><span data-stu-id="eca66-107">**Single monolithic app:** Choose Azure App Service</span></span>
- <span data-ttu-id="eca66-108">**N katmanlı uygulama:** Tek bir veya birkaç arka uç Hizmetleri varsa, Azure Kubernetes Service (AKS) veya App Service gibi düzenleyiciler arasından seçim yapın</span><span class="sxs-lookup"><span data-stu-id="eca66-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS)or App Service if you have a single or few back-end services</span></span>
- <span data-ttu-id="eca66-109">**Mikro hizmetler:** AKS veya Azure Web uygulaması için kapsayıcı seçin</span><span class="sxs-lookup"><span data-stu-id="eca66-109">**Microservices:** Choose AKS or Azure Web Apps for Containers</span></span>
- <span data-ttu-id="eca66-110">**& Olay işleyicileri sunucusuz İşlevler:** Azure işlevleri'ni seçin</span><span class="sxs-lookup"><span data-stu-id="eca66-110">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
- <span data-ttu-id="eca66-111">**Büyük ölçekli Batch:** Azure Batch seçin</span><span class="sxs-lookup"><span data-stu-id="eca66-111">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="eca66-112">Ancak, ürünün seçimi belirli uygulamanızın gereksinimlerini ve özelliklerini bağlı olarak bu öneriyi güvenlik değeri,'bir tabletinizde ile dikkat edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="eca66-112">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="eca66-113">Hatta Başlangıçta bunlar benzer türler görünebilir, tüm uygulamalar aynı olur.</span><span class="sxs-lookup"><span data-stu-id="eca66-113">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="eca66-114">Uygulama gereksinimleri hakkında daha ayrıntılı çözümleme sonrasında, seçili ürün farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="eca66-114">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="eca66-115">Ancak, bir başlangıç noktası olarak değerlendiriliyor başlayabileceğiniz gelen başlangıç düzeyi bir kılavuz olmanız faydalı olacaktır ve belirli önceliğine bağlı olarak test etme.</span><span class="sxs-lookup"><span data-stu-id="eca66-115">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="eca66-116">Sonraki şekilde, farklı türde uygulamaları ve bunların ideal Azure barındırma senaryolarında dökümünü görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eca66-116">In the next figure, you can see a breakdown of different kinds of apps and their ideal Azure hosting scenarios.</span></span>

![](./media/image8.5.png)

> [!div class="step-by-step"]
> <span data-ttu-id="eca66-117">[Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [İleri](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="eca66-117">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
