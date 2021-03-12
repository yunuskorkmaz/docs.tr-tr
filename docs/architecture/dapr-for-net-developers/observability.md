---
title: Davpr Observability yapı taşı
description: Observability yapı bloğunun açıklaması, özellikleri, avantajları ve nasıl uygulanacağı
author: edwinvw
ms.date: 02/07/2021
ms.reviewer: robvet
ms.openlocfilehash: 6add36b2030c3061ee522604b2e07f05875b98a9
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604716"
---
# <a name="the-dapr-observability-building-block"></a><span data-ttu-id="5e1e8-103">Davpr Observability yapı taşı</span><span class="sxs-lookup"><span data-stu-id="5e1e8-103">The Dapr observability building block</span></span>

<span data-ttu-id="5e1e8-104">Modern dağıtılmış sistemler karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-104">Modern distributed systems are complex.</span></span> <span data-ttu-id="5e1e8-105">Küçük, gevşek olarak bağlanmış ve bağımsız dağıtılabilir hizmetlerle başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-105">You start with small, loosely coupled, independently deployable services.</span></span> <span data-ttu-id="5e1e8-106">Bu hizmetler çapraz işlem ve sunucu sınırları.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-106">These services cross process and server boundaries.</span></span> <span data-ttu-id="5e1e8-107">Daha sonra farklı türlerde altyapı yedekleme hizmetleri (veritabanları, ileti aracıları, Anahtar kasaları) kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-107">They then consume different kinds of infrastructure backing services (databases, message brokers, key vaults).</span></span> <span data-ttu-id="5e1e8-108">Son olarak, bu farklı parçalar bir uygulama oluşturmak için birlikte oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-108">Finally, these disparate pieces compose together to form an application.</span></span>

<span data-ttu-id="5e1e8-109">Çok sayıda ayrı, hareketli parçalar sayesinde ne olduğunu nasıl anladığınızda?</span><span class="sxs-lookup"><span data-stu-id="5e1e8-109">With so many separate, moving parts, how do you make sense of what is going on?</span></span> <span data-ttu-id="5e1e8-110">Ne yazık ki, geçmişteki eski izleme yaklaşımları yeterince fazla değil.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-110">Unfortunately, legacy monitoring approaches from the past aren't enough.</span></span> <span data-ttu-id="5e1e8-111">Bunun yerine, sistemin uçtan uca **observable** olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-111">Instead, the system must be **observable** from end-to-end.</span></span> <span data-ttu-id="5e1e8-112">Modern [Observability](../cloud-native/observability-patterns.md) uygulamaları, her zaman uygulamanın sistem durumu hakkında görünürlük ve öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-112">Modern [observability](../cloud-native/observability-patterns.md) practices provide visibility and insight into the health of the application at all times.</span></span> <span data-ttu-id="5e1e8-113">Bu kişiler, çıktıyı gözlemleyerek iç durumu çıkarımı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-113">They enable you to infer the internal state by observing the output.</span></span> <span data-ttu-id="5e1e8-114">Observability, dağıtılmış uygulamaları izlemek ve sorunlarını gidermek için zorunludur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-114">Observability is mandatory for monitoring and troubleshooting distributed applications.</span></span>

<span data-ttu-id="5e1e8-115">Observability kazanmak için kullanılan sistem bilgileri **telemetri** olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-115">The system information used to gain observability is referred to as **telemetry**.</span></span> <span data-ttu-id="5e1e8-116">Bu, dört geniş kategoriye ayrılabilir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-116">It can be divided into four broad categories:</span></span>

1. <span data-ttu-id="5e1e8-117">**Dağıtılmış izleme** , Dağıtılmış işlemlerde yer alan hizmetler ve hizmetler arasındaki trafiğe ilişkin öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-117">**Distributed tracing** provides insight into the traffic between services and services involved in distributed transactions.</span></span>
1. <span data-ttu-id="5e1e8-118">**Ölçümler** , bir hizmetin performansına ve kaynak tüketimine ilişkin öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-118">**Metrics** provides insight into the performance of a service and its resource consumption.</span></span>
1. <span data-ttu-id="5e1e8-119">**Günlüğe kaydetme** , kodun nasıl yürütüldüğü ve hataların oluşma hakkında öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-119">**Logging** provides insight into how the code is executing and if errors have occurred.</span></span>
1. <span data-ttu-id="5e1e8-120">**Sistem durumu** uç noktaları, bir hizmetin kullanılabilirliğine ilişkin öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-120">**Health** endpoints provide insight into the availability of a service.</span></span>

<span data-ttu-id="5e1e8-121">Telemetri derinliği, bir uygulama platformunun Observability özellikleri tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-121">The depth of telemetry is determined by the observability features of an application platform.</span></span> <span data-ttu-id="5e1e8-122">Azure bulutunu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-122">Consider the Azure cloud.</span></span> <span data-ttu-id="5e1e8-123">Telemetri kategorilerinin tümünü içeren zengin bir telemetri deneyimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-123">It provides a rich telemetry experience that includes all of the telemetry categories.</span></span> <span data-ttu-id="5e1e8-124">Herhangi bir yapılandırma olmadan, Azure IaaS ve PaaS hizmetlerinin çoğu Azure [Application Insights](/azure/azure-monitor/app/app-insights-overview) hizmetine telemetri yayar ve yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-124">Without any configuration, most Azure IaaS and PaaS services propagate and publish telemetry to the [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview) service.</span></span> <span data-ttu-id="5e1e8-125">Application Insights, yüksek görsel panolarla sistem günlüğü, izleme ve sorun alanı sunar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-125">Application Insights presents system logging, tracing, and problem areas with highly visual dashboards.</span></span> <span data-ttu-id="5e1e8-126">Hatta, iletişim özelliklerini temel alan hizmetler arasındaki bağımlılıkları gösteren bir diyagramı işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-126">It can even render a diagram showing the dependencies between services based on their communication.</span></span>

<span data-ttu-id="5e1e8-127">Ancak, bir uygulama Azure PaaS ve IaaS kaynaklarını kullanamıyoruz ne olursa?</span><span class="sxs-lookup"><span data-stu-id="5e1e8-127">However, what if an application can't use Azure PaaS and IaaS resources?</span></span> <span data-ttu-id="5e1e8-128">Application Insights zengin telemetri deneyiminden yararlanmak yine de mümkün mü?</span><span class="sxs-lookup"><span data-stu-id="5e1e8-128">Is it still possible to take advantage of the rich telemetry experience of Application Insights?</span></span> <span data-ttu-id="5e1e8-129">Yanıt Evet 'tir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-129">The answer is yes.</span></span> <span data-ttu-id="5e1e8-130">Azure olmayan bir uygulama, Azure Application Insights telemetri yaymak için kitaplıkları içeri aktarabilir, yapılandırma ve araç kodu ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-130">A non-Azure application can import libraries, add configuration, and instrument code to emit telemetry to Azure Application Insights.</span></span> <span data-ttu-id="5e1e8-131">Ancak, bu yaklaşım uygulamayı Application Insights sıkı bir şekilde **bağar** .</span><span class="sxs-lookup"><span data-stu-id="5e1e8-131">However, this approach **tightly couples** the application to Application Insights.</span></span> <span data-ttu-id="5e1e8-132">Uygulamayı farklı bir izleme platformuna taşımak, pahalı yeniden düzenleme gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-132">Moving the app to a different monitoring platform could involve expensive refactoring.</span></span> <span data-ttu-id="5e1e8-133">Sıkı bir şekilde Observability mek ve kodun dışından kullanım sağlamak için harika olmaz misiniz?</span><span class="sxs-lookup"><span data-stu-id="5e1e8-133">Wouldn't it be great to avoid tight coupling and consume observability outside of the code?</span></span>

<span data-ttu-id="5e1e8-134">Davpr ile yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-134">With Dapr, you can.</span></span> <span data-ttu-id="5e1e8-135">Daha sonra, bir Davpr 'nin dağıtılmış uygulamalarınıza nasıl Observability ekleyebilmesine bakalım.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-135">Let's look at how Dapr can add observability to our distributed applications.</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="5e1e8-136">Ne çözdüğü</span><span class="sxs-lookup"><span data-stu-id="5e1e8-136">What it solves</span></span>

<span data-ttu-id="5e1e8-137">Davpr Observability Building bloğu uygulamadan uples Observability ayrışar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-137">The Dapr observability building block decouples observability from the application.</span></span> <span data-ttu-id="5e1e8-138">Bu, davpr sıdecars ve davpr denetim düzlemi oluşturan Davpr sistem hizmetleri tarafından oluşturulan trafiği otomatik olarak yakalar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-138">It automatically captures traffic generated by Dapr sidecars and Dapr system services that make up the Dapr control plane.</span></span> <span data-ttu-id="5e1e8-139">Blok, trafiği birden çok hizmete yayılan tek bir işlemden ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-139">The block correlates traffic from a single operation that spans multiple services.</span></span> <span data-ttu-id="5e1e8-140">Ayrıca performans ölçümlerini, kaynak kullanımını ve sistemin sistem durumunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-140">It also exposes performance metrics, resource utilization, and the health of the system.</span></span> <span data-ttu-id="5e1e8-141">Telemetri, açık standart biçimlerde yayımlanır ve bu sayede, bilgilerin izleme arka ucuna eklenmesi sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-141">Telemetry is published in open-standard formats enabling information to be fed into your monitoring back end of choice.</span></span> <span data-ttu-id="5e1e8-142">Burada bilgiler görselleştirilir, sorgulanabilir ve analiz edilebilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-142">There, the information can be visualized, queried, and analyzed.</span></span>

<span data-ttu-id="5e1e8-143">Davpr, sıhhi tesisat 'yi uztığından, uygulama Observability nasıl uygulandığının farkında değildir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-143">As Dapr abstracts away the plumbing, the application is unaware of how observability is implemented.</span></span> <span data-ttu-id="5e1e8-144">Kitaplıklara başvurulmasına veya özel izleme kodu uygulamanıza gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-144">There's no need to reference libraries or implement custom instrumentation code.</span></span> <span data-ttu-id="5e1e8-145">Davpr, geliştiricinin Observability tesisat değil iş mantığı oluşturmaya odaklanarak çalışmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-145">Dapr allows the developer to focus on building business logic and not observability plumbing.</span></span> <span data-ttu-id="5e1e8-146">Observability, mepr düzeyinde yapılandırılır ve farklı takımlar tarafından oluşturulduğunda bile hizmetler genelinde tutarlıdır ve farklı teknoloji yığınları ile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-146">Observability is configured at the Dapr level and is consistent across services, even when created by different teams, and built with different technology stacks.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="5e1e8-147">Nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="5e1e8-147">How it works</span></span>

<span data-ttu-id="5e1e8-148">Davpr 'nin [Dışarıdan yükleme mimarisi](dapr-at-20000-feet.md#sidecar-architecture) , yerleşik Observability özellikleri sunar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-148">Dapr's [sidecar architecture](dapr-at-20000-feet.md#sidecar-architecture) enables built-in observability features.</span></span> <span data-ttu-id="5e1e8-149">Hizmetler iletişim kurarken, Davpr 'ler trafiği durdurur ve izleme, ölçümler ve günlüğe kaydetme bilgilerini ayıklar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-149">As services communicate, Dapr sidecars intercept the traffic and extract tracing, metrics, and logging information.</span></span> <span data-ttu-id="5e1e8-150">Telemetri açık bir standartlar biçiminde yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-150">Telemetry is published in an open standards format.</span></span> <span data-ttu-id="5e1e8-151">Varsayılan olarak, Davpr [Opentelemetri](https://opentelemetry.io/) ve [zipy](https://zipkin.io/)'yi destekler.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-151">By default, Dapr supports [OpenTelemetry](https://opentelemetry.io/) and [Zipkin](https://zipkin.io/).</span></span>

<span data-ttu-id="5e1e8-152">Davpr, farklı arka uç izleme araçlarına telemetri yayımlayabilen [toplayıcılar](https://docs.dapr.io/operations/monitoring/tracing/open-telemetry-collector/) sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-152">Dapr provides [collectors](https://docs.dapr.io/operations/monitoring/tracing/open-telemetry-collector/) that can publish telemetry to different back-end monitoring tools.</span></span> <span data-ttu-id="5e1e8-153">Bu araçlar analiz ve sorgulama için bir Dadpr telemetrisi sunar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-153">These tools present Dapr telemetry for analysis and querying.</span></span> <span data-ttu-id="5e1e8-154">Şekil 9-1, Davpr Observability mimarisini gösterir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-154">Figure 9-1 shows the Dapr observability architecture:</span></span>

![Davpr Observability mimarisi](media/observability/observability-architecture.png)

<span data-ttu-id="5e1e8-156">**Şekil 9-1**.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-156">**Figure 9-1**.</span></span> <span data-ttu-id="5e1e8-157">Davpr Observability mimarisi.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-157">Dapr observability architecture.</span></span>

1. <span data-ttu-id="5e1e8-158">A hizmeti, B hizmetinde bir işlem çağırır. Çağrı, a hizmeti için a 'nın B hizmeti için bir kacar sepet 'ten yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-158">Service A calls an operation on Service B. The call is routed from a Dapr sidecar for Service A to a sidecar for Service B.</span></span>
1. <span data-ttu-id="5e1e8-159">Hizmet B işlemi tamamlarsa, bir yanıt hizmet A 'ya bir yanıt gönderilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-159">When Service B completes the operation, a response is sent back to Service A through the Dapr sidecars.</span></span> <span data-ttu-id="5e1e8-160">Her istek ve yanıt için tüm kullanılabilir telemetri toplar ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-160">They gather and publish all available telemetry for every request and response.</span></span>
1. <span data-ttu-id="5e1e8-161">Yapılandırılan toplayıcı telemetri alır ve izleme arka ucuna gönderir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-161">The configured collector ingests the telemetry and sends it to the monitoring back end.</span></span>  

<span data-ttu-id="5e1e8-162">Geliştirici olarak, Observability eklemenin, pub/Sub veya State Management gibi diğer Davpr oluşturma bloklarını yapılandırmadan farklı olduğunu aklınızda bulundurun.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-162">As a developer, keep in mind that adding observability is different from configuring other Dapr building blocks, like pub/sub or state management.</span></span> <span data-ttu-id="5e1e8-163">Bir yapı bloğuna başvurmak yerine bir toplayıcı ve izleme arka ucu eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-163">Instead of referencing a building block, you add a collector and a monitoring back end.</span></span> <span data-ttu-id="5e1e8-164">Şekil 9-1, farklı izleme arka uçları ile tümleştirilen birden çok toplayıcı yapılandırmak için mümkün olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-164">Figure 9-1 shows it's possible to configure multiple collectors that integrate with different monitoring back ends.</span></span>

<span data-ttu-id="5e1e8-165">Bu bölümün başlangıcında dört telemetri kategorisi tanımlanmıştı.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-165">At the beginning of this chapter, four categories of telemetry were identified.</span></span> <span data-ttu-id="5e1e8-166">Aşağıdaki bölümler her kategori için ayrıntı sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-166">The following sections will provide detail for each category.</span></span> <span data-ttu-id="5e1e8-167">Bunlar, popüler izleme arka uçları ile tümleştirilen toplayıcıların nasıl yapılandırılacağı hakkında yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-167">They'll include instruction on how to configure collectors that integrate with popular monitoring back ends.</span></span>

### <a name="distributed-tracing"></a><span data-ttu-id="5e1e8-168">Dağıtılmış izleme</span><span class="sxs-lookup"><span data-stu-id="5e1e8-168">Distributed tracing</span></span>

<span data-ttu-id="5e1e8-169">Dağıtılmış izleme, dağıtılmış bir uygulamadaki hizmetler arasında akan trafiğe ilişkin öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-169">Distributed tracing provides insight into the traffic that flows across services in a distributed application.</span></span> <span data-ttu-id="5e1e8-170">Değiştirilen istek ve yanıt iletilerinin günlüğü, sorun giderme sorunları için değerli bir bilgi kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-170">The log of exchanged request and response messages is an invaluable source of information for troubleshooting issues.</span></span> <span data-ttu-id="5e1e8-171">Sabit bölüm, aynı işlemden kaynaklanan *iletileri eş* olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-171">The hard part is *correlating messages* that originate from the same operation.</span></span>

<span data-ttu-id="5e1e8-172">Davpr, ilgili iletileri ilişkilendirmek için [W3C Trace bağlamını](https://www.w3.org/TR/trace-context) kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-172">Dapr uses the [W3C Trace Context](https://www.w3.org/TR/trace-context) to correlate related messages.</span></span> <span data-ttu-id="5e1e8-173">Aynı bağlam bilgilerini, benzersiz bir işlem oluşturan istek ve yanıtlara çıkartır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-173">It injects the same context information into requests and responses that form a unique operation.</span></span> <span data-ttu-id="5e1e8-174">Şekil 9-2, bağıntı 'nın nasıl çalıştığını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-174">Figure 9-2 shows how correlation works:</span></span>

![W3C Trace bağlam örneği](media/observability/w3c-trace-context.png)

<span data-ttu-id="5e1e8-176">**Şekil 9-2**.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-176">**Figure 9-2**.</span></span> <span data-ttu-id="5e1e8-177">W3C Trace bağlam örneği.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-177">W3C Trace Context example.</span></span>

1. <span data-ttu-id="5e1e8-178">Hizmet A, B hizmetinde bir işlem çağırır. Service A çağrısı başlattığı için, Davpr benzersiz bir izleme bağlamı oluşturur ve bu dosyayı istek içine çıkarır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-178">Service A invokes an operation on Service B. As Service A starts the call, Dapr creates a unique trace context and injects it into the request.</span></span>
1. <span data-ttu-id="5e1e8-179">B hizmeti, isteği alır ve hizmeti C üzerinde bir işlem çağırır. Davpr gelen isteğin bir izleme bağlamı içerdiğini algılar ve bunu, ekleme to Service to the The The The The The The The The Service a The The The The</span><span class="sxs-lookup"><span data-stu-id="5e1e8-179">Service B receives the request and invokes an operation on Service C. Dapr detects that the incoming request contains a trace context and propagates it by injecting it into the outgoing request to Service C.</span></span>  
1. <span data-ttu-id="5e1e8-180">Service C, isteği alır ve işler.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-180">Service C receives the request and handles it.</span></span> <span data-ttu-id="5e1e8-181">Davpr, gelen isteğin bir izleme bağlamı içerdiğini algılar ve bunu yeniden B hizmetine geri giden yanıtı ekleme göre yayar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-181">Dapr detects that the incoming request contains a trace context and propagates it by injecting it into the outgoing response back to Service B.</span></span>
1. <span data-ttu-id="5e1e8-182">B hizmeti yanıtı alır ve işler.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-182">Service B receives the response and handles it.</span></span> <span data-ttu-id="5e1e8-183">Daha sonra yeni bir yanıt oluşturur ve izleme bağlamını bir A hizmetine geri giden yanıt ekleme olarak yayar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-183">It then creates a new response and propagates the trace context by injecting it into the outgoing response back to Service A.</span></span>

<span data-ttu-id="5e1e8-184">Birlikte gelen bir istek ve yanıt kümesine *izleme* denir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-184">A set of requests and responses that belong together is called a *trace*.</span></span> <span data-ttu-id="5e1e8-185">Şekil 9-3 bir izlemeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-185">Figure 9-3 shows a trace:</span></span>

![İzlemeler ve yayılmalar](media/observability/traces-spans.png)

<span data-ttu-id="5e1e8-187">**Şekil 9-3**.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-187">**Figure 9-3**.</span></span> <span data-ttu-id="5e1e8-188">İzlemeler ve yayılmalar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-188">Traces and spans.</span></span>

<span data-ttu-id="5e1e8-189">Şekilde, izlemenin birçok hizmet arasında gerçekleşen benzersiz bir uygulama işlemini nasıl temsil ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-189">In the figure, note how the trace represents a unique application transaction that takes place across many services.</span></span> <span data-ttu-id="5e1e8-190">İzleme, *yayılmalar* koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-190">A trace is a collection of *spans*.</span></span> <span data-ttu-id="5e1e8-191">Her yayılma, izleme içinde yapılan tek bir işlem veya iş birimini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-191">Each span represents a single operation or unit of work done within the trace.</span></span> <span data-ttu-id="5e1e8-192">Yayılmalar, benzersiz işlemi uygulayan hizmetler arasında gönderilen isteklerdir ve yanıtlardır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-192">Spans are the requests and responses that are sent between services that implement the unique transaction.</span></span>

<span data-ttu-id="5e1e8-193">Sonraki bölümlerde, izleme telemetrisini bir izleme arka ucuna yayımlayarak nasıl inceleyeceğiniz açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-193">The next sections discuss how to inspect tracing telemetry by publishing it to a monitoring back end.</span></span>

#### <a name="use-a-zipkin-monitoring-back-end"></a><span data-ttu-id="5e1e8-194">Bir sıkıştırma arka ucu kullanın</span><span class="sxs-lookup"><span data-stu-id="5e1e8-194">Use a Zipkin monitoring back end</span></span>

<span data-ttu-id="5e1e8-195">[Zipkabağı](https://zipkin.io/) , açık kaynaklı bir dağıtılmış izleme sistemidir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-195">[Zipkin](https://zipkin.io/) is an open-source distributed tracing system.</span></span> <span data-ttu-id="5e1e8-196">Telemetri verilerini alabilir ve görselleştirin.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-196">It can ingest and visualize telemetry data.</span></span> <span data-ttu-id="5e1e8-197">Davpr, Ferkaya için varsayılan destek sunar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-197">Dapr offers default support for Zipkin.</span></span> <span data-ttu-id="5e1e8-198">Aşağıdaki örnek, Davpr telemetrisini görselleştirmek üzere Zipkabağı 'nın nasıl yapılandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-198">The following example demonstrates how to configure Zipkin to visualize Dapr telemetry.</span></span>

##### <a name="enable-and-configure-tracing"></a><span data-ttu-id="5e1e8-199">İzlemeyi etkinleştirme ve yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5e1e8-199">Enable and configure tracing</span></span>

<span data-ttu-id="5e1e8-200">Başlamak için, bir Davpr yapılandırma dosyası kullanan Davpr çalışma zamanı için izlemenin etkinleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-200">To start, tracing must be enabled for the Dapr runtime using a Dapr configuration file.</span></span> <span data-ttu-id="5e1e8-201">Aşağıda adlı bir yapılandırma dosyası örneği verilmiştir `tracing-config.yaml` :</span><span class="sxs-lookup"><span data-stu-id="5e1e8-201">Here's an example of a configuration file named `tracing-config.yaml`:</span></span>  

```yaml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: tracing-config
  namespace: default
spec:
  tracing:
    samplingRate: "1"
    zipkin:
      endpointAddress: "http://zipkin.default.svc.cluster.local:9411/api/v2/spans"
```

<span data-ttu-id="5e1e8-202">`samplingRate`Öznitelik, izlemeleri yayımlamak için kullanılan aralığı belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-202">The `samplingRate` attribute specifies the interval used for publishing traces.</span></span> <span data-ttu-id="5e1e8-203">Değer `0` (izleme devre dışı) ve `1` (her izleme yayımlanır) arasında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-203">The value must be between `0` (tracing disabled) and `1` (every trace is published).</span></span> <span data-ttu-id="5e1e8-204">Örneğin, bir değeri ile, `0.5` yayımlanan trafiği önemli ölçüde azaltan diğer tüm izleme yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-204">With a value of `0.5`, for example, every other trace is published, significantly reducing published traffic.</span></span> <span data-ttu-id="5e1e8-205">`endpointAddress`Bir Kubernetes kümesinde çalışan bir Zipkaya sunucusunda bir uç noktaya işaret eder.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-205">The `endpointAddress` points to an endpoint on a Zipkin server running in a Kubernetes cluster.</span></span> <span data-ttu-id="5e1e8-206">Zipkaya için varsayılan bağlantı noktası `9411` .</span><span class="sxs-lookup"><span data-stu-id="5e1e8-206">The default port for Zipkin is `9411`.</span></span> <span data-ttu-id="5e1e8-207">Yapılandırma Kubernetes CLı kullanılarak Kubernetes kümesine uygulanmalıdır:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-207">The configuration must be applied to the Kubernetes cluster using the Kubernetes CLI:</span></span>

```console
kubectl apply -f tracing-config.yaml
```

##### <a name="install-the-zipkin-server"></a><span data-ttu-id="5e1e8-208">Zipkaya sunucusu 'nı yükler</span><span class="sxs-lookup"><span data-stu-id="5e1e8-208">Install the Zipkin server</span></span>

<span data-ttu-id="5e1e8-209">Şirket içinde iç barındırılan modda Davpr yüklenirken, bir sıkıştırma sunucusu otomatik olarak yüklenir ve izleme, `$HOME/.dapr/config.yaml` veya Windows üzerinde bulunan varsayılan yapılandırma dosyasında etkinleştirilir `%USERPROFILE%\.dapr\config.yaml` .</span><span class="sxs-lookup"><span data-stu-id="5e1e8-209">When installing Dapr in self-hosted mode, a Zipkin server is automatically installed and tracing is enabled in the default configuration file located in `$HOME/.dapr/config.yaml` or `%USERPROFILE%\.dapr\config.yaml` on Windows.</span></span>

<span data-ttu-id="5e1e8-210">Aynı halde bir Kubernetes kümesine düğüm yüklerken, varsayılan olarak Zipbağı eklenmez.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-210">When installing Dapr on a Kubernetes cluster though, Zipkin isn't added by default.</span></span> <span data-ttu-id="5e1e8-211">Adlı aşağıdaki Kubernetes bildirim dosyası `zipkin.yaml` , kümeye standart bir Zipkaya sunucusu dağıtır:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-211">The following Kubernetes manifest file named `zipkin.yaml`, deploys a standard Zipkin server to the cluster:</span></span>

```yaml
kind: Deployment
apiVersion: apps/v1
metadata:
  name: zipkin
  namespace: eshop
  labels:
    service: zipkin
spec:
  replicas: 1
  selector:
    matchLabels:
      service: zipkin
  template:
    metadata:
      labels:
        service: zipkin
    spec:
      containers:
        - name: zipkin
          image: openzipkin/zipkin-slim
          imagePullPolicy: IfNotPresent
          ports:
            - name: http
              containerPort: 9411
              protocol: TCP

---

kind: Service
apiVersion: v1
metadata:
  name: zipkin
  namespace: eshop
  labels:
    service: zipkin
spec:
  type: NodePort
  ports:
    - port: 9411
      targetPort: 9411
      nodePort: 32411
      protocol: TCP
      name: zipkin
  selector:
    service: zipkin

```

<span data-ttu-id="5e1e8-212">Dağıtım standart `openzipkin/zipkin-slim` kapsayıcı görüntüsünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-212">The deployment uses the standard `openzipkin/zipkin-slim` container image.</span></span> <span data-ttu-id="5e1e8-213">Sıkıştırma hizmeti, bağlantı noktasındaki Telemetriyi görüntülemek için kullanabileceğiniz, Web ön ucu 'nı kullanıma sunar `32411` .</span><span class="sxs-lookup"><span data-stu-id="5e1e8-213">The Zipkin service exposes the Zipkin web front end, which you can use to view the telemetry on port `32411`.</span></span> <span data-ttu-id="5e1e8-214">Kubernetes CLı ' yı kullanarak Kubernetes kümesine Zipbir bildirim dosyasını uygulayın ve Zipkabağı sunucusunu dağıtın:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-214">Use the Kubernetes CLI to apply the Zipkin manifest file to the Kubernetes cluster and deploy the Zipkin server:</span></span>

```console
kubectl apply -f zipkin.yaml
```

##### <a name="configure-the-services-to-use-the-tracing-configuration"></a><span data-ttu-id="5e1e8-215">İzleme yapılandırmasını kullanmak için Hizmetleri yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5e1e8-215">Configure the services to use the tracing configuration</span></span>

<span data-ttu-id="5e1e8-216">Artık her şey telemetri yayımlamaya başlamak için doğru şekilde ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-216">Now everything is set up correctly to start publishing telemetry.</span></span> <span data-ttu-id="5e1e8-217">Uygulamanın bir parçası olarak dağıtılan her bir Davpr sepet, başlatıldığında telemetri yayma konusunda talimat verilmelidir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-217">Every Dapr sidecar that is deployed as part of the application must be instructed to emit telemetry when started.</span></span> <span data-ttu-id="5e1e8-218">Bunu yapmak için, her bir `dapr.io/config` hizmetin dağıtımına, yapılandırmaya başvuran bir ek açıklama ekleyin `tracing-config` .</span><span class="sxs-lookup"><span data-stu-id="5e1e8-218">To do that, add a `dapr.io/config` annotation that references the `tracing-config` configuration to the deployment of each service.</span></span> <span data-ttu-id="5e1e8-219">Aşağıda, ek açıklamayı içeren bir eShop sıralaması API hizmetinin bildirim dosyasına bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-219">Here's an example of the eShop ordering API service's manifest file containing the annotation:</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ordering-api
  namespace: eshop
  labels:
    app: eshop
spec:
  replicas: 1
  selector:
    matchLabels:
      app: eshop
  template:
    metadata:
      labels:
        app: simulation
      annotations:
        dapr.io/enabled: "true"
        dapr.io/app-id: "ordering-api"
        dapr.io/config: "tracing-config"
    spec:
      containers:
      - name: simulation
        image: eshop/ordering.api:linux-latest
```

##### <a name="inspect-the-telemetry-in-zipkin"></a><span data-ttu-id="5e1e8-220">Kabağı 'nda Telemetriyi inceleyin</span><span class="sxs-lookup"><span data-stu-id="5e1e8-220">Inspect the telemetry in Zipkin</span></span>

<span data-ttu-id="5e1e8-221">Uygulama başlatıldıktan sonra, Davpr sideckileri, Telemetriyi bir sunucuya yayIr.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-221">Once the application is started, the Dapr sidecars will emit telemetry to the Zipkin server.</span></span> <span data-ttu-id="5e1e8-222">Bu Telemetriyi incelemek için bir Web tarayıcısının üzerine gelin <http://localhost:32411> .</span><span class="sxs-lookup"><span data-stu-id="5e1e8-222">To inspect this telemetry, point a web-browser to <http://localhost:32411>.</span></span> <span data-ttu-id="5e1e8-223">Bir Web ön ucu görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-223">You'll see the Zipkin web front end:</span></span>

![Ferkabağı başlangıç sayfası](media/observability/zipkin.png)

<span data-ttu-id="5e1e8-225">*Izleme bul* sekmesinde, izlemeleri sorgulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-225">On the *Find a trace* tab, you can query traces.</span></span> <span data-ttu-id="5e1e8-226">*Sorgu Çalıştır* düğmesine herhangi bir kısıtlama belirtmeden basmak, alınan tüm *izlemeleri* gösterir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-226">Pressing the *RUN QUERY* button without specifying any restrictions will show all the ingested *traces*:</span></span>

![İzlemelerin listesi](media/observability/zipkin-traces-overview.png)

<span data-ttu-id="5e1e8-228">Belirli bir izlemenin yanındaki *göster* düğmesine tıkladığınızda, bu izlemenin ayrıntıları gösterilir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-228">Clicking the *SHOW* button next to a specific trace, will show the details of that trace:</span></span>

![İzlemenin ayrıntıları](media/observability/zipkin-trace-details.png)

<span data-ttu-id="5e1e8-230">Ayrıntılar sayfasındaki her öğe, seçili izlemenin parçası olan bir isteği temsil eden bir yaydır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-230">Each item on the details page, is a span that represents a request that is part of the selected trace.</span></span>

##### <a name="inspect-the-dependencies-between-services"></a><span data-ttu-id="5e1e8-231">Hizmetler arasındaki bağımlılıkları inceleyin</span><span class="sxs-lookup"><span data-stu-id="5e1e8-231">Inspect the dependencies between services</span></span>

<span data-ttu-id="5e1e8-232">NPR 'ler arasındaki trafiği işlerken, Ferkabağı hizmetler arasındaki bağımlılıkları tespit etmek için izleme bilgilerini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-232">Because Dapr sidecars handle traffic between services, Zipkin can use the trace information to determine the dependencies between the services.</span></span> <span data-ttu-id="5e1e8-233">Bunu işlem içinde görmek için, Ferkabağı Web sayfasındaki *Bağımlılıklar* sekmesine gidin ve Büyüteç Camı ile düğmeyi seçin.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-233">To see it in action, go to the *Dependencies* tab on the Zipkin web page and select the button with the magnifying glass.</span></span> <span data-ttu-id="5e1e8-234">Kabağı, hizmetlere ve bunların bağımlılıklarına genel bir bakış gösterecektir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-234">Zipkin will show an overview of the services and their dependencies:</span></span>

![Ferkata bir bağımlılık grafiği](media/observability/zipkin-dependencies.png)

<span data-ttu-id="5e1e8-236">Hizmetler arasındaki satırlardaki animasyonlu noktalar istekleri temsil eder ve kaynaktan hedefe taşınır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-236">The animated dots on the lines between the services represent requests and move from source to destination.</span></span> <span data-ttu-id="5e1e8-237">Kırmızı noktalar başarısız bir isteği gösterir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-237">Red dots indicate a failed request.</span></span>

#### <a name="use-a-jaeger-or-new-relic-monitoring-back-end"></a><span data-ttu-id="5e1e8-238">Bir Jaeger veya yeni bir relik izleme arka ucu kullanın</span><span class="sxs-lookup"><span data-stu-id="5e1e8-238">Use a Jaeger or New Relic monitoring back end</span></span>

<span data-ttu-id="5e1e8-239">Aynı zamanda, diğer izleme arka uç yazılımları de Zipkabağı biçimini kullanarak Telemetriyi destekler.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-239">Beyond Zipkin itself, other monitoring back-end software also supports ingesting telemetry using the Zipkin format.</span></span> <span data-ttu-id="5e1e8-240">[Jaeger](https://www.jaegertracing.io/) , Uber teknolojileri tarafından oluşturulan açık kaynaklı bir izleme sistemidir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-240">[Jaeger](https://www.jaegertracing.io/) is an open source tracing system created by Uber Technologies.</span></span> <span data-ttu-id="5e1e8-241">Dağıtılmış hizmetler arasındaki işlemleri izlemek ve karmaşık mikro hizmet ortamlarının sorunlarını gidermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-241">It's used to trace transactions between distributed services and troubleshoot complex microservices environments.</span></span> <span data-ttu-id="5e1e8-242">[New relik](https://newrelic.com/) , bir *tam yığın* Observability platformudur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-242">[New Relic](https://newrelic.com/) is a *full-stack* observability platform.</span></span> <span data-ttu-id="5e1e8-243">Bir dağıtılmış uygulamadaki ilgili verileri, sisteminizin tamamına yönelik bir resim ile bağlantılandırır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-243">It links relevant data from a distributed application to provide a complete picture of your system.</span></span> <span data-ttu-id="5e1e8-244">Denemek için, `endpointAddress` DAPR yapılandırma dosyasında bir Caeger ya da yeni relik sunucusu için bir işaret noktası belirtin.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-244">To try them out, specify an `endpointAddress` pointing to either a Jaeger or New Relic server in the Dapr configuration file.</span></span> <span data-ttu-id="5e1e8-245">Aşağıda, DAPR 'yi bir Caeger sunucusuna telemetri gönderecek şekilde yapılandıran bir yapılandırma dosyası örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-245">Here's an example of a configuration file that configures Dapr to send telemetry to a Jaeger server.</span></span> <span data-ttu-id="5e1e8-246">Caeger URL 'SI, Ferkabağı URL 'siyle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-246">The URL for Jaeger is identical to the URL for the Zipkin.</span></span> <span data-ttu-id="5e1e8-247">Tek fark sunucunun çalıştığı bağlantı noktasıdır:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-247">The only difference is the port on which the server runs:</span></span>

 ```yaml
 apiVersion: dapr.io/v1alpha1
 kind: Configuration
 metadata:
   name: tracing-config
   namespace: default
 spec:
   tracing:
     samplingRate: "1"
     zipkin:
       endpointAddress: "http://localhost:9415/api/v2/spans"
 ```

<span data-ttu-id="5e1e8-248">Yeni yeniden denemek için yeni relik API 'sinin uç noktasını belirtin.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-248">To try out New Relic, specify the endpoint of the New Relic API.</span></span> <span data-ttu-id="5e1e8-249">Yeni relik için yapılandırma dosyasına bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-249">Here's an example of a configuration file for New Relic:</span></span>

 ```yaml
apiVersion: dapr.io/v1alpha1
 kind: Configuration
 metadata:
   name: tracing-config
   namespace: default
 spec:
   tracing:
     samplingRate: "1"
     zipkin:
       endpointAddress: "https://trace-api.newrelic.com/trace/v1?Api-Key=<NR-API-KEY>&Data-Format=zipkin&Data-Format-Version=2"
 ```

<span data-ttu-id="5e1e8-250">Kullanım hakkında daha fazla bilgi için, Jaeger ve yeni relik Web sitelerine göz atın.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-250">Check out the Jaeger and New Relic websites for more information on how to use them.</span></span>

### <a name="metrics"></a><span data-ttu-id="5e1e8-251">Ölçümler</span><span class="sxs-lookup"><span data-stu-id="5e1e8-251">Metrics</span></span>

<span data-ttu-id="5e1e8-252">Ölçümler, performans ve kaynak tüketimine ilişkin öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-252">Metrics provide insight into performance and resource consumption.</span></span> <span data-ttu-id="5e1e8-253">Aynı şekilde, Davpr, sistem ve çalışma zamanı ölçümlerinin geniş bir koleksiyonunu yayar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-253">Under the hood, Dapr emits a wide collection of system and runtime metrics.</span></span> <span data-ttu-id="5e1e8-254">Davpr, ölçüm standardı olarak [Prometheus](https://prometheus.io/) kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-254">Dapr uses [Prometheus](https://prometheus.io/) as a metric standard.</span></span> <span data-ttu-id="5e1e8-255">Davpr sıdecars ve sistem hizmetleri, bağlantı noktasında ölçüm uç noktasını kullanıma sunar `9090` .</span><span class="sxs-lookup"><span data-stu-id="5e1e8-255">Dapr sidecars and system services, expose a metrics endpoint on port `9090`.</span></span> <span data-ttu-id="5e1e8-256">Bir *Prometheus atık* , bu uç noktayı, ölçümleri toplamak için önceden tanımlanmış bir aralıkta çağırır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-256">A *Prometheus scraper* calls this endpoint at a predefined interval to collect metrics.</span></span> <span data-ttu-id="5e1e8-257">Atık oluşturma, ölçüm değerlerini bir izleme arka ucuna gönderir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-257">The scraper sends metric values to a monitoring back end.</span></span> <span data-ttu-id="5e1e8-258">Şekil 9-4, scraping işlemini gösterir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-258">Figure 9-4 shows the scraping process:</span></span>

![Scraping Prometheus ölçümleri](media/observability/prometheus-scraper.png)

<span data-ttu-id="5e1e8-260">**Şekil 9-4**.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-260">**Figure 9-4**.</span></span> <span data-ttu-id="5e1e8-261">Scraping Prometheus ölçümleri.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-261">Scraping Prometheus metrics.</span></span>

<span data-ttu-id="5e1e8-262">Yukarıdaki şekilde, her sepet ve sistem hizmeti, 9090 bağlantı noktasını dinleyen bir ölçüm uç noktası sunar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-262">In the above figure, each sidecar and system service exposes a metric endpoint that listens on port 9090.</span></span> <span data-ttu-id="5e1e8-263">Prometheus ölçümleri, her bir uç noktadan ölçümleri yakalar ve bilgileri izleme arka ucuna yayımlamış.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-263">The Prometheus Metrics Scrapper captures metrics from each endpoint and published the information to the monitoring back end.</span></span>  

#### <a name="service-discovery"></a><span data-ttu-id="5e1e8-264">Hizmet bulma</span><span class="sxs-lookup"><span data-stu-id="5e1e8-264">Service discovery</span></span>

<span data-ttu-id="5e1e8-265">Ölçümlerin, ölçümlerin nerede toplanacağını öğrendiğinde merak edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-265">You might wonder how the metrics scraper knows where to collect metrics.</span></span> <span data-ttu-id="5e1e8-266">Prometheus, hedef dağıtım ortamlarında yerleşik olarak bulunan keşif mekanizmalarıyla tümleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-266">Prometheus can integrate with discovery mechanisms built into target deployment environments.</span></span> <span data-ttu-id="5e1e8-267">Örneğin, Kubernetes 'te çalışırken Prometheus, ortamda çalışan tüm kullanılabilir Kubernetes kaynaklarını bulmak için Kubernetes API 'siyle tümleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-267">For example, when running in Kubernetes, Prometheus can integrate with the Kubernetes API to find all available Kubernetes resources running in the environment.</span></span>

#### <a name="metrics-list"></a><span data-ttu-id="5e1e8-268">Ölçüm listesi</span><span class="sxs-lookup"><span data-stu-id="5e1e8-268">Metrics list</span></span>

<span data-ttu-id="5e1e8-269">Davpr, Davpr sistem hizmetleri ve çalışma zamanı için büyük bir ölçüm kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-269">Dapr generates a large set of metrics for Dapr system services and its runtime.</span></span> <span data-ttu-id="5e1e8-270">Bazı örnekler:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-270">Some examples include:</span></span>

| <span data-ttu-id="5e1e8-271">Metric</span><span class="sxs-lookup"><span data-stu-id="5e1e8-271">Metric</span></span>                                         | <span data-ttu-id="5e1e8-272">Kaynak</span><span class="sxs-lookup"><span data-stu-id="5e1e8-272">Source</span></span> | <span data-ttu-id="5e1e8-273">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e1e8-273">Description</span></span>                                                  |
| ---------------------------------------------- | :----: | ------------------------------------------------------------ |
| <span data-ttu-id="5e1e8-274">dapr_operator_service_created_total</span><span class="sxs-lookup"><span data-stu-id="5e1e8-274">dapr_operator_service_created_total</span></span>            | <span data-ttu-id="5e1e8-275">Sistem</span><span class="sxs-lookup"><span data-stu-id="5e1e8-275">System</span></span> | <span data-ttu-id="5e1e8-276">DAPR Işleç hizmeti tarafından oluşturulan toplam DAPR Hizmetleri sayısıdır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-276">The total number of Dapr services created by the Dapr Operator service.</span></span> |
| <span data-ttu-id="5e1e8-277">dapr_injector_sidecar_injection/requests_total</span><span class="sxs-lookup"><span data-stu-id="5e1e8-277">dapr_injector_sidecar_injection/requests_total</span></span> | <span data-ttu-id="5e1e8-278">Sistem</span><span class="sxs-lookup"><span data-stu-id="5e1e8-278">System</span></span> | <span data-ttu-id="5e1e8-279">Davpr Sidecar-Injector hizmeti tarafından alınan sepet ekleme isteklerinin toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-279">The total number of sidecar injection requests received by the Dapr Sidecar-Injector service.</span></span> |
| <span data-ttu-id="5e1e8-280">dapr_placement_runtimes_total</span><span class="sxs-lookup"><span data-stu-id="5e1e8-280">dapr_placement_runtimes_total</span></span>                  | <span data-ttu-id="5e1e8-281">Sistem</span><span class="sxs-lookup"><span data-stu-id="5e1e8-281">System</span></span> | <span data-ttu-id="5e1e8-282">Davpr yerleştirme hizmetine bildirilen toplam ana bilgisayar sayısı.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-282">The total number of hosts reported to the Dapr Placement service.</span></span> |
| <span data-ttu-id="5e1e8-283">dapr_sentry_cert_sign_request_received_total</span><span class="sxs-lookup"><span data-stu-id="5e1e8-283">dapr_sentry_cert_sign_request_received_total</span></span>   | <span data-ttu-id="5e1e8-284">Sistem</span><span class="sxs-lookup"><span data-stu-id="5e1e8-284">System</span></span> | <span data-ttu-id="5e1e8-285">Davpr Sentry hizmeti tarafından alınan sertifika imzalama isteği (CRSs) sayısı.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-285">The number of certificate signing requests (CRSs) received by the Dapr Sentry service.</span></span> |
| <span data-ttu-id="5e1e8-286">dapr_runtime_component_loaded</span><span class="sxs-lookup"><span data-stu-id="5e1e8-286">dapr_runtime_component_loaded</span></span>      | <span data-ttu-id="5e1e8-287">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5e1e8-287">Runtime</span></span> | <span data-ttu-id="5e1e8-288">Başarıyla yüklenen Davpr bileşenleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-288">The number of successfully loaded Dapr components.</span></span>           |
| <span data-ttu-id="5e1e8-289">dapr_grpc_io_server_completed_rpcs</span><span class="sxs-lookup"><span data-stu-id="5e1e8-289">dapr_grpc_io_server_completed_rpcs</span></span> | <span data-ttu-id="5e1e8-290">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5e1e8-290">Runtime</span></span> | <span data-ttu-id="5e1e8-291">Yönteme ve duruma göre gRPC çağrılarının sayısı.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-291">Count of gRPC calls by method and status.</span></span>                    |
| <span data-ttu-id="5e1e8-292">dapr_http_server_request_count</span><span class="sxs-lookup"><span data-stu-id="5e1e8-292">dapr_http_server_request_count</span></span>     | <span data-ttu-id="5e1e8-293">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5e1e8-293">Runtime</span></span> | <span data-ttu-id="5e1e8-294">HTTP sunucusunda başlatılan HTTP isteklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-294">Number of HTTP requests started in an HTTP server.</span></span>           |
| <span data-ttu-id="5e1e8-295">dapr_http/Client/sent_bytes</span><span class="sxs-lookup"><span data-stu-id="5e1e8-295">dapr_http/client/sent_bytes</span></span>        | <span data-ttu-id="5e1e8-296">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5e1e8-296">Runtime</span></span> | <span data-ttu-id="5e1e8-297">Bir HTTP istemcisi tarafından istek gövdesinde (üstbilgiler dahil değil) gönderilen toplam bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-297">Total bytes sent in request body (not including headers) by an HTTP client.</span></span> |

<span data-ttu-id="5e1e8-298">Kullanılabilir ölçümler hakkında daha fazla bilgi için bkz. [Davpr ölçümleri belgeleri](https://docs.dapr.io/operations/monitoring/metrics/).</span><span class="sxs-lookup"><span data-stu-id="5e1e8-298">For more information on available metrics, see the [Dapr metrics documentation](https://docs.dapr.io/operations/monitoring/metrics/).</span></span>

#### <a name="configure-dapr-metrics"></a><span data-ttu-id="5e1e8-299">Davpr ölçümlerini yapılandırma</span><span class="sxs-lookup"><span data-stu-id="5e1e8-299">Configure Dapr metrics</span></span>

<span data-ttu-id="5e1e8-300">Çalışma zamanında, `--enable-metrics=false` bağımsız değişkenini Davpr komutuna ekleyerek ölçüm toplama uç noktasını devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-300">At runtime, you can disable the metrics collection endpoint by including the `--enable-metrics=false` argument in the Dapr command.</span></span> <span data-ttu-id="5e1e8-301">Ayrıca, uç nokta için varsayılan bağlantı noktasını `--metrics-port 9090` bağımsız değişkenle de değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-301">Or, you can also change the default port for the endpoint with the `--metrics-port 9090` argument.</span></span>

<span data-ttu-id="5e1e8-302">Ayrıca, çalışma zamanı ölçümleri toplamasını statik olarak etkinleştirmek veya devre dışı bırakmak için bir Davpr yapılandırma dosyası da kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-302">You can also use a Dapr configuration file to statically enable or disable runtime metrics collection:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: dapr-config
  namespace: eshop
spec:
  tracing:
    samplingRate: "1"
  metric:
    enabled: false
```

#### <a name="visualize-dapr-metrics"></a><span data-ttu-id="5e1e8-303">Davpr ölçümlerini görselleştirin</span><span class="sxs-lookup"><span data-stu-id="5e1e8-303">Visualize Dapr metrics</span></span>

<span data-ttu-id="5e1e8-304">Prometheus atık oluşturma ve ölçümleri izleme arka ucuna yayımlama konusunda, ham verileri nasıl anladınız?</span><span class="sxs-lookup"><span data-stu-id="5e1e8-304">With the Prometheus scraper collecting and publishing metrics into the monitoring back end, how do you make sense of the raw data?</span></span> <span data-ttu-id="5e1e8-305">Ölçümleri çözümlemek için popüler bir görselleştirme aracı [Grafana](https://grafana.com/grafana/).</span><span class="sxs-lookup"><span data-stu-id="5e1e8-305">A popular visualization tool for analyzing metrics is [Grafana](https://grafana.com/grafana/).</span></span> <span data-ttu-id="5e1e8-306">Grafana ile, kullanılabilir ölçülerden panolar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-306">With Grafana, you can create dashboards from the available metrics.</span></span> <span data-ttu-id="5e1e8-307">Aşağıda, Davpr sistem hizmetleri ölçümlerini görüntüleyen bir panoya örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-307">Here's an example of a dashboard displaying Dapr system services metrics:</span></span>

![Grafana, Davpr sistem hizmetleri ölçümlerini görüntüleyen Pano](media/observability/grafana-sample.png)

<span data-ttu-id="5e1e8-309">Davpr belgeleri, [Prometheus ve Grafana yükleme öğreticisini](https://docs.dapr.io/operations/monitoring/metrics/grafana/)içerir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-309">The Dapr documentation includes a [tutorial for installing Prometheus and Grafana](https://docs.dapr.io/operations/monitoring/metrics/grafana/).</span></span>

### <a name="logging"></a><span data-ttu-id="5e1e8-310">Günlüğe Kaydetme</span><span class="sxs-lookup"><span data-stu-id="5e1e8-310">Logging</span></span>

<span data-ttu-id="5e1e8-311">Günlüğe kaydetme, çalışma zamanında bir hizmette neler olduğunu gösteren öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-311">Logging provides insight into what is happening with a service at runtime.</span></span> <span data-ttu-id="5e1e8-312">Bir uygulamayı çalıştırırken, Davpr sıdecars ve Davpr sistem hizmetlerinden günlük girdilerini otomatik olarak yayar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-312">When running an application, Dapr automatically emits log entries from Dapr sidecars and Dapr system services.</span></span> <span data-ttu-id="5e1e8-313">Ancak, uygulama kodunuzda belgelenmiş günlüğe kaydetme girdileri otomatik olarak dahil **edilmez** .</span><span class="sxs-lookup"><span data-stu-id="5e1e8-313">However, logging entries instrumented in your application code **aren't** automatically included.</span></span> <span data-ttu-id="5e1e8-314">Uygulama kodundan günlük yayma yapmak için, [.net Için Opentelemetri SDK](https://opentelemetry.io/docs/net/)gibi belırlı bir SDK 'yı içeri aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-314">To emit logging from application code, you can import a specific SDK like [OpenTelemetry SDK for .NET](https://opentelemetry.io/docs/net/).</span></span> <span data-ttu-id="5e1e8-315">Günlüğe kaydetme uygulama kodu, bu bölümün ilerleyen kısımlarında, *Davpr .NET SDK kullanılarak* bölümünde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-315">Logging application code is covered later in this chapter in the section *Using the Dapr .NET SDK*.</span></span>  

#### <a name="log-entry-structure"></a><span data-ttu-id="5e1e8-316">Günlük girdisi yapısı</span><span class="sxs-lookup"><span data-stu-id="5e1e8-316">Log entry structure</span></span>

<span data-ttu-id="5e1e8-317">Davpr yapılandırılmış günlüğe kaydetme yayar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-317">Dapr emits structured logging.</span></span> <span data-ttu-id="5e1e8-318">Her günlük girdisi aşağıdaki biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-318">Each log entry has the following format:</span></span>

| <span data-ttu-id="5e1e8-319">Alan</span><span class="sxs-lookup"><span data-stu-id="5e1e8-319">Field</span></span>    | <span data-ttu-id="5e1e8-320">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e1e8-320">Description</span></span>                                          | <span data-ttu-id="5e1e8-321">Örnek</span><span class="sxs-lookup"><span data-stu-id="5e1e8-321">Example</span></span>                             |
| -------- | ---------------------------------------------------- | ----------------------------------- |
| <span data-ttu-id="5e1e8-322">time</span><span class="sxs-lookup"><span data-stu-id="5e1e8-322">time</span></span>     | <span data-ttu-id="5e1e8-323">ISO8601 biçimli zaman damgası</span><span class="sxs-lookup"><span data-stu-id="5e1e8-323">ISO8601 formatted timestamp</span></span>                          | `2021-01-10T14:19:31.000Z`          |
| <span data-ttu-id="5e1e8-324">düzey</span><span class="sxs-lookup"><span data-stu-id="5e1e8-324">level</span></span>    | <span data-ttu-id="5e1e8-325">Girişin düzeyi ( `debug` \| `info` \| `warn` \| `error` )  </span><span class="sxs-lookup"><span data-stu-id="5e1e8-325">Level of the entry (`debug` \| `info` \| `warn`  \| `error`)</span></span> | `info`                              |
| <span data-ttu-id="5e1e8-326">tür</span><span class="sxs-lookup"><span data-stu-id="5e1e8-326">type</span></span>     | <span data-ttu-id="5e1e8-327">Günlük Türü</span><span class="sxs-lookup"><span data-stu-id="5e1e8-327">Log Type</span></span>                                             | `log`                               |
| <span data-ttu-id="5e1e8-328">msg</span><span class="sxs-lookup"><span data-stu-id="5e1e8-328">msg</span></span>      | <span data-ttu-id="5e1e8-329">Günlük Iletisi</span><span class="sxs-lookup"><span data-stu-id="5e1e8-329">Log Message</span></span>                                          | `metrics server started on :62408/` |
| <span data-ttu-id="5e1e8-330">scope</span><span class="sxs-lookup"><span data-stu-id="5e1e8-330">scope</span></span>    | <span data-ttu-id="5e1e8-331">Günlüğe kaydetme kapsamı</span><span class="sxs-lookup"><span data-stu-id="5e1e8-331">Logging Scope</span></span>                                        | `dapr.runtime`                      |
| <span data-ttu-id="5e1e8-332">örnek</span><span class="sxs-lookup"><span data-stu-id="5e1e8-332">instance</span></span> | <span data-ttu-id="5e1e8-333">Bapr 'nin çalıştığı ana bilgisayar adı</span><span class="sxs-lookup"><span data-stu-id="5e1e8-333">Hostname where Dapr runs</span></span>                             | <span data-ttu-id="5e1e8-334">TSTSRV01</span><span class="sxs-lookup"><span data-stu-id="5e1e8-334">TSTSRV01</span></span>                            |
| <span data-ttu-id="5e1e8-335">app_id</span><span class="sxs-lookup"><span data-stu-id="5e1e8-335">app_id</span></span>   | <span data-ttu-id="5e1e8-336">Davpr uygulama KIMLIĞI</span><span class="sxs-lookup"><span data-stu-id="5e1e8-336">Dapr App ID</span></span>                                          | <span data-ttu-id="5e1e8-337">sıralama-API</span><span class="sxs-lookup"><span data-stu-id="5e1e8-337">ordering-api</span></span>                        |
| <span data-ttu-id="5e1e8-338">ver</span><span class="sxs-lookup"><span data-stu-id="5e1e8-338">ver</span></span>      | <span data-ttu-id="5e1e8-339">Davpr çalışma zamanı sürümü</span><span class="sxs-lookup"><span data-stu-id="5e1e8-339">Dapr Runtime Version</span></span>                                 | <span data-ttu-id="5e1e8-340">`1.0.0`-RC. 2</span><span class="sxs-lookup"><span data-stu-id="5e1e8-340">`1.0.0`-rc.2</span></span>                        |

<span data-ttu-id="5e1e8-341">Sorun giderme senaryosunda günlüğe kaydetme girişlerinde arama yaparken, `time` ve `level` alanları özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-341">When searching through logging entries in a troubleshooting scenario, the `time` and `level` fields are especially helpful.</span></span> <span data-ttu-id="5e1e8-342">Zaman alanı, belirli zaman aralıklarını belirleyebilmeniz için günlük girdilerini sıralar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-342">The time field orders log entries so that you can pinpoint specific time periods.</span></span> <span data-ttu-id="5e1e8-343">Sorun giderirken, *hata ayıklama düzeyindeki* günlük girişleri kodun davranışı hakkında daha fazla bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-343">When troubleshooting, log entries at the *debug level* provide more information on the behavior of the code.</span></span>

#### <a name="plain-text-versus-json-format"></a><span data-ttu-id="5e1e8-344">Düz metin ve JSON biçimi</span><span class="sxs-lookup"><span data-stu-id="5e1e8-344">Plain text versus JSON format</span></span>

<span data-ttu-id="5e1e8-345">Varsayılan olarak, Davpr yapılandırılmış günlük ' i düz metin biçiminde yayar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-345">By default, Dapr emits structured logging in plain-text format.</span></span> <span data-ttu-id="5e1e8-346">Her günlük girdisi, anahtar/değer çiftlerini içeren bir dize olarak biçimlendirilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-346">Every log entry is formatted as a string containing key/value pairs.</span></span> <span data-ttu-id="5e1e8-347">Düz metinde günlüğe kaydetme örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-347">Here's an example of logging in plain text:</span></span>

```text
== DAPR == time="2021-01-12T16:11:39.4669323+01:00" level=info msg="starting Dapr Runtime -- version 1.0.0-rc.2 -- commit 196483d" app_id=ordering-api instance=TSTSRV03 scope=dapr.runtime type=log ver=1.0.0-rc.2
== DAPR == time="2021-01-12T16:11:39.467933+01:00" level=info msg="log level set to: info" app_id=ordering-api instance=TSTSRV03 scope=dapr.runtime type=log ver=1.0.0-rc.2
== DAPR == time="2021-01-12T16:11:39.467933+01:00" level=info msg="metrics server started on :62408/" app_id=ordering-api instance=TSTSRV03 scope=dapr.metrics type=log ver=1.0.0-rc.2
```

<span data-ttu-id="5e1e8-348">Basit olsa da, bu biçimin ayrıştırılması zordur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-348">While simple, this format is difficult to parse.</span></span> <span data-ttu-id="5e1e8-349">Günlük girişlerini bir izleme aracıyla görüntülüyorsanız, JSON biçimli günlüğe kaydetmeyi etkinleştirmek isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-349">If viewing log entries with a monitoring tool, you'll want to enable JSON formatted logging.</span></span> <span data-ttu-id="5e1e8-350">JSON girdileriyle, bir izleme aracı tek tek alanları dizinedebilir ve sorgulayabilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-350">With JSON entries, a monitoring tool can index and query individual fields.</span></span> <span data-ttu-id="5e1e8-351">JSON biçiminde aynı günlük girdileri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-351">Here's the same log entries in JSON format:</span></span>

```json
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "starting Dapr Runtime -- version 1.0.0-rc.2 -- commit 196483d", "scope": "dapr.runtime", "time": "2021-01-12T16:11:39.4669323+01:00", "type": "log", "ver": "1.0.0-rc.2"}
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "log level set to: info", "scope": "dapr.runtime", "type": "log", "time": "2021-01-12T16:11:39.467933+01:00", "ver": "1.0.0-rc.2"}
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "metrics server started on :62408/", "scope": "dapr.metrics", "type": "log", "time": "2021-01-12T16:11:39.467933+01:00", "ver": "1.0.0-rc.2"}
```

<span data-ttu-id="5e1e8-352">JSON biçimlendirmesini etkinleştirmek için, her bir Davpr sidecar 'yi yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-352">To enable JSON formatting, you need to configure each Dapr sidecar.</span></span> <span data-ttu-id="5e1e8-353">Kendi kendine barındırılan modda, `--log-as-json` komut satırında bayrağını belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-353">In self-hosted mode, you can specify the flag `--log-as-json` on the command line:</span></span>

```console
dapr run --app-id ordering-api --log-level info --log-as-json dotnet run
```

<span data-ttu-id="5e1e8-354">Kubernetes 'de, `dapr.io/log-as-json` uygulamanın her dağıtımına bir ek açıklama ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-354">In Kubernetes, you can add a `dapr.io/log-as-json` annotation to each deployment for the application:</span></span>

```yaml
annotations:
   dapr.io/enabled: "true"
   dapr.io/app-id: "ordering-api"
   dapr.io/app-port: "80"
   dapr.io/config: "dapr-config"
   dapr.io/log-as-json: "true"
```

<span data-ttu-id="5e1e8-355">Helk kullanarak bir Kubernetes kümesinde Davpr 'yi yüklediğinizde, tüm Davpr sistem hizmetleri için JSON biçimli günlüğe kaydetmeyi etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-355">When you install Dapr in a Kubernetes cluster using Helm, you can enable JSON formatted logging for all the Dapr system services:</span></span>

```console
helm repo add dapr https://dapr.github.io/helm-charts/
helm repo update
kubectl create namespace dapr-system
helm install dapr dapr/dapr --namespace dapr-system --set global.logAsJson=true
```

#### <a name="collect-logs"></a><span data-ttu-id="5e1e8-356">Günlük toplama</span><span class="sxs-lookup"><span data-stu-id="5e1e8-356">Collect logs</span></span>

<span data-ttu-id="5e1e8-357">Davpr tarafından yayılan Günlükler analiz için bir izleme arka ucuna dağıtılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-357">The logs emitted by Dapr can be fed into a monitoring back end for analysis.</span></span> <span data-ttu-id="5e1e8-358">Günlük Toplayıcısı, bir sistemden günlükleri toplayan ve bunları bir izleme arka ucuna gönderen bir bileşendir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-358">A log collector is a component that collects logs from a system and sends them to a monitoring back end.</span></span> <span data-ttu-id="5e1e8-359">Popüler bir günlük toplayıcısı [akıcı Entd](https://www.fluentd.org/).</span><span class="sxs-lookup"><span data-stu-id="5e1e8-359">A popular log collector is [Fluentd](https://www.fluentd.org/).</span></span> <span data-ttu-id="5e1e8-360">Bkz. [nasıl yapılır: vapr belgelerindeki Kubernetes 'te, akıcı Entd, elastik arama ve kibana ayarlama](https://docs.dapr.io/operations/monitoring/logging/fluentd/) .</span><span class="sxs-lookup"><span data-stu-id="5e1e8-360">Check out the [How-To: Set up Fluentd, Elastic search and Kibana in Kubernetes](https://docs.dapr.io/operations/monitoring/logging/fluentd/) in the Dapr documentation.</span></span> <span data-ttu-id="5e1e8-361">Bu makale, izleme arka ucu olarak Akıştoplayıcı ve [elk yığınını](https://www.elastic.co/elastic-stack) (elastik arama ve kibana) ayarlamaya yönelik yönergeler içerir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-361">This article contains instructions for setting up Fluentd as log collector and the [ELK Stack](https://www.elastic.co/elastic-stack) (Elastic Search and Kibana) as a monitoring back end.</span></span>

### <a name="health-status"></a><span data-ttu-id="5e1e8-362">Sistem durumu</span><span class="sxs-lookup"><span data-stu-id="5e1e8-362">Health status</span></span>

<span data-ttu-id="5e1e8-363">Bir hizmetin sistem durumu, kullanılabilirliği hakkında öngörüler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-363">The health status of a service provides insight into its availability.</span></span> <span data-ttu-id="5e1e8-364">Her bir Davpr dışarıdan yükleme, sepet durumunu anlamak için barındırma ortamı tarafından kullanılabilen bir sistem durumu API 'SI sunar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-364">Each Dapr sidecar exposes a health API that can be used by the hosting environment to determine the health of the sidecar.</span></span> <span data-ttu-id="5e1e8-365">API 'de bir işlem vardır:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-365">The API has one operation:</span></span>

```console
GET http://localhost:3500/v1.0/healthz
```

<span data-ttu-id="5e1e8-366">İşlem iki HTTP durum kodu döndürür:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-366">The operation returns two HTTP status codes:</span></span>

- <span data-ttu-id="5e1e8-367">204: sepet sağlıklı olduğunda</span><span class="sxs-lookup"><span data-stu-id="5e1e8-367">204: When the sidecar is healthy</span></span>
- <span data-ttu-id="5e1e8-368">500: sepet sağlıklı olmadığında</span><span class="sxs-lookup"><span data-stu-id="5e1e8-368">500: when the sidecar isn't healthy</span></span>

<span data-ttu-id="5e1e8-369">Şirket içinde barındırılan modda çalışırken sistem durumu API 'SI otomatik olarak çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-369">When running in self-hosted mode, the health API isn't automatically invoked.</span></span> <span data-ttu-id="5e1e8-370">API 'yi, uygulama kodundan veya bir sistem durumu izleme aracından çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-370">You can invoke the API though from application code or a health monitoring tool.</span></span>

<span data-ttu-id="5e1e8-371">Kubernetes 'te çalışırken, DAPR sidecar-Injector, Kubernetes 'i otomatik olarak *yapılandırır.* </span><span class="sxs-lookup"><span data-stu-id="5e1e8-371">When running in Kubernetes, the Dapr sidecar-injector automatically configures Kubernetes to use the health API for executing *liveness probes* and *readiness probes*.</span></span>

<span data-ttu-id="5e1e8-372">Kubernetes, bir kapsayıcının çalışır duruma getirme olup olmadığını anlamak için emize yönelik yoklamalar kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-372">Kubernetes uses liveness probes to determine whether a container is up and running.</span></span> <span data-ttu-id="5e1e8-373">Bir limek araştırması bir hata kodu döndürürse, Kubernetes kapsayıcının ölü olduğunu varsayar ve otomatik olarak yeniden başlatır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-373">If a liveness probe returns a failure code, Kubernetes will assume the container is dead and automatically restart it.</span></span> <span data-ttu-id="5e1e8-374">Bu özellik, uygulamanızın genel kullanılabilirliğini artırır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-374">This feature increases the overall availability of your application.</span></span>

<span data-ttu-id="5e1e8-375">Kubernetes, bir kapsayıcının trafiği kabul etmeye hazır olup olmadığını anlamak için hazırlık araştırmaları kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-375">Kubernetes uses readiness probes to determine whether a container is ready to start accepting traffic.</span></span> <span data-ttu-id="5e1e8-376">Tüm kapsayıcıları kullanılabilir olduğunda Pod, Ready olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-376">A pod is considered ready when all of its containers are ready.</span></span> <span data-ttu-id="5e1e8-377">Hazır olma durumu, bir Kubernetes hizmetinin bir yük dengeleme senaryosunda bir pod 'e trafik iletip yönlendirmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-377">Readiness determines whether a Kubernetes service can direct traffic to a pod in a load-balancing scenario.</span></span> <span data-ttu-id="5e1e8-378">Artık, yok, yük dengeleyiciden otomatik olarak kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-378">Pods that aren't ready are automatically removed from the load-balancer.</span></span>

<span data-ttu-id="5e1e8-379">Lileleme ve hazırlık araştırmaları birkaç yapılandırılabilir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-379">Liveness and readiness probes have several configurable parameters.</span></span> <span data-ttu-id="5e1e8-380">Her ikisi de Pod 'ın bildirim dosyasının kapsayıcı belirtimi bölümünde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-380">Both are configured in the container spec section of a pod's manifest file.</span></span> <span data-ttu-id="5e1e8-381">Varsayılan olarak, Davpr her sepet kapsayıcısı için aşağıdaki yapılandırmayı kullanır:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-381">By default, Dapr uses the following configuration for each sidecar container:</span></span>

```yaml
livenessProbe:
      httpGet:
        path: v1.0/healthz
        port: 3500
      initialDelaySeconds: 5
      periodSeconds: 10
      timeoutSeconds : 5
      failureThreshold : 3
readinessProbe:
      httpGet:
        path: v1.0/healthz
        port: 3500
      initialDelaySeconds: 5
      periodSeconds: 10
      timeoutSeconds : 5
      failureThreshold: 3
```

 <span data-ttu-id="5e1e8-382">Yoklamalar için aşağıdaki parametreler mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-382">The following parameters are available for the probes:</span></span>

- <span data-ttu-id="5e1e8-383">, `path` Davpr SAĞLıK API uç noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-383">The `path` specifies the Dapr health API endpoint.</span></span>
- <span data-ttu-id="5e1e8-384">, `port` Davpr sağlık API 'si bağlantı noktasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-384">The `port` specifies the Dapr health API port.</span></span>
- <span data-ttu-id="5e1e8-385">, `initialDelaySeconds` Kubernetes 'ın kapsayıcıyı ilk kez yoklamaya başlamadan önce bekleyeceği saniye sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-385">The `initialDelaySeconds`specifies the number of seconds Kubernetes will wait before it starts probing a container for the first time.</span></span>
- <span data-ttu-id="5e1e8-386">, `periodSeconds` Kubernetes 'lerin her bir yoklama arasında bekleyeceği saniye sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-386">The `periodSeconds` specifies the number of seconds Kubernetes will wait between each probe.</span></span>
- <span data-ttu-id="5e1e8-387">, `timeoutSeconds` Kubernetes 'in zaman aşımından önce API 'den Yanıt beklemesi gereken saniye sayısını belirtir. Zaman aşımı hata olarak yorumlanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-387">The `timeoutSeconds` specifies the number of seconds Kubernetes will wait on a response from the API before timing out. A timeout is interpreted as a failure.</span></span>
- <span data-ttu-id="5e1e8-388">`failureThreshold`Kapsayıcının etkin değil veya hazır değil olduğunu düşünmeden önce, Kubernetes 'nin kabul edeceği başarısız durum kodu sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-388">The `failureThreshold`specifies the number of failed status code Kubernetes will accept before considering the container not alive or not ready.</span></span>

### <a name="dapr-dashboard"></a><span data-ttu-id="5e1e8-389">Davpr panosu</span><span class="sxs-lookup"><span data-stu-id="5e1e8-389">Dapr dashboard</span></span>

<span data-ttu-id="5e1e8-390">Davpr, Davpr uygulamaları, bileşenleri ve yapılandırmalarında durum bilgilerini sunan bir pano sunar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-390">Dapr offers a dashboard that presents status information on Dapr applications, components, and configurations.</span></span> <span data-ttu-id="5e1e8-391">Panoyu 8080 numaralı bağlantı noktasında yerel makinede bir Web uygulaması olarak başlatmak için Davpr CLı kullanın:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-391">Use the Dapr CLI to start the dashboard as a web-application on the local machine on port 8080:</span></span>

```console
dapr dashboard
```

<span data-ttu-id="5e1e8-392">Kubernetes 'te çalışan Davpr uygulaması için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-392">For Dapr application running in Kubernetes, use the following command:</span></span>

```console
dapr dashboard -k
```

<span data-ttu-id="5e1e8-393">Pano, uygulamanızdaki bir Davpr dışarıdan arabası bulunduğu tüm hizmetlere genel bir bakış ile açılır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-393">The dashboard opens with an overview of all services in your application that have a Dapr sidecar.</span></span> <span data-ttu-id="5e1e8-394">Aşağıdaki ekran görüntüsünde, Kubernetes 'te çalışan Eshopondadpr uygulamasının Davpr panosu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-394">The following screenshot shows the Dapr dashboard for the eShopOnDapr application running in Kubernetes:</span></span>

![Davpr panosuna genel bakış sayfası](media/observability/dapr-dashboard-overview.png)

<span data-ttu-id="5e1e8-396">Bir Davpr uygulamasının sorunlarını giderirken, Davpr panosu önemli değildir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-396">The Dapr dashboard is invaluable when troubleshooting a Dapr application.</span></span> <span data-ttu-id="5e1e8-397">Bu, Davpr sıdecars ve sistem hizmetleri hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-397">It provides information about Dapr sidecars and system services.</span></span> <span data-ttu-id="5e1e8-398">Günlük girişleri dahil olmak üzere her bir hizmetin yapılandırmasında ayrıntıya gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-398">You can drill down into the configuration of each service, including the logging entries.</span></span>

<span data-ttu-id="5e1e8-399">Pano Ayrıca uygulamanızın yapılandırılmış bileşenlerini (ve yapılandırmalarını) gösterir:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-399">The dashboard also shows the configured components (and their configuration) for your application:</span></span>

![Davpr Pano bileşenleri sayfası](media/observability/dapr-dashboard-components.png)

<span data-ttu-id="5e1e8-401">Pano aracılığıyla kullanılabilecek büyük miktarda bilgi vardır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-401">There's a large amount of information available through the dashboard.</span></span> <span data-ttu-id="5e1e8-402">Bunu, bir Davpr uygulaması çalıştırarak ve panoya göz atarak keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-402">You can discover it by running a Dapr application and browsing the dashboard.</span></span> <span data-ttu-id="5e1e8-403">Başlamak için eşlik eden Eshopondadpr uygulamasını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-403">You can use the accompanying eShopOnDapr application to start.</span></span>

<span data-ttu-id="5e1e8-404">Davpr Pano komutları hakkında daha fazla bilgi için, davpr belgelerinden [davpr Pano CLI komut başvurusunu](https://docs.dapr.io/reference/cli/dapr-dashboard/) inceleyin.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-404">Check out the [Dapr dashboard CLI command reference](https://docs.dapr.io/reference/cli/dapr-dashboard/) in the Dapr docs for more information on the Dapr dashboard commands.</span></span>

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="5e1e8-405">Davpr .NET SDK 'sını kullanma</span><span class="sxs-lookup"><span data-stu-id="5e1e8-405">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="5e1e8-406">Davpr .NET SDK 'Sı herhangi bir belirli Observability özelliği içermiyor.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-406">The Dapr .NET SDK doesn't contain any specific observability features.</span></span> <span data-ttu-id="5e1e8-407">Tüm Observability özellikleri, Davpr düzeyinde sunulur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-407">All observability features are offered at the Dapr level.</span></span>

<span data-ttu-id="5e1e8-408">.NET uygulama kodunuzda telemetri yaymak istiyorsanız [.net Için Opentelemetri SDK 'sını](https://opentelemetry.io/docs/net/)göz önünde bulundurmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-408">If you want to emit telemetry from your .NET application code, you should consider the [OpenTelemetry SDK for .NET](https://opentelemetry.io/docs/net/).</span></span> <span data-ttu-id="5e1e8-409">Açık telemetri projesi platformlar arası, açık kaynak ve satıcı belirsiz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-409">The Open Telemetry project is cross-platform, open source, and vendor agnostic.</span></span> <span data-ttu-id="5e1e8-410">Telemetri verilerini oluşturma, yayma, toplama, işleme ve dışarı aktarmaya yönelik uçtan uca bir uygulama sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-410">It provides an end-to-end implementation to generate, emit, collect, process, and export telemetry data.</span></span> <span data-ttu-id="5e1e8-411">Otomatik ve el ile izleme desteği sunan dil başına tek bir izleme kitaplığı vardır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-411">There's a single instrumentation library per language that supports automatic and manual instrumentation.</span></span> <span data-ttu-id="5e1e8-412">Telemetri, açık telemetri standardı kullanılarak yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-412">Telemetry is published using the Open Telemetry standard.</span></span> <span data-ttu-id="5e1e8-413">Projenin bulut sağlayıcılarından, satıcılarından ve son kullanıcılardan geniş sektör desteği ve benimseme olanağı vardır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-413">The project has broad industry support and adoption from cloud providers, vendors, and end users.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="5e1e8-414">Başvuru uygulaması: Eshopondadpr</span><span class="sxs-lookup"><span data-stu-id="5e1e8-414">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="5e1e8-415">Eşlik eden Eshopondadpr başvuru uygulamasındaki Observability, birkaç bölümden oluşur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-415">Observability in accompanying eShopOnDapr reference application consists of several parts.</span></span> <span data-ttu-id="5e1e8-416">Tüm nesnelerin telemetrisi yakalanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-416">Telemetry from all of the sidecars is captured.</span></span> <span data-ttu-id="5e1e8-417">Ayrıca, önceki eShopOnContainers örneğinden devralınan diğer Observability özellikleri de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-417">Additionally, there are other observability features inherited from the earlier eShopOnContainers sample.</span></span>

### <a name="custom-health-dashboard"></a><span data-ttu-id="5e1e8-418">Özel durum panosu</span><span class="sxs-lookup"><span data-stu-id="5e1e8-418">Custom health dashboard</span></span>

<span data-ttu-id="5e1e8-419">Eshopondadpr 'deki **Webstatus** projesi, eShop hizmetlerinin sistem durumuna ilişkin Öngörüler sağlayan özel bir sistem durumu panosıdır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-419">The **WebStatus** project in eShopOnDapr is a custom health dashboard that gives insight into the health of the eShop services.</span></span> <span data-ttu-id="5e1e8-420">Bu Pano, Davpr sistem durumu API 'sini kullanmaz, ancak ASP.NET Core yerleşik [durum denetimleri mekanizmasını](/aspnet/core/host-and-deploy/health-checks) kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-420">This dashboard doesn't use the Dapr health API but uses the built-in [health checks mechanism](/aspnet/core/host-and-deploy/health-checks) of ASP.NET Core.</span></span> <span data-ttu-id="5e1e8-421">Pano yalnızca hizmetlerin sistem durumunu değil, hizmetlerin bağımlılıklarının durumunu da sağlamaz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-421">The dashboard not only provides the health status of the services, but also the health of the dependencies of the services.</span></span> <span data-ttu-id="5e1e8-422">Örneğin, bir veritabanı kullanan bir hizmet, aşağıdaki ekran görüntüsünde gösterildiği gibi bu veritabanının sistem durumunu da sağlar:</span><span class="sxs-lookup"><span data-stu-id="5e1e8-422">For example, a service that uses a database also provides the health status of this database as shown in the following screenshot:</span></span>

![Eshopondadpr özel durum panosu](media/observability/eshop-health-dashboard.png)

### <a name="seq-log-aggregator"></a><span data-ttu-id="5e1e8-424">Seq Günlük Toplayıcısı</span><span class="sxs-lookup"><span data-stu-id="5e1e8-424">Seq log aggregator</span></span>

<span data-ttu-id="5e1e8-425">[Sıra](https://datalust.co/seq) , günlükleri toplamak Için Eshopondadpr 'de kullanılan popüler bir günlük toplayıcısı sunucusudur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-425">[Seq](https://datalust.co/seq) is a popular log aggregator server that is used in eShopOnDapr to aggregate logs.</span></span> <span data-ttu-id="5e1e8-426">Uygulama hizmetlerinden günlüğe kaydetme, ancak Davpr sistem hizmetlerinden veya sıfları olmayan sıra.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-426">Seq ingests logging from application services, but not from Dapr system services or sidecars.</span></span> <span data-ttu-id="5e1e8-427">Seq uygulama günlüğünü oluşturur ve günlükleri analiz etmek ve sorgulamak için bir Web ön ucu sunar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-427">Seq indexes application logging and offers a web front end for analyzing and querying the logs.</span></span> <span data-ttu-id="5e1e8-428">İzleme panoları oluşturmaya yönelik işlevler de sunar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-428">It also offers functionality for building monitoring dashboards.</span></span>

<span data-ttu-id="5e1e8-429">Eshopondadpr uygulama hizmetleri, [SeriLog](https://serilog.net/) günlük kitaplığını kullanarak yapılandırılmış günlüğü yayar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-429">The eShopOnDapr application services emit structured logging using the [SeriLog](https://serilog.net/) logging library.</span></span> <span data-ttu-id="5e1e8-430">Serilog, **Havuz** adlı bir yapı için günlük olaylarını yayımlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-430">Serilog publishes log events to a construct called a **sink**.</span></span> <span data-ttu-id="5e1e8-431">Havuz, Serilog 'in günlüğe kaydetme olaylarını yazdığı bir hedef platformdur.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-431">A sink is simply a target platform to which Serilog writes its logging events.</span></span> <span data-ttu-id="5e1e8-432">Seq için bir de dahil olmak üzere [birçok Serilog havuzları mevcuttur](https://github.com/serilog/serilog/wiki/Provided-Sinks).</span><span class="sxs-lookup"><span data-stu-id="5e1e8-432">[Many Serilog sinks are available](https://github.com/serilog/serilog/wiki/Provided-Sinks), including one for Seq.</span></span> <span data-ttu-id="5e1e8-433">Sıra, Eshopondadpr içinde kullanılan Serilog Havuzu.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-433">Seq is the Serilog sink used in eShopOnDapr.</span></span>

### <a name="application-insights"></a><span data-ttu-id="5e1e8-434">Application Insights</span><span class="sxs-lookup"><span data-stu-id="5e1e8-434">Application Insights</span></span>

<span data-ttu-id="5e1e8-435">Eshopondadpr Hizmetleri ayrıca .NET Core için Microsoft Application Insights SDK 'sını kullanarak doğrudan Azure Application Insights telemetri gönderir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-435">eShopOnDapr services also send telemetry directly to Azure Application Insights using the Microsoft Application Insights SDK for .NET Core.</span></span> <span data-ttu-id="5e1e8-436">Daha fazla bilgi için bkz. Microsoft docs 'taki [ASP.NET Core uygulamalar Için Azure Application Insights](/azure/azure-monitor/app/asp-net-core) .</span><span class="sxs-lookup"><span data-stu-id="5e1e8-436">For more information, see [Azure Application Insights for ASP.NET Core applications](/azure/azure-monitor/app/asp-net-core) in the Microsoft docs.</span></span>

## <a name="summary"></a><span data-ttu-id="5e1e8-437">Özet</span><span class="sxs-lookup"><span data-stu-id="5e1e8-437">Summary</span></span>

<span data-ttu-id="5e1e8-438">Üretim ortamında Dağıtılmış bir sistem çalıştırılırken iyi Observability çok önemlidir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-438">Good observability is crucial when running a distributed system in production.</span></span>

<span data-ttu-id="5e1e8-439">Davpr, dağıtılmış izleme, günlüğe kaydetme, ölçümler ve sistem durumu gibi farklı türlerde telemetri sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-439">Dapr provides different types of telemetry, including distributed tracing, logging, metrics, and health status.</span></span>

<span data-ttu-id="5e1e8-440">Davpr yalnızca, Davpr sistem hizmetleri ve sıfları için telemetri üretir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-440">Dapr only produces telemetry for the Dapr system services and sidecars.</span></span> <span data-ttu-id="5e1e8-441">Uygulama kodunuzun telemetrisi otomatik olarak dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-441">Telemetry from your application code isn't automatically included.</span></span> <span data-ttu-id="5e1e8-442">Ancak, uygulama kodunuzda telemetri göstermek için .NET için Opentelemetri SDK gibi belirli bir SDK 'Yı kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-442">You can however use a specific SDK like the OpenTelemetry SDK for .NET to emit telemetry from your application code.</span></span>

<span data-ttu-id="5e1e8-443">Davpr telemetrisi, Açık standartlara dayalı bir biçimde üretilerek, büyük bir kullanılabilir izleme araçları kümesiyle gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-443">Dapr telemetry is produced in an open-standards based format so it can be ingested by a large set of available monitoring tools.</span></span> <span data-ttu-id="5e1e8-444">Bazı örnekler şunlardır: Zipar, Azure Application Insights, ELK yığını, New relik ve Grafana.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-444">Some examples are: Zipkin, Azure Application Insights, the ELK Stack, New Relic, and Grafana.</span></span> <span data-ttu-id="5e1e8-445">Belirli izleme arka uçları ile Davpr uygulamalarınızı izlemeye yönelik öğreticiler için bkz. davpr belgelerindeki [davpr ile uygulamanızı izleme](https://docs.dapr.io/operations/monitoring/) .</span><span class="sxs-lookup"><span data-stu-id="5e1e8-445">See [Monitor your application with Dapr](https://docs.dapr.io/operations/monitoring/) in the Dapr documentation for tutorials on how to monitor your Dapr applications with specific monitoring back ends.</span></span>

<span data-ttu-id="5e1e8-446">Bu telemetri için bir telemetri atık ve izleme arka ucuna yayınlıyor olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-446">You'll need a telemetry scraper that ingests telemetry and publishes it to the monitoring back end.</span></span>

<span data-ttu-id="5e1e8-447">Davpr yapılandırılmış günlüğe kaydetmeyi yayan yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-447">Dapr can be configured to emit structured logging.</span></span> <span data-ttu-id="5e1e8-448">Yapılandırılmış günlüğe kaydetme, arka uç izleme araçlarıyla dizin oluşturulduğundan daha kırmızıdır.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-448">Structured logging is favored as it can be indexed by back-end monitoring tools.</span></span> <span data-ttu-id="5e1e8-449">Dizini oluşturulmuş günlük kaydı, kullanıcıların günlüğe kaydetme sırasında arama yaparken zengin sorguları yürütmelerine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-449">Indexed logging enables users to execute rich queries when searching through the logging.</span></span>

<span data-ttu-id="5e1e8-450">Davpr, Davpr Hizmetleri ve yapılandırması hakkında bilgi sunan bir pano sunar.</span><span class="sxs-lookup"><span data-stu-id="5e1e8-450">Dapr offers a dashboard that presents information about the Dapr services and configuration.</span></span>

## <a name="references"></a><span data-ttu-id="5e1e8-451">Başvurular</span><span class="sxs-lookup"><span data-stu-id="5e1e8-451">References</span></span>

- [<span data-ttu-id="5e1e8-452">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="5e1e8-452">Azure Application Insights</span></span>](/azure/azure-monitor/app/app-insights-overview/)
- [<span data-ttu-id="5e1e8-453">Telemetriyi açın</span><span class="sxs-lookup"><span data-stu-id="5e1e8-453">Open Telemetry</span></span>](https://opentelemetry.io/)
- [<span data-ttu-id="5e1e8-454">Ferkabağı</span><span class="sxs-lookup"><span data-stu-id="5e1e8-454">Zipkin</span></span>](https://zipkin.io/)
- [<span data-ttu-id="5e1e8-455">W3C Trace bağlamı</span><span class="sxs-lookup"><span data-stu-id="5e1e8-455">W3C Trace Context</span></span>](https://www.w3.org/TR/trace-context/)
- [<span data-ttu-id="5e1e8-456">Jaeger</span><span class="sxs-lookup"><span data-stu-id="5e1e8-456">Jaeger</span></span>](https://www.jaegertracing.io/)
- [<span data-ttu-id="5e1e8-457">New Relic</span><span class="sxs-lookup"><span data-stu-id="5e1e8-457">New Relic</span></span>](https://newrelic.com/)
- [<span data-ttu-id="5e1e8-458">Prometheus</span><span class="sxs-lookup"><span data-stu-id="5e1e8-458">Prometheus</span></span>](https://prometheus.io/)
- [<span data-ttu-id="5e1e8-459">Grafana</span><span class="sxs-lookup"><span data-stu-id="5e1e8-459">Grafana</span></span>](https://grafana.com/grafana/)
- [<span data-ttu-id="5e1e8-460">.NET için telemetri SDK 'sını açın</span><span class="sxs-lookup"><span data-stu-id="5e1e8-460">Open Telemetry SDK for .NET</span></span>](https://opentelemetry.io/docs/net/)
- [<span data-ttu-id="5e1e8-461">Fluentd</span><span class="sxs-lookup"><span data-stu-id="5e1e8-461">Fluentd</span></span>](https://www.fluentd.org/)
- [<span data-ttu-id="5e1e8-462">ELK yığını</span><span class="sxs-lookup"><span data-stu-id="5e1e8-462">ELK stack</span></span>](https://www.elastic.co/elastic-stack)
- [<span data-ttu-id="5e1e8-463">Sıra</span><span class="sxs-lookup"><span data-stu-id="5e1e8-463">Seq</span></span>](https://datalust.co/seq)
- [<span data-ttu-id="5e1e8-464">Serilog</span><span class="sxs-lookup"><span data-stu-id="5e1e8-464">Serilog</span></span>](https://serilog.net/)

> [!div class="step-by-step"]
> <span data-ttu-id="5e1e8-465">[Önceki](bindings.md) 
>  [Sonraki](secrets.md)</span><span class="sxs-lookup"><span data-stu-id="5e1e8-465">[Previous](bindings.md)
[Next](secrets.md)</span></span>
