---
title: Akış Gerçekleştirme Örneği
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: ede1dbb4f5c682b8182dda4888a9cbd373b95dd8
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976369"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="20aef-102">Akış Gerçekleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="20aef-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="20aef-103">Bu örnek, çok sayıda öğe içeren dağıtım akışlarının nasıl yönetileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="20aef-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="20aef-104">Sunucusunda, örnek, öğe ağ akışına yazılmadan önce, akış içinde bireysel <xref:System.ServiceModel.Syndication.SyndicationItem> nesnelerinin oluşturulma süresinin nasıl geciktirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="20aef-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="20aef-105">İstemcide, bu örnek, okunan akışın hiçbir şekilde bellekte tam olarak arabelleğe alınabilmesi için ağ akışından tek tek öğeleri okumak için özel bir dağıtım akış biçimlendiricinin nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="20aef-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="20aef-106">Bu örnek, dağıtım API 'sinin akış yeteneğini en iyi şekilde göstermek için, sunucunun sonsuz sayıda öğe içeren bir akışı kullanıma sunduğunu belirten, olası bir senaryoyu kullanır.</span><span class="sxs-lookup"><span data-stu-id="20aef-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="20aef-107">Bu durumda, sunucu akışın akıştan belirtilen sayıda öğeyi okuduğunuzu (varsayılan olarak 10) bulana kadar akışa yeni öğe oluşturmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="20aef-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="20aef-108">Kolaylık olması için hem istemci hem de sunucu aynı işleme uygulanır ve istemcinin kaç öğe üretmekte olduğunu izlemek için paylaşılan bir `ItemCounter` nesnesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="20aef-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="20aef-109">`ItemCounter` türü yalnızca örnek senaryonun düzgün sonlandırılmasına izin vermek için vardır ve gösterilen deseninin bir çekirdek öğesi değildir.</span><span class="sxs-lookup"><span data-stu-id="20aef-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="20aef-110">Gösterim, görsel C# yineleyiciler (`yield return` anahtar sözcük yapısını kullanarak) kullanır.</span><span class="sxs-lookup"><span data-stu-id="20aef-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="20aef-111">Yineleyiciler hakkında daha fazla bilgi için MSDN 'deki "yineleyiciler kullanma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="20aef-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="20aef-112">Hizmet</span><span class="sxs-lookup"><span data-stu-id="20aef-112">Service</span></span>  
 <span data-ttu-id="20aef-113">Hizmet, aşağıdaki kodda gösterildiği gibi, bir işlemden oluşan temel bir <xref:System.ServiceModel.Web.WebGetAttribute> sözleşme uygular.</span><span class="sxs-lookup"><span data-stu-id="20aef-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="20aef-114">Hizmet, aşağıdaki kodda gösterildiği gibi bir yineleyici kullanarak <xref:System.ServiceModel.Syndication.SyndicationItem> örneklerinin potansiyel olarak sonsuz bir akışını oluşturmak için bir `ItemGenerator` sınıfını kullanarak bu sözleşmeyi uygular.</span><span class="sxs-lookup"><span data-stu-id="20aef-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="20aef-115">Hizmet uygulama akışı oluşturduğunda, `ItemGenerator.GenerateItems()` çıkışı, arabelleğe alınmış bir öğe koleksiyonu yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20aef-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
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
  
 <span data-ttu-id="20aef-116">Sonuç olarak, öğe akışının hiçbir şekilde bellekte tam olarak arabelleğe alınmayacağı.</span><span class="sxs-lookup"><span data-stu-id="20aef-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="20aef-117">`ItemGenerator.GenerateItems()` yönteminin içindeki `yield return` bildiriminde bir kesme noktası ayarlayarak ve bu kesme noktasının, hizmet `StreamedFeed()` yönteminin sonucunu döndürdüğünden ilk kez ilgili olduğunu belirterek bu davranışı gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20aef-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="20aef-118">İstemci</span><span class="sxs-lookup"><span data-stu-id="20aef-118">Client</span></span>  
 <span data-ttu-id="20aef-119">Bu örnekteki istemci, akışa arabelleğe almak yerine akıştaki tek tek öğelerin bir kez uygulanmasını gecikmesi için özel bir <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> uygulamasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="20aef-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="20aef-120">Özel `StreamedAtom10FeedFormatter` örneği aşağıdaki gibi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="20aef-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="20aef-121">Normalde, bir <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> çağrısı, akışın tüm içeriği ağdan okunana ve belleğe arabelleğe alınana kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="20aef-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="20aef-122">Ancak, `StreamedAtom10FeedFormatter` nesnesi, aşağıdaki kodda gösterildiği gibi, arabelleğe alınmış bir koleksiyon yerine bir yineleyici döndürecek şekilde <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="20aef-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="20aef-123">Sonuç olarak, `ReadItems()` sonuçlarından geçen istemci uygulaması tarafından kullanıma hazırlanana kadar her öğe ağdan okunmaz.</span><span class="sxs-lookup"><span data-stu-id="20aef-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="20aef-124">Bu davranışı, `StreamedAtom10FeedFormatter.DelayReadItems()` içindeki `yield return` bildiriminde bir kesme noktası ayarlayarak ve bu kesme noktasının `ReadFrom()` tamamlandıktan sonra ilk kez karşılaşdığını gözlemleyerek gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20aef-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="20aef-125">Aşağıdaki yönergelerde örneği oluşturma ve çalıştırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="20aef-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="20aef-126">İstemci 10 öğe okuduktan sonra sunucu öğeleri oluşturmayı durdursa da çıkış, istemcinin 10 ' dan fazla öğeden çok önemli bir şekilde okuduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="20aef-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="20aef-127">Bunun nedeni, örnek tarafından kullanılan ağ bağlamasının verileri dört kilobayt (KB) kesimlerde iletmesidir.</span><span class="sxs-lookup"><span data-stu-id="20aef-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="20aef-128">Bu nedenle, istemci, daha önce bir öğe okumak için bir tane olmak üzere 4KB 'lık öğe verileri alır.</span><span class="sxs-lookup"><span data-stu-id="20aef-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="20aef-129">Bu normal davranıştır (makul ölçekli kesimlerde akış HTTP verileri gönderilmesi performansı artırır).</span><span class="sxs-lookup"><span data-stu-id="20aef-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="20aef-130">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="20aef-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="20aef-131">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="20aef-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="20aef-132">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="20aef-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="20aef-133">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="20aef-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="20aef-134">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="20aef-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="20aef-135">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="20aef-135">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="20aef-136">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin.</span><span class="sxs-lookup"><span data-stu-id="20aef-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20aef-137">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="20aef-137">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="20aef-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20aef-138">See also</span></span>

- [<span data-ttu-id="20aef-139">Bağımsız Tanılama Akışı</span><span class="sxs-lookup"><span data-stu-id="20aef-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
