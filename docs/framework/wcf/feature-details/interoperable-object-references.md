---
title: Birlikte çalışabilir nesne başvuruları
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 0927f217a1666f8f27ca9c3e68f80a96b9c0f2b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184699"
---
# <a name="interoperable-object-references"></a>Birlikte çalışabilir nesne başvuruları
Varsayılan olarak, <xref:System.Runtime.Serialization.DataContractSerializer> nesneleri değere göre serileştirir. Nesneleri seri <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> hale alırken nesne başvurularını korumak için veri sözleşmesi serileştiricisini eğitmek için özelliği kullanabilirsiniz.  
  
## <a name="generated-xml"></a>Oluşturulan XML  
 Örnek olarak, aşağıdaki nesneyi göz önünde bulundurun:  
  
```csharp  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass
{  
}  
```  
  
 Ayarlanan <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> `false` (varsayılan) ile aşağıdaki XML oluşturulur:  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> Ayarlamak ile, `true`aşağıdaki XML oluşturulur:  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 Ancak, <xref:System.Runtime.Serialization.XsdDataContractExporter> `preserveObjectReferences` özelliği `true`olarak ayarlanmış `ref` olsa bile, şema ve öznitelikleri açıklamıyor. `id`  
  
## <a name="using-isreference"></a>IsReference'ı kullanma  
 Bunu açıklayan şemaya göre geçerli olan nesne başvuru bilgilerini oluşturmak <xref:System.Runtime.Serialization.DataContractAttribute> için, özniteliği bir türe <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> `true`uygulayın ve bayrağı . Aşağıdaki örnek, önceki `X` örnekte sınıfı aşağıdakileri ekleyerek `IsReference`değiştirir:  
  
```csharp
[DataContract(IsReference=true)]
public class X
{  
     SomeClass someInstance = new SomeClass();
     [DataMember]
     public SomeClass A = someInstance;
     [DataMember]
     public SomeClass B = someInstance;
}
  
public class SomeClass
{
}  
````

 Oluşturulan XML aşağıdaki gibidir:  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 Kullanarak `IsReference` ileti yuvarlak tripping üzerinde uyumluluk sağlar. Bu olmadan, şema bir tür oluşturulduğunda, bu tür için XML çıkışı mutlaka şema başlangıçta kabul ile uyumlu değildir. Başka bir deyişle, `id` `ref` öznitelikleri serihale edilmiş olsa da, özgün şema bu öznitelikleri (veya tüm öznitelikleri) XML'de oluşmasını engelleyebilir. Bir `IsReference` veri üyesine uygulandığında, üye gidiş-dönüş yapıldığında *başvurulabilir* olarak tanınmaya devam etmektedir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
