---
title: Akış Biçimlendirici (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 742d9be71d40a7f8ac15404c0d0ad573a570209d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33501435"
---
# <a name="feed-formatter-json"></a>Akış Biçimlendirici (JSON)
Bu örnek, bir örneğini serileştirmek gösterilmiştir bir <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfı bir özel kullanarak JavaScript nesne gösterimi (JSON) biçiminde <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="architecture-of-the-sample"></a>Örnek mimarisi  
 Adlı bir sınıf örneği uygulayan `JsonFeedFormatter` devraldığı <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. `JsonFeedFormatter` Sınıfı kullanır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> okumak ve JSON biçiminde veri yazmak için. Dahili olarak, veri sözleşme türleri adlı özel bir dizi biçimlendirici kullanır `JsonSyndicationFeed` ve `JsonSyndicationItem` seri hale getirici tarafından üretilen JSON veri biçimini denetlemek için. Bu uygulama ayrıntılarını standartlarla yapılması çağrıları izin vererek son kullanıcıdan gizli <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> sınıfları.  
  
## <a name="writing-json-feeds"></a>Yazma JSON akışları  
 Akış JSON yazma gerçekleştirilebilir kullanarak `JsonFeedFormatter` (Bu örnekte uygulanan) ile <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> aşağıdaki örnek kodda gösterildiği gibi.  
  
```  
//Basic feed with sample data  
SyndicationFeed feed = new SyndicationFeed("Custom JSON feed", "A Syndication extensibility sample", null);  
feed.LastUpdatedTime = DateTime.Now;  
feed.Items = from s in new string[] { "hello", "world" }  
select new SyndicationItem()  
{  
    Summary = SyndicationContent.CreatePlaintextContent(s)  
};  
  
//Write the feed out to a MemoryStream in JSON format  
DataContractJsonSerializer writeSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));  
writeSerializer.WriteObject(stream, new JsonFeedFormatter(feed));  
```  
  
## <a name="reading-a-json-feed"></a>Bir JSON akışından okuma  
 Alma bir <xref:System.ServiceModel.Syndication.SyndicationFeed> bir akış, JSON biçimli verileri ile gerçekleştirilebilir `JsonFeedFormatter` aşağıdaki kodda olarak göster.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Örnekler, bilgisayarınızda yüklü. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
  
## <a name="see-also"></a>Ayrıca Bkz.
