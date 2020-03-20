---
title: LINQ İleti Kuyruğu Bağıntısı
ms.date: 03/30/2017
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
ms.openlocfilehash: 507001b165efdcbe7c1e27a07749dbe2eafb468f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182799"
---
# <a name="linq-message-query-correlation"></a><span data-ttu-id="03b6f-102">LINQ İleti Kuyruğu Bağıntısı</span><span class="sxs-lookup"><span data-stu-id="03b6f-102">LINQ Message Query Correlation</span></span>
<span data-ttu-id="03b6f-103">Bu örnek, sistem tarafından sağlanan <xref:System.ServiceModel.Dispatcher.MessageQuery> <xref:System.ServiceModel.XPathMessageQuery>ın aksine özel bir uygulama kullanarak içerik tabanlı korelasyonun nasıl yapılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="03b6f-103">This sample demonstrates how to do content-based correlation using a custom <xref:System.ServiceModel.Dispatcher.MessageQuery> implementation as opposed to the system-provided <xref:System.ServiceModel.XPathMessageQuery>.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="03b6f-104">Gösteriler</span><span class="sxs-lookup"><span data-stu-id="03b6f-104">Demonstrates</span></span>  
 <span data-ttu-id="03b6f-105">Özel <xref:System.ServiceModel.Dispatcher.MessageQuery>, Içerik Tabanlı Korelasyon.</span><span class="sxs-lookup"><span data-stu-id="03b6f-105">Custom <xref:System.ServiceModel.Dispatcher.MessageQuery>, Content-Based Correlation.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="03b6f-106">Tartışma</span><span class="sxs-lookup"><span data-stu-id="03b6f-106">Discussion</span></span>  
 <span data-ttu-id="03b6f-107">Bu örnek, korelasyon <xref:System.ServiceModel.Dispatcher.MessageQuery> amacıyla taban sınıftan nasıl genişletilecektir gösterir.</span><span class="sxs-lookup"><span data-stu-id="03b6f-107">This sample shows how to extend from the <xref:System.ServiceModel.Dispatcher.MessageQuery> base class for the purposes of correlation.</span></span> <span data-ttu-id="03b6f-108">Özel uygulama, `LinqMessageQuery`, kullanıcıların XLinq kullanarak mesaj içinde bulmak için bir XName sağlamak için izin verir.</span><span class="sxs-lookup"><span data-stu-id="03b6f-108">The custom implementation, `LinqMessageQuery`, allows users to provide an XName to find within the message using XLinq.</span></span> <span data-ttu-id="03b6f-109">Sorgu tarafından alınan veriler, iletileri uygun iş akışı örneğine göndermek için korelasyon anahtarını oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="03b6f-109">The data retrieved by the query is used to form the correlation key to dispatch messages to the appropriate workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="03b6f-110">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="03b6f-110">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="03b6f-111">Bu örnek, HTTP uç noktalarını kullanarak bir iş akışı hizmetini ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="03b6f-111">This sample exposes a workflow service using HTTP endpoints.</span></span> <span data-ttu-id="03b6f-112">Bu örneği çalıştırmak için, uygun URL ALA'ları eklenmelidir (ayrıntılar için [HTTP ve HTTPS yapılandırmaya](../../wcf/feature-details/configuring-http-and-https.md) bakınız), Visual Studio'yu Yönetici olarak çalıştırarak veya uygun ALA'ları eklemek için yükseltilmiş bir komut istemiyle aşağıdaki komutu çalıştırarak.</span><span class="sxs-lookup"><span data-stu-id="03b6f-112">To run this sample, proper URL ACLs must be added (see [Configuring HTTP and HTTPS](../../wcf/feature-details/configuring-http-and-https.md) for details), either by running Visual Studio as Administrator or by executing the following command at an elevated prompt to add the appropriate ACLs.</span></span> <span data-ttu-id="03b6f-113">Etki Alanınızın ve Kullanıcı Adınızın değiştirilip değiştirilediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="03b6f-113">Ensure that your Domain and Username are substituted.</span></span>  
  
    ```console  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2. <span data-ttu-id="03b6f-114">URL ALA'ları eklendikten sonra aşağıdaki adımları kullanın.</span><span class="sxs-lookup"><span data-stu-id="03b6f-114">Once the URL ACLs are added, use the following steps.</span></span>  
  
    1. <span data-ttu-id="03b6f-115">Çözümü derleyin.</span><span class="sxs-lookup"><span data-stu-id="03b6f-115">Build the solution.</span></span>  
  
    2. <span data-ttu-id="03b6f-116">Çözüme sağ tıklayarak ve **Başlangıç Projeleri Ayarla'yı**seçerek birden çok başlangıç projesi ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="03b6f-116">Set multiple start-up projects by right-clicking the solution and selecting **Set Startup Projects**.</span></span> <span data-ttu-id="03b6f-117">**Hizmet** ve **İstemciyi** (bu sırada) birden çok başlangıç projesi olarak ekleyin.</span><span class="sxs-lookup"><span data-stu-id="03b6f-117">Add **Service** and **Client** (in that order) as multiple start-up projects.</span></span>  
  
    3. <span data-ttu-id="03b6f-118">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="03b6f-118">Run the application.</span></span> <span data-ttu-id="03b6f-119">İstemci konsolu, sipariş gönderen ve satınalma siparişidini alan ve daha sonra siparişi onaylayan bir iş akışı gösterir.</span><span class="sxs-lookup"><span data-stu-id="03b6f-119">The client console shows a workflow  sending an order and receiving the purchase order id and then subsequently confirming the order.</span></span> <span data-ttu-id="03b6f-120">Hizmet penceresi, işlenen istekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="03b6f-120">The Service window will show the requests being processed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="03b6f-121">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="03b6f-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="03b6f-122">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="03b6f-122">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="03b6f-123">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="03b6f-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="03b6f-124">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="03b6f-124">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
