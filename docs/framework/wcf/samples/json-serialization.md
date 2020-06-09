---
title: DataContractJsonSerializer örneği
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 4aa0ee679ae424251000b14abfbacf0590a6ccd3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592040"
---
# <a name="datacontractjsonserializer-sample"></a><span data-ttu-id="3a18f-102">DataContractJsonSerializer örneği</span><span class="sxs-lookup"><span data-stu-id="3a18f-102">DataContractJsonSerializer sample</span></span>

> [!NOTE]
> <span data-ttu-id="3a18f-103">Bu örnek için <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="3a18f-103">This sample is for <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="3a18f-104">JSON serileştirilmesinin ve serisini kaldırma ile ilgili çoğu senaryo için, [System. Text. JSON ad alanındaki](../../../standard/serialization/system-text-json-overview.md)API 'leri öneririz.</span><span class="sxs-lookup"><span data-stu-id="3a18f-104">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="3a18f-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ile aynı türleri destekler <xref:System.Runtime.Serialization.DataContractSerializer> .</span><span class="sxs-lookup"><span data-stu-id="3a18f-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="3a18f-106">JSON veri biçimi, zaman uyumsuz JavaScript ve XML (AJAX) stili Web uygulamaları yazarken özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="3a18f-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="3a18f-107">Windows Communication Foundation (WCF) ' de AJAX desteği, ScriptManager denetimi aracılığıyla ASP.NET AJAX ile kullanım için iyileştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3a18f-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="3a18f-108">ASP.NET AJAX ile Windows Communication Foundation (WCF) kullanmanın örnekleri için bkz. [Ajax örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="3a18f-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
<span data-ttu-id="3a18f-109">Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.</span><span class="sxs-lookup"><span data-stu-id="3a18f-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="3a18f-110">Örnek, `Person` serileştirme ve seri durumdan çıkarma göstermek için bir veri sözleşmesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a18f-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

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

 <span data-ttu-id="3a18f-111">Türünün bir örneğini JSON olarak seri hale getirmek için `Person` , önce oluşturun <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve `WriteObject` bir akışa JSON verisi yazmak için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="3a18f-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="3a18f-112">Bellek akışı geçerli JSON verileri içeriyor.</span><span class="sxs-lookup"><span data-stu-id="3a18f-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="3a18f-113">Örnek, JSON verilerinden bir nesne olarak seri durumdan çıkarmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a18f-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="3a18f-114">Ardından akışı geri sarın ve çağırın `ReadObject` .</span><span class="sxs-lookup"><span data-stu-id="3a18f-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="3a18f-115">Nesnesi incelen, `p2` JSON verilerinin seri durumdan çıkarılmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a18f-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3a18f-116">Örnekler makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="3a18f-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3a18f-117">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="3a18f-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3a18f-118">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3a18f-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a18f-119">Bu örnek, aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="3a18f-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3a18f-120">Bunu ayarlamak için örneği oluşturun ve çalıştırın</span><span class="sxs-lookup"><span data-stu-id="3a18f-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="3a18f-121">[Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümünde açıklandığı gibi jsonSerialization. sln çözümünü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="3a18f-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="3a18f-122">Ortaya çıkan konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3a18f-122">Run the resulting console application.</span></span>  
