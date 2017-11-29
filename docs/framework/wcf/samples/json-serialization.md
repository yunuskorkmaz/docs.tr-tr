---
title: JSON Seri Hale Getirme
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9c270740eda992653fc4e60072f1276cf20ad584
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="json-serialization"></a>JSON Seri Hale Getirme
Bu örnek nasıl kullanılacağı ortaya <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> seri hale getirmek ve JavaScript nesne gösterimi (JSON) biçimindeki verileri seri durumdan için. Bu seri hale getirme altyapısı JSON verilerini örneğine dönüştürür [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türleri ve tekrar JSON verilerini içine. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>aynı türlerini destekleyen <xref:System.Runtime.Serialization.DataContractSerializer>. Zaman uyumsuz JavaScript ve XML (AJAX) yazılırken JSON veri biçimi özellikle yararlı olur-Web uygulamaları stili. AJAX Destek [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ScriptManager denetimi ile ASP.NET AJAX ile kullanım için optimize edilmiştir. Kullanımıyla ilgili örnekler için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ASP.NET AJAX ile bkz [AJAX örnekleri](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).  
  
> [!NOTE]
>  Kurulum yordam ve yapılandırma yönergeleri Bu örneği için bu konunun sonunda yer alır.  
  
 Örnek kullanan bir `Person` veri sözleşmesi seri hale getirme ve seri durumdan çıkarma göstermek.  
  
```  
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
  
```  
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
  
```  
Person p2 = (Person)ser.ReadObject(stream1);  
```  
  
 İnceleme `p2` nesne ortaya çıkarır JSON verilerini doğru seri olduğunu.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse, Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnek](http://go.microsoft.com/fwlink/?LinkId=150780) tüm indirmek için [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırma  
  
1.  Çözüm JsonSerialization.sln açıklandığı gibi yapı [Windows Communication Foundation örnekleri derleme](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Sonuçta elde edilen konsol uygulamasını çalıştırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.
