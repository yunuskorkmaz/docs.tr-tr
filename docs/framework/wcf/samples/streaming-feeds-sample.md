---
title: Akış Gerçekleştirme Örneği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1eb5d8e0b19bc32ea5158d1614447b76f4924440
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="33798-102">Akış Gerçekleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="33798-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="33798-103">Bu örnek, çok sayıda öğe içeren dağıtım akışlarını yönetmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="33798-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="33798-104">Sunucu üzerinde örnek tek tek oluşturulması gecikme gösterilmiştir <xref:System.ServiceModel.Syndication.SyndicationItem> nesneleri hemen kadar akış içinde öğe ağ akışa yazılmadan önce.</span><span class="sxs-lookup"><span data-stu-id="33798-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="33798-105">İstemci üzerinde örnek akış biçimlendirici özel bir dağıtım okunan akışın belleğe hiçbir zaman tamamen arabelleğe alınıp böylece ayrı öğeleri ağ akıştan okumak için nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="33798-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="33798-106">En iyi dağıtım API akış yeteneğini göstermek için bu örnek sunucu sonsuz sayıda öğe içeren bir akış sunar biraz olası bir senaryo kullanır.</span><span class="sxs-lookup"><span data-stu-id="33798-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="33798-107">Bu durumda, sunucunun istemci belirtilen sayıda öğeyi akıştan (varsayılan olarak, 10) okuma izni olduğunu belirler kadar akışa yeni öğeler oluşturma devam eder.</span><span class="sxs-lookup"><span data-stu-id="33798-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="33798-108">Basitlik, hem istemci hem de sunucunun aynı işlem içinde uygulanan ve paylaşılan kullanın `ItemCounter` kaç istemci öğelerini izlemek için nesne üretilen.</span><span class="sxs-lookup"><span data-stu-id="33798-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="33798-109">`ItemCounter` Türü yalnızca düzgün bir şekilde sonlandırmak Örnek senaryo izin vermek amacıyla var ve gösterilen deseni çekirdek öğesi değil.</span><span class="sxs-lookup"><span data-stu-id="33798-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="33798-110">Visual C#, kullanan Tanıtımı yararlanır yineleyiciler (kullanarak `yield``return` anahtar sözcüğü yapı).</span><span class="sxs-lookup"><span data-stu-id="33798-110">The demonstration makes use of Visual C# iterators (using the `yield``return` keyword construct).</span></span> <span data-ttu-id="33798-111">Yineleyiciler hakkında daha fazla bilgi için MSDN'de "Yineleyiciler kullanma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="33798-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="33798-112">Hizmet</span><span class="sxs-lookup"><span data-stu-id="33798-112">Service</span></span>  
 <span data-ttu-id="33798-113">Temel bir hizmet uygulayan <xref:System.ServiceModel.Web.WebGetAttribute> aşağıdaki kodda gösterildiği gibi bir işleme, oluşur sözleşme.</span><span class="sxs-lookup"><span data-stu-id="33798-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="33798-114">Kullanarak bu sözleşme hizmeti uygulayan bir `ItemGenerator` olası sonsuz akışı oluşturmak için sınıf <xref:System.ServiceModel.Syndication.SyndicationItem> aşağıdaki kodda gösterildiği gibi bir yineleyici kullanarak örnekleri.</span><span class="sxs-lookup"><span data-stu-id="33798-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```  
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="33798-115">Hizmet uygulaması, akış çıkışı oluşturduğunda `ItemGenerator.GenerateItems()` arabelleğe alınan öğeleri koleksiyonu yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33798-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```  
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
```  
  
 <span data-ttu-id="33798-116">Sonuç olarak, öğesi akış belleğe hiçbir zaman tamamen arabelleğe alınıp.</span><span class="sxs-lookup"><span data-stu-id="33798-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="33798-117">Üzerinde bir kesme noktası ayarlayarak bu davranış gözlenir `yield``return` deyimi içinde `ItemGenerator.GenerateItems()` yöntemi ve bu kesme hizmet sonucu döndürdü sonra ilk kez karşılaşılana belirtmeye `StreamedFeed()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="33798-117">You can observe this behavior by setting a breakpoint on the `yield``return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="33798-118">İstemci</span><span class="sxs-lookup"><span data-stu-id="33798-118">Client</span></span>  
 <span data-ttu-id="33798-119">Özel bir istemcinin bu örnekteki <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> belleğe arabelleğe yerine akıştaki tek tek öğelerin materialization gecikmeler uygulama.</span><span class="sxs-lookup"><span data-stu-id="33798-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="33798-120">Özel `StreamedAtom10FeedFormatter` örneği aşağıdaki gibi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33798-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="33798-121">Normal olarak yapılan bir çağrı <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> akışın tüm içeriği ağdan okuyun ve belleğe arabelleğe kadar döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="33798-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="33798-122">Ancak, `StreamedAtom10FeedFormatter` Nesne geçersiz kılmaları <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> aşağıdaki kodda gösterildiği gibi yineleyici arabelleğe alınan bir koleksiyon yerine döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="33798-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
```  
  
 <span data-ttu-id="33798-123">Sonuç olarak, her bir öğeyi ağdan sonuçlarını çapraz geçiş yapan istemci uygulaması kadar okunamaz `ReadItems()` kullanmak hazırdır.</span><span class="sxs-lookup"><span data-stu-id="33798-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="33798-124">Üzerinde bir kesme noktası ayarlayarak bu davranış gözlenir `yield``return` deyimi içinde `StreamedAtom10FeedFormatter.DelayReadItems()` ve bu kesme çağrısından sonra ilk kez karşılaşılana haberiniz bile `ReadFrom()` tamamlar.</span><span class="sxs-lookup"><span data-stu-id="33798-124">You can observe this behavior by setting a breakpoint on the `yield``return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="33798-125">Aşağıdaki yönergeler, derlemeyi ve çalıştırmayı örnek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="33798-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="33798-126">Sunucunun istemci 10 Öğe Okuma sonra öğeleri oluşturma durdurur ancak çıktı istemci önemli ölçüde birden fazla 10 öğe okur gösterdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="33798-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="33798-127">Örnek tarafından kullanılan ağ bağlama dört kilobayt (KB) Segment veri aktaran olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="33798-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="33798-128">Bu nedenle, tek öğe okunur fırsatına sahip önce istemci 4 KB öğesi veri alır.</span><span class="sxs-lookup"><span data-stu-id="33798-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="33798-129">(Makul boyutlu kesimler artar performans akış HTTP veri gönderme) normal davranış budur.</span><span class="sxs-lookup"><span data-stu-id="33798-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="33798-130">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="33798-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="33798-131">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33798-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="33798-132">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33798-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="33798-133">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33798-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="33798-134">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="33798-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="33798-135">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="33798-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="33798-136">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="33798-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33798-137">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="33798-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="33798-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33798-138">See Also</span></span>  
 [<span data-ttu-id="33798-139">Bağımsız Tanılama Akışı</span><span class="sxs-lookup"><span data-stu-id="33798-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
