---
title: DataContractJsonSerializer örneği
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: d3456582d73640f1802c17d7f29f4931a6f920b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144636"
---
# <a name="datacontractjsonserializer-sample"></a><span data-ttu-id="5045a-102">DataContractJsonSerializer örneği</span><span class="sxs-lookup"><span data-stu-id="5045a-102">DataContractJsonSerializer sample</span></span>

> [!NOTE]
> <span data-ttu-id="5045a-103">Bu örnek <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>için.</span><span class="sxs-lookup"><span data-stu-id="5045a-103">This sample is for <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="5045a-104">JSON'u serihale ve deserializing içeren çoğu senaryo için [System.Text.Json ad alanında](../../../standard/serialization/system-text-json-overview.md)API'leri öneririz.</span><span class="sxs-lookup"><span data-stu-id="5045a-104">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="5045a-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>olarak aynı türleri <xref:System.Runtime.Serialization.DataContractSerializer>destekler.</span><span class="sxs-lookup"><span data-stu-id="5045a-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="5045a-106">JSON veri biçimi özellikle Asynchronous JavaScript ve XML (AJAX) tarzı Web uygulamaları yazarken kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="5045a-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="5045a-107">Windows Communication Foundation'daki (WCF) AJAX desteği, ScriptManager denetimi aracılığıyla ASP.NET AJAX ile kullanılmak üzere optimize edilebilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5045a-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="5045a-108">ASP.NET AJAX ile Windows Communication Foundation 'ın (WCF) nasıl kullanılacağına örnekler için [AJAX Örnekleri'ne](ajax.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5045a-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
<span data-ttu-id="5045a-109">Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="5045a-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
<span data-ttu-id="5045a-110">Örnek, serileştirme ve deserialization göstermek için bir `Person` veri sözleşmesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="5045a-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

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

 <span data-ttu-id="5045a-111">JSON `Person` türünün bir örneğini seri hale <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> getirmek için, ilkini oluşturun ve JSON verilerini bir akışa yazmak için `WriteObject` yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="5045a-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="5045a-112">Bellek akışı geçerli JSON verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="5045a-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="5045a-113">Örnek, JSON verilerinden bir nesneye deserialing gösterir.</span><span class="sxs-lookup"><span data-stu-id="5045a-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="5045a-114">Daha sonra akışı geri `ReadObject`sarın ve .</span><span class="sxs-lookup"><span data-stu-id="5045a-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="5045a-115">Nesnenin `p2` incelenmesi, JSON verilerinin doğru şekilde deserialed olduğunu ortaya koymaktadır.</span><span class="sxs-lookup"><span data-stu-id="5045a-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5045a-116">Numuneler makinenize zaten yüklenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="5045a-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5045a-117">Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="5045a-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5045a-118">Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin.</span><span class="sxs-lookup"><span data-stu-id="5045a-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5045a-119">Bu örnek aşağıdaki dizinde yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="5045a-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5045a-120">Örneği ayarlamak, oluşturmak ve çalıştırmak için</span><span class="sxs-lookup"><span data-stu-id="5045a-120">To set up, build and run the sample</span></span>  
  
1. <span data-ttu-id="5045a-121">[Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)açıklandığı gibi JsonSerialization.sln çözümlerini oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5045a-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="5045a-122">Ortaya çıkan konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5045a-122">Run the resulting console application.</span></span>  
