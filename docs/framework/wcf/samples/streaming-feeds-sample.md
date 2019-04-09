---
title: Akış Gerçekleştirme Örneği
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: cc09d4c7d0e9ff75806c1c5e9d3ec1ef77507638
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172451"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="3c8da-102">Akış Gerçekleştirme Örneği</span><span class="sxs-lookup"><span data-stu-id="3c8da-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="3c8da-103">Bu örnek çok sayıda öğe içeren dağıtım akışlarını yönetmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c8da-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="3c8da-104">Sunucuda örnek tek tek oluşturulması gecikme yapmayı gösteren <xref:System.ServiceModel.Syndication.SyndicationItem> nesneleri hemen kadar akışın içinde öğe ağ akışa yazılmadan önce.</span><span class="sxs-lookup"><span data-stu-id="3c8da-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="3c8da-105">İstemcide, örnek okunan akışın belleğe hiçbir zaman tam olarak yürütülmeden, tek tek öğeleri ağ akışından okunacak akış biçimlendirici bir özel dağıtım'ın nasıl kullanılabileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c8da-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="3c8da-106">En iyi API dağıtım akış yeteneğini göstermek için bu örnek sunucu sonsuz sayıda öğe içeren bir akış kullanıma sunan biraz olası bir senaryo kullanır.</span><span class="sxs-lookup"><span data-stu-id="3c8da-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="3c8da-107">Bu durumda, sunucunun istemci (varsayılan: 10) akıştan belirtilen sayıda öğeyi okudu belirler kadar yeni öğeler akış oluşturma devam eder.</span><span class="sxs-lookup"><span data-stu-id="3c8da-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="3c8da-108">Kolaylık olması için istemci ve sunucu aynı işlem içinde uygulanır ve paylaşılan kullanın `ItemCounter` kaç istemci öğelerini izlemek için nesne oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="3c8da-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="3c8da-109">`ItemCounter` Türü amacı doğrultusunda yalnızca düzgün bir şekilde sonlandırmak Örnek senaryo izin vererek var ve gösterilen düzeninin bir çekirdek öğesi değil.</span><span class="sxs-lookup"><span data-stu-id="3c8da-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="3c8da-110">Tanıtım Visual C#, yararlanır yineleyiciler (kullanarak `yield return` anahtar sözcüğü yapısı).</span><span class="sxs-lookup"><span data-stu-id="3c8da-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="3c8da-111">Yineleyiciler hakkında daha fazla bilgi için MSDN'de "Yineleyicileri kullanma" konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="3c8da-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="3c8da-112">Hizmet</span><span class="sxs-lookup"><span data-stu-id="3c8da-112">Service</span></span>  
 <span data-ttu-id="3c8da-113">Temel hizmeti uygulayan <xref:System.ServiceModel.Web.WebGetAttribute> aşağıdaki kodda gösterildiği gibi bir işleme, oluşan sözleşme.</span><span class="sxs-lookup"><span data-stu-id="3c8da-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="3c8da-114">Kullanarak, bu sözleşme hizmeti uygulayan bir `ItemGenerator` olası sonsuz bir akışı oluşturmak için sınıf <xref:System.ServiceModel.Syndication.SyndicationItem> aşağıdaki kodda gösterildiği gibi bir yineleyici kullanarak örnekler.</span><span class="sxs-lookup"><span data-stu-id="3c8da-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="3c8da-115">Hizmet uygulaması, akışın çıkışına oluşturduğunda `ItemGenerator.GenerateItems()` arabelleğe alınan öğelerin koleksiyonunu yerine kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c8da-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
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
  
 <span data-ttu-id="3c8da-116">Sonuç olarak, akış öğesi hiçbir zaman tam olarak belleğe yürütülmeden.</span><span class="sxs-lookup"><span data-stu-id="3c8da-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="3c8da-117">Üzerinde bir kesme noktası ayarlayarak bu davranış gözlenir `yield return` deyimi içinde `ItemGenerator.GenerateItems()` yöntemi ve bu Kesme noktasının hizmet sonucunu verdi sonra ilk kez karşılaşılanaa belirtmeye `StreamedFeed()` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3c8da-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="3c8da-118">İstemci</span><span class="sxs-lookup"><span data-stu-id="3c8da-118">Client</span></span>  
 <span data-ttu-id="3c8da-119">Özel bir istemcinin bu <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> belleğe arabelleğe yerine akış içinde tek tek öğelerin materialization gecikmeler uygulama.</span><span class="sxs-lookup"><span data-stu-id="3c8da-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="3c8da-120">Özel `StreamedAtom10FeedFormatter` örneği şu şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c8da-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="3c8da-121">Normalde, bir çağrı <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> akışın tüm içeriği ağdan okuyun ve belleğe arabelleğe kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="3c8da-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="3c8da-122">Ancak, `StreamedAtom10FeedFormatter` Nesne geçersiz kılmaları <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> aşağıdaki kodda gösterildiği gibi bir yineleyici arabelleğe alınan bir koleksiyon yerine döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="3c8da-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="3c8da-123">Sonuç olarak, her öğe ağdan sonuçlarını geçiş istemci uygulaması kadar okunamaz `ReadItems()` , kullanıma hazır.</span><span class="sxs-lookup"><span data-stu-id="3c8da-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="3c8da-124">Üzerinde bir kesme noktası ayarlayarak bu davranış gözlenir `yield return` deyimi içinde `StreamedAtom10FeedFormatter.DelayReadItems()` ve bu Kesme noktasının çağrısından sonra ilk kez girildiğinde tercihinize `ReadFrom()` tamamlar.</span><span class="sxs-lookup"><span data-stu-id="3c8da-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="3c8da-125">Aşağıdaki yönergeler, derleme ve çalıştırma örneği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3c8da-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="3c8da-126">Sunucunun istemci 10 Öğe Okuma sonra öğeleri oluşturma durdurur ancak çıkış istemci fazla 10 öğe okur gösterdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="3c8da-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="3c8da-127">Örnek tarafından kullanılan ağ bağlama dört kilobayt (KB) kesimlerinde veri aktaran olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3c8da-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="3c8da-128">Bu nedenle, tek bir öğesi okuma fırsatına sahip önce istemci 4 KB'lık veri öğesi alır.</span><span class="sxs-lookup"><span data-stu-id="3c8da-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="3c8da-129">(Makul boyutlu kesimler arttıkça performans akış HTTP veri gönderme) normal davranış budur.</span><span class="sxs-lookup"><span data-stu-id="3c8da-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3c8da-130">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="3c8da-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3c8da-131">Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c8da-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="3c8da-132">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c8da-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="3c8da-133">Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3c8da-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3c8da-134">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="3c8da-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3c8da-135">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3c8da-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3c8da-136">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="3c8da-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3c8da-137">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3c8da-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="3c8da-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c8da-138">See also</span></span>

- [<span data-ttu-id="3c8da-139">Bağımsız Tanılama Akışı</span><span class="sxs-lookup"><span data-stu-id="3c8da-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
