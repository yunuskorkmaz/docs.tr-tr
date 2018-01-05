---
title: "LINQ ileti sorgu bağıntısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1207f371da5b447903e2846229860fd8c214a46e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="7f9e4-102">LINQ ileti sorgu bağıntısı</span><span class="sxs-lookup"><span data-stu-id="7f9e4-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="7f9e4-103">Bu örnek özel bir kullanılarak içerik tabanlı bağıntı bunu nasıl yapacağınızı gösterir <xref:System.ServiceModel.Dispatcher.MessageQuery> sistem tarafından sağlanan aksine uygulama <xref:System.ServiceModel.XPathMessageQuery>.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7f9e4-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="7f9e4-104">Demonstrates</span></span>  
 <span data-ttu-id="7f9e4-105">Özel <xref:System.ServiceModel.Dispatcher.MessageQuery>, içerik tabanlı bağıntı.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="7f9e4-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="7f9e4-106">Discussion</span></span>  
 <span data-ttu-id="7f9e4-107">Bu örnek, gelen genişletmek gösterilmiştir <xref:System.ServiceModel.Dispatcher.MessageQuery> bağıntı amaçları doğrultusunda temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="7f9e4-108">Özel uygulama `LinqMessageQuery`, kullanıcıların XLinq kullanarak iletisi içinde bulmak için bir XName belirtmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="7f9e4-109">Sorgu tarafından alınan veri uygun iş akışı örneği iletileri gönderme bağıntı anahtarı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7f9e4-110">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="7f9e4-110">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7f9e4-111">Bu örnek, HTTP uç noktalarını kullanarak bir iş akışı hizmeti kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="7f9e4-112">Bu örnek, uygun URL ACL çalıştırmak için eklenmesi gerekir (bkz [yapılandırma HTTP ve HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için), Visual Studio Yönetici olarak çalıştırarak veya uygun ACL'ler eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu çalıştırarak.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="7f9e4-113">Etki alanı ve kullanıcı adı yerine emin olun.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  <span data-ttu-id="7f9e4-114">URL ACL eklendikten sonra aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1.  <span data-ttu-id="7f9e4-115">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-115">Build the solution.</span></span>  
  
    2.  <span data-ttu-id="7f9e4-116">Çözüme sağ tıklayıp seçerek birden çok başlangıç projesi ayarlama **başlangıç projelerini Ayarla**.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="7f9e4-117">Ekleme **hizmet** ve **istemci** (sırayla) birden fazla başlangıç projesi olarak.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3.  <span data-ttu-id="7f9e4-118">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-118">Run the application.</span></span> <span data-ttu-id="7f9e4-119">İstemci konsolunu bir sipariş göndermek, satın alma siparişi kimliği alma ve daha sonra sipariş onayı iş akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="7f9e4-120">Hizmet verme penceresi işlenmekte olan istek gösterir.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7f9e4-121">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7f9e4-122">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7f9e4-123">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7f9e4-124">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="7f9e4-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
