---
title: JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 389bdc8b064bda9870b33a2e4c46fdf90bb7f3ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502516"
---
# <a name="json-serialization"></a><span data-ttu-id="d7db8-102">JSON Seri Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="d7db8-102">JSON Serialization</span></span>
<span data-ttu-id="d7db8-103">Bu örnek nasıl kullanılacağı ortaya <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> seri hale getirmek ve JavaScript nesne gösterimi (JSON) biçimindeki verileri seri durumdan için.</span><span class="sxs-lookup"><span data-stu-id="d7db8-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="d7db8-104">Bu seri hale getirme altyapısı JSON verilerini örneğine dönüştürür [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri ve tekrar JSON verilerini içine.</span><span class="sxs-lookup"><span data-stu-id="d7db8-104">This serialization engine converts JSON data into instances of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and back into JSON data.</span></span> <span data-ttu-id="d7db8-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> aynı türlerini destekleyen <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d7db8-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="d7db8-106">Zaman uyumsuz JavaScript ve XML (AJAX) yazılırken JSON veri biçimi özellikle yararlı olur-Web uygulamaları stili.</span><span class="sxs-lookup"><span data-stu-id="d7db8-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="d7db8-107">AJAX destek Windows Communication Foundation (WCF) ScriptManager denetimi ile ASP.NET AJAX ile kullanım için optimize edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d7db8-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="d7db8-108">ASP.NET AJAX ile Windows Communication Foundation (WCF) kullanma örnekleri için bkz: [AJAX örnekleri](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span><span class="sxs-lookup"><span data-stu-id="d7db8-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7db8-109">Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="d7db8-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d7db8-110">Örnek kullanan bir `Person` veri sözleşmesi seri hale getirme ve seri durumdan çıkarma göstermek.</span><span class="sxs-lookup"><span data-stu-id="d7db8-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

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

 <span data-ttu-id="d7db8-111">Örneğini serileştirmek için `Person` türü için JSON, oluşturma <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ilk ve `WriteObject` JSON verilerini bir akışa yazmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d7db8-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="d7db8-112">Bellek akışı geçerli JSON verilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d7db8-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="d7db8-113">Örnek, bir nesneye JSON verilerini seri durumdan çıkarılırken gösterir.</span><span class="sxs-lookup"><span data-stu-id="d7db8-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="d7db8-114">Ardından akış ve çağrı geri `ReadObject`.</span><span class="sxs-lookup"><span data-stu-id="d7db8-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="d7db8-115">İnceleme `p2` nesne ortaya çıkarır JSON verilerini doğru seri olduğunu.</span><span class="sxs-lookup"><span data-stu-id="d7db8-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d7db8-116">Örnekler, makinenizde zaten yüklü olabilir.</span><span class="sxs-lookup"><span data-stu-id="d7db8-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d7db8-117">Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.</span><span class="sxs-lookup"><span data-stu-id="d7db8-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d7db8-118">Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d7db8-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d7db8-119">Bu örnek aşağıdaki dizinde bulunur.</span><span class="sxs-lookup"><span data-stu-id="d7db8-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d7db8-120">Ayarlamak için derleme ve örnek çalıştırma</span><span class="sxs-lookup"><span data-stu-id="d7db8-120">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="d7db8-121">Çözüm JsonSerialization.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d7db8-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="d7db8-122">Sonuçta elde edilen konsol uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d7db8-122">Run the resulting console application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7db8-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d7db8-123">See Also</span></span>
