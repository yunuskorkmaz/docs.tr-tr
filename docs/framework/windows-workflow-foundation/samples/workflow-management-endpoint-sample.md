---
title: İş akışı Yönetimi uç nokta örneği
ms.date: 03/30/2017
ms.assetid: 3ac6e08f-c43d-4bb7-83c3-e3890a4dac03
ms.openlocfilehash: 3d99cbef20895381f5e40ee939e1d94a409f1391
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873295"
---
# <a name="workflow-management-endpoint-sample"></a><span data-ttu-id="a2763-102">İş akışı Yönetimi uç nokta örneği</span><span class="sxs-lookup"><span data-stu-id="a2763-102">Workflow Management Endpoint Sample</span></span>
<span data-ttu-id="a2763-103">Bu örnek, bir iş akışı denetim uç noktası oluşturma ve yerel olarak ve Uzaktan iş akışlarını çalıştırmak için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2763-103">This sample shows how a workflow control endpoint can be used to create and run workflows both locally and remotely.</span></span> <span data-ttu-id="a2763-104">Örnek, bir denetim uç noktası ana bilgisayar ve istemcileri yazma gösterir oluşturmak ve bir iş akışı örneğini çalıştırmak için denetim uç noktası çağrısı.</span><span class="sxs-lookup"><span data-stu-id="a2763-104">The sample demonstrates how to host a control endpoint and write clients that call the control endpoint to create and run the instance of a workflow.</span></span> <span data-ttu-id="a2763-105">İş akışı, bir hizmeti değil.</span><span class="sxs-lookup"><span data-stu-id="a2763-105">The workflow is not a service.</span></span>  
  
 <span data-ttu-id="a2763-106">Örnek sunucusu tarafında WorkflowServiceHost ile iş akışı barındırılır ve istemcilerin denetimi işlemleri (askıya alma, Başlat, vb.) gerçekleştirebilmeleri için bir WorkflowControlEndpoint eklenir.</span><span class="sxs-lookup"><span data-stu-id="a2763-106">On the service side of the sample a workflow is hosted with WorkflowServiceHost and a WorkflowControlEndpoint is added so that clients can perform control operations (Suspend, Start, etc).</span></span> <span data-ttu-id="a2763-107">Kullanıcı tanımlı bir CreationEndpoint oluşturulacak iş akışının izin vermek için de eklenir.</span><span class="sxs-lookup"><span data-stu-id="a2763-107">A user-defined CreationEndpoint is also added to allow the workflow to be created.</span></span> <span data-ttu-id="a2763-108">Hizmet, ardından iş akışını askıya alınmış durumda başlatmak için bu uç noktaları kullanır ve ardından iş akışını sürdürmek.</span><span class="sxs-lookup"><span data-stu-id="a2763-108">The service then uses these endpoints to start the workflow in a suspended state and then resume the workflow.</span></span> <span data-ttu-id="a2763-109">İstemci aynı işlemleri gerçekleştirir. ancak bu, istemci kodu.</span><span class="sxs-lookup"><span data-stu-id="a2763-109">The client performs the same operations but from the client code.</span></span> <span data-ttu-id="a2763-110">Bunlar hakkında daha fazla bilgi için bkz arabirimleri için [iş akışı denetim uç noktası](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) ve [nasıl yapılır: IIS'de hizmet olmayan iş akışı barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span><span class="sxs-lookup"><span data-stu-id="a2763-110">For more information about these interfaces see, [Workflow Control Endpoint](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) and [How to: Host a non-service workflow in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-non-service-workflow-in-iis.md)</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="a2763-111">Örnek çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a2763-111">To run the sample</span></span>  
  
1.  <span data-ttu-id="a2763-112">Çalıştırma [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] yönetici ayrıcalıklarına sahip.</span><span class="sxs-lookup"><span data-stu-id="a2763-112">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator privileges.</span></span>  
  
2.  <span data-ttu-id="a2763-113">ManagementEndpoint.sln çözümde açık [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2763-113">Open the ManagementEndpoint.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
3.  <span data-ttu-id="a2763-114">Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın veya seçin **Çözümü Derle** gelen **derleme** menüsü.</span><span class="sxs-lookup"><span data-stu-id="a2763-114">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
4.  <span data-ttu-id="a2763-115">ManagementEndpoint.exe uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="a2763-115">Start the ManagementEndpoint.exe application.</span></span>  
  
5.  <span data-ttu-id="a2763-116">Client.exe uygulamayı başlatın.</span><span class="sxs-lookup"><span data-stu-id="a2763-116">Start the Client.exe application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a2763-117">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="a2763-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a2763-118">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a2763-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a2763-119">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="a2763-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a2763-120">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a2763-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ManagementEndpoint`