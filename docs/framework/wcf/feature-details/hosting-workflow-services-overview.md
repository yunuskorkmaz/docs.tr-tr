---
title: İş Akışı Hizmetlerini Barındırma Genel Bakış
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: 7b5de31b5931af13b41b11af6e48a52b5628e27c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489566"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="1dc30-102">İş Akışı Hizmetlerini Barındırma Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1dc30-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="1dc30-103">İş akışı hizmetleri yürütmek için barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1dc30-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="1dc30-104"><xref:System.ServiceModel.WorkflowServiceHost> (İş akışları barındırılması için Mesajlaşma kullanmak için gerekli olmasa da) destekleyen birden çok örneği, yapılandırma ve WCF ileti Giden kutusu iş akışı ana bilgisayardır.</span><span class="sxs-lookup"><span data-stu-id="1dc30-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="1dc30-105">Ayrıca Kalıcılık, izleme ve bir dizi hizmet davranışları örneği denetimi ile tümleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1dc30-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="1dc30-106">WCF'ın ' olduğu gibi <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> herhangi bir yönetilen .NET uygulamasında kendi kendini barındıran veya web (.xamlx dosyası olarak) IIS'de barındırılan / OLUŞTU.</span><span class="sxs-lookup"><span data-stu-id="1dc30-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="1dc30-107">Bu bölümdeki konular, bir iş akışı hizmeti barındırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="1dc30-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1dc30-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1dc30-108">In This Section</span></span>  
 [<span data-ttu-id="1dc30-109">İş Akışı Hizmetlerini Barındırma</span><span class="sxs-lookup"><span data-stu-id="1dc30-109">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 <span data-ttu-id="1dc30-110">İş akışı hizmetlerini barındırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="1dc30-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="1dc30-111">İş Akışı Hizmeti Konağı Dahili Bileşenleri</span><span class="sxs-lookup"><span data-stu-id="1dc30-111">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <span data-ttu-id="1dc30-112">Açıklar nasıl <xref:System.ServiceModel.WorkflowServiceHost> gelen iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="1dc30-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="1dc30-113">İş Akışı Hizmeti Konak Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="1dc30-113">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 <span data-ttu-id="1dc30-114">İş akışı hizmeti ana bilgisayarı işlevselliğini genişletmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="1dc30-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="1dc30-115">İş Akışı Denetim Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="1dc30-115">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 <span data-ttu-id="1dc30-116">İş akışı örnekleri oluşturmanıza olanak tanıyan bir uç nokta tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1dc30-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>  
  
 [<span data-ttu-id="1dc30-117">Nasıl yapılır: IIS'de hizmet olmayan iş akışı barındırma</span><span class="sxs-lookup"><span data-stu-id="1dc30-117">How to: Host a non-service workflow in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)  
 <span data-ttu-id="1dc30-118">Bir iş akışı hizmeti IIS olmayan bir iş akışı barındırma gösterir.</span><span class="sxs-lookup"><span data-stu-id="1dc30-118">Demonstrates hosting a workflow that is not a workflow service in IIS.</span></span>  
  
 [<span data-ttu-id="1dc30-119">Nasıl yapılır: Windows Server App Fabric ile İş Akışı Hizmeti Barındırma</span><span class="sxs-lookup"><span data-stu-id="1dc30-119">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="1dc30-120">Windows Server App Fabric var olan bir iş akışı hizmetinde barındırmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="1dc30-120">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="1dc30-121">WorkflowServiceHost Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="1dc30-121">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 <span data-ttu-id="1dc30-122">Kalıcılık, izleme, boşta ve işlenmeyen özel durum davranışını denetlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="1dc30-122">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1dc30-123">Başvuru</span><span class="sxs-lookup"><span data-stu-id="1dc30-123">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="1dc30-124">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="1dc30-124">Related Sections</span></span>  
 [<span data-ttu-id="1dc30-125">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="1dc30-125">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
