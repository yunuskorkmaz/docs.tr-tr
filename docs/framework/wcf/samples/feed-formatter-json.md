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
# <a name="feed-formatter-json"></a><span data-ttu-id="bc4bf-102">Akış Biçimlendirici (JSON)</span><span class="sxs-lookup"><span data-stu-id="bc4bf-102">Feed Formatter (JSON)</span></span>
<span data-ttu-id="bc4bf-103">Bu örnek, JavaScript Nesne Gösterimi (JSON) biçiminde bir <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfın örneğini <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> özel <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>ve .</span><span class="sxs-lookup"><span data-stu-id="bc4bf-103">This sample shows how to serialize an instance of a <xref:System.ServiceModel.Syndication.SyndicationFeed> class in JavaScript Object Notation (JSON) format by using a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> and the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="architecture-of-the-sample"></a><span data-ttu-id="bc4bf-104">Örneğin Mimarisi</span><span class="sxs-lookup"><span data-stu-id="bc4bf-104">Architecture of the Sample</span></span>  
 <span data-ttu-id="bc4bf-105">Örnek, 'den `JsonFeedFormatter` <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>devralan adlı bir sınıf uygular.</span><span class="sxs-lookup"><span data-stu-id="bc4bf-105">The sample implements a class named `JsonFeedFormatter` that inherits from <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="bc4bf-106">Sınıf, `JsonFeedFormatter` verileri JSON formatında okuyup yazmaya güvenir. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer></span><span class="sxs-lookup"><span data-stu-id="bc4bf-106">The `JsonFeedFormatter` class relies on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to read and write the data in JSON format.</span></span> <span data-ttu-id="bc4bf-107">Dahili olarak, formatter adlı ve serializer `JsonSyndicationItem` tarafından üretilen JSON verilerinin biçimini denetlemek için özel `JsonSyndicationFeed` bir veri sözleşmesi türleri kümesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="bc4bf-107">Internally, the formatter uses a custom set of data contract types named `JsonSyndicationFeed` and `JsonSyndicationItem` to control the format of the JSON data produced by the serializer.</span></span> <span data-ttu-id="bc4bf-108">Bu uygulama ayrıntıları son kullanıcıdan gizlenerek, çağrıların standart <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> ve sınıflara karşı yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bc4bf-108">These implementation details are hidden from the end user, allowing calls to be made against the standard <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> classes.</span></span>  
  
## <a name="writing-json-feeds"></a><span data-ttu-id="bc4bf-109">Yazma JSON yayınları</span><span class="sxs-lookup"><span data-stu-id="bc4bf-109">Writing JSON feeds</span></span>  
 <span data-ttu-id="bc4bf-110">JSON beslemesi yazmak, aşağıdaki `JsonFeedFormatter` örnek kodda gösterildiği <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> gibi (bu örnekte uygulanan) kullanılarak gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bc4bf-110">Writing a JSON feed can be accomplished by using the `JsonFeedFormatter` (implemented in this sample) with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as shown in the following sample code.</span></span>  
  
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
  
## <a name="reading-a-json-feed"></a><span data-ttu-id="bc4bf-111">JSON beslemesi okuma</span><span class="sxs-lookup"><span data-stu-id="bc4bf-111">Reading a JSON feed</span></span>  
 <span data-ttu-id="bc4bf-112">JSON <xref:System.ServiceModel.Syndication.SyndicationFeed> biçimlendirilmiş veri akışından a elde etmek, aşağıdaki `JsonFeedFormatter` koddaki gibi bir şekilde gerçekleştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="bc4bf-112">Obtaining a <xref:System.ServiceModel.Syndication.SyndicationFeed> from a stream of JSON-formatted data can be accomplished with the `JsonFeedFormatter` as show in the following code.</span></span>  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bc4bf-113">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="bc4bf-113">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bc4bf-114">Windows Communication Foundation [Samples için Tek Seferlik Kurulum Yordamı'nı](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)gerçekleştirdiğinizi emin olun.</span><span class="sxs-lookup"><span data-stu-id="bc4bf-114">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="bc4bf-115">Çözümün C# veya Visual Basic .NET sürümünü oluşturmak [için, Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="bc4bf-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="bc4bf-116">Örneği tek veya çapraz makine yapılandırmasında çalıştırmak için, [Windows Communication Foundation Samples'ı çalıştıran](../../../../docs/framework/wcf/samples/running-the-samples.md)yönergeleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="bc4bf-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bc4bf-117">Örnekler bilgisayarınıza zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="bc4bf-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bc4bf-118">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="bc4bf-118">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="bc4bf-119">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="bc4bf-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bc4bf-120">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="bc4bf-120">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
