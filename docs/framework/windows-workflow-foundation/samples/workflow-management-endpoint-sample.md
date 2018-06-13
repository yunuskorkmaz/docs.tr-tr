---
title: İş akışı Yönetimi uç nokta örnek
ms.date: 03/30/2017
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
ms.openlocfilehash: e34a23f76edbd957b1be7caff1b18f6934b1588b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517105"
---
# <a name="workflow-management-endpoint-sample"></a><span data-ttu-id="218b1-102">İş akışı Yönetimi uç nokta örnek</span><span class="sxs-lookup"><span data-stu-id="218b1-102">Workflow Management Endpoint Sample</span></span>
<span data-ttu-id="218b1-103">Bu örnek, bir iş akışı denetim uç noktası oluşturmak ve iş akışları hem yerel hem de uzaktan çalıştırmak için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="218b1-103">This sample shows how a workflow control endpoint can be used to create and run workflows both locally and remotely.</span></span> <span data-ttu-id="218b1-104">Örnek bir denetim uç noktası ana bilgisayar ve istemcileri yazma nasıl oluşturulduğunu gösteren oluşturmak ve bir iş akışı örneği çalıştırmak için denetim uç noktası çağırın.</span><span class="sxs-lookup"><span data-stu-id="218b1-104">The sample demonstrates how to host a control endpoint and write clients that call the control endpoint to create and run the instance of a workflow.</span></span> <span data-ttu-id="218b1-105">İş akışı bir hizmeti değil.</span><span class="sxs-lookup"><span data-stu-id="218b1-105">The workflow is not a service.</span></span>  
  
 <span data-ttu-id="218b1-106">Örnek hizmet tarafında WorkflowServiceHost ile iş akışı barındırılır ve istemcilerin denetimi işlemleri (askıya alma, Başlat, vb.) gerçekleştirebilmeleri için bir WorkflowControlEndpoint eklenir.</span><span class="sxs-lookup"><span data-stu-id="218b1-106">On the service side of the sample a workflow is hosted with WorkflowServiceHost and a WorkflowControlEndpoint is added so that clients can perform control operations (Suspend, Start, etc).</span></span> <span data-ttu-id="218b1-107">Kullanıcı tanımlı bir CreationEndpoint, iş akışının oluşturulmasına izin de eklenir.</span><span class="sxs-lookup"><span data-stu-id="218b1-107">A user-defined CreationEndpoint is also added to allow the workflow to be created.</span></span> <span data-ttu-id="218b1-108">Hizmet askıya alınmış durumda iş akışını başlatmak için bu uç noktalar kullanır ve iş akışını devam ettirin.</span><span class="sxs-lookup"><span data-stu-id="218b1-108">The service then uses these endpoints to start the workflow in a suspended state and then resume the workflow.</span></span> <span data-ttu-id="218b1-109">İstemci aynı işlemleri gerçekleştirir ancak istemci kodu.</span><span class="sxs-lookup"><span data-stu-id="218b1-109">The client performs the same operations but from the client code.</span></span> <span data-ttu-id="218b1-110">Bunlar hakkında daha fazla bilgi için bkz arabirimleri için [iş akışı denetim uç noktası](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) ve [nasıl yapılır: IIS'de hizmet olmayan iş akışı barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span><span class="sxs-lookup"><span data-stu-id="218b1-110">For more information about these interfaces see, [Workflow Control Endpoint](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) and [How to: Host a non-service workflow in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="218b1-111">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="218b1-111">To run the sample</span></span>  
  
1.  <span data-ttu-id="218b1-112">Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici ayrıcalıklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="218b1-112">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="218b1-113">ManagementEndpoint.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="218b1-113">Open the ManagementEndpoint.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="218b1-114">Çözümü derlemek için CTRL + SHIFT + B tuşuna basın veya seçin **yapı çözümü** gelen **yapı** menüsü.</span><span class="sxs-lookup"><span data-stu-id="218b1-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
4.  <span data-ttu-id="218b1-115">ManagementEndpoint.exe uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="218b1-115">Start the ManagementEndpoint.exe application.</span></span>  
  
5.  <span data-ttu-id="218b1-116">Client.exe uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="218b1-116">Start the Client.exe application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="218b1-117">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="218b1-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="218b1-118">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="218b1-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="218b1-119">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="218b1-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="218b1-120">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="218b1-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`