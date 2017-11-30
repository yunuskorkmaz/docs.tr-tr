---
title: "İş akışı Yönetimi uç nokta örnek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a6be74ba917a8684571a64394ec902cf51bc67bd
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="workflow-management-endpoint-sample"></a><span data-ttu-id="9be29-102">İş akışı Yönetimi uç nokta örnek</span><span class="sxs-lookup"><span data-stu-id="9be29-102">Workflow Management Endpoint Sample</span></span>
<span data-ttu-id="9be29-103">Bu örnek, bir iş akışı denetim uç noktası oluşturmak ve iş akışları hem yerel hem de uzaktan çalıştırmak için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9be29-103">This sample shows how a workflow control endpoint can be used to create and run workflows both locally and remotely.</span></span> <span data-ttu-id="9be29-104">Örnek bir denetim uç noktası ana bilgisayar ve istemcileri yazma nasıl oluşturulduğunu gösteren oluşturmak ve bir iş akışı örneği çalıştırmak için denetim uç noktası çağırın.</span><span class="sxs-lookup"><span data-stu-id="9be29-104">The sample demonstrates how to host a control endpoint and write clients that call the control endpoint to create and run the instance of a workflow.</span></span> <span data-ttu-id="9be29-105">İş akışı bir hizmeti değil.</span><span class="sxs-lookup"><span data-stu-id="9be29-105">The workflow is not a service.</span></span>  
  
 <span data-ttu-id="9be29-106">Örnek hizmet tarafında WorkflowServiceHost ile iş akışı barındırılır ve istemcilerin denetimi işlemleri (askıya alma, Başlat, vb.) gerçekleştirebilmeleri için bir WorkflowControlEndpoint eklenir.</span><span class="sxs-lookup"><span data-stu-id="9be29-106">On the service side of the sample a workflow is hosted with WorkflowServiceHost and a WorkflowControlEndpoint is added so that clients can perform control operations (Suspend, Start, etc).</span></span> <span data-ttu-id="9be29-107">Kullanıcı tanımlı bir CreationEndpoint, iş akışının oluşturulmasına izin de eklenir.</span><span class="sxs-lookup"><span data-stu-id="9be29-107">A user-defined CreationEndpoint is also added to allow the workflow to be created.</span></span> <span data-ttu-id="9be29-108">Hizmet askıya alınmış durumda iş akışını başlatmak için bu uç noktalar kullanır ve iş akışını devam ettirin.</span><span class="sxs-lookup"><span data-stu-id="9be29-108">The service then uses these endpoints to start the workflow in a suspended state and then resume the workflow.</span></span> <span data-ttu-id="9be29-109">İstemci aynı işlemleri gerçekleştirir ancak istemci kodu.</span><span class="sxs-lookup"><span data-stu-id="9be29-109">The client performs the same operations but from the client code.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9be29-110">Bu arabirimleri bakın, [iş akışı denetim uç noktası](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) ve [nasıl yapılır: IIS'de hizmet olmayan iş akışı barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span><span class="sxs-lookup"><span data-stu-id="9be29-110"> these interfaces see, [Workflow Control Endpoint](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) and [How to: Host a non-service workflow in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="9be29-111">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9be29-111">To run the sample</span></span>  
  
1.  <span data-ttu-id="9be29-112">Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici ayrıcalıklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="9be29-112">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="9be29-113">ManagementEndpoint.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9be29-113">Open the ManagementEndpoint.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="9be29-114">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="9be29-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
4.  <span data-ttu-id="9be29-115">ManagementEndpoint.exe uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="9be29-115">Start the ManagementEndpoint.exe application.</span></span>  
  
5.  <span data-ttu-id="9be29-116">Client.exe uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="9be29-116">Start the Client.exe application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9be29-117">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="9be29-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9be29-118">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9be29-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9be29-119">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="9be29-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9be29-120">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9be29-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`