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
# <a name="streaming-feeds-sample"></a>Akış Gerçekleştirme Örneği
Bu örnek, çok sayıda öğe içeren dağıtım akışlarını yönetmek gösterilmiştir. Sunucu üzerinde örnek tek tek oluşturulması gecikme gösterilmiştir <xref:System.ServiceModel.Syndication.SyndicationItem> nesneleri hemen kadar akış içinde öğe ağ akışa yazılmadan önce.  
  
 İstemci üzerinde örnek akış biçimlendirici özel bir dağıtım okunan akışın belleğe hiçbir zaman tamamen arabelleğe alınıp böylece ayrı öğeleri ağ akıştan okumak için nasıl kullanılabileceğini gösterir.  
  
 En iyi dağıtım API akış yeteneğini göstermek için bu örnek sunucu sonsuz sayıda öğe içeren bir akış sunar biraz olası bir senaryo kullanır. Bu durumda, sunucunun istemci belirtilen sayıda öğeyi akıştan (varsayılan olarak, 10) okuma izni olduğunu belirler kadar akışa yeni öğeler oluşturma devam eder. Basitlik, hem istemci hem de sunucunun aynı işlem içinde uygulanan ve paylaşılan kullanın `ItemCounter` kaç istemci öğelerini izlemek için nesne üretilen. `ItemCounter` Türü yalnızca düzgün bir şekilde sonlandırmak Örnek senaryo izin vermek amacıyla var ve gösterilen deseni çekirdek öğesi değil.  
  
 Visual C#, kullanan Tanıtımı yararlanır yineleyiciler (kullanarak `yield``return` anahtar sözcüğü yapı). Yineleyiciler hakkında daha fazla bilgi için MSDN'de "Yineleyiciler kullanma" konusuna bakın.  
  
## <a name="service"></a>Hizmet  
 Temel bir hizmet uygulayan <xref:System.ServiceModel.Web.WebGetAttribute> aşağıdaki kodda gösterildiği gibi bir işleme, oluşur sözleşme.  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Kullanarak bu sözleşme hizmeti uygulayan bir `ItemGenerator` olası sonsuz akışı oluşturmak için sınıf <xref:System.ServiceModel.Syndication.SyndicationItem> aşağıdaki kodda gösterildiği gibi bir yineleyici kullanarak örnekleri.  
  
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
  
 Hizmet uygulaması, akış çıkışı oluşturduğunda `ItemGenerator.GenerateItems()` arabelleğe alınan öğeleri koleksiyonu yerine kullanılır.  
  
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
  
 Sonuç olarak, öğesi akış belleğe hiçbir zaman tamamen arabelleğe alınıp. Üzerinde bir kesme noktası ayarlayarak bu davranış gözlenir `yield``return` deyimi içinde `ItemGenerator.GenerateItems()` yöntemi ve bu kesme hizmet sonucu döndürdü sonra ilk kez karşılaşılana belirtmeye `StreamedFeed()` yöntemi.  
  
## <a name="client"></a>İstemci  
 Özel bir istemcinin bu örnekteki <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> belleğe arabelleğe yerine akıştaki tek tek öğelerin materialization gecikmeler uygulama. Özel `StreamedAtom10FeedFormatter` örneği aşağıdaki gibi kullanılır.  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Normal olarak yapılan bir çağrı <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> akışın tüm içeriği ağdan okuyun ve belleğe arabelleğe kadar döndürmüyor. Ancak, `StreamedAtom10FeedFormatter` Nesne geçersiz kılmaları <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> aşağıdaki kodda gösterildiği gibi yineleyici arabelleğe alınan bir koleksiyon yerine döndürülecek.  
  
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
  
 Sonuç olarak, her bir öğeyi ağdan sonuçlarını çapraz geçiş yapan istemci uygulaması kadar okunamaz `ReadItems()` kullanmak hazırdır. Üzerinde bir kesme noktası ayarlayarak bu davranış gözlenir `yield``return` deyimi içinde `StreamedAtom10FeedFormatter.DelayReadItems()` ve bu kesme çağrısından sonra ilk kez karşılaşılana haberiniz bile `ReadFrom()` tamamlar.  
  
 Aşağıdaki yönergeler, derlemeyi ve çalıştırmayı örnek gösterilmektedir. Sunucunun istemci 10 Öğe Okuma sonra öğeleri oluşturma durdurur ancak çıktı istemci önemli ölçüde birden fazla 10 öğe okur gösterdiğine dikkat edin. Örnek tarafından kullanılan ağ bağlama dört kilobayt (KB) Segment veri aktaran olmasıdır. Bu nedenle, tek öğe okunur fırsatına sahip önce istemci 4 KB öğesi veri alır. (Makul boyutlu kesimler artar performans akış HTTP veri gönderme) normal davranış budur.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bağımsız Tanılama Akışı](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
