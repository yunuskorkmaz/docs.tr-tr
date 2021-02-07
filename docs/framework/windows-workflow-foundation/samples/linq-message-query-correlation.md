---
description: 'Daha fazla bilgi edinin: LINQ Ileti sorgusu bağıntısı'
title: LINQ İleti Kuyruğu Bağıntısı
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 7b979e3bdc2c0ede8f4f9d4595957f90581a0ecc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755284"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="a16cf-103">LINQ İleti Kuyruğu Bağıntısı</span><span class="sxs-lookup"><span data-stu-id="a16cf-103">LINQ Message Query Correlation</span></span>

<span data-ttu-id="a16cf-104">Bu örnek <xref:System.ServiceModel.Dispatcher.MessageQuery> , sistem tarafından sağlanın aksine özel bir uygulama kullanarak içerik tabanlı bağıntı oluşturmayı gösterir <xref:System.ServiceModel.XPathMessageQuery> .</span><span class="sxs-lookup"><span data-stu-id="a16cf-104">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="a16cf-105">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="a16cf-105">Demonstrates</span></span>  

 <span data-ttu-id="a16cf-106">Özel <xref:System.ServiceModel.Dispatcher.MessageQuery> , Içerik tabanlı bağıntı.</span><span class="sxs-lookup"><span data-stu-id="a16cf-106">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="a16cf-107">Tartışma</span><span class="sxs-lookup"><span data-stu-id="a16cf-107">Discussion</span></span>  

 <span data-ttu-id="a16cf-108">Bu örnek <xref:System.ServiceModel.Dispatcher.MessageQuery> , bağıntı amaçları doğrultusunda temel sınıftan genişletmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="a16cf-108">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="a16cf-109">Özel uygulama, `LinqMessageQuery` kullanıcıların Xlınq kullanarak ileti içinde bulmak için bir XName sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="a16cf-109">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="a16cf-110">Sorgu tarafından alınan veriler, uygun iş akışı örneğine ileti göndermek için bağıntı anahtarını oluşturmak üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a16cf-110">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a16cf-111">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="a16cf-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a16cf-112">Bu örnek, HTTP uç noktaları kullanarak bir iş akışı hizmeti sunar.</span><span class="sxs-lookup"><span data-stu-id="a16cf-112">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="a16cf-113">Bu örneği çalıştırmak için, doğru URL ACL 'Leri eklenmelidir (Ayrıntılar için bkz. [http ve https 'Yi yapılandırmak](../../wcf/feature-details/configuring-http-and-https.md) için), Visual Studio 'yu yönetici olarak çalıştırarak veya uygun ACL 'leri eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu yürüterek.</span><span class="sxs-lookup"><span data-stu-id="a16cf-113">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="a16cf-114">Etki alanı ve Kullanıcı adınızın yerini aldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="a16cf-114">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="a16cf-115">URL ACL 'Leri eklendikten sonra aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="a16cf-115">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="a16cf-116">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="a16cf-116">Build the solution.</span></span>  
  
    2. <span data-ttu-id="a16cf-117">Çözüme sağ tıklayıp **Başlangıç projelerini ayarla**' yı seçerek birden çok başlangıç projesi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a16cf-117">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="a16cf-118">**Hizmet** ve **istemci** (Bu sırada) birden çok başlangıç projesi olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a16cf-118">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="a16cf-119">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a16cf-119">Run the application.</span></span> <span data-ttu-id="a16cf-120">İstemci konsolu sipariş gönderen ve satın alma siparişi kimliğini alan ve ardından siparişi onaylayan bir iş akışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a16cf-120">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="a16cf-121">Hizmet penceresinde işlenmekte olan istekler gösterilir.</span><span class="sxs-lookup"><span data-stu-id="a16cf-121">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a16cf-122">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="a16cf-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a16cf-123">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a16cf-123">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a16cf-124">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="a16cf-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a16cf-125">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="a16cf-125">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
