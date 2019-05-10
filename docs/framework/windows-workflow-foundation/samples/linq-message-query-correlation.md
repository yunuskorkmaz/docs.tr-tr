---
title: LINQ İleti Kuyruğu Bağıntısı
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 5e979e6539d94d15b74f1da14f7082431ed2ff8c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622722"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="38ceb-102">LINQ İleti Kuyruğu Bağıntısı</span><span class="sxs-lookup"><span data-stu-id="38ceb-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="38ceb-103">Bu örnek özel bir kullanarak içerik temelli bağıntı yapmak nasıl gösterir <xref:System.ServiceModel.Dispatcher.MessageQuery> aksine, sistem tarafından sağlanan uygulama <xref:System.ServiceModel.XPathMessageQuery>.</span><span class="sxs-lookup"><span data-stu-id="38ceb-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="38ceb-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="38ceb-104">Demonstrates</span></span>  
 <span data-ttu-id="38ceb-105">Özel <xref:System.ServiceModel.Dispatcher.MessageQuery>, içerik temelli bağıntı.</span><span class="sxs-lookup"><span data-stu-id="38ceb-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="38ceb-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="38ceb-106">Discussion</span></span>  
 <span data-ttu-id="38ceb-107">Bu örnek nasıl gelen genişletileceğini gösterir <xref:System.ServiceModel.Dispatcher.MessageQuery> bağıntı amaçları için temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="38ceb-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="38ceb-108">Özel uygulama `LinqMessageQuery`, XLinq kullanarak ileti içinde bulunacak bir XName sağlamak kullanıcıların sağlar.</span><span class="sxs-lookup"><span data-stu-id="38ceb-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="38ceb-109">Sorgu tarafından alınan verileri, uygun iş akışı örneği iletileri gönderme bağıntı anahtar oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="38ceb-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="38ceb-110">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="38ceb-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="38ceb-111">Bu örnek, bir iş akışı hizmeti kullanarak HTTP uç noktalarını kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="38ceb-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="38ceb-112">Bu örnek, uygun URL ACL çalıştırılacak eklenmesi gerekir (bkz [yapılandırma HTTP ve HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) Ayrıntılar için), Visual Studio'yu yönetici olarak çalıştırdığınızdan veya uygun ACL'lerin eklemek için aşağıdaki komutu yükseltilmiş bir isteminde yürütülüyor.</span><span class="sxs-lookup"><span data-stu-id="38ceb-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="38ceb-113">Kullanıcı adı ve etki alanı başvurulduğunda emin olun.</span><span class="sxs-lookup"><span data-stu-id="38ceb-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="38ceb-114">URL ACL eklendikten sonra aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="38ceb-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="38ceb-115">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="38ceb-115">Build the solution.</span></span>  
  
    2. <span data-ttu-id="38ceb-116">Çözüme sağ tıklayıp seçerek birden çok başlangıç projesi ayarlama **başlangıç projelerini Ayarla**.</span><span class="sxs-lookup"><span data-stu-id="38ceb-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="38ceb-117">Ekleme **hizmet** ve **istemci** (bu sırayla) birden çok başlangıç projesi olarak.</span><span class="sxs-lookup"><span data-stu-id="38ceb-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="38ceb-118">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="38ceb-118">Run the application.</span></span> <span data-ttu-id="38ceb-119">İstemci konsolu bir sipariş göndermeden, Sipariş No alma ve daha sonra siparişi onaylayan bir iş akışı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="38ceb-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="38ceb-120">Hizmet verme penceresi işlenmekte olan istek gösterir.</span><span class="sxs-lookup"><span data-stu-id="38ceb-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="38ceb-121">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="38ceb-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="38ceb-122">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="38ceb-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="38ceb-123">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="38ceb-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="38ceb-124">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="38ceb-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
