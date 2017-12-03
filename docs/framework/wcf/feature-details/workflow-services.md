---
title: "İş Akışı Hizmetleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b05c766-f181-425d-9a3d-2a5e150c85f7
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 043aa541e32077faf8141701a5ec7e8c0e711959
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-services"></a><span data-ttu-id="cb0a2-102">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="cb0a2-102">Workflow Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="cb0a2-103">tam olarak bir iş akışı tabanlı hizmet bildirimli olarak XAML'de açıklamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-103"> allows you to fully describe a workflow-based service declaratively in XAML.</span></span> <span data-ttu-id="cb0a2-104">Hizmetinizi uygulayan bir iş akışı tanımlayın ve hizmet sunan tüm tamamen XAML'de uç noktaları açıklar.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-104">You can define a workflow that implements your service and describe endpoints the service exposes, all entirely in XAML.</span></span> <span data-ttu-id="cb0a2-105">Bu bölümdeki konular, bildirimli olarak yazma hizmetleri destekleyen programlama modeli ayrıntılı olarak açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-105">The topics in this section describe, in detail, the programming model that supports writing services declaratively.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb0a2-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cb0a2-106">In This Section</span></span>  
 [<span data-ttu-id="cb0a2-107">İş akışı hizmetleri genel bakış</span><span class="sxs-lookup"><span data-stu-id="cb0a2-107">Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services-overview.md)  
 <span data-ttu-id="cb0a2-108">Oluşturma ve bir iş akışı hizmeti barındırma ilgili bileşenlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-108">Describes the components involved in creating and hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="cb0a2-109">Mesajlaşma etkinlikleri</span><span class="sxs-lookup"><span data-stu-id="cb0a2-109">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 <span data-ttu-id="cb0a2-110">İleti gönderme ve alma için iş akışlarını izin etkinlikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-110">Discusses activities that allow workflows to send and receive messages.</span></span>  
  
 [<span data-ttu-id="cb0a2-111">Nasıl yapılır: Mesajlaşma etkinlikleriyle iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb0a2-111">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 <span data-ttu-id="cb0a2-112">Mesajlaşma etkinlikleri bir iş akışı hizmeti oluşturma için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-112">Describes how to use messaging activities to create a workflow service.</span></span>  
  
 [<span data-ttu-id="cb0a2-113">Nasıl yapılır: bir iş akışı uygulamasından bir hizmete erişim</span><span class="sxs-lookup"><span data-stu-id="cb0a2-113">How To: Access a Service From a Workflow Application</span></span>](../../../../docs/framework/wcf/feature-details/how-to-access-a-service-from-a-workflow-application.md)  
 <span data-ttu-id="cb0a2-114">Bir iş akışı uygulamasından bir hizmetin nasıl ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-114">Discusses how to call a service from a workflow application.</span></span>  
  
 [<span data-ttu-id="cb0a2-115">Bağıntı</span><span class="sxs-lookup"><span data-stu-id="cb0a2-115">Correlation</span></span>](../../../../docs/framework/wcf/feature-details/correlation.md)  
 <span data-ttu-id="cb0a2-116">Birbirine ve örnekleri bağıntı iletileri nasıl eşlendiğini açıklanır.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-116">Discusses how correlation maps messages to each other and to instances.</span></span>  
  
 [<span data-ttu-id="cb0a2-117">Düzen dışı ileti işleme</span><span class="sxs-lookup"><span data-stu-id="cb0a2-117">Out-of-Order Message Processing</span></span>](../../../../docs/framework/wcf/feature-details/out-of-order-message-processing.md)  
 <span data-ttu-id="cb0a2-118">Bir hizmeti bozuk iletileri kabul edecek şekilde yapılandırılmasını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-118">Describes configuring a service to accept out of order messages.</span></span>  
  
 [<span data-ttu-id="cb0a2-119">Nasıl yapılır: başka bir iş akışı hizmeti çağıran bir iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb0a2-119">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 <span data-ttu-id="cb0a2-120">Zaman uyumlu olarak başka bir iş akışı hizmeti içinde bir iş akışı hizmeti çağırmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-120">Describes how to synchronously call a workflow service from within another workflow service.</span></span>  
  
 [<span data-ttu-id="cb0a2-121">Sözleşme ilk iş akışı hizmeti geliştirme</span><span class="sxs-lookup"><span data-stu-id="cb0a2-121">Contract First Workflow Service Development</span></span>](../../../../docs/framework/windows-workflow-foundation/contract-first-workflow-service-development.md)  
 <span data-ttu-id="cb0a2-122">Varolan bir servis sözleşmesine dayalı bir iş akışı hizmeti oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-122">Describes creating a workflow service based on an existing service contract.</span></span>  
  
 [<span data-ttu-id="cb0a2-123">Nasıl yapılır: varolan bir hizmet sözleşmesini tüketen bir iş akışı hizmeti oluşturma</span><span class="sxs-lookup"><span data-stu-id="cb0a2-123">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)  
 <span data-ttu-id="cb0a2-124">Var olan bir hizmet sözleşmesini kullanarak bir iş akışı hizmeti oluşturma adım adım bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-124">Provides a step-by-step example of creating a workflow service using an existing service contract.</span></span>  
  
 [<span data-ttu-id="cb0a2-125">İş akışı hizmetlerini barındırma genel bakış</span><span class="sxs-lookup"><span data-stu-id="cb0a2-125">Hosting Workflow Services Overview</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 <span data-ttu-id="cb0a2-126">Bir iş akışı hizmeti barındırma farklı yönleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-126">Describes the different aspects of hosting a workflow service.</span></span>  
  
 [<span data-ttu-id="cb0a2-127">İş akışında sözleşmeleri kullanma</span><span class="sxs-lookup"><span data-stu-id="cb0a2-127">Using Contracts in Workflow</span></span>](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md)  
 <span data-ttu-id="cb0a2-128">Sözleşmeler ve sözleşme çıkarım farklı türleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb0a2-128">Describes the different types of contracts and contract inference.</span></span>
