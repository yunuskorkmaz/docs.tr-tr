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
# <a name="datacontractjsonserializer-sample"></a>DataContractJsonSerializer örneği

> [!NOTE]
> Bu örnek için <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> . JSON serileştirilmesinin ve serisini kaldırma ile ilgili çoğu senaryo için, [System. Text. JSON ad alanındaki](../../../standard/serialization/system-text-json-overview.md)API 'leri öneririz.

<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ile aynı türleri destekler <xref:System.Runtime.Serialization.DataContractSerializer> . JSON veri biçimi, zaman uyumsuz JavaScript ve XML (AJAX) stili Web uygulamaları yazarken özellikle yararlıdır. Windows Communication Foundation (WCF) ' de AJAX desteği, ScriptManager denetimi aracılığıyla ASP.NET AJAX ile kullanım için iyileştirilmiştir. ASP.NET AJAX ile Windows Communication Foundation (WCF) kullanmanın örnekleri için bkz. [Ajax örnekleri](ajax.md).  
  
Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
Örnek, `Person` serileştirme ve seri durumdan çıkarma göstermek için bir veri sözleşmesi kullanır.  

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

 Türünün bir örneğini JSON olarak seri hale getirmek için `Person` , önce oluşturun <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve `WriteObject` bir akışa JSON verisi yazmak için yöntemini kullanın.  

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
  
 Örnek, JSON verilerinden bir nesne olarak seri durumdan çıkarmayı gösterir. Ardından akışı geri sarın ve çağırın `ReadObject` .  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 Nesnesi incelen, `p2` JSON verilerinin seri durumdan çıkarılmadığını gösterir.  
  
> [!IMPORTANT]
> Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ' e gidin [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Bu örnek, aşağıdaki dizinde bulunur.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Bunu ayarlamak için örneği oluşturun ve çalıştırın  
  
1. [Windows Communication Foundation örnekleri oluşturma](building-the-samples.md)bölümünde açıklandığı gibi jsonSerialization. sln çözümünü oluşturun.  
  
2. Ortaya çıkan konsol uygulamasını çalıştırın.  
