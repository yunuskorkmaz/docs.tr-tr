---
title: JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 2d1daa3388c49964430fe462ea92bf4ac310a974
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332019"
---
# <a name="json-serialization"></a><span data-ttu-id="52ff0-102">JSON Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="52ff0-102">JSON Serialization</span></span>
<span data-ttu-id="52ff0-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> JavaScript nesne gösterimi (JSON) biçimindeki verileri seri hale getrime ve için.</span><span class="sxs-lookup"><span data-stu-id="52ff0-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="52ff0-104">Bu serileştirme motoruna JSON verilerini örneğine dönüştürür [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türler ve JSON verilerini içine geri.</span><span class="sxs-lookup"><span data-stu-id="52ff0-104">This serialization engine converts JSON data into instances of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and back into JSON data.</span></span> <span data-ttu-id="52ff0-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> aynı türlerini destekleyen <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="52ff0-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="52ff0-106">JSON veri biçimi zaman uyumsuz JavaScript ve XML (AJAX) yazma sırasında özellikle yararlı olur-Web uygulamaları stili.</span><span class="sxs-lookup"><span data-stu-id="52ff0-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="52ff0-107">AJAX desteği Windows Communication Foundation (WCF) ScriptManager denetimi aracılığıyla ASP.NET AJAX ile kullanım için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="52ff0-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="52ff0-108">ASP.NET AJAX ile Windows Communication Foundation (WCF) kullanma örnekleri için bkz: [AJAX örnekleri](ajax.md).</span><span class="sxs-lookup"><span data-stu-id="52ff0-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52ff0-109">Bu örnek için Kurulum yordamı ve derleme yönergeleri Bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="52ff0-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="52ff0-110">Örnek kullanan bir `Person` veri sözleşme serileştirme ve seri durumundan çıkarma göstermek.</span><span class="sxs-lookup"><span data-stu-id="52ff0-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

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

 <span data-ttu-id="52ff0-111">Bir örneğini serileştirmek için `Person` JSON olarak yazın, oluşturun <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ilk ve `WriteObject` JSON verilerini bir akışa yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="52ff0-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="52ff0-112">Bellek akışı geçerli JSON verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="52ff0-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="52ff0-113">Örnek, bir nesnede JSON verileri seri durumdan çıkarılırken gösterir.</span><span class="sxs-lookup"><span data-stu-id="52ff0-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="52ff0-114">Ardından akış ve çağrı rewind `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="52ff0-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="52ff0-115">İnceleme `p2` nesnesi, JSON verilerini doğru şekilde seri durumdan, ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="52ff0-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52ff0-116">Örnekler, makinenizde zaten yüklü.</span><span class="sxs-lookup"><span data-stu-id="52ff0-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="52ff0-117">Devam etmeden önce şu (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="52ff0-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="52ff0-118">Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="52ff0-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52ff0-119">Bu örnek, şu dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="52ff0-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="52ff0-120">Ayarlamak için derleme ve örneği çalıştırma</span><span class="sxs-lookup"><span data-stu-id="52ff0-120">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="52ff0-121">' % S'çözüm JsonSerialization.sln açıklandığı gibi oluşturmak [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52ff0-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="52ff0-122">Sonuçta elde edilen konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="52ff0-122">Run the resulting console application.</span></span>  
