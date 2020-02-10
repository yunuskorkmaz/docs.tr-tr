---
title: LINQ İleti Kuyruğu Bağıntısı
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: cd91a171f3242cfd7e8ac0404e24ac065919bcce
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094624"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="138ad-102">LINQ İleti Kuyruğu Bağıntısı</span><span class="sxs-lookup"><span data-stu-id="138ad-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="138ad-103">Bu örnek, sistem tarafından sağlanmış <xref:System.ServiceModel.XPathMessageQuery>aksine özel bir <xref:System.ServiceModel.Dispatcher.MessageQuery> uygulamasını kullanarak içerik tabanlı bağıntı oluşturmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="138ad-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="138ad-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="138ad-104">Demonstrates</span></span>  
 <span data-ttu-id="138ad-105">Özel <xref:System.ServiceModel.Dispatcher.MessageQuery>, Içerik tabanlı bağıntı.</span><span class="sxs-lookup"><span data-stu-id="138ad-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="138ad-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="138ad-106">Discussion</span></span>  
 <span data-ttu-id="138ad-107">Bu örnek, bağıntı amaçları doğrultusunda <xref:System.ServiceModel.Dispatcher.MessageQuery> temel sınıftan genişletmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="138ad-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="138ad-108">`LinqMessageQuery`özel uygulama, kullanıcıların Xlınq kullanarak ileti içinde bulmak için bir XName sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="138ad-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="138ad-109">Sorgu tarafından alınan veriler, uygun iş akışı örneğine ileti göndermek için bağıntı anahtarını oluşturmak üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="138ad-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="138ad-110">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="138ad-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="138ad-111">Bu örnek, HTTP uç noktaları kullanarak bir iş akışı hizmeti sunar.</span><span class="sxs-lookup"><span data-stu-id="138ad-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="138ad-112">Bu örneği çalıştırmak için, doğru URL ACL 'Leri eklenmelidir (Ayrıntılar için bkz. [http ve https 'Yi yapılandırmak](../../wcf/feature-details/configuring-http-and-https.md) için), Visual Studio 'yu yönetici olarak çalıştırarak veya uygun ACL 'leri eklemek için yükseltilmiş bir komut isteminde aşağıdaki komutu yürüterek.</span><span class="sxs-lookup"><span data-stu-id="138ad-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="138ad-113">Etki alanı ve Kullanıcı adınızın yerini aldığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="138ad-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="138ad-114">URL ACL 'Leri eklendikten sonra aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="138ad-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="138ad-115">Çözümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="138ad-115">Build the solution.</span></span>  
  
    2. <span data-ttu-id="138ad-116">Çözüme sağ tıklayıp **Başlangıç projelerini ayarla**' yı seçerek birden çok başlangıç projesi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="138ad-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="138ad-117">**Hizmet** ve **istemci** (Bu sırada) birden çok başlangıç projesi olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="138ad-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="138ad-118">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="138ad-118">Run the application.</span></span> <span data-ttu-id="138ad-119">İstemci konsolu sipariş gönderen ve satın alma siparişi kimliğini alan ve ardından siparişi onaylayan bir iş akışını gösterir.</span><span class="sxs-lookup"><span data-stu-id="138ad-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="138ad-120">Hizmet penceresinde işlenmekte olan istekler gösterilir.</span><span class="sxs-lookup"><span data-stu-id="138ad-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="138ad-121">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="138ad-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="138ad-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="138ad-122">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="138ad-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="138ad-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="138ad-124">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="138ad-124">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
