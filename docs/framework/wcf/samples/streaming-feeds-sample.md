---
title: Akış Gerçekleştirme Örneği
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 7a887fa1eceac4d8ee323f03fd5bc536bb1dc579
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143973"
---
# <a name="streaming-feeds-sample"></a>Akış Gerçekleştirme Örneği
Bu örnek, çok sayıda öğe içeren sendikasyon akışlarının nasıl yönetilenini gösterir. Sunucuda, örnek, öğe ağ akışına yazılmadan hemen önceye kadar besleme içindeki tek tek <xref:System.ServiceModel.Syndication.SyndicationItem> nesnelerin oluşturulmasını nasıl geciktirleyeceğini gösterir.  
  
 İstemci de örnek, okunan özet akışının hiçbir zaman belleğe tam olarak arabelleğe alınmaması için ağ akışındaki tek tek öğeleri okumak için özel bir sendikasyon akışı nın nasıl kullanılabileceğini gösterir.  
  
 Sendikasyon API'sının akış yeteneğini en iyi şekilde göstermek için, bu örnek, sunucunun sonsuz sayıda öğe içeren bir akışı ortaya çıkardığı olası olmayan bir senaryo kullanır. Bu durumda, istemcinin akıştan belirli sayıda öğe okuduğunu belirleyene kadar sunucu özet akışına yeni öğeler üretmeye devam eder (varsayılan olarak, 10). Basitlik için, istemci ve sunucu aynı işlemde uygulanır ve istemcinin kaç öğe ürettiğini izlemek için paylaşılan `ItemCounter` bir nesne kullanır. Tür, `ItemCounter` yalnızca örnek senaryonun temiz bir şekilde sonlandırılmasına izin vermek amacıyla vardır ve gösterilen desenin temel öğesi değildir.  
  
 Gösteri, Visual C# yineleyicilerini `yield return` (anahtar kelime yapısı kullanarak) kullanır. Yineleyiciler hakkında daha fazla bilgi için MSDN'deki "Yineleyicileri Kullanma" konusuna bakın.  
  
## <a name="service"></a>Hizmet  
 Hizmet, aşağıdaki kodda gösterildiği gibi, tek bir işlemden oluşan temel <xref:System.ServiceModel.Web.WebGetAttribute> bir sözleşme uygular.  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Hizmet, aşağıdaki kodda gösterildiği `ItemGenerator` gibi bir yineleyici kullanarak <xref:System.ServiceModel.Syndication.SyndicationItem> olası sonsuz bir örnek akışı oluşturmak için bir sınıf kullanarak bu sözleşmeyi uygular.  
  
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
  
 Hizmet uygulaması özet akışı oluşturduğunda, `ItemGenerator.GenerateItems()` arabelleğe alan madde koleksiyonu yerine çıktı kullanılır.  
  
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
  
 Sonuç olarak, öğe akışı hiçbir zaman tam olarak belleğe arabelleğe almaz. Yöntemin `yield return` `ItemGenerator.GenerateItems()` içindeki deyime bir kesme noktası ayarlayarak ve hizmet `StreamedFeed()` yöntemin sonucunu döndürdikten sonra bu kesme noktasına ilk kez rastlandığını belirterek bu davranışı gözlemleyebilirsiniz.  
  
## <a name="client"></a>İstemci  
 Bu örnekteki istemci, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> bunları belleğe arabelleğe almak yerine akıştaki tek tek öğelerin somutlaştırılmasını geciktiren özel bir uygulama kullanır. Özel `StreamedAtom10FeedFormatter` örnek aşağıdaki gibi kullanılır.  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Normalde, özet akışı <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> içeriğinin tamamı ağdan okunup belleğe arabelleğe alınana kadar bir çağrı geri dönmez. Ancak, `StreamedAtom10FeedFormatter` nesne aşağıdaki <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> kodda gösterildiği gibi arabelleğe alan bir koleksiyon yerine bir yineleyici döndürmek için geçersiz kılar.  
  
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
  
 Sonuç olarak, sonuçları `ReadItems()` geçiş istemci uygulaması kullanmaya hazır olana kadar her öğe ağdan okunmaz. Bu davranışı, içindeki deyime `yield return` bir kesme noktası `StreamedAtom10FeedFormatter.DelayReadItems()` ayarlayarak ve bu kesme noktasının `ReadFrom()` çağrı tamamlandıktan sonra ilk kez karşılaşılan olduğunu fark ederek bu davranışı gözlemleyebilirsiniz.  
  
 Aşağıdaki yönergeler, örneğin nasıl oluşturup çalıştırılabildiğini gösterir. Sunucu, istemci 10 öğe okuduktan sonra öğe oluşturmayı durdursa da, çıktının istemcinin önemli ölçüde 10'dan fazla öğe okuduğunu gösterir. Bunun nedeni, örnek tarafından kullanılan ağ bağlamanın verileri dört kilobaytlık (KB) segmentlerde iletmesidir. Bu nedenle, istemci bir öğeyi bile okuma fırsatı nasahip olmadan önce 4KB madde verilerini alır. Bu normal davranıştır (akışlı HTTP verilerini makul boyutlu segmentlerde göndermek performansı artırır).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.  
  
3. Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınıza zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımsız Tanılama Akışı](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
