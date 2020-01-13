---
title: DataContractJsonSerializer örneği
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 52e10ee28137b16bd90e6f3f3ac41f839528f334
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904536"
---
# <a name="datacontractjsonserializer-sample"></a><span data-ttu-id="2e854-102">DataContractJsonSerializer örneği</span><span class="sxs-lookup"><span data-stu-id="2e854-102">DataContractJsonSerializer sample</span></span>

> [!NOTE]
> <span data-ttu-id="2e854-103">Bu örnek <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>içindir.</span><span class="sxs-lookup"><span data-stu-id="2e854-103">This sample is for <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="2e854-104">JSON serileştirilmesinin ve serisini kaldırma ile ilgili çoğu senaryo için, [System. Text. JSON ad alanındaki](../../../standard/serialization/system-text-json-overview.md)API 'leri öneririz.</span><span class="sxs-lookup"><span data-stu-id="2e854-104">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span> 

<span data-ttu-id="2e854-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.Runtime.Serialization.DataContractSerializer>aynı türleri destekler.</span><span class="sxs-lookup"><span data-stu-id="2e854-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="2e854-106">JSON veri biçimi, zaman uyumsuz JavaScript ve XML (AJAX) stili Web uygulamaları yazarken özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2e854-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="2e854-107">Windows Communication Foundation (WCF) ' de AJAX desteği, ScriptManager denetimi aracılığıyla ASP.NET AJAX ile kullanım için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2e854-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="2e854-108">ASP.NET AJAX ile Windows Communication Foundation (WCF) kullanmanın örnekleri için bkz. [Ajax örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="2e854-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
<span data-ttu-id="2e854-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="2e854-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="2e854-110">Örnek, serileştirme ve seri durumdan çıkarma göstermek için bir `Person` veri sözleşmesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2e854-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 <span data-ttu-id="2e854-111">`Person` türünün bir örneğini JSON olarak seri hale getirmek için önce <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> oluşturun ve `WriteObject` metodunu kullanarak JSON verilerini bir akışa yazın.</span><span class="sxs-lookup"><span data-stu-id="2e854-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="2e854-112">Bellek akışı geçerli JSON verileri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="2e854-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="2e854-113">Örnek, JSON verilerinden bir nesne olarak seri durumdan çıkarmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e854-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="2e854-114">Sonra akışı geri sarın ve `ReadObject`çağırın.</span><span class="sxs-lookup"><span data-stu-id="2e854-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="2e854-115">`p2` nesnesini incelemek, JSON verilerinin doğru şekilde seri durumdan çıkarılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2e854-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2e854-116">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="2e854-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2e854-117">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="2e854-117">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2e854-118">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="2e854-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e854-119">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="2e854-119">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2e854-120">Bunu ayarlamak için örneği oluşturun ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="2e854-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="2e854-121">[Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi jsonSerialization. sln çözümünü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2e854-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="2e854-122">Ortaya çıkan konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2e854-122">Run the resulting console application.</span></span>  
