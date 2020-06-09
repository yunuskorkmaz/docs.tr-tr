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
# <a name="streaming-feeds-sample"></a>Akış Gerçekleştirme Örneği
Bu örnek, çok sayıda öğe içeren dağıtım akışlarının nasıl yönetileceğini gösterir. Sunucusunda, örnek, <xref:System.ServiceModel.Syndication.SyndicationItem> öğe ağ akışına yazılmadan önce, akış içinde tek tek nesnelerin oluşturulmasına nasıl geciktirileceğini gösterir.  
  
 İstemcide, bu örnek, okunan akışın hiçbir şekilde bellekte tam olarak arabelleğe alınabilmesi için ağ akışından tek tek öğeleri okumak için özel bir dağıtım akış biçimlendiricinin nasıl kullanılabileceğini gösterir.  
  
 Bu örnek, dağıtım API 'sinin akış yeteneğini en iyi şekilde göstermek için, sunucunun sonsuz sayıda öğe içeren bir akışı kullanıma sunduğunu belirten, olası bir senaryoyu kullanır. Bu durumda, sunucu akışın akıştan belirtilen sayıda öğeyi okuduğunuzu (varsayılan olarak 10) bulana kadar akışa yeni öğe oluşturmaya devam eder. Basitlik için hem istemci hem de sunucu aynı işleme uygulanır ve `ItemCounter` istemcinin kaç öğe üretmekte olduğunu izlemek için paylaşılan bir nesne kullanır. `ItemCounter`Tür yalnızca örnek senaryonun düzgün sonlandırılmasına izin vermek için vardır ve gösterilen deseninin bir çekirdek öğesi değildir.  
  
 Demo, Visual C# yineleyicilerinin kullanımını ( `yield return` anahtar sözcük yapısını kullanarak) kullanır. Yineleyiciler hakkında daha fazla bilgi için MSDN 'deki "yineleyiciler kullanma" konusuna bakın.  
  
## <a name="service"></a>Hizmet  
 Hizmet, <xref:System.ServiceModel.Web.WebGetAttribute> aşağıdaki kodda gösterildiği gibi, bir işlemden oluşan temel bir sözleşme uygular.  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Hizmet, `ItemGenerator` <xref:System.ServiceModel.Syndication.SyndicationItem> aşağıdaki kodda gösterildiği gibi bir yineleyici kullanarak muhtemelen sınırsız bir örnek akışı oluşturmak için bir sınıf kullanarak bu sözleşmeyi uygular.  
  
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
  
 Hizmet uygulamasının akışı oluşturduğunda, çıkışı, `ItemGenerator.GenerateItems()` arabelleğe alınmış bir öğe koleksiyonu yerine kullanılır.  
  
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
  
 Sonuç olarak, öğe akışının hiçbir şekilde bellekte tam olarak arabelleğe alınmayacağı. Yöntemin içindeki bildiriminde bir kesme noktası ayarlayarak `yield return` `ItemGenerator.GenerateItems()` ve bu kesme noktasının, hizmetin yöntemin sonucunu döndürdüğünden ilk kez karşılaşdığını belirten bu davranışı gözlemleyebilirsiniz `StreamedFeed()` .  
  
## <a name="client"></a>İstemci  
 Bu örnekteki istemci, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> her bir öğenin, bunları belleğe almak yerine akıştaki bireysel öğelerin bir şekilde kullanılmasını gecikme özel bir uygulama kullanır. Özel `StreamedAtom10FeedFormatter` örnek aşağıdaki gibi kullanılır.  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Normalde, ' a yapılan bir çağrı, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> akışın tüm içeriği ağdan okunana ve belleğe arabelleğe alınana kadar döndürmez. Ancak, `StreamedAtom10FeedFormatter` nesne, <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> aşağıdaki kodda gösterildiği gibi, arabelleğe alınmış bir koleksiyon yerine bir yineleyici döndürecek şekilde geçersiz kılar.  
  
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
  
 Sonuç olarak, sonuçları geçen istemci uygulama tarafından kullanıma hazırlanana kadar her öğe ağdan okunmaz `ReadItems()` . Bu davranışı, ' ın içindeki bildiriminde bir kesme noktası ayarlayarak `yield return` `StreamedAtom10FeedFormatter.DelayReadItems()` ve bu kesme noktasının, çağrının tamamlanmasından sonra ilk kez karşılaşdığını yaşıyorsanız ile gözlemleyebilirsiniz `ReadFrom()` .  
  
 Aşağıdaki yönergelerde örneği oluşturma ve çalıştırma gösterilmektedir. İstemci 10 öğe okuduktan sonra sunucu öğeleri oluşturmayı durdursa da çıkış, istemcinin 10 ' dan fazla öğeden çok önemli bir şekilde okuduğunu gösterir. Bunun nedeni, örnek tarafından kullanılan ağ bağlamasının verileri dört kilobayt (KB) kesimlerde iletmesidir. Bu nedenle, istemci, daha önce bir öğe okumak için bir tane olmak üzere 4KB 'lık öğe verileri alır. Bu normal davranıştır (makul ölçekli kesimlerde akış HTTP verileri gönderilmesi performansı artırır).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, derlemek ve çalıştırmak için  
  
1. [Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.  
  
2. Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.  
  
3. Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.  
  
> [!IMPORTANT]
> Örnekler bilgisayarınızda zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımsız Tanılama Akışı](stand-alone-diagnostics-feed-sample.md)
