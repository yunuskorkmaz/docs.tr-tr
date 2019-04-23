---
title: Akış Gerçekleştirme Örneği
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 8b48bc5ec65d6ca30d6ffeed7ca68dc246f74d94
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320437"
---
# <a name="streaming-feeds-sample"></a>Akış Gerçekleştirme Örneği
Bu örnek çok sayıda öğe içeren dağıtım akışlarını yönetmek nasıl gösterir. Sunucuda örnek tek tek oluşturulması gecikme yapmayı gösteren <xref:System.ServiceModel.Syndication.SyndicationItem> nesneleri hemen kadar akışın içinde öğe ağ akışa yazılmadan önce.  
  
 İstemcide, örnek okunan akışın belleğe hiçbir zaman tam olarak yürütülmeden, tek tek öğeleri ağ akışından okunacak akış biçimlendirici bir özel dağıtım'ın nasıl kullanılabileceğini gösterir.  
  
 En iyi API dağıtım akış yeteneğini göstermek için bu örnek sunucu sonsuz sayıda öğe içeren bir akış kullanıma sunan biraz olası bir senaryo kullanır. Bu durumda, sunucunun istemci (varsayılan: 10) akıştan belirtilen sayıda öğeyi okudu belirler kadar yeni öğeler akış oluşturma devam eder. Kolaylık olması için istemci ve sunucu aynı işlem içinde uygulanır ve paylaşılan kullanın `ItemCounter` kaç istemci öğelerini izlemek için nesne oluşturulur. `ItemCounter` Türü amacı doğrultusunda yalnızca düzgün bir şekilde sonlandırmak Örnek senaryo izin vererek var ve gösterilen düzeninin bir çekirdek öğesi değil.  
  
 Tanıtım Visual C#, yararlanır yineleyiciler (kullanarak `yield return` anahtar sözcüğü yapısı). Yineleyiciler hakkında daha fazla bilgi için MSDN'de "Yineleyicileri kullanma" konusuna bakın.  
  
## <a name="service"></a>Hizmet  
 Temel hizmeti uygulayan <xref:System.ServiceModel.Web.WebGetAttribute> aşağıdaki kodda gösterildiği gibi bir işleme, oluşan sözleşme.  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Kullanarak, bu sözleşme hizmeti uygulayan bir `ItemGenerator` olası sonsuz bir akışı oluşturmak için sınıf <xref:System.ServiceModel.Syndication.SyndicationItem> aşağıdaki kodda gösterildiği gibi bir yineleyici kullanarak örnekler.  
  
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
  
 Hizmet uygulaması, akışın çıkışına oluşturduğunda `ItemGenerator.GenerateItems()` arabelleğe alınan öğelerin koleksiyonunu yerine kullanılır.  
  
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
  
 Sonuç olarak, akış öğesi hiçbir zaman tam olarak belleğe yürütülmeden. Üzerinde bir kesme noktası ayarlayarak bu davranış gözlenir `yield return` deyimi içinde `ItemGenerator.GenerateItems()` yöntemi ve bu Kesme noktasının hizmet sonucunu verdi sonra ilk kez karşılaşılanaa belirtmeye `StreamedFeed()` yöntemi.  
  
## <a name="client"></a>İstemci  
 Özel bir istemcinin bu <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> belleğe arabelleğe yerine akış içinde tek tek öğelerin materialization gecikmeler uygulama. Özel `StreamedAtom10FeedFormatter` örneği şu şekilde kullanılır.  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Normalde, bir çağrı <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> akışın tüm içeriği ağdan okuyun ve belleğe arabelleğe kadar döndürmez. Ancak, `StreamedAtom10FeedFormatter` Nesne geçersiz kılmaları <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> aşağıdaki kodda gösterildiği gibi bir yineleyici arabelleğe alınan bir koleksiyon yerine döndürülecek.  
  
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
  
 Sonuç olarak, her öğe ağdan sonuçlarını geçiş istemci uygulaması kadar okunamaz `ReadItems()` , kullanıma hazır. Üzerinde bir kesme noktası ayarlayarak bu davranış gözlenir `yield return` deyimi içinde `StreamedAtom10FeedFormatter.DelayReadItems()` ve bu Kesme noktasının çağrısından sonra ilk kez girildiğinde tercihinize `ReadFrom()` tamamlar.  
  
 Aşağıdaki yönergeler, derleme ve çalıştırma örneği gösterilmektedir. Sunucunun istemci 10 Öğe Okuma sonra öğeleri oluşturma durdurur ancak çıkış istemci fazla 10 öğe okur gösterdiğine dikkat edin. Örnek tarafından kullanılan ağ bağlama dört kilobayt (KB) kesimlerinde veri aktaran olmasıdır. Bu nedenle, tek bir öğesi okuma fırsatına sahip önce istemci 4 KB'lık veri öğesi alır. (Makul boyutlu kesimler arttıkça performans akış HTTP veri gönderme) normal davranış budur.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örneği çalıştırma  
  
1. Gerçekleştirdiğinizden emin olmak [Windows Communication Foundation örnekleri için bir kerelik Kurulum yordamı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için yönergeleri izleyin. [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Tek veya çapraz makine yapılandırmasında örneği çalıştırmak için yönergeleri izleyin. [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bağımsız Tanılama Akışı](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
