---
title: "Geçiş Kılavuzu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb65c132-58c9-4028-b3d4-1efc71d5e60e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e04c63754960dca44558d888b8ce357220562ea7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="migration-guidance"></a><span data-ttu-id="97736-102">Geçiş Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="97736-102">Migration Guidance</span></span>
<span data-ttu-id="97736-103">İçinde [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ikinci ana sürümüne yönelik Microsoft serbest bırakma [!INCLUDE[wf](../../../includes/wf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97736-103">In the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], Microsoft is releasing the second major version of [!INCLUDE[wf](../../../includes/wf-md.md)].</span></span> [!INCLUDE[wf1](../../../includes/wf1-md.md)]<span data-ttu-id="97736-104">içinde yayımlanan [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (Bu System.Workflow.\* ad alanlarında türleri dahil; şimdi WF3 adlandırılır) ve geliştirilmiş içinde [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97736-104"> was released in [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] (this included the types in the System.Workflow.\* namespaces; now referred to as WF3) and enhanced in [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)].</span></span> <span data-ttu-id="97736-105">WF3 olduğu da parçası [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], ancak yanı sıra yeni iş akışı teknolojisi vardır (System.Activities. türlerinde\* ad alanları; için WF4 adlandırılır).</span><span class="sxs-lookup"><span data-stu-id="97736-105">WF3 is also part of the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], but it exists there alongside new workflow technology (the types in the System.Activities.\* namespaces; referred to as WF4).</span></span> <span data-ttu-id="97736-106">WF4 benimsemek ne zaman değerlendirirken zamanlamasını denetlemek ilk bilmek önemlidir.</span><span class="sxs-lookup"><span data-stu-id="97736-106">When considering when to adopt WF4, it is important to first recognize that you control the timing.</span></span>  
  
-   <span data-ttu-id="97736-107">WF3 tam olarak desteklenen bir parçası olan [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="97736-107">WF3 is a fully supported part of the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span>  
  
-   <span data-ttu-id="97736-108">WF3 uygulamaları çalıştıracağınız [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] değişiklik yapmadan ve tam olarak desteklemeye devam eder.</span><span class="sxs-lookup"><span data-stu-id="97736-108">WF3 applications run on the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] without modification and continue to be fully supported.</span></span>  
  
-   <span data-ttu-id="97736-109">Yeni WF3 uygulamaları oluşturulabilir ve var olan uygulamalarınız içinde düzenlenebilir [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] ve tam olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="97736-109">New WF3 applications can be created and your existing applications can be edited in [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] and are fully supported.</span></span>  
  
 <span data-ttu-id="97736-110">Bu nedenle, .NET Framework 4 benimsemeye karar WF4 için taşımaya karar den düşünülebilir (System.Activities.*) WF3 gelen (System.Workflow.\*).</span><span class="sxs-lookup"><span data-stu-id="97736-110">Thus, the decision to adopt the .NET Framework 4 is decoupled from your decision to move to WF4 (System.Activities.*) from WF3 (System.Workflow.\*).</span></span> <span data-ttu-id="97736-111">Bu konuda WF3 ve WF4 ile çalışma hakkında bilgi sağlar WF geçiş yönergelere bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="97736-111">This topic provides links to WF migration guidance that provides information about working with WF3 and WF4.</span></span>  
  
## <a name="wf-migration-whitepapers-and-cookbooks"></a><span data-ttu-id="97736-112">WF geçiş teknik incelemeler ve Cookbooks</span><span class="sxs-lookup"><span data-stu-id="97736-112">WF Migration Whitepapers and Cookbooks</span></span>  
 <span data-ttu-id="97736-113">[WF geçişine genel bakış](http://go.microsoft.com/fwlink/?LinkId=153873) konu WF3 ve WF4 ve geçiş stratejileri arasındaki ilişkinin kapsamlı bir genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="97736-113">The [WF Migration Overview](http://go.microsoft.com/fwlink/?LinkId=153873) topic provides a broad overview of the relationship between WF3 and WF4 and migration strategies.</span></span> <span data-ttu-id="97736-114">Yardımcısı konuları belirli konulara ayrıntıya.</span><span class="sxs-lookup"><span data-stu-id="97736-114">Companion topics drill into specific topics.</span></span>  
  
 [<span data-ttu-id="97736-115">WF geçişine genel bakış</span><span class="sxs-lookup"><span data-stu-id="97736-115">WF Migration Overview</span></span>](http://go.microsoft.com/fwlink/?LinkId=153873)  
 <span data-ttu-id="97736-116">WF3 ve WF4 ve bir kullanıcı veya iş akışı teknolojisinin .NET 4'te olası bir kullanıcı olarak sahip seçenekleri arasındaki ilişkiyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="97736-116">Describes the relationship between WF3 and WF4, and the choices you have as a user or a potential user of workflow technology in .NET 4.</span></span>  
  
 [<span data-ttu-id="97736-117">WF geçişi: WF3 geliştirme için en iyi yöntemler</span><span class="sxs-lookup"><span data-stu-id="97736-117">WF Migration: Best Practices for WF3 Development</span></span>](http://go.microsoft.com/fwlink/?LinkId=153852)  
 <span data-ttu-id="97736-118">WF4 için daha kolay geçirilebilecek şekilde WF3 yapıları tasarlamak nasıl ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="97736-118">Discusses how to design WF3 artifacts so they can be more easily migrated to WF4.</span></span>  
  
 [<span data-ttu-id="97736-119">WF Kılavuzu: kuralları</span><span class="sxs-lookup"><span data-stu-id="97736-119">WF Guidance: Rules</span></span>](http://go.microsoft.com/fwlink/?LinkId=153854)  
 <span data-ttu-id="97736-120">Kuralları ile ilgili Yatırımlar İleri içine nasıl ele [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] çözümler.</span><span class="sxs-lookup"><span data-stu-id="97736-120">Discusses how to bring rules-related investments forward into [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] solutions.</span></span>  
  
 [<span data-ttu-id="97736-121">WF Kılavuzu: Durum makinesi</span><span class="sxs-lookup"><span data-stu-id="97736-121">WF Guidance: State Machine</span></span>](http://go.microsoft.com/fwlink/?LinkId=153855)  
 <span data-ttu-id="97736-122">Durum makinesinin Etkinlik olmaması durumunda modelleme WF4 denetim akışı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="97736-122">Discusses WF4 control flow modeling in the absence of a State-Machine activity.</span></span>  
  
 <span data-ttu-id="97736-123">Bu kılavuz yalnızca .NET Framework 4 hedefleyen iş akışı projeler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="97736-123">Note that this guidance only applies to workflow projects that target .NET Framework 4.</span></span> <span data-ttu-id="97736-124">Durum makinesi iş akışları .NET 4.0.1 Platform güncelleştirme 1'in çıkışıyla eklenmiştir ve .NET Framework 4. 5 ' bir parçası olarak dahil.</span><span class="sxs-lookup"><span data-stu-id="97736-124">State Machine workflows were added in .NET 4.0.1 with the release of Platform Update 1, and were included as part of .NET Framework 4.5.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="97736-125">Durum makinesi .NET 4.0.1 - 4.0.3 ve .NET Framework 4.5, iş akışlarında bkz [4.0.1 Microsoft .NET Framework 4 özellikleri için güncelleştirme](http://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) ve [durumu makine iş akışları](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).</span><span class="sxs-lookup"><span data-stu-id="97736-125"> state machine workflows in .NET 4.0.1 - 4.0.3 and .NET Framework 4.5, see [Update 4.0.1 for Microsoft .NET Framework 4 Features](http://msdn.microsoft.com/library/de3297bd-c3e1-4126-95be-2ed7fe2a98fc) and [State Machine Workflows](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).</span></span>  
  
 [<span data-ttu-id="97736-126">WF Geçiş Kılavuzu: Özel etkinlikler</span><span class="sxs-lookup"><span data-stu-id="97736-126">WF Migration Cookbook: Custom Activities</span></span>](http://go.microsoft.com/fwlink/?LinkId=153856)  
 <span data-ttu-id="97736-127">Örnekler ve WF4 WF3 özel etkinlikleri yeniden için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="97736-127">Provides examples and instructions for redesigning WF3 custom activities on WF4.</span></span>  
  
 [<span data-ttu-id="97736-128">WF Geçiş Kılavuzu: Özel etkinlikler Gelişmiş</span><span class="sxs-lookup"><span data-stu-id="97736-128">WF Migration Cookbook: Advanced Custom Activities</span></span>](http://go.microsoft.com/fwlink/?LinkId=275560)  
 <span data-ttu-id="97736-129">WF3 kuyrukları kullanan gelişmiş WF3 özel etkinlikler ve zamanlama alt etkinlikleri WF4 özel etkinlikler olarak yeniden ilişkin yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="97736-129">Provides guidance for redesigning advanced WF3 custom activities that use WF3 queues and schedule child activities as WF4 custom activities.</span></span>  
  
 [<span data-ttu-id="97736-130">WF Geçiş Kılavuzu: iş akışları</span><span class="sxs-lookup"><span data-stu-id="97736-130">WF Migration Cookbook: Workflows</span></span>](http://go.microsoft.com/fwlink/?LinkId=153858)  
 <span data-ttu-id="97736-131">Örnekler ve WF4 WF3 iş akışlarında yeniden için yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="97736-131">Provides examples and instructions for redesigning WF3 workflows on WF4.</span></span>  
  
 [<span data-ttu-id="97736-132">WF Geçiş Kılavuzu: İş akışı barındırma</span><span class="sxs-lookup"><span data-stu-id="97736-132">WF Migration Cookbook: Workflow Hosting</span></span>](http://go.microsoft.com/fwlink/?LinkId=275561)  
 <span data-ttu-id="97736-133">WF3 barındırma kodu WF4 barındırma kodu olarak yeniden ilişkin yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="97736-133">Provides guidance for redesigning WF3 hosting code as WF4 hosting code.</span></span> <span data-ttu-id="97736-134">İş akışı barındırma WF3 ve WF4 temel farklılıkları kapsayacak şekilde belirtilir.</span><span class="sxs-lookup"><span data-stu-id="97736-134">The goal is to cover the key differences in workflow hosting between WF3 and WF4.</span></span>  
  
 [<span data-ttu-id="97736-135">WF Geçiş Kılavuzu: İş akışı izleme</span><span class="sxs-lookup"><span data-stu-id="97736-135">WF Migration Cookbook: Workflow Tracking</span></span>](http://go.microsoft.com/fwlink/?LinkId=275562)  
 <span data-ttu-id="97736-136">WF3 izleme kodu ve eşdeğer WF4 izleme kodunu ve yapılandırma kullanarak yapılandırmayı yeniden ilişkin yönergeler sağlar.</span><span class="sxs-lookup"><span data-stu-id="97736-136">Provides guidance for redesigning WF3 tracking code and configuration using equivalent WF4 tracking code and configuration.</span></span>  
  
 [<span data-ttu-id="97736-137">WF Kılavuzu: İş akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="97736-137">WF Guidance: Workflow Services</span></span>](http://go.microsoft.com/fwlink/?LinkId=275564)  
 <span data-ttu-id="97736-138">(Genellikle iş akışı Hizmetleri olarak adlandırılır) Windows Communication Foundation (WCF) web hizmetlerini out-of-box için genel senaryolar için WF4, kullanılacak WF3 oluşturulan uygulama iş akışlarını yeniden örnek yönelik adım adım yönergeler sağlar etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="97736-138">Provides example-oriented step-by-step instructions for redesigning workflows that implement Windows Communication Foundation (WCF) web services (commonly referred to as workflow services) created in WF3 to use WF4, for common scenarios for out-of-box activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97736-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="97736-139">See Also</span></span>  
 <xref:System.Activities.Statements.Interop>
