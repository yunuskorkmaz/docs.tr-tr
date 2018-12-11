---
title: Kapsayıcı tabanlı uygulamalar için Azure işlem platformlarını seçme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | Kapsayıcı tabanlı uygulamalar için Azure işlem platformlarını seçme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/04/2018
ms.openlocfilehash: 20d8899d404ec72e3b1b9c2471524133a6428c44
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125502"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a><span data-ttu-id="6f70f-103">Kapsayıcı tabanlı uygulamalar için Azure işlem platformlarını seçme</span><span class="sxs-lookup"><span data-stu-id="6f70f-103">Choosing Azure compute platforms for container-based applications</span></span>

<span data-ttu-id="6f70f-104">Önceki bölümlerde okuduktan sonra fark etmiş gibi birden çok seçenek sunan bir açık bulut azure'dur.</span><span class="sxs-lookup"><span data-stu-id="6f70f-104">As you have noticed after reading the previous sections, Azure is an open cloud that offers multiple choices.</span></span> <span data-ttu-id="6f70f-105">İhtiyaçlarınıza en uygun kullanabilirsiniz, ancak bunu ayrıca kapsayıcılı uygulamalarınız için kullanması gereken hangi ürün/teknoloji hakkında sorular ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6f70f-105">You can use the best fit for your needs, however, it also surfaces questions about what product/technology you should use for your containerized applications.</span></span>

<span data-ttu-id="6f70f-106">Olarak bir *varsayılan olarak* öneri, bu kılavuzda önerilen ana ölçüt aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6f70f-106">As a *by-default* recommendation, the following is the main criteria recommended in this guidance:</span></span>

  - <span data-ttu-id="6f70f-107">**Tek tek parçalı uygulama:** Azure uygulama hizmeti seçin</span><span class="sxs-lookup"><span data-stu-id="6f70f-107">**Single monolithic app:** Choose Azure App Service</span></span>
  - <span data-ttu-id="6f70f-108">**N katmanlı uygulama:** Tek bir veya birkaç arka uç Hizmetleri varsa, Azure Kubernetes Service (AKS), Service Fabric (BT) veya App Service gibi düzenleyiciler arasından seçim yapın</span><span class="sxs-lookup"><span data-stu-id="6f70f-108">**N-Tier app:** Choose orchestrators such as Azure Kubernetes Service (AKS), Service Fabric (SF) or App Service if you have a single or few back-end services</span></span>
  - <span data-ttu-id="6f70f-109">**Linux mikro hizmetler:** AKS/Kubernetes seçin</span><span class="sxs-lookup"><span data-stu-id="6f70f-109">**Linux microservices:** Choose AKS/Kubernetes</span></span>
  - <span data-ttu-id="6f70f-110">**Windows mikro hizmetler:** Service Fabric seçin</span><span class="sxs-lookup"><span data-stu-id="6f70f-110">**Windows microservices:** Choose Service Fabric</span></span>
  - <span data-ttu-id="6f70f-111">**& Olay işleyicileri sunucusuz İşlevler:** Azure işlevleri'ni seçin</span><span class="sxs-lookup"><span data-stu-id="6f70f-111">**Serverless functions & event handlers:** Choose Azure Functions</span></span>
  - <span data-ttu-id="6f70f-112">**Büyük ölçekli Batch:** Azure Batch seçin</span><span class="sxs-lookup"><span data-stu-id="6f70f-112">**Large-scale Batch:** Choose Azure Batch</span></span>

<span data-ttu-id="6f70f-113">Ancak, ürünün seçimi belirli uygulamanızın gereksinimlerini ve özelliklerini bağlı olarak bu öneriyi güvenlik değeri,'bir tabletinizde ile dikkat edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="6f70f-113">However, this recommendation should be taken with a pinch of salt, as the product’s selection will depend on your specific application’s needs and characteristics.</span></span> <span data-ttu-id="6f70f-114">Hatta Başlangıçta bunlar benzer türler görünebilir, tüm uygulamalar aynı olur.</span><span class="sxs-lookup"><span data-stu-id="6f70f-114">Not all applications are the same even when initially they might look similar types.</span></span>

<span data-ttu-id="6f70f-115">Uygulama gereksinimleri hakkında daha ayrıntılı çözümleme sonrasında, seçili ürün farklı olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f70f-115">After a deeper analysis of the application’s needs, the product selected could be different.</span></span> <span data-ttu-id="6f70f-116">Ancak, bir başlangıç noktası olarak değerlendiriliyor başlayabileceğiniz gelen başlangıç düzeyi bir kılavuz olmanız faydalı olacaktır ve belirli önceliğine bağlı olarak test etme.</span><span class="sxs-lookup"><span data-stu-id="6f70f-116">But, as a starting point, it is good to have initial guidance from where you can start evaluating and testing based on certain priority.</span></span>

<span data-ttu-id="6f70f-117">Sonraki şekilde, daha genel bir ayrıntılı karar tablosu sırasında çözümleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f70f-117">In the next figure, you can analyze a more global while detailed decision table.</span></span>

![](./media/image8.5.png)

<span data-ttu-id="6f70f-118">Bildirim nasıl temel işletim sistemi (Windows vs. Linux) bir karar faktör daha olgun Linux kapsayıcıları üzerinde ve Windows kapsayıcılarına diğer bazı düzenleyiciler da olabilir.</span><span class="sxs-lookup"><span data-stu-id="6f70f-118">Notice how the underlying OS (Windows vs. Linux) can also be a decision factor as some orchestrators are more mature on Linux containers and other on Windows containers.</span></span> <span data-ttu-id="6f70f-119">Örneğin, Linux kapsayıcıları Service Fabric üzerinde daha az olgun ancak (AKS azure'da) Kubernetes içinde çok olgun.</span><span class="sxs-lookup"><span data-stu-id="6f70f-119">For instance, Linux containers are very mature in Kubernetes (AKS in Azure) but less mature on Service Fabric.</span></span> <span data-ttu-id="6f70f-120">Diğer taraftan, Windows kapsayıcıları Service Fabric (Mayıs 2017'de yayımlanan) daha olgun ve daha az AKS olgun.</span><span class="sxs-lookup"><span data-stu-id="6f70f-120">On the other hand, Windows Containers are more mature in Service Fabric (released in May 2017) and less mature in AKS.</span></span>

<span data-ttu-id="6f70f-121">Ancak, bu işletim sistemi olgunluk farklılıkları gelecekte kaybolacaktır ve birden çok platform karşılaştırılabilir işletim sistemi olgunluk olduğundan ve kararı uygulamanız gerekebilir veya üzerinde her platformun ekosistemi dayalı belirli özelliklere bağlı olarak tercihleri üzerinde daha fazla düzenleme nedenleri.</span><span class="sxs-lookup"><span data-stu-id="6f70f-121">However, those differences in OS maturity will fade in the future and multiple platforms will have comparable OS maturity and the decision will lay more on preferences based on specific features your application might need or based on each platform's ecosystem reasons.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6f70f-122">[Önceki](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[İleri](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="6f70f-122">[Previous](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>