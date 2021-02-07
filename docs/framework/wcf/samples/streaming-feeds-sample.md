---
description: Daha fazla bilgi için bkz. akış akışları örneği
title: Akış Gerçekleştirme Örneği
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 1de295391316396d6c454496d34d8b82ad8129d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668755"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="3b22b-103">Akış Gerçekleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="3b22b-103">Streaming Feeds Sample</span></span>

<span data-ttu-id="3b22b-104">Bu örnek, çok sayıda öğe içeren dağıtım akışlarının nasıl yönetileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b22b-104">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="3b22b-105">Sunucusunda, örnek, <xref:System.ServiceModel.Syndication.SyndicationItem> öğe ağ akışına yazılmadan önce, akış içinde tek tek nesnelerin oluşturulmasına nasıl geciktirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b22b-105">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="3b22b-106">İstemcide, bu örnek, okunan akışın hiçbir şekilde bellekte tam olarak arabelleğe alınabilmesi için ağ akışından tek tek öğeleri okumak için özel bir dağıtım akış biçimlendiricinin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b22b-106">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="3b22b-107">Bu örnek, dağıtım API 'sinin akış yeteneğini en iyi şekilde göstermek için, sunucunun sonsuz sayıda öğe içeren bir akışı kullanıma sunduğunu belirten, olası bir senaryoyu kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b22b-107">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="3b22b-108">Bu durumda, sunucu akışın akıştan belirtilen sayıda öğeyi okuduğunuzu (varsayılan olarak 10) bulana kadar akışa yeni öğe oluşturmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="3b22b-108">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="3b22b-109">Basitlik için hem istemci hem de sunucu aynı işleme uygulanır ve `ItemCounter` istemcinin kaç öğe üretmekte olduğunu izlemek için paylaşılan bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b22b-109">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="3b22b-110">`ItemCounter`Tür yalnızca örnek senaryonun düzgün sonlandırılmasına izin vermek için vardır ve gösterilen deseninin bir çekirdek öğesi değildir.</span><span class="sxs-lookup"><span data-stu-id="3b22b-110">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="3b22b-111">Demo, Visual C# yineleyicilerinin kullanımını ( `yield return` anahtar sözcük yapısını kullanarak) kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b22b-111">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="3b22b-112">Yineleyiciler hakkında daha fazla bilgi için MSDN 'deki "yineleyiciler kullanma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="3b22b-112">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="3b22b-113">Hizmet</span><span class="sxs-lookup"><span data-stu-id="3b22b-113">Service</span></span>  

 <span data-ttu-id="3b22b-114">Hizmet, <xref:System.ServiceModel.Web.WebGetAttribute> aşağıdaki kodda gösterildiği gibi, bir işlemden oluşan temel bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="3b22b-114">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="3b22b-115">Hizmet, `ItemGenerator` <xref:System.ServiceModel.Syndication.SyndicationItem> aşağıdaki kodda gösterildiği gibi bir yineleyici kullanarak muhtemelen sınırsız bir örnek akışı oluşturmak için bir sınıf kullanarak bu sözleşmeyi uygular.</span><span class="sxs-lookup"><span data-stu-id="3b22b-115">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="3b22b-116">Hizmet uygulamasının akışı oluşturduğunda, çıkışı, `ItemGenerator.GenerateItems()` arabelleğe alınmış bir öğe koleksiyonu yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b22b-116">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="3b22b-117">Sonuç olarak, öğe akışının hiçbir şekilde bellekte tam olarak arabelleğe alınmayacağı.</span><span class="sxs-lookup"><span data-stu-id="3b22b-117">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="3b22b-118">Yöntemin içindeki bildiriminde bir kesme noktası ayarlayarak `yield return` `ItemGenerator.GenerateItems()` ve bu kesme noktasının, hizmetin yöntemin sonucunu döndürdüğünden ilk kez karşılaşdığını belirten bu davranışı gözlemleyebilirsiniz `StreamedFeed()` .</span><span class="sxs-lookup"><span data-stu-id="3b22b-118">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="3b22b-119">İstemci</span><span class="sxs-lookup"><span data-stu-id="3b22b-119">Client</span></span>  

 <span data-ttu-id="3b22b-120">Bu örnekteki istemci, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> her bir öğenin, bunları belleğe almak yerine akıştaki bireysel öğelerin bir şekilde kullanılmasını gecikme özel bir uygulama kullanır.</span><span class="sxs-lookup"><span data-stu-id="3b22b-120">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="3b22b-121">Özel `StreamedAtom10FeedFormatter` örnek aşağıdaki gibi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3b22b-121">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="3b22b-122">Normalde, ' a yapılan bir çağrı, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> akışın tüm içeriği ağdan okunana ve belleğe arabelleğe alınana kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="3b22b-122">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="3b22b-123">Ancak, `StreamedAtom10FeedFormatter` nesne, <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> aşağıdaki kodda gösterildiği gibi, arabelleğe alınmış bir koleksiyon yerine bir yineleyici döndürecek şekilde geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3b22b-123">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="3b22b-124">Sonuç olarak, sonuçları geçen istemci uygulama tarafından kullanıma hazırlanana kadar her öğe ağdan okunmaz `ReadItems()` .</span><span class="sxs-lookup"><span data-stu-id="3b22b-124">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="3b22b-125">Bu davranışı, ' ın içindeki bildiriminde bir kesme noktası ayarlayarak `yield return` `StreamedAtom10FeedFormatter.DelayReadItems()` ve bu kesme noktasının, çağrının tamamlanmasından sonra ilk kez karşılaşdığını yaşıyorsanız ile gözlemleyebilirsiniz `ReadFrom()` .</span><span class="sxs-lookup"><span data-stu-id="3b22b-125">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="3b22b-126">Aşağıdaki yönergelerde örneği oluşturma ve çalıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3b22b-126">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="3b22b-127">İstemci 10 öğe okuduktan sonra sunucu öğeleri oluşturmayı durdursa da çıkış, istemcinin 10 ' dan fazla öğeden çok önemli bir şekilde okuduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3b22b-127">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="3b22b-128">Bunun nedeni, örnek tarafından kullanılan ağ bağlamasının verileri dört kilobayt (KB) kesimlerde iletmesidir.</span><span class="sxs-lookup"><span data-stu-id="3b22b-128">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="3b22b-129">Bu nedenle, istemci, daha önce bir öğe okumak için bir tane olmak üzere 4KB 'lık öğe verileri alır.</span><span class="sxs-lookup"><span data-stu-id="3b22b-129">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="3b22b-130">Bu normal davranıştır (makul ölçekli kesimlerde akış HTTP verileri gönderilmesi performansı artırır).</span><span class="sxs-lookup"><span data-stu-id="3b22b-130">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3b22b-131">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3b22b-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3b22b-132">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3b22b-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3b22b-133">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3b22b-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3b22b-134">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3b22b-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3b22b-135">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3b22b-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3b22b-136">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3b22b-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3b22b-137">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3b22b-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3b22b-138">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3b22b-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="3b22b-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b22b-139">See also</span></span>

- [<span data-ttu-id="3b22b-140">Bağımsız Tanılama Akışı</span><span class="sxs-lookup"><span data-stu-id="3b22b-140">Stand-Alone Diagnostics Feed</span></span>](stand-alone-diagnostics-feed-sample.md)
