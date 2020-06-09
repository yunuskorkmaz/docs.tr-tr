---
title: Akış Gerçekleştirme Örneği
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 551a97f3cc54915a831fc28eca6ae0ff23101e0b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589792"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="9a085-102">Akış Gerçekleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="9a085-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="9a085-103">Bu örnek, çok sayıda öğe içeren dağıtım akışlarının nasıl yönetileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a085-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="9a085-104">Sunucusunda, örnek, <xref:System.ServiceModel.Syndication.SyndicationItem> öğe ağ akışına yazılmadan önce, akış içinde tek tek nesnelerin oluşturulmasına nasıl geciktirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a085-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="9a085-105">İstemcide, bu örnek, okunan akışın hiçbir şekilde bellekte tam olarak arabelleğe alınabilmesi için ağ akışından tek tek öğeleri okumak için özel bir dağıtım akış biçimlendiricinin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a085-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="9a085-106">Bu örnek, dağıtım API 'sinin akış yeteneğini en iyi şekilde göstermek için, sunucunun sonsuz sayıda öğe içeren bir akışı kullanıma sunduğunu belirten, olası bir senaryoyu kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a085-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="9a085-107">Bu durumda, sunucu akışın akıştan belirtilen sayıda öğeyi okuduğunuzu (varsayılan olarak 10) bulana kadar akışa yeni öğe oluşturmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="9a085-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="9a085-108">Basitlik için hem istemci hem de sunucu aynı işleme uygulanır ve `ItemCounter` istemcinin kaç öğe üretmekte olduğunu izlemek için paylaşılan bir nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a085-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="9a085-109">`ItemCounter`Tür yalnızca örnek senaryonun düzgün sonlandırılmasına izin vermek için vardır ve gösterilen deseninin bir çekirdek öğesi değildir.</span><span class="sxs-lookup"><span data-stu-id="9a085-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="9a085-110">Demo, Visual C# yineleyicilerinin kullanımını ( `yield return` anahtar sözcük yapısını kullanarak) kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a085-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="9a085-111">Yineleyiciler hakkında daha fazla bilgi için MSDN 'deki "yineleyiciler kullanma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="9a085-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="9a085-112">Hizmet</span><span class="sxs-lookup"><span data-stu-id="9a085-112">Service</span></span>  
 <span data-ttu-id="9a085-113">Hizmet, <xref:System.ServiceModel.Web.WebGetAttribute> aşağıdaki kodda gösterildiği gibi, bir işlemden oluşan temel bir sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="9a085-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="9a085-114">Hizmet, `ItemGenerator` <xref:System.ServiceModel.Syndication.SyndicationItem> aşağıdaki kodda gösterildiği gibi bir yineleyici kullanarak muhtemelen sınırsız bir örnek akışı oluşturmak için bir sınıf kullanarak bu sözleşmeyi uygular.</span><span class="sxs-lookup"><span data-stu-id="9a085-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="9a085-115">Hizmet uygulamasının akışı oluşturduğunda, çıkışı, `ItemGenerator.GenerateItems()` arabelleğe alınmış bir öğe koleksiyonu yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a085-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
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
  
 <span data-ttu-id="9a085-116">Sonuç olarak, öğe akışının hiçbir şekilde bellekte tam olarak arabelleğe alınmayacağı.</span><span class="sxs-lookup"><span data-stu-id="9a085-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="9a085-117">Yöntemin içindeki bildiriminde bir kesme noktası ayarlayarak `yield return` `ItemGenerator.GenerateItems()` ve bu kesme noktasının, hizmetin yöntemin sonucunu döndürdüğünden ilk kez karşılaşdığını belirten bu davranışı gözlemleyebilirsiniz `StreamedFeed()` .</span><span class="sxs-lookup"><span data-stu-id="9a085-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="9a085-118">İstemci</span><span class="sxs-lookup"><span data-stu-id="9a085-118">Client</span></span>  
 <span data-ttu-id="9a085-119">Bu örnekteki istemci, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> her bir öğenin, bunları belleğe almak yerine akıştaki bireysel öğelerin bir şekilde kullanılmasını gecikme özel bir uygulama kullanır.</span><span class="sxs-lookup"><span data-stu-id="9a085-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="9a085-120">Özel `StreamedAtom10FeedFormatter` örnek aşağıdaki gibi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9a085-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="9a085-121">Normalde, ' a yapılan bir çağrı, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> akışın tüm içeriği ağdan okunana ve belleğe arabelleğe alınana kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="9a085-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="9a085-122">Ancak, `StreamedAtom10FeedFormatter` nesne, <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> aşağıdaki kodda gösterildiği gibi, arabelleğe alınmış bir koleksiyon yerine bir yineleyici döndürecek şekilde geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9a085-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="9a085-123">Sonuç olarak, sonuçları geçen istemci uygulama tarafından kullanıma hazırlanana kadar her öğe ağdan okunmaz `ReadItems()` .</span><span class="sxs-lookup"><span data-stu-id="9a085-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="9a085-124">Bu davranışı, ' ın içindeki bildiriminde bir kesme noktası ayarlayarak `yield return` `StreamedAtom10FeedFormatter.DelayReadItems()` ve bu kesme noktasının, çağrının tamamlanmasından sonra ilk kez karşılaşdığını yaşıyorsanız ile gözlemleyebilirsiniz `ReadFrom()` .</span><span class="sxs-lookup"><span data-stu-id="9a085-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="9a085-125">Aşağıdaki yönergelerde örneği oluşturma ve çalıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9a085-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="9a085-126">İstemci 10 öğe okuduktan sonra sunucu öğeleri oluşturmayı durdursa da çıkış, istemcinin 10 ' dan fazla öğeden çok önemli bir şekilde okuduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="9a085-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="9a085-127">Bunun nedeni, örnek tarafından kullanılan ağ bağlamasının verileri dört kilobayt (KB) kesimlerde iletmesidir.</span><span class="sxs-lookup"><span data-stu-id="9a085-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="9a085-128">Bu nedenle, istemci, daha önce bir öğe okumak için bir tane olmak üzere 4KB 'lık öğe verileri alır.</span><span class="sxs-lookup"><span data-stu-id="9a085-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="9a085-129">Bu normal davranıştır (makul ölçekli kesimlerde akış HTTP verileri gönderilmesi performansı artırır).</span><span class="sxs-lookup"><span data-stu-id="9a085-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9a085-130">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="9a085-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9a085-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="9a085-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9a085-132">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9a085-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9a085-133">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="9a085-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9a085-134">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="9a085-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9a085-135">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="9a085-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9a085-136">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="9a085-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9a085-137">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="9a085-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="9a085-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a085-138">See also</span></span>

- [<span data-ttu-id="9a085-139">Bağımsız Tanılama Akışı</span><span class="sxs-lookup"><span data-stu-id="9a085-139">Stand-Alone Diagnostics Feed</span></span>](stand-alone-diagnostics-feed-sample.md)
