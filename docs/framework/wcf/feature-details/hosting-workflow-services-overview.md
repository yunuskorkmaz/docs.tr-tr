---
title: İş Akışı Hizmetlerini Barındırma Genel Bakış
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: dbe271e30e9c4e98a52c01ffaa21de25c127c7ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855900"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="d841f-102">İş Akışı Hizmetlerini Barındırma Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d841f-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="d841f-103">Yürütülecek iş akışı hizmetleri barındırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d841f-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="d841f-104"><xref:System.ServiceModel.WorkflowServiceHost> (İş akışları barındırılması için Mesajlaşma kullanmak için gerekli olmasa da) destekleyen birden çok örneği, yapılandırma ve WCF ileti kullanıma hazır iş akışı ana bilgisayarı.</span><span class="sxs-lookup"><span data-stu-id="d841f-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="d841f-105">Ayrıca Kalıcılık, izleme ve hizmet davranışlarını bir dizi aracılığıyla örneği denetimi ile tümleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d841f-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="d841f-106">WCF'ın ' olduğu gibi <xref:System.ServiceModel.ServiceHost>, <xref:System.ServiceModel.WorkflowServiceHost> herhangi bir yönetilen .NET uygulamasında şirket içinde barındırılan veya web barındırılan-(.xamlx dosyası) IIS / WAS'da.</span><span class="sxs-lookup"><span data-stu-id="d841f-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="d841f-107">Bu bölümdeki konular, bir iş akışı hizmeti barındırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="d841f-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d841f-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d841f-108">In This Section</span></span>  
 [<span data-ttu-id="d841f-109">İş Akışı Hizmetlerini Barındırma</span><span class="sxs-lookup"><span data-stu-id="d841f-109">Hosting Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 <span data-ttu-id="d841f-110">İş akışı hizmetlerini barındırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="d841f-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="d841f-111">İş Akışı Hizmeti Konağı Dahili Bileşenleri</span><span class="sxs-lookup"><span data-stu-id="d841f-111">Workflow Service Host Internals</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)  
 <span data-ttu-id="d841f-112">Açıklayan nasıl <xref:System.ServiceModel.WorkflowServiceHost> gelen iletileri işler.</span><span class="sxs-lookup"><span data-stu-id="d841f-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="d841f-113">İş Akışı Hizmeti Konak Genişletilebilirliği</span><span class="sxs-lookup"><span data-stu-id="d841f-113">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 <span data-ttu-id="d841f-114">İş akışı hizmeti konağı genişletmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="d841f-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="d841f-115">İş Akışı Denetim Uç Noktası</span><span class="sxs-lookup"><span data-stu-id="d841f-115">Workflow Control Endpoint</span></span>](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 <span data-ttu-id="d841f-116">İş akışı örnekleri oluşturmak izin veren bir uç nokta tanımlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d841f-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>
  
 [<span data-ttu-id="d841f-117">Nasıl yapılır: Windows Server App Fabric ile bir iş akışı hizmeti barındırma</span><span class="sxs-lookup"><span data-stu-id="d841f-117">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="d841f-118">Windows Server App Fabric içinde var olan bir iş akışı hizmeti barındırma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d841f-118">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="d841f-119">WorkflowServiceHost Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="d841f-119">Configuring WorkflowServiceHost</span></span>](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)  
 <span data-ttu-id="d841f-120">Kalıcılık, izleme, boş ve işlenmeyen özel durum davranışını denetlemek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="d841f-120">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d841f-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="d841f-121">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="d841f-122">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="d841f-122">Related Sections</span></span>  
 [<span data-ttu-id="d841f-123">İş Akışı Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="d841f-123">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
