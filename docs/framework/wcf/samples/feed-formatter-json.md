---
title: Akış Biçimlendirici (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: c3e3378cd2465e26e4b6ff7b4c12a55050301095
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990112"
---
# <a name="feed-formatter-json"></a>Akış Biçimlendirici (JSON)
Bu örnek, örneğini serileştirmek nasıl gösterir. bir <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfı özel kullanarak JavaScript nesne gösterimi (JSON) biçiminde <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="architecture-of-the-sample"></a>Örneğinin mimarisi  
 Örnek adlı bir sınıf uygulayan `JsonFeedFormatter` öğesinden devralan <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. `JsonFeedFormatter` Sınıfı dayanır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> okuyup verileri JSON biçiminde yazmak için. Dahili olarak, veri anlaşması türleri adlı özel bir dizi biçimlendirici kullanır `JsonSyndicationFeed` ve `JsonSyndicationItem` JSON verilerini seri hale getirici tarafından üretilen biçimini denetlemek için. Bu uygulama ayrıntılarını karşı standart yapılacak çağrıları izin verme son kullanıcıdan gizlenir <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> sınıfları.  
  
## <a name="writing-json-feeds"></a>Yazma JSON akışları  
 Akış bir JSON yazma gerçekleştirilebilir kullanarak `JsonFeedFormatter` (Bu örnekte uygulanmış) ile <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> aşağıdaki örnek kodda gösterildiği gibi.  
  
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
  
## <a name="reading-a-json-feed"></a>Bir JSON akışı okuma  
 Alma bir <xref:System.ServiceModel.Syndication.SyndicationFeed> akışı, JSON ile biçimlendirilmiş bir veri ile gerçekleştirilebilir `JsonFeedFormatter` aşağıdaki kodda gösterilen şekilde.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
