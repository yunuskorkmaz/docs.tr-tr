---
title: Kapsayıcı uygulama hizmetlerini izleme
description: Konteyner mimarilerini izlemenin bazı önemli yönlerini öğrenin
ms.date: 02/15/2019
ms.openlocfilehash: e14553d510751d8a75020a1b6beb9fd7bc29596e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295621"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="6ca03-103">Kapsayıcı uygulama hizmetlerini izleme</span><span class="sxs-lookup"><span data-stu-id="6ca03-103">Monitor containerized application services</span></span>

<span data-ttu-id="6ca03-104">Tüm uygulamanın davranışını izlemek ve analiz etmek için birden çok kapsayıcıya ve mikro hizmetlere bölünmüş uygulamalar için çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="6ca03-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="6ca03-105">Azure İzleyici</span><span class="sxs-lookup"><span data-stu-id="6ca03-105">Azure Monitor</span></span>

<span data-ttu-id="6ca03-106">[Azure Monitor,](https://azure.microsoft.com/services/monitor/) canlı uygulamanızı izleyen genişletilebilir bir analiz hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="6ca03-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="6ca03-107">Performans sorunlarını algılamanıza ve tanılamanıza ve kullanıcıların uygulamanızla gerçekte ne yaptığını anlamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="6ca03-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="6ca03-108">Hizmetlerinizin veya uygulamalarınızın performansını ve kullanılabilirliğini sürekli olarak geliştirmenize yardımcı olmak amacıyla geliştiriciler için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6ca03-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="6ca03-109">Azure Monitor, .NET, Java, Node.js ve şirket içinde veya bulutta barındırılan diğer birçok platform gibi çok çeşitli platformlarda hem web/hizmetler hem de bağımsız uygulamalarla çalışır.</span><span class="sxs-lookup"><span data-stu-id="6ca03-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="6ca03-110">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="6ca03-110">Additional resources</span></span>

- <span data-ttu-id="6ca03-111">**Azure Monitörüne Genel Bakış** </span><span class="sxs-lookup"><span data-stu-id="6ca03-111">**Overview of Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="6ca03-112">**Application Insights nedir?**</span><span class="sxs-lookup"><span data-stu-id="6ca03-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="6ca03-113">**Azure Monitör Ölçümleri nedir?**</span><span class="sxs-lookup"><span data-stu-id="6ca03-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="6ca03-114">**Azure Monitör'de Konteyner İzleme çözümü** </span><span class="sxs-lookup"><span data-stu-id="6ca03-114">**Container Monitoring solution in Azure Monitor** </span></span>\
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="6ca03-115">Güvenlik ve yedekleme hizmetleri</span><span class="sxs-lookup"><span data-stu-id="6ca03-115">Security and backup services</span></span>

<span data-ttu-id="6ca03-116">Uygulamalarınızın ve altyapınızın iş gereksinimlerini desteklemek için en üst düzey durumda olduğundan ve mikro hizmetler alanında durumun daha karmaşık hale gelmesiiçin, işlemeniz gereken birçok ayrıntıiçeren birçok destek işi vardır, bu nedenle harekete geçmeniz gerektiğinde hem üst düzey hem de ayrıntılı görünümlere sahip olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ca03-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="6ca03-117">Azure, hem bulutunuzun hem de şirket içi kaynaklarınızın dört kritik yönünü yönetmek ve birleşik bir görünüm sağlamak için araçlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6ca03-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="6ca03-118">**Güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="6ca03-118">**Security**.</span></span> <span data-ttu-id="6ca03-119">[Azure Güvenlik Merkezi](https://azure.microsoft.com/services/security-center/)ile.</span><span class="sxs-lookup"><span data-stu-id="6ca03-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="6ca03-120">Sanal makinelerinizin, uygulamalarınızın ve iş yüklerinizin güvenliği üzerinde tam görünürlük ve denetim edinin.</span><span class="sxs-lookup"><span data-stu-id="6ca03-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="6ca03-121">Güvenlik politikalarınızın yönetimini merkezileştirin ve varolan süreç ve araçları entegre edin.</span><span class="sxs-lookup"><span data-stu-id="6ca03-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="6ca03-122">Gelişmiş analitikle gerçek tehditleri algılayın.</span><span class="sxs-lookup"><span data-stu-id="6ca03-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="6ca03-123">**Yedek**.</span><span class="sxs-lookup"><span data-stu-id="6ca03-123">**Backup**.</span></span> <span data-ttu-id="6ca03-124">[Azure Yedekleme](https://azure.microsoft.com/services/backup/)ile .</span><span class="sxs-lookup"><span data-stu-id="6ca03-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="6ca03-125">Maliyetli iş aksaklıklarından kaçının, uyumluluk hedeflerini karşın ve verilerinizi fidye yazılımlarına ve insan hatalarına karşı koruyun.</span><span class="sxs-lookup"><span data-stu-id="6ca03-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="6ca03-126">Yedekleme verilerinizi aktarım sırasında ve istirahatte şifrelenmiş tutun.</span><span class="sxs-lookup"><span data-stu-id="6ca03-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="6ca03-127">Yetkisiz kullanımı önlemek için çok faktörlü kimlik doğrulamayı temel alan erişim sağlayın.</span><span class="sxs-lookup"><span data-stu-id="6ca03-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="6ca03-128">**Şirket içi kaynaklar.**</span><span class="sxs-lookup"><span data-stu-id="6ca03-128">**On-premises resources**.</span></span> <span data-ttu-id="6ca03-129">[Gerçekten tutarlı bir hibrid bulut](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/)ile .</span><span class="sxs-lookup"><span data-stu-id="6ca03-129">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6ca03-130">[Önceki](manage-production-docker-environments.md)
>[Sonraki](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="6ca03-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
