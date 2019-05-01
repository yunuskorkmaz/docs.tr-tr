---
title: İzleme ve telemetri ile uygulamalarınızı modernleştirme
description: Azure Bulut ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme | İzleme ve telemetri ile uygulamalarınızı modernleştirin
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: cd54861600127191b852e0a966baae6e0fe7914e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012123"
---
# <a name="modernize-your-apps-with-monitoring-and-telemetry"></a><span data-ttu-id="62edb-103">İzleme ve telemetri ile uygulamalarınızı modernleştirme</span><span class="sxs-lookup"><span data-stu-id="62edb-103">Modernize your apps with monitoring and telemetry</span></span>

<span data-ttu-id="62edb-104">Üretim ortamında bir uygulamayı çalıştırdığınızda, uygulamanızın performansıyla ilgili içgörüler olması önemlidir.</span><span class="sxs-lookup"><span data-stu-id="62edb-104">When you run an application in production, it's critical that you have insights about how your application is performing.</span></span> <span data-ttu-id="62edb-105">Bu, yüksek bir düzeyde çalışıyor mu?</span><span class="sxs-lookup"><span data-stu-id="62edb-105">Is it performing at a high level?</span></span> <span data-ttu-id="62edb-106">Kullanıcılar hataları alıyorsanız veya düzenli ve güvenilir uygulamasıdır?</span><span class="sxs-lookup"><span data-stu-id="62edb-106">Are users getting errors, or is the application stable and reliable?</span></span> <span data-ttu-id="62edb-107">Zengin performans izleme, güçlü uyarı ve uygulamanızın kullanılabilir ve beklendiği gibi olduğunu sağlamak için panolar ihtiyacınız var.</span><span class="sxs-lookup"><span data-stu-id="62edb-107">You need rich performance monitoring, powerful alerting, and dashboards to help ensure that your application is available and performing as expected.</span></span> <span data-ttu-id="62edb-108">Ayrıca, hızlı bir şekilde bir sorun olup olmadığını görmek için kaç müşterinin etkilendiğini ve bulmak ve sorunu düzeltmek için bir kök neden analizi gerçekleştirmek belirlemek mümkün olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="62edb-108">You also need to be able to see quickly if there's a problem, determine how many customers are affected, and perform a root-cause analysis to find and fix the issue.</span></span>

## <a name="monitor-your-application-with-application-insights"></a><span data-ttu-id="62edb-109">Uygulamanızı Application Insights ile izleme</span><span class="sxs-lookup"><span data-stu-id="62edb-109">Monitor your application with Application Insights</span></span>

<span data-ttu-id="62edb-110">Application Insights, birden çok platformda çalışan web geliştiricilerine yönelik kapsamlı bir uygulama performans yönetimi (APM) hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="62edb-110">Application Insights is an extensible Application Performance Management (APM) service for web developers who work on multiple platforms.</span></span> <span data-ttu-id="62edb-111">Bunu, canlı web uygulamanızı izlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62edb-111">Use it to monitor your live web application.</span></span> <span data-ttu-id="62edb-112">Application Insights performans anormalliklerini otomatik olarak algılar.</span><span class="sxs-lookup"><span data-stu-id="62edb-112">Application Insights automatically detects performance anomalies.</span></span> <span data-ttu-id="62edb-113">Bu sorunları tanılamanıza yardımcı olmak ve ne kullanıcıların uygulamanızla aslında yaptığını anlamanıza yardımcı olacak güçlü analiz araçları içerir.</span><span class="sxs-lookup"><span data-stu-id="62edb-113">It includes powerful analytics tools to help you diagnose issues, and to help you understand what users actually do with your app.</span></span> <span data-ttu-id="62edb-114">Application Insights, performansı ve kullanılabilirliği sürekli geliştirmenize yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="62edb-114">Application Insights is designed to help you continuously improve performance and usability.</span></span> <span data-ttu-id="62edb-115">Uygulamalar için çok çeşitli platformlarda, .NET, Node.js ve J2EE, dahil, üzerinde çalıştığı şirket içinde barındırılan veya bulutta.</span><span class="sxs-lookup"><span data-stu-id="62edb-115">It works for apps on a wide variety of platforms, including .NET, Node.js, and J2EE, whether hosted on-premises or in the cloud.</span></span> <span data-ttu-id="62edb-116">Application Insights, DevOps süreçlerinizin ile tümleşir ve geliştirme araçları çeşitli bağlantı noktaları vardır.</span><span class="sxs-lookup"><span data-stu-id="62edb-116">Application Insights integrates with your DevOps processes, and has connection points to a variety of development tools.</span></span>

<span data-ttu-id="62edb-117">Şekil 4-10 nasıl Application Insights uygulamanızı izler ve nasıl bir panoya içgörüleri yüzeyler örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="62edb-117">Figure 4-10 shows an example of how Application Insights monitors your application and how it surfaces those insights to a dashboard.</span></span>

![Application Insights izleme Panosu](./media/image10.png)

> <span data-ttu-id="62edb-119">**Şekil 4-10.**</span><span class="sxs-lookup"><span data-stu-id="62edb-119">**Figure 4-10.**</span></span> <span data-ttu-id="62edb-120">Application Insights izleme Panosu</span><span class="sxs-lookup"><span data-stu-id="62edb-120">Application Insights monitoring dashboard</span></span>

## <a name="monitor-your-docker-infrastructure-with-log-analytics-and-its-container-monitoring-solution"></a><span data-ttu-id="62edb-121">Log Analytics ve kapsayıcı izleme çözümü ile Docker altyapısını izleme</span><span class="sxs-lookup"><span data-stu-id="62edb-121">Monitor your Docker infrastructure with Log Analytics and its Container Monitoring solution</span></span>

<span data-ttu-id="62edb-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) parçasıdır [izleme çözümü genel Microsoft Azure](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span><span class="sxs-lookup"><span data-stu-id="62edb-122">[Azure Log Analytics](https://docs.microsoft.com/azure/log-analytics/log-analytics-overview) is part of the [Microsoft Azure overall monitoring solution](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview).</span></span> <span data-ttu-id="62edb-123">Ayrıca bir hizmetin içinde bulunduğu [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span><span class="sxs-lookup"><span data-stu-id="62edb-123">It's also a service in [Operations Management Suite (OMS)](https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview).</span></span> <span data-ttu-id="62edb-124">Log Analytics bulut izler ve ortamları (OMS şirket içi) kullanılabilirliğini ve performansını sağlamak için şirket içinde.</span><span class="sxs-lookup"><span data-stu-id="62edb-124">Log Analytics monitors cloud and on-premises environments (OMS for on-premises) to help maintain availability and performance.</span></span> <span data-ttu-id="62edb-125">Birden fazla kaynak arasında analiz sağlamak üzere bulut ve şirket içi ortamlarınızdaki kaynaklar ile diğer izleme araçları tarafından oluşturulan verileri toplar.</span><span class="sxs-lookup"><span data-stu-id="62edb-125">It collects data generated by resources in your cloud and on-premises environments and from other monitoring tools to provide analysis across multiple sources.</span></span>

<span data-ttu-id="62edb-126">Azure altyapı günlükleri ile ilgili olarak, bir Azure hizmeti olduğundan Log Analytics, diğer Azure Hizmetleri'den günlük ve ölçüm verilerini alır. (aracılığıyla [Azure İzleyici](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure Vm'leri, Docker kapsayıcıları ve şirket içinde veya diğer bulut altyapıları.</span><span class="sxs-lookup"><span data-stu-id="62edb-126">In relation to Azure infrastructure logs, Log Analytics, as an Azure service, ingests log and metric data from other Azure services (via [Azure Monitor](https://docs.microsoft.com/azure/monitoring-and-diagnostics/monitoring-overview-azure-monitor)), Azure VMs, Docker containers, and on-premises or other cloud infrastructures.</span></span> <span data-ttu-id="62edb-127">Log Analytics, esnek bir günlük araması ve bu veriler üzerinde analiz out-hazır sunar.</span><span class="sxs-lookup"><span data-stu-id="62edb-127">Log Analytics offers flexible log search and out-of-the box analytics on top of this data.</span></span> <span data-ttu-id="62edb-128">Bu, veri kaynaklarında analiz etmek için kullanabileceğiniz, tüm günlükleri arasında karmaşık sorgular sağlar ve proaktif olarak uyarabilir zengin Araçlar belirli koşullara göre sağlar.</span><span class="sxs-lookup"><span data-stu-id="62edb-128">It provides rich tools that you can use to analyze data across sources, it allows complex queries across all logs, and it can proactively alert based on specified conditions.</span></span> <span data-ttu-id="62edb-129">Hatta, sorgu ve bunları görselleştirmek merkezi Log Analytics deposunda, özel veri toplayabilir.</span><span class="sxs-lookup"><span data-stu-id="62edb-129">You can even collect custom data in the central Log Analytics repository, where you can query and visualize it.</span></span> <span data-ttu-id="62edb-130">Hemen güvenliği hakkında Öngörüler elde etmek için Log Analytics yerleşik çözümleri avantajlarından ve altyapınızı işlevselliğini da yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62edb-130">You also can take advantage of the Log Analytics built-in solutions to immediately gain insights into the security and functionality of your infrastructure.</span></span>

<span data-ttu-id="62edb-131">OMS portalı veya tüm tarayıcılarda çalıştırmak, Azure portalı Log Analytics'e erişimi ve yapılandırma ayarlarını erişmenizi ve çok sayıda araç çözümlemek ve toplanan verilerde işlem yapmak için sağlayın.</span><span class="sxs-lookup"><span data-stu-id="62edb-131">You can access Log Analytics through the OMS portal or the Azure portal, which run in any browser, and provide you with access to configuration settings and multiple tools to analyze and act on collected data.</span></span>

<span data-ttu-id="62edb-132">[Kapsayıcı izleme çözümü](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) Log Analytics yardımcı olarak görüntüleyin ve Docker ve Windows kapsayıcı konaklarınız tek bir konumda yönetin.</span><span class="sxs-lookup"><span data-stu-id="62edb-132">The [Container Monitoring solution](https://docs.microsoft.com/azure/log-analytics/log-analytics-containers) in Log Analytics helps you view and manage your Docker and Windows Container hosts in a single location.</span></span> <span data-ttu-id="62edb-133">Çözüm gösterir hangi kapsayıcıları çalıştırmak, hangi kapsayıcı görüntüsü ister çalışıyor ve kapsayıcıları çalıştığı.</span><span class="sxs-lookup"><span data-stu-id="62edb-133">The solution shows which containers are running, what container image they're running, and where containers are running.</span></span> <span data-ttu-id="62edb-134">Kapsayıcılar ile kullanılan komutları dahil olmak üzere ayrıntılı denetim bilgileri görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62edb-134">You can view detailed audit information, including commands that are being used with containers.</span></span> <span data-ttu-id="62edb-135">Kapsayıcılar, Docker veya Windows konak uzaktan görüntülemeye gerek kalmadan merkezi günlükleri, arama ve görüntüleme de giderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62edb-135">You also can troubleshoot containers by viewing and searching centralized logs, without needing to remotely view Docker or Windows hosts.</span></span> <span data-ttu-id="62edb-136">Bir konakta gürültülü ve alıcı aşırı kaynakları olabilecek kapsayıcıları bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62edb-136">You can find containers that might be noisy and consuming excess resources on a host.</span></span> <span data-ttu-id="62edb-137">Ayrıca, merkezileştirilmiş CPU, bellek, depolama ve ağ kullanımını ve kapsayıcılar için performans bilgilerini görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="62edb-137">Additionally, you can view centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span> <span data-ttu-id="62edb-138">Windows çalıştıran bilgisayarlarda, merkezileştirme ve Windows Server günlüklerinden karşılaştırın Hyper-V ve Docker kapsayıcıları.</span><span class="sxs-lookup"><span data-stu-id="62edb-138">On computers running Windows, you can centralize and compare logs from Windows Server, Hyper-V, and Docker containers.</span></span> <span data-ttu-id="62edb-139">Çözüm, aşağıdaki kapsayıcı düzenleyicileri destekler:</span><span class="sxs-lookup"><span data-stu-id="62edb-139">The solution supports the following container orchestrators:</span></span>

- <span data-ttu-id="62edb-140">Docker Swarm</span><span class="sxs-lookup"><span data-stu-id="62edb-140">Docker Swarm</span></span>

- <span data-ttu-id="62edb-141">DC/OS</span><span class="sxs-lookup"><span data-stu-id="62edb-141">DC/OS</span></span>

- <span data-ttu-id="62edb-142">Kubernetes</span><span class="sxs-lookup"><span data-stu-id="62edb-142">Kubernetes</span></span>

- <span data-ttu-id="62edb-143">Service Fabric</span><span class="sxs-lookup"><span data-stu-id="62edb-143">Service Fabric</span></span>

- <span data-ttu-id="62edb-144">Red Hat OpenShift</span><span class="sxs-lookup"><span data-stu-id="62edb-144">Red Hat OpenShift</span></span>

<span data-ttu-id="62edb-145">Şekil 4-11 çeşitli kapsayıcı konakları ve aracıları ve OMS arasındaki ilişkiler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="62edb-145">Figure 4-11 shows the relationships between various container hosts and agents and OMS.</span></span>

![Log Analytics kapsayıcı izleme çözümü](./media/image11.png)

> <span data-ttu-id="62edb-147">**Şekil 4-11.**</span><span class="sxs-lookup"><span data-stu-id="62edb-147">**Figure 4-11.**</span></span> <span data-ttu-id="62edb-148">Log Analytics kapsayıcı izleme çözümü</span><span class="sxs-lookup"><span data-stu-id="62edb-148">Log Analytics Container Monitoring solution</span></span>

<span data-ttu-id="62edb-149">Log Analytics kapsayıcı izleme çözümü kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="62edb-149">You can use the Log Analytics Container Monitoring solution to:</span></span>

- <span data-ttu-id="62edb-150">Tek bir konumda tüm kapsayıcı konakları hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="62edb-150">See information about all container hosts in a single location.</span></span>

- <span data-ttu-id="62edb-151">Kapsayıcıları olduğunuzu çalıştırmak, hangi görüntüyü çalıştırdıkları ve bunların nereye çalıştırdığınızdan.</span><span class="sxs-lookup"><span data-stu-id="62edb-151">Know which containers are running, what image they're running, and where they're running.</span></span>

- <span data-ttu-id="62edb-152">Eylemler için bir denetim kaydı kapsayıcılarında bakın.</span><span class="sxs-lookup"><span data-stu-id="62edb-152">See an audit trail for actions on containers.</span></span>

- <span data-ttu-id="62edb-153">Docker ana bilgisayarları için uzaktan oturum açma olmadan Merkezi günlük arama ve görüntüleme sorunlarını giderin.</span><span class="sxs-lookup"><span data-stu-id="62edb-153">Troubleshoot by viewing and searching centralized logs without remote login to the Docker hosts.</span></span>

- <span data-ttu-id="62edb-154">"Gürültülü komşu" olabilir ve bir konak üzerinde aşırı kaynakları kullanan kapsayıcıları bulun.</span><span class="sxs-lookup"><span data-stu-id="62edb-154">Find containers that might be "noisy neighbors," and be consuming excess resources on a host.</span></span>

- <span data-ttu-id="62edb-155">Merkezileştirilmiş CPU, bellek, depolama ve ağ kullanımını ve kapsayıcılar için performans bilgilerini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="62edb-155">View centralized CPU, memory, storage, and network usage, and performance information, for containers.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="62edb-156">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="62edb-156">Additional resources</span></span>

- <span data-ttu-id="62edb-157">**Microsoft Azure'da izlemeye genel bakış**</span><span class="sxs-lookup"><span data-stu-id="62edb-157">**Overview of monitoring in Microsoft Azure**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="62edb-158">**Application Insights nedir?**</span><span class="sxs-lookup"><span data-stu-id="62edb-158">**What is Application Insights?**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview>

- <span data-ttu-id="62edb-159">**Log Analytics nedir?**</span><span class="sxs-lookup"><span data-stu-id="62edb-159">**What is Log Analytics?**</span></span>

<https://docs.microsoft.com/azure/log-analytics/log-analytics-overview>

- <span data-ttu-id="62edb-160">**Azure İzleyici'de kapsayıcı izleme çözümü**</span><span class="sxs-lookup"><span data-stu-id="62edb-160">**Container Monitoring solution in Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/insights/containers>

- <span data-ttu-id="62edb-161">**Azure İzleyicisi'ne genel bakış**</span><span class="sxs-lookup"><span data-stu-id="62edb-161">**Overview of Azure Monitor**</span></span>

<https://docs.microsoft.com/azure/azure-monitor/overview>

- <span data-ttu-id="62edb-162">**Operations Management Suite (OMS) nedir?**</span><span class="sxs-lookup"><span data-stu-id="62edb-162">**What is Operations Management Suite (OMS)?**</span></span>

<https://docs.microsoft.com/azure/operations-management-suite/operations-management-suite-overview>

- <span data-ttu-id="62edb-163">**Windows Server kapsayıcıları Service fabric'te OMS ile izleme**</span><span class="sxs-lookup"><span data-stu-id="62edb-163">**Monitoring Windows Server containers in Service Fabric with OMS**</span></span>

<https://docs.microsoft.com/azure/service-fabric/service-fabric-diagnostics-containers-windowsserver>

>[!div class="step-by-step"]
><span data-ttu-id="62edb-164">[Önceki](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
>[İleri](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="62edb-164">[Previous](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
[Next](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)</span></span>
