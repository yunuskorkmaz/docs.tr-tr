---
title: Akış Biçimlendirici (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: dfdcd0920980e7e5cc1fe1c8910ee7cfbe59b5a0
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715836"
---
# <a name="feed-formatter-json"></a>Akış Biçimlendirici (JSON)
Bu örnek, özel bir <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>kullanılarak JavaScript Nesne Gösterimi (JSON) biçiminde bir <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfının örneğinin serileştirilme şeklini gösterir.  
  
## <a name="architecture-of-the-sample"></a>Örneğin mimarisi  
 Örnek, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>devralan `JsonFeedFormatter` adlı bir sınıfı uygular. `JsonFeedFormatter` sınıfı, verileri JSON biçiminde okumak ve yazmak için <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> kullanır. Dahili olarak, biçimlendirici, serileştirici tarafından üretilen JSON verilerinin biçimini denetlemek için `JsonSyndicationFeed` ve `JsonSyndicationItem` adlı özel bir veri anlaşması kümesi kullanır. Bu uygulama ayrıntıları, son kullanıcıdan gizlenir ve standart <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> sınıflarına yönelik çağrılara izin verir.  
  
## <a name="writing-json-feeds"></a>JSON akışlarını yazma  
 JSON akışı yazmak, aşağıdaki örnek kodda gösterildiği gibi <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> `JsonFeedFormatter` (Bu örnekte uygulanan) kullanılarak gerçekleştirilebilir.  
  
```csharp  
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
  
## <a name="reading-a-json-feed"></a>JSON akışını okuma  
 JSON biçimli verilerin akışından bir <xref:System.ServiceModel.Syndication.SyndicationFeed> alma, aşağıdaki kodda göster olarak `JsonFeedFormatter` ile gerçekleştirilebilir.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
