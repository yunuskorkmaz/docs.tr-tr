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
# <a name="datacontractjsonserializer-sample"></a>DataContractJsonSerializer örneği

> [!NOTE]
> Bu örnek <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>için. JSON'u serihale ve deserializing içeren çoğu senaryo için [System.Text.Json ad alanında](../../../standard/serialization/system-text-json-overview.md)API'leri öneririz.

<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>olarak aynı türleri <xref:System.Runtime.Serialization.DataContractSerializer>destekler. JSON veri biçimi özellikle Asynchronous JavaScript ve XML (AJAX) tarzı Web uygulamaları yazarken kullanışlıdır. Windows Communication Foundation'daki (WCF) AJAX desteği, ScriptManager denetimi aracılığıyla ASP.NET AJAX ile kullanılmak üzere optimize edilebilmektedir. ASP.NET AJAX ile Windows Communication Foundation 'ın (WCF) nasıl kullanılacağına örnekler için [AJAX Örnekleri'ne](ajax.md)bakın.  
  
Bu örnek için kurulum yordamı ve yapı yönergeleri bu konunun sonunda yer alır.  
  
Örnek, serileştirme ve deserialization göstermek için bir `Person` veri sözleşmesi kullanır.  

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

 JSON `Person` türünün bir örneğini seri hale <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> getirmek için, ilkini oluşturun ve JSON verilerini bir akışa yazmak için `WriteObject` yöntemi kullanın.  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 Bellek akışı geçerli JSON verileri içerir.
  
```json  
{"age":42,"name":"John"}  
```  
  
 Örnek, JSON verilerinden bir nesneye deserialing gösterir. Daha sonra akışı geri `ReadObject`sarın ve .  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 Nesnenin `p2` incelenmesi, JSON verilerinin doğru şekilde deserialed olduğunu ortaya koymaktadır.  
  
> [!IMPORTANT]
> Numuneler makinenize zaten yüklenmiş olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örneklerini indirmek için .NET Framework 4 için Windows Communication [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Foundation [(WCF) ve Windows İş Akışı Temeli (WF) Örneklerine](https://www.microsoft.com/download/details.aspx?id=21459) gidin. Bu örnek aşağıdaki dizinde yer almaktadır.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Örneği ayarlamak, oluşturmak ve çalıştırmak için  
  
1. [Windows Communication Foundation Samples'i oluştururken](../../../../docs/framework/wcf/samples/building-the-samples.md)açıklandığı gibi JsonSerialization.sln çözümlerini oluşturun.  
  
2. Ortaya çıkan konsol uygulamasını çalıştırın.  
