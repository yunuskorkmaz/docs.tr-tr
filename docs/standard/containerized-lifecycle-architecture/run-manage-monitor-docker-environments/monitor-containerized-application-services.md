---
title: Kapsayıcı uygulama hizmetlerini izleme
description: Kapsayıcı mimarileri izleme bazı önemli noktalar öğrenin
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 4553a35c8db6cfc46187525ef2ffc65cb3ba07c9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59672054"
---
# <a name="monitor-containerized-application-services"></a><span data-ttu-id="c7b3a-103">Kapsayıcı uygulama hizmetlerini izleme</span><span class="sxs-lookup"><span data-stu-id="c7b3a-103">Monitor containerized application services</span></span>

<span data-ttu-id="c7b3a-104">Tüm uygulama davranışını çözümlemenize yarayan bir yol sağlamak bölme birden fazla kapsayıcılar ve mikro hizmet uygulamaları için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-104">It's critical for applications split into multiple containers and microservices to have a way to monitor and analyze the behavior of the whole application.</span></span>

## <a name="azure-monitor"></a><span data-ttu-id="c7b3a-105">Azure İzleyici</span><span class="sxs-lookup"><span data-stu-id="c7b3a-105">Azure Monitor</span></span>

<span data-ttu-id="c7b3a-106">[Azure İzleyici](https://azure.microsoft.com/services/monitor/) Canlı uygulamanızı izler, bir genişletilebilir bir analiz hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-106">[Azure Monitor](https://azure.microsoft.com/services/monitor/) is an extensible analytics service that monitors your live application.</span></span> <span data-ttu-id="c7b3a-107">Performans sorunlarını algılayıp tanılamanıza ve kullanıcıların gerçekten uygulamanızla neler anlamak için yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-107">It helps you to detect and diagnose performance issues and to understand what users actually do with your app.</span></span> <span data-ttu-id="c7b3a-108">Sürekli olarak performansını artırmak için yardımcı hedefi ve hizmet veya uygulamalardan birinde kullanılabilirliği içeren, geliştiricilere yönelik tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-108">It's designed for developers, with the intent of helping you to continuously improve the performance and usability of your services or applications.</span></span> <span data-ttu-id="c7b3a-109">Azure İzleyici, .NET, Java, Node.js ve diğer birçok platformda şirket içinde barındırılan gibi platformlarda veya bulutta çeşitli uygulamalar web/hizmetleri ve tek başına ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-109">Azure Monitor works with both web/services and standalone apps on a wide variety of platforms like .NET, Java, Node.js and many other platforms, hosted on-premises or in the cloud.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c7b3a-110">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="c7b3a-110">Additional resources</span></span>

- <span data-ttu-id="c7b3a-111">**Azure İzleyicisi'ne genel bakış** \\</span><span class="sxs-lookup"><span data-stu-id="c7b3a-111">**Overview of Azure Monitor** \\</span></span>
  <https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="c7b3a-112">**Application Insights nedir?**</span><span class="sxs-lookup"><span data-stu-id="c7b3a-112">**What is Application Insights?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="c7b3a-113">**Azure İzleyici ölçümleri nedir?**</span><span class="sxs-lookup"><span data-stu-id="c7b3a-113">**What is Azure Monitor Metrics?**</span></span> \
  <https://docs.microsoft.com/azure/azure-monitor/platform/data-platform-metrics>

- <span data-ttu-id="c7b3a-114">**Azure İzleyici'de kapsayıcı izleme çözümü** \\</span><span class="sxs-lookup"><span data-stu-id="c7b3a-114">**Container Monitoring solution in Azure Monitor** \\</span></span>
  <https://docs.microsoft.com/azure/azure-monitor/insights/containers>

## <a name="security-and-backup-services"></a><span data-ttu-id="c7b3a-115">Güvenlik ve yedekleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="c7b3a-115">Security and backup services</span></span>

<span data-ttu-id="c7b3a-116">Çok bileşenli uygulamalar ve altyapı iş gereksinimlerini desteklemek için üstteki dişli durumda olduklarından emin olmak için işlemesine gerek ayrıntıları birçok destek işlerini vardır ve böylece, bir şekilde durum mikro hizmetler erişim, daha karmaşık hale gelir üst düzey ve ayrıntılı görünümlerini işlem yapması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-116">There are many support chores with lots of details that you have to handle to ensure your applications and infrastructure are in top notch condition to support business needs, and the situation becomes more complicated in the microservices realm, so you need a way to have both high-level and detailed views when you need to take action.</span></span>

<span data-ttu-id="c7b3a-117">Azure, yönetmek ve hem bulut hem de şirket içi kaynaklar dört önemli yönlerini birleşik bir görünümünü sağlamak için geliştirme araçlarına sahiptir:</span><span class="sxs-lookup"><span data-stu-id="c7b3a-117">Azure has the tools to manage and provide a unified view of four critical aspects of both your cloud and on-premises resources:</span></span>

- <span data-ttu-id="c7b3a-118">**Güvenlik**.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-118">**Security**.</span></span> <span data-ttu-id="c7b3a-119">İle [Azure Güvenlik Merkezi](https://azure.microsoft.com/services/security-center/).</span><span class="sxs-lookup"><span data-stu-id="c7b3a-119">With [Azure Security Center](https://azure.microsoft.com/services/security-center/).</span></span>
  - <span data-ttu-id="c7b3a-120">Sanal makineler, uygulamalarınızı ve iş yüklerinin güvenliğini üzerinde tam görünürlük ve denetim alın.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-120">Get full visibility and control over the security of your virtual machines, apps, and workloads.</span></span>
  - <span data-ttu-id="c7b3a-121">Güvenlik ilkelerinizin yönetimini merkezileştirin; mevcut işlemleri ve araçları tümleştirin.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-121">Centralize the management of your security policies and integrate existing processes and tools.</span></span>
  - <span data-ttu-id="c7b3a-122">Gelişmiş analiz sayesinde gerçek tehditleri algılayın.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-122">Detect real threats with advanced analytics.</span></span>

- <span data-ttu-id="c7b3a-123">**Yedekleme**.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-123">**Backup**.</span></span> <span data-ttu-id="c7b3a-124">İle [Azure yedekleme](https://azure.microsoft.com/services/backup/).</span><span class="sxs-lookup"><span data-stu-id="c7b3a-124">With [Azure Backup](https://azure.microsoft.com/services/backup/).</span></span>
  - <span data-ttu-id="c7b3a-125">Maliyetli iş kesintilerinden kaçının, uyumluluk hedeflerinizi karşılayın ve verilerinizi fidye yazılımlarına ve insan hatalarına karşı koruyun.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-125">Avoid costly business disruptions, meet compliance goals, and protect your data against ransomware and human errors.</span></span>
  - <span data-ttu-id="c7b3a-126">Yedekleme verileriniz aktarımda ve bekleme sırasında şifrelenmiş tutun.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-126">Keep your backup data encrypted in transit and at rest.</span></span>
  - <span data-ttu-id="c7b3a-127">Yetkisiz kullanımı önlemek için çok faktörlü kimlik doğrulamasını temel alan erişim emin olun.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-127">Ensure access based on multifactor authentication to prevent unauthorized use.</span></span>

- <span data-ttu-id="c7b3a-128">**Şirket içi kaynaklara**.</span><span class="sxs-lookup"><span data-stu-id="c7b3a-128">**On-premises resources**.</span></span> <span data-ttu-id="c7b3a-129">İle [tamamen tutarlı hibrit bulut](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span><span class="sxs-lookup"><span data-stu-id="c7b3a-129">With [a truly consistent hybrid cloud](https://azure.microsoft.com/resources/truly-consistent-hybrid-cloud-with-microsoft-azure/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c7b3a-130">[Önceki](manage-production-docker-environments.md)
>[İleri](../key-takeaways/index.md)</span><span class="sxs-lookup"><span data-stu-id="c7b3a-130">[Previous](manage-production-docker-environments.md)
[Next](../key-takeaways/index.md)</span></span>
