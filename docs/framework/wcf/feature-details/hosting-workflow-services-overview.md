---
description: 'Hakkında daha fazla bilgi edinin: barındırma Iş akışı hizmetleri genel bakış'
title: İş Akışı Hizmetlerini Barındırma Genel Bakış
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: e183dfd7428c11cf20e731ab4a9975a7388b6f98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743089"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="360cf-103">İş Akışı Hizmetlerini Barındırma Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="360cf-103">Hosting Workflow Services Overview</span></span>

<span data-ttu-id="360cf-104">İş akışı hizmetlerinin yürütülmesi için barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="360cf-104">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="360cf-105">, <xref:System.ServiceModel.WorkflowServiceHost> Birden çok örneği, yapılandırmayı ve WCF iletilerini destekleyen, kullanıma hazır olan iş akışı ana bilgisayarı olur (ancak iş akışlarının barındırılmak için mesajlaşma kullanması gerekmez).</span><span class="sxs-lookup"><span data-stu-id="360cf-105">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="360cf-106">Ayrıca, bir dizi hizmet davranışı aracılığıyla Kalıcılık, izleme ve örnek denetimiyle tümleştirilir.</span><span class="sxs-lookup"><span data-stu-id="360cf-106">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="360cf-107">WCF 'nin de olduğu gibi, <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.WorkflowServiceHost> IIS/was içinde herhangi bir yönetilen .NET uygulamasında veya Web 'de barındırılan (bir. xamlx dosyası olarak) şirket içinde barınabilir.</span><span class="sxs-lookup"><span data-stu-id="360cf-107">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="360cf-108">Bu bölümdeki konular, bir iş akışı hizmetinin nasıl barındıralınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="360cf-108">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="360cf-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="360cf-109">In This Section</span></span>  

 [<span data-ttu-id="360cf-110">İş Akışı Hizmetlerini Barındırma</span><span class="sxs-lookup"><span data-stu-id="360cf-110">Hosting Workflow Services</span></span>](hosting-workflow-services.md)  
 <span data-ttu-id="360cf-111">Barındırma iş akışı hizmetlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="360cf-111">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="360cf-112">İş Akışı Hizmeti Ana Bilgisayar Dahili Bileşenleri</span><span class="sxs-lookup"><span data-stu-id="360cf-112">Workflow Service Host Internals</span></span>](workflow-service-host-internals.md)  
 <span data-ttu-id="360cf-113"><xref:System.ServiceModel.WorkflowServiceHost>Gelen iletileri işleme biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="360cf-113">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="360cf-114">İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="360cf-114">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)  
 <span data-ttu-id="360cf-115">İş akışı hizmeti Konağı işlevinin nasıl genişletileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="360cf-115">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="360cf-116">İş Akışı Denetim Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="360cf-116">Workflow Control Endpoint</span></span>](workflow-control-endpoint.md)  
 <span data-ttu-id="360cf-117">İş akışı örnekleri oluşturmanıza izin veren bir uç noktanın nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="360cf-117">Describes how to define an endpoint that allows you to create workflow instances.</span></span>
  
 [<span data-ttu-id="360cf-118">Nasıl yapılır: Windows Server App Fabric ile İş Akışı Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="360cf-118">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="360cf-119">Windows Server App Fabric 'te mevcut bir iş akışı hizmetinin nasıl barındırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="360cf-119">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="360cf-120">WorkflowServiceHost Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="360cf-120">Configuring WorkflowServiceHost</span></span>](configuring-workflowservicehost.md)  
 <span data-ttu-id="360cf-121">Kalıcılık, izleme, boşta ve işlenmemiş özel durum davranışının nasıl kontrol edileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="360cf-121">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="360cf-122">Başvuru</span><span class="sxs-lookup"><span data-stu-id="360cf-122">Reference</span></span>  

 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="360cf-123">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="360cf-123">Related Sections</span></span>  

 [<span data-ttu-id="360cf-124">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="360cf-124">Workflow Services</span></span>](workflow-services.md)
