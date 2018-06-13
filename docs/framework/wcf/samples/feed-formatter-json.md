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
# <a name="feed-formatter-json"></a><span data-ttu-id="aca71-102">Akış Biçimlendirici (JSON)</span><span class="sxs-lookup"><span data-stu-id="aca71-102">Feed Formatter (JSON)</span></span>
<span data-ttu-id="aca71-103">Bu örnek, bir örneğini serileştirmek gösterilmiştir bir <xref:System.ServiceModel.Syndication.SyndicationFeed> sınıfı bir özel kullanarak JavaScript nesne gösterimi (JSON) biçiminde <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="aca71-103">This sample shows how to serialize an instance of a <xref:System.ServiceModel.Syndication.SyndicationFeed> class in JavaScript Object Notation (JSON) format by using a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> and the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="architecture-of-the-sample"></a><span data-ttu-id="aca71-104">Örnek mimarisi</span><span class="sxs-lookup"><span data-stu-id="aca71-104">Architecture of the Sample</span></span>  
 <span data-ttu-id="aca71-105">Adlı bir sınıf örneği uygulayan `JsonFeedFormatter` devraldığı <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="aca71-105">The sample implements a class named `JsonFeedFormatter` that inherits from <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="aca71-106">`JsonFeedFormatter` Sınıfı kullanır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> okumak ve JSON biçiminde veri yazmak için.</span><span class="sxs-lookup"><span data-stu-id="aca71-106">The `JsonFeedFormatter` class relies on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to read and write the data in JSON format.</span></span> <span data-ttu-id="aca71-107">Dahili olarak, veri sözleşme türleri adlı özel bir dizi biçimlendirici kullanır `JsonSyndicationFeed` ve `JsonSyndicationItem` seri hale getirici tarafından üretilen JSON veri biçimini denetlemek için.</span><span class="sxs-lookup"><span data-stu-id="aca71-107">Internally, the formatter uses a custom set of data contract types named `JsonSyndicationFeed` and `JsonSyndicationItem` to control the format of the JSON data produced by the serializer.</span></span> <span data-ttu-id="aca71-108">Bu uygulama ayrıntılarını standartlarla yapılması çağrıları izin vererek son kullanıcıdan gizli <xref:System.ServiceModel.Syndication.SyndicationFeed> ve <xref:System.ServiceModel.Syndication.SyndicationItem> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="aca71-108">These implementation details are hidden from the end user, allowing calls to be made against the standard <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> classes.</span></span>  
  
## <a name="writing-json-feeds"></a><span data-ttu-id="aca71-109">Yazma JSON akışları</span><span class="sxs-lookup"><span data-stu-id="aca71-109">Writing JSON feeds</span></span>  
 <span data-ttu-id="aca71-110">Akış JSON yazma gerçekleştirilebilir kullanarak `JsonFeedFormatter` (Bu örnekte uygulanan) ile <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> aşağıdaki örnek kodda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="aca71-110">Writing a JSON feed can be accomplished by using the `JsonFeedFormatter` (implemented in this sample) with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as shown in the following sample code.</span></span>  
  
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
  
## <a name="reading-a-json-feed"></a><span data-ttu-id="aca71-111">Bir JSON akışından okuma</span><span class="sxs-lookup"><span data-stu-id="aca71-111">Reading a JSON feed</span></span>  
 <span data-ttu-id="aca71-112">Alma bir <xref:System.ServiceModel.Syndication.SyndicationFeed> bir akış, JSON biçimli verileri ile gerçekleştirilebilir `JsonFeedFormatter` aşağıdaki kodda olarak göster.</span><span class="sxs-lookup"><span data-stu-id="aca71-112">Obtaining a <xref:System.ServiceModel.Syndication.SyndicationFeed> from a stream of JSON-formatted data can be accomplished with the `JsonFeedFormatter` as show in the following code.</span></span>  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aca71-113">Ayarlamak için derleme ve örnek çalıştırın</span><span class="sxs-lookup"><span data-stu-id="aca71-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="aca71-114">Gerçekleştirmiş emin olun [kerelik Kurulum prosedürü Windows Communication Foundation örnekleri için](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aca71-114">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="aca71-115">Çözüm C# veya Visual Basic .NET sürümünü oluşturmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aca71-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="aca71-116">Tek veya çapraz makine yapılandırmada örneği çalıştırmak için'ndaki yönergeleri izleyin [Windows Communication Foundation örneklerini çalıştırma](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="aca71-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="aca71-117">Örnekler, bilgisayarınızda yüklü.</span><span class="sxs-lookup"><span data-stu-id="aca71-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="aca71-118">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="aca71-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="aca71-119">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="aca71-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aca71-120">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="aca71-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="aca71-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="aca71-121">See Also</span></span>
