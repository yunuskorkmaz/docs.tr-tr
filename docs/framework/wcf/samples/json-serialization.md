---
title: JSON Seri Hale Getirme
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 389bdc8b064bda9870b33a2e4c46fdf90bb7f3ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="json-serialization"></a>JSON Seri Hale Getirme
Bu örnek nasıl kullanılacağı ortaya <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> seri hale getirmek ve JavaScript nesne gösterimi (JSON) biçimindeki verileri seri durumdan için. Bu seri hale getirme altyapısı JSON verilerini örneğine dönüştürür [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri ve tekrar JSON verilerini içine. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> aynı türlerini destekleyen <xref:System.Runtime.Serialization.DataContractSerializer>. Zaman uyumsuz JavaScript ve XML (AJAX) yazılırken JSON veri biçimi özellikle yararlı olur-Web uygulamaları stili. AJAX destek Windows Communication Foundation (WCF) ScriptManager denetimi ile ASP.NET AJAX ile kullanım için optimize edilmiştir. ASP.NET AJAX ile Windows Communication Foundation (WCF) kullanma örnekleri için bkz: [AJAX örnekleri](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.  
  
 Örnek kullanan bir `Person` veri sözleşmesi seri hale getirme ve seri durumdan çıkarma göstermek.  

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

 Örneğini serileştirmek için `Person` türü için JSON, oluşturma <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ilk ve `WriteObject` JSON verilerini bir akışa yazmak için yöntem.  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 Bellek akışı geçerli JSON verilerini içerir.
  
```json  
{"age":42,"name":"John"}  
```  
  
 Örnek, bir nesneye JSON verilerini seri durumdan çıkarılırken gösterir. Ardından akış ve çağrı geri `ReadObject`.  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 İnceleme `p2` nesne ortaya çıkarır JSON verilerini doğru seri olduğunu.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırma  
  
1.  Çözüm JsonSerialization.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Sonuçta elde edilen konsol uygulamasını çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
