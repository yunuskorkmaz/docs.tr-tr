---
title: Akış Gerçekleştirme Örneği
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 9d40a07b81474a283a8edbeb7aca1aa7ab3993b2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716647"
---
# <a name="streaming-feeds-sample"></a>Akış Gerçekleştirme Örneği
Bu örnek, çok sayıda öğe içeren dağıtım akışlarının nasıl yönetileceğini gösterir. Sunucusunda, örnek, öğe ağ akışına yazılmadan önce, akış içinde bireysel <xref:System.ServiceModel.Syndication.SyndicationItem> nesnelerinin oluşturulma süresinin nasıl geciktirileceğini gösterir.  
  
 İstemcide, bu örnek, okunan akışın hiçbir şekilde bellekte tam olarak arabelleğe alınabilmesi için ağ akışından tek tek öğeleri okumak için özel bir dağıtım akış biçimlendiricinin nasıl kullanılabileceğini gösterir.  
  
 Bu örnek, dağıtım API 'sinin akış yeteneğini en iyi şekilde göstermek için, sunucunun sonsuz sayıda öğe içeren bir akışı kullanıma sunduğunu belirten, olası bir senaryoyu kullanır. Bu durumda, sunucu akışın akıştan belirtilen sayıda öğeyi okuduğunuzu (varsayılan olarak 10) bulana kadar akışa yeni öğe oluşturmaya devam eder. Kolaylık olması için hem istemci hem de sunucu aynı işleme uygulanır ve istemcinin kaç öğe üretmekte olduğunu izlemek için paylaşılan bir `ItemCounter` nesnesi kullanır. `ItemCounter` türü yalnızca örnek senaryonun düzgün sonlandırılmasına izin vermek için vardır ve gösterilen deseninin bir çekirdek öğesi değildir.  
  
 Gösterim, görsel C# yineleyiciler (`yield return` anahtar sözcük yapısını kullanarak) kullanır. Yineleyiciler hakkında daha fazla bilgi için MSDN 'deki "yineleyiciler kullanma" konusuna bakın.  
  
## <a name="service"></a>Hizmet  
 Hizmet, aşağıdaki kodda gösterildiği gibi, bir işlemden oluşan temel bir <xref:System.ServiceModel.Web.WebGetAttribute> sözleşme uygular.  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Hizmet, aşağıdaki kodda gösterildiği gibi bir yineleyici kullanarak <xref:System.ServiceModel.Syndication.SyndicationItem> örneklerinin potansiyel olarak sonsuz bir akışını oluşturmak için bir `ItemGenerator` sınıfını kullanarak bu sözleşmeyi uygular.  
  
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
  
 Hizmet uygulama akışı oluşturduğunda, `ItemGenerator.GenerateItems()` çıkışı, arabelleğe alınmış bir öğe koleksiyonu yerine kullanılır.  
  
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
  
 Sonuç olarak, öğe akışının hiçbir şekilde bellekte tam olarak arabelleğe alınmayacağı. `ItemGenerator.GenerateItems()` yönteminin içindeki `yield return` bildiriminde bir kesme noktası ayarlayarak ve bu kesme noktasının, hizmet `StreamedFeed()` yönteminin sonucunu döndürdüğünden ilk kez ilgili olduğunu belirterek bu davranışı gözlemleyebilirsiniz.  
  
## <a name="client"></a>İstemci  
 Bu örnekteki istemci, akışa arabelleğe almak yerine akıştaki tek tek öğelerin bir kez uygulanmasını gecikmesi için özel bir <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> uygulamasını kullanır. Özel `StreamedAtom10FeedFormatter` örneği aşağıdaki gibi kullanılır.  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Normalde, bir <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> çağrısı, akışın tüm içeriği ağdan okunana ve belleğe arabelleğe alınana kadar döndürmez. Ancak, `StreamedAtom10FeedFormatter` nesnesi, aşağıdaki kodda gösterildiği gibi, arabelleğe alınmış bir koleksiyon yerine bir yineleyici döndürecek şekilde <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> geçersiz kılar.  
  
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
  
 Sonuç olarak, `ReadItems()` sonuçlarından geçen istemci uygulaması tarafından kullanıma hazırlanana kadar her öğe ağdan okunmaz. Bu davranışı, `StreamedAtom10FeedFormatter.DelayReadItems()` içindeki `yield return` bildiriminde bir kesme noktası ayarlayarak ve bu kesme noktasının `ReadFrom()` tamamlandıktan sonra ilk kez karşılaşdığını gözlemleyerek gözlemleyebilirsiniz.  
  
 Aşağıdaki yönergelerde örneği oluşturma ve çalıştırma gösterilmektedir. İstemci 10 öğe okuduktan sonra sunucu öğeleri oluşturmayı durdursa da çıkış, istemcinin 10 ' dan fazla öğeden çok önemli bir şekilde okuduğunu gösterir. Bunun nedeni, örnek tarafından kullanılan ağ bağlamasının verileri dört kilobayt (KB) kesimlerde iletmesidir. Bu nedenle, istemci, daha önce bir öğe okumak için bir tane olmak üzere 4KB 'lık öğe verileri alır. Bu normal davranıştır (makul ölçekli kesimlerde akış HTTP verileri gönderilmesi performansı artırır).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak Için [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımsız Tanılama Akışı](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
