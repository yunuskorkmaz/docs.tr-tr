---
title: JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 9b1e20c6262f286a4b81f8c368a153fb5a26193b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913954"
---
# <a name="json-serialization"></a>JSON Seri Hale Getirme
Bu örnek, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> JavaScript nesne gösterimi (JSON) biçimindeki verileri seri hale getirmek ve seri durumdan çıkarmak için ' nin nasıl kullanılacağını gösterir. Bu serileştirme altyapısı JSON verilerini .NET Framework türü örneklerine ve JSON verilerine geri dönüştürür. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ile <xref:System.Runtime.Serialization.DataContractSerializer>aynı türleri destekler. JSON veri biçimi, zaman uyumsuz JavaScript ve XML (AJAX) stili Web uygulamaları yazarken özellikle yararlıdır. Windows Communication Foundation (WCF) ' de AJAX desteği, ScriptManager denetimi aracılığıyla ASP.NET AJAX ile kullanım için iyileştirilmiştir. ASP.NET AJAX ile Windows Communication Foundation (WCF) kullanmanın örnekleri için bkz. [Ajax örnekleri](ajax.md).  
  
> [!NOTE]
> Bu örneğe ilişkin Kurulum yordamı ve derleme yönergeleri bu konunun sonunda bulunur.  
  
 Örnek, serileştirme ve `Person` seri durumdan çıkarma göstermek için bir veri sözleşmesi kullanır.  

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

 `Person` Türünün bir örneğini JSON olarak seri hale getirmek için, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> önce oluşturun ve bir akışa JSON `WriteObject` verisi yazmak için yöntemini kullanın.  

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
  
 Örnek, JSON verilerinden bir nesne olarak seri durumdan çıkarmayı gösterir. Ardından akışı geri sarın ve çağırın `ReadObject`.  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 `p2` Nesnesi incelen, JSON verilerinin seri durumdan çıkarılmadığını gösterir.  
  
> [!IMPORTANT]
>  Örnekler makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizini denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin yoksa, tüm Windows Communication Foundation (WCF) ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri indirmek için [Windows Communication Foundation (WCF) ve Windows Workflow Foundation (WF) örneklerine .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ' e gidin. Bu örnek, aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Bunu ayarlamak için örneği oluşturun ve çalıştırın  
  
1. [Windows Communication Foundation örnekleri oluşturma](../../../../docs/framework/wcf/samples/building-the-samples.md)bölümünde açıklandığı gibi jsonSerialization. sln çözümünü oluşturun.  
  
2. Ortaya çıkan konsol uygulamasını çalıştırın.  
