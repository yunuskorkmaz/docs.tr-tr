---
title: DataContractJsonSerializer örneği
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 509f80812bb815e4fa56fa3ebdc9236ac0622ace
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141827"
---
# <a name="datacontractjsonserializer-sample"></a>DataContractJsonSerializer örneği

> [!NOTE]
> Bu örnek <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>içindir. JSON serileştirilmesinin ve serisini kaldırma ile ilgili çoğu senaryo için, [System. Text. JSON ad alanındaki](../../../standard/serialization/system-text-json-overview.md)araçları öneririz. 

<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.Runtime.Serialization.DataContractSerializer>aynı türleri destekler. JSON veri biçimi, zaman uyumsuz JavaScript ve XML (AJAX) stili Web uygulamaları yazarken özellikle yararlıdır. Windows Communication Foundation (WCF) ' de AJAX desteği, ScriptManager denetimi aracılığıyla ASP.NET AJAX ile kullanım için iyileştirilmiştir. ASP.NET AJAX ile Windows Communication Foundation (WCF) kullanmanın örnekleri için bkz. [Ajax örnekleri](ajax.md).  
  
Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
Örnek, serileştirme ve seri durumdan çıkarma göstermek için bir `Person` veri sözleşmesi kullanır.  

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

 `Person` türünün bir örneğini JSON olarak seri hale getirmek için önce <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> oluşturun ve `WriteObject` metodunu kullanarak JSON verilerini bir akışa yazın.  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 Bellek akışı geçerli JSON verileri içeriyor.
  
```json  
{"age":42,"name":"John"}  
```  
  
 Örnek, JSON verilerinden bir nesne olarak seri durumdan çıkarmayı gösterir. Sonra akışı geri sarın ve `ReadObject`çağırın.  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 `p2` nesnesini incelemek, JSON verilerinin doğru şekilde seri durumdan çıkarılmadığını gösterir.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örneklerini indirmek üzere [.NET Framework 4 için Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine](https://go.microsoft.com/fwlink/?LinkId=150780) gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Bunu ayarlamak için örneği oluşturun ve çalıştırın  
  
1. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi jsonSerialization. sln çözümünü oluşturun.  
  
2. Ortaya çıkan konsol uygulamasını çalıştırın.  
