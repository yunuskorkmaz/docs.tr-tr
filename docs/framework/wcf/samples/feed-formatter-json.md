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
# <a name="feed-formatter-json"></a><span data-ttu-id="3a885-102">Akış Biçimlendirici (JSON)</span><span class="sxs-lookup"><span data-stu-id="3a885-102">Feed Formatter (JSON)</span></span>
<span data-ttu-id="3a885-103">Bu örnek <xref:System.ServiceModel.Syndication.SyndicationFeed> , JavaScript nesne gösterimi (JSON) biçiminde bir sınıfın örneğini özel ve ile kullanarak serileştirmek gösterilmektedir <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="3a885-103">This sample shows how to serialize an instance of a <xref:System.ServiceModel.Syndication.SyndicationFeed> class in JavaScript Object Notation (JSON) format by using a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> and the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="architecture-of-the-sample"></a><span data-ttu-id="3a885-104">Örneğin mimarisi</span><span class="sxs-lookup"><span data-stu-id="3a885-104">Architecture of the Sample</span></span>  
 <span data-ttu-id="3a885-105">Örnek, öğesinden devralan adlı bir sınıfı uygular `JsonFeedFormatter` <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> .</span><span class="sxs-lookup"><span data-stu-id="3a885-105">The sample implements a class named `JsonFeedFormatter` that inherits from <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="3a885-106">`JsonFeedFormatter`Sınıfı, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> verileri JSON biçiminde okumak ve yazmak için öğesine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="3a885-106">The `JsonFeedFormatter` class relies on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to read and write the data in JSON format.</span></span> <span data-ttu-id="3a885-107">Dahili olarak, biçimlendirici, `JsonSyndicationFeed` `JsonSyndicationItem` seri hale getirici tarafından üretilen JSON verilerinin biçimini denetlemek için ve adlı özel bir veri anlaşması türü kümesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a885-107">Internally, the formatter uses a custom set of data contract types named `JsonSyndicationFeed` and `JsonSyndicationItem` to control the format of the JSON data produced by the serializer.</span></span> <span data-ttu-id="3a885-108">Bu uygulama ayrıntıları, son kullanıcıdan gizlenir ve standart ve sınıflara karşı çağrılara izin verir <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> .</span><span class="sxs-lookup"><span data-stu-id="3a885-108">These implementation details are hidden from the end user, allowing calls to be made against the standard <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> classes.</span></span>  
  
## <a name="writing-json-feeds"></a><span data-ttu-id="3a885-109">JSON akışlarını yazma</span><span class="sxs-lookup"><span data-stu-id="3a885-109">Writing JSON feeds</span></span>  
 <span data-ttu-id="3a885-110">JSON akışı yazmak `JsonFeedFormatter` , <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> Aşağıdaki örnek kodda gösterildiği gibi ile (Bu örnekte uygulanan) kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3a885-110">Writing a JSON feed can be accomplished by using the `JsonFeedFormatter` (implemented in this sample) with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as shown in the following sample code.</span></span>  
  
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
  
## <a name="reading-a-json-feed"></a><span data-ttu-id="3a885-111">JSON akışını okuma</span><span class="sxs-lookup"><span data-stu-id="3a885-111">Reading a JSON feed</span></span>  
 <span data-ttu-id="3a885-112"><xref:System.ServiceModel.Syndication.SyndicationFeed>JSON biçimli verilerin akışından alma, `JsonFeedFormatter` aşağıdaki kodda gösterildiği gibi ile gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3a885-112">Obtaining a <xref:System.ServiceModel.Syndication.SyndicationFeed> from a stream of JSON-formatted data can be accomplished with the `JsonFeedFormatter` as show in the following code.</span></span>  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3a885-113">Örneği ayarlamak, derlemek ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="3a885-113">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3a885-114">[Windows Communication Foundation Örnekleri Için tek seferlik Kurulum yordamını](one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="3a885-114">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3a885-115">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak için [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)konusundaki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3a885-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3a885-116">Örneği tek veya bir çapraz makine yapılandırmasında çalıştırmak için [Windows Communication Foundation Örnekleri çalıştırma](running-the-samples.md)bölümündeki yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="3a885-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3a885-117">Örnekler bilgisayarınızda zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3a885-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3a885-118">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3a885-118">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3a885-119">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3a885-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a885-120">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3a885-120">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
