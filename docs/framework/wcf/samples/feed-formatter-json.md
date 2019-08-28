---
title: Akış Biçimlendirici (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 028d2f9abd7e23f18eb90e5ecae8c57da3a871d1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039650"
---
# <a name="feed-formatter-json"></a>Akış Biçimlendirici (JSON)
Bu örnek, <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> JavaScriptnesnegösterimi(JSON)biçimindebirsınıfınörneğiniözelveilekullanarak<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>serileştirmek gösterilmektedir.  
  
## <a name="architecture-of-the-sample"></a>Örneğin mimarisi  
 Örnek, öğesinden `JsonFeedFormatter` <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>devralan adlı bir sınıfı uygular. `JsonFeedFormatter` Sınıfı ,<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> verileri JSON biçiminde okumak ve yazmak için öğesine bağımlıdır. Dahili olarak, biçimlendirici, seri hale getirici tarafından üretilen JSON verilerinin biçimini `JsonSyndicationFeed` denetlemek `JsonSyndicationItem` için ve adlı özel bir veri anlaşması türü kümesi kullanır. Bu uygulama ayrıntıları, son kullanıcıdan gizlenir ve standart <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> sınıflara karşı çağrılara izin verir.  
  
## <a name="writing-json-feeds"></a>JSON akışlarını yazma  
 JSON akışı yazmak, `JsonFeedFormatter` <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> aşağıdaki örnek kodda gösterildiği gibi ile (Bu örnekte uygulanan) kullanılarak gerçekleştirilebilir.  
  
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
  
## <a name="reading-a-json-feed"></a>JSON akışını okuma  
 JSON biçimli verilerin akışından alma, `JsonFeedFormatter` aşağıdaki kodda gösterildiği gibi ile gerçekleştirilebilir. <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
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
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
