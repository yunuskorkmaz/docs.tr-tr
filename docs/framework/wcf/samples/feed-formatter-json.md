---
title: Akış Biçimlendirici (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 350e07ad37b09f39fc709e20d8f73a41f9d01f30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183648"
---
# <a name="feed-formatter-json"></a>Akış Biçimlendirici (JSON)
Bu örnek, JavaScript Nesne Gösterimi (JSON) biçiminde bir <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfın örneğini <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> özel <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>ve .  
  
## <a name="architecture-of-the-sample"></a>Örneğin Mimarisi  
 Örnek, 'den `JsonFeedFormatter` <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>devralan adlı bir sınıf uygular. Sınıf, `JsonFeedFormatter` verileri JSON formatında okuyup yazmaya güvenir. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Dahili olarak, formatter adlı ve serializer `JsonSyndicationItem` tarafından üretilen JSON verilerinin biçimini denetlemek için özel `JsonSyndicationFeed` bir veri sözleşmesi türleri kümesi kullanır. Bu uygulama ayrıntıları son kullanıcıdan gizlenerek, çağrıların standart <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> ve sınıflara karşı yapılmasını sağlar.  
  
## <a name="writing-json-feeds"></a>Yazma JSON yayınları  
 JSON beslemesi yazmak, aşağıdaki `JsonFeedFormatter` örnek kodda gösterildiği <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> gibi (bu örnekte uygulanan) kullanılarak gerçekleştirilebilir.  
  
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
  
## <a name="reading-a-json-feed"></a>JSON beslemesi okuma  
 JSON <xref:System.ServiceModel.Syndication.SyndicationFeed> biçimlendirilmiş veri akışından a elde etmek, aşağıdaki `JsonFeedFormatter` koddaki gibi bir şekilde gerçekleştirilebilir.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
