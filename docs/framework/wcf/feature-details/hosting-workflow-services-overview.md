---
title: İş Akışı Hizmetlerini Barındırma Genel Bakış
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: 150cb98ab3cef8231489219a16709344cbd19bd5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242974"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="996bb-102">İş Akışı Hizmetlerini Barındırma Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="996bb-102">Hosting Workflow Services Overview</span></span>

<span data-ttu-id="996bb-103">İş akışı hizmetlerinin yürütülmesi için barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="996bb-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="996bb-104">, <xref:System.ServiceModel.WorkflowServiceHost> Birden çok örneği, yapılandırmayı ve WCF iletilerini destekleyen, kullanıma hazır olan iş akışı ana bilgisayarı olur (ancak iş akışlarının barındırılmak için mesajlaşma kullanması gerekmez).</span><span class="sxs-lookup"><span data-stu-id="996bb-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="996bb-105">Ayrıca, bir dizi hizmet davranışı aracılığıyla Kalıcılık, izleme ve örnek denetimiyle tümleştirilir.</span><span class="sxs-lookup"><span data-stu-id="996bb-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="996bb-106">WCF 'nin de olduğu gibi, <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.WorkflowServiceHost> IIS/was içinde herhangi bir yönetilen .NET uygulamasında veya Web 'de barındırılan (bir. xamlx dosyası olarak) şirket içinde barınabilir.</span><span class="sxs-lookup"><span data-stu-id="996bb-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="996bb-107">Bu bölümdeki konular, bir iş akışı hizmetinin nasıl barındıralınacağını açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="996bb-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="996bb-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="996bb-108">In This Section</span></span>  

 [<span data-ttu-id="996bb-109">İş Akışı Hizmetlerini Barındırma</span><span class="sxs-lookup"><span data-stu-id="996bb-109">Hosting Workflow Services</span></span>](hosting-workflow-services.md)  
 <span data-ttu-id="996bb-110">Barındırma iş akışı hizmetlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="996bb-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="996bb-111">İş Akışı Hizmeti Ana Bilgisayar Dahili Bileşenleri</span><span class="sxs-lookup"><span data-stu-id="996bb-111">Workflow Service Host Internals</span></span>](workflow-service-host-internals.md)  
 <span data-ttu-id="996bb-112"><xref:System.ServiceModel.WorkflowServiceHost>Gelen iletileri işleme biçimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="996bb-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="996bb-113">İş Akışı Hizmeti Ana Bilgisayar Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="996bb-113">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)  
 <span data-ttu-id="996bb-114">İş akışı hizmeti Konağı işlevinin nasıl genişletileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="996bb-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="996bb-115">İş Akışı Denetim Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="996bb-115">Workflow Control Endpoint</span></span>](workflow-control-endpoint.md)  
 <span data-ttu-id="996bb-116">İş akışı örnekleri oluşturmanıza izin veren bir uç noktanın nasıl tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="996bb-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>
  
 [<span data-ttu-id="996bb-117">Nasıl yapılır: Windows Server App Fabric ile İş Akışı Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="996bb-117">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="996bb-118">Windows Server App Fabric 'te mevcut bir iş akışı hizmetinin nasıl barındırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="996bb-118">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="996bb-119">WorkflowServiceHost Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="996bb-119">Configuring WorkflowServiceHost</span></span>](configuring-workflowservicehost.md)  
 <span data-ttu-id="996bb-120">Kalıcılık, izleme, boşta ve işlenmemiş özel durum davranışının nasıl kontrol edileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="996bb-120">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="996bb-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="996bb-121">Reference</span></span>  

 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="996bb-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="996bb-122">Related Sections</span></span>  

 [<span data-ttu-id="996bb-123">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="996bb-123">Workflow Services</span></span>](workflow-services.md)
