---
title: Akış Biçimlendirici (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 7b535a5090d3c7df59b7faada35fc324a77b5651
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594679"
---
# <a name="feed-formatter-json"></a>Akış Biçimlendirici (JSON)
Bu örnek <xref:System.ServiceModel.Syndication.SyndicationFeed> , JavaScript nesne gösterimi (JSON) biçiminde bir sınıfın örneğini özel ve ile kullanarak serileştirmek gösterilmektedir <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .  
  
## <a name="architecture-of-the-sample"></a>Örneğin mimarisi  
 Örnek, öğesinden devralan adlı bir sınıfı uygular `JsonFeedFormatter` <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> . `JsonFeedFormatter`Sınıfı, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> verileri JSON biçiminde okumak ve yazmak için öğesine bağımlıdır. Dahili olarak, biçimlendirici, `JsonSyndicationFeed` `JsonSyndicationItem` seri hale getirici tarafından üretilen JSON verilerinin biçimini denetlemek için ve adlı özel bir veri anlaşması türü kümesi kullanır. Bu uygulama ayrıntıları, son kullanıcıdan gizlenir ve standart ve sınıflara karşı çağrılara izin verir <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> .  
  
## <a name="writing-json-feeds"></a>JSON akışlarını yazma  
 JSON akışı yazmak `JsonFeedFormatter` , <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Aşağıdaki örnek kodda gösterildiği gibi ile (Bu örnekte uygulanan) kullanılarak gerçekleştirilebilir.  
  
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
 <xref:System.ServiceModel.Syndication.SyndicationFeed>JSON biçimli verilerin akışından alma, `JsonFeedFormatter` aşağıdaki kodda gösterildiği gibi ile gerçekleştirilebilir.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
