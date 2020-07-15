---
title: Kapsayıcı uygulama hizmetlerini izleme
description: İzleme kapsayıcısı mimarilerinin bazı önemli yönlerini öğrenin
ms.date: 02/15/2019
ms.openlocfilehash: e41df53ad94784436442c3cf7defed3fab510455
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374448"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="33068-103">Kapsayıcı uygulama hizmetlerini izleme</span><span class="sxs-lookup"><span data-stu-id="33068-103">Monitor containerized application services</span></span>

<span data-ttu-id="33068-104">Birden çok kapsayıcıya ve mikro hizmetlere bölünen uygulamalar, tüm uygulamanın davranışını izlemek ve analiz etmek için bir yola sahip olmak açısından önemlidir.</span><span class="sxs-lookup"><span data-stu-id="33068-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="33068-105">Azure İzleyici</span><span class="sxs-lookup"><span data-stu-id="33068-105">Azure Monitor</span></span>

<span data-ttu-id="33068-106">[Azure izleyici](https://azure.microsoft.com/services/monitor/) , canlı uygulamanızı izleyen genişletilebilir bir analiz hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="33068-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="33068-107">Performans sorunlarını saptamanıza ve tanılamanıza ve hangi kullanıcıların uygulamanızla gerçekten ne yaptığını anlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="33068-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="33068-108">Hizmetlerinizin veya uygulamalarınızın performansını ve kullanılabilirliğini sürekli olarak iyileştirmenize yardımcı olmak amacıyla geliştiriciler için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="33068-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="33068-109">Azure Izleyici, şirket içinde veya bulutta barındırılan .NET, Java, Node.js ve diğer birçok platform gibi çok çeşitli platformlarda hem Web/Hizmetler hem de tek başına uygulamalarla birlikte çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33068-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="33068-110">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="33068-110">Additional resources</span></span>

- <span data-ttu-id="33068-111">**Azure Izleyici 'ye Genel Bakış** </span><span class="sxs-lookup"><span data-stu-id="33068-111">**Overview of Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="33068-112">**Application Insights nedir?**</span><span class="sxs-lookup"><span data-stu-id="33068-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="33068-113">**Azure Izleyici ölçümleri nedir?**</span><span class="sxs-lookup"><span data-stu-id="33068-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="33068-114">**Azure Izleyici 'de kapsayıcı Izleme çözümü** </span><span class="sxs-lookup"><span data-stu-id="33068-114">**Container Monitoring solution in Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="33068-115">Güvenlik ve yedekleme hizmetleri</span><span class="sxs-lookup"><span data-stu-id="33068-115">Security and backup services</span></span>

<span data-ttu-id="33068-116">Uygulamalarınızın ve altyapınızın iş ihtiyaçlarını desteklemeye yönelik en önemli koşullarda ve bu durumun mikro hizmetler alanında daha karmaşık hale gelmesi için işlem yapmanız gereken çok fazla ayrıntı desteği vardır. bu nedenle, işlem yapmanız gerektiğinde hem yüksek düzeyde hem de ayrıntılı görünümlere sahip olmak için bir yönteme ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="33068-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="33068-117">Azure, hem bulut hem de şirket içi kaynaklarınızın dört kritik yönünü yönetmek ve sunmak için araçlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="33068-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="33068-118">**Güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="33068-118">**Security**.</span></span> <span data-ttu-id="33068-119">[Azure Güvenlik Merkezi](https://azure.microsoft.com/services/security-center/)ile.</span><span class="sxs-lookup"><span data-stu-id="33068-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="33068-120">Sanal makinelerinizin, uygulamalarınızın ve iş yüklerinizin güvenliği üzerinde tam görünürlük ve denetim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="33068-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="33068-121">Güvenlik ilkelerinizin yönetimini merkezileştirin ve var olan işlem ve araçları tümleştirin.</span><span class="sxs-lookup"><span data-stu-id="33068-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="33068-122">Gelişmiş analiz ile gerçek tehditleri algılayın.</span><span class="sxs-lookup"><span data-stu-id="33068-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="33068-123">**Yedekleme**.</span><span class="sxs-lookup"><span data-stu-id="33068-123">**Backup**.</span></span> <span data-ttu-id="33068-124">[Azure Backup](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="33068-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="33068-125">Maliyetli iş kesintilerini önleyin, uyumluluk hedeflerini karşılayın ve verilerinizi fidye ve insan hatalarına karşı koruyun.</span><span class="sxs-lookup"><span data-stu-id="33068-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="33068-126">Yedekleme verilerinizi, iletim sırasında ve bekleyen zamanda şifreli tutun.</span><span class="sxs-lookup"><span data-stu-id="33068-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="33068-127">Yetkisiz kullanımı engellemek için çok faktörlü kimlik doğrulamasına göre erişim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="33068-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="33068-128">**Şirket içi kaynaklar**.</span><span class="sxs-lookup"><span data-stu-id="33068-128">**On-premises resources**.</span></span> <span data-ttu-id="33068-129">[Karma bulut çözümleri](https://azure.microsoft.com/solutions/hybrid-cloud-app/)ile.</span><span class="sxs-lookup"><span data-stu-id="33068-129">With [hybrid cloud solutions](https://azure.microsoft.com/solutions/hybrid-cloud-app/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="33068-130">[Önceki](manage-production-docker-environments.md) 
> [Sonraki](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="33068-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
