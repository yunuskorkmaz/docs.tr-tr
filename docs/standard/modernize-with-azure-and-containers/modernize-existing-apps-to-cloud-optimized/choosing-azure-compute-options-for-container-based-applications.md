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
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="7973f-103">Kapsayıcı tabanlı uygulamalar için Azure işlem platformları seçme</span><span class="sxs-lookup"><span data-stu-id="7973f-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="7973f-104">Önceki bölümlerde okuduktan sonra fark etmiş, Azure birden çok seçenek sunar açık bir bulut aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7973f-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="7973f-105">Gereksinimleriniz için en uygun şekilde kullanabilirsiniz, ancak, bu aynı zamanda kapsayıcılı uygulamalarınız için kullanması gereken hangi ürün ve teknoloji hakkında sorular ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="7973f-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="7973f-106">Farklı bir *varsayılan olarak* öneri, bu kılavuzunda önerilen ana ölçütleri aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7973f-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

  - <span data-ttu-id="7973f-107">**Tek tek yapılı uygulama:** Azure uygulama hizmeti seçin</span><span class="sxs-lookup"><span data-stu-id="7973f-107">**Single monolithic app:** Choose Azure App Service</span></span>
  - <span data-ttu-id="7973f-108">**N katmanlı uygulama:** tek bir veya birkaç arka uç hizmetlerini varsa Azure Kubernetes hizmet (AKS), Service Fabric (BT) veya uygulama hizmeti gibi orchestrators seçin</span><span class="sxs-lookup"><span data-stu-id="7973f-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS), Service Fabric (SF) or App Service if you have a single or few back-end services</span></span>
  - <span data-ttu-id="7973f-109">**Linux mikro:** AKS/Kubernetes seçin</span><span class="sxs-lookup"><span data-stu-id="7973f-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
  - <span data-ttu-id="7973f-110">**Windows mikro:** Service Fabric seçin</span><span class="sxs-lookup"><span data-stu-id="7973f-110">**Windows microservices:** Choose Service Fabric</span></span>
  - <span data-ttu-id="7973f-111">**Sunucusuz işlevleri & olay işleyicileri:** Azure işlevleri seçin</span><span class="sxs-lookup"><span data-stu-id="7973f-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
  - <span data-ttu-id="7973f-112">**Büyük ölçekli Batch:** Azure toplu işlem seçin</span><span class="sxs-lookup"><span data-stu-id="7973f-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="7973f-113">Ancak, ürünün seçimi belirli uygulamanızın gereksinimlerine ve özelliklere bağlıdır gibi Bu öneri bir salt, tutarak ile yapılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7973f-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="7973f-114">Hatta Başlangıçta bunlar benzer türler görünebilir, tüm uygulamalar aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="7973f-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="7973f-115">Uygulamanın gereksinimlerini daha derin çözümleme sonrasında, seçilen ürün farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="7973f-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="7973f-116">Ancak, bir başlangıç noktası olarak değerlendiriliyor başlayabileceğiniz gelen ilk kılavuz yararlı olan ve belirli önceliği temelinde test etme.</span><span class="sxs-lookup"><span data-stu-id="7973f-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="7973f-117">Sonraki şekilde, ayrıntılı karar tablosu çalışırken daha genel analiz edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7973f-117">In the next figure, you can analyze a more global while detailed decision table.</span></span>

![](./media/image8.5.png)

<span data-ttu-id="7973f-118">Bildirim nasıl temel işletim sistemi (Windows vs. Linux) karar faktörü daha Linux kapsayıcılarında olgun ve Windows kapsayıcılarında diğer bazı orchestrators de olabilir.</span><span class="sxs-lookup"><span data-stu-id="7973f-118">Notice how the underlying OS (Windows vs. Linux) can also be a decision factor as some orchestrators are more mature on Linux containers and other on Windows containers.</span></span> <span data-ttu-id="7973f-119">Örneğin, Linux Service Fabric üzerinde daha az olgun ancak Kubernetes (azure'da AKS) içinde çok olgun kapsayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="7973f-119">For instance, Linux containers are very mature in Kubernetes (AKS in Azure) but less mature on Service Fabric.</span></span> <span data-ttu-id="7973f-120">Diğer taraftan, Windows Service Fabric (Mayıs 2017 serbest) daha olgun ve AKS daha az olgun kapsayıcılardır.</span><span class="sxs-lookup"><span data-stu-id="7973f-120">On the other hand, Windows Containers are more mature in Service Fabric (released in May 2017) and less mature in AKS.</span></span>

<span data-ttu-id="7973f-121">Ancak, bu işletim sistemi olgunluk farklılıkları gelecekte kaybolacaktır ve birden çok platform karşılaştırılabilir OS olgunluk sahip olur ve kararı, tercihlerine uygulamanız gerekebilir veya üzerinde her platformun ekosistemi dayalı belirli özelliklere bağlı olarak daha fazla düzenleme nedenleri.</span><span class="sxs-lookup"><span data-stu-id="7973f-121">However, those differences in OS maturity will fade in the future and multiple platforms will have comparable OS maturity and the decision will lay more on preferences based on specific features your application might need or based on each platform's ecosystem reasons.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7973f-122">[Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[sonraki](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="7973f-122">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
