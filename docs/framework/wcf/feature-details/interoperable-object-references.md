---
description: 'Daha fazla bilgi edinin: birlikte çalışabilen nesne başvuruları'
title: Birlikte çalışabilen nesne başvuruları
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 27c801fb3954c7ea3f821a6588a2229502702989
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802690"
---
# <a name="interoperable-object-references"></a>Birlikte çalışabilen nesne başvuruları

Varsayılan olarak, <xref:System.Runtime.Serialization.DataContractSerializer> nesneleri değere göre seri hale getirir. <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>Nesneleri serileştirilirken nesne başvurularını korumak üzere veri sözleşmesinin serileştiriciye bildirmek için özelliğini kullanabilirsiniz.  
  
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
  
 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> `false` , (Varsayılan) olarak ayarlandığında, aşağıdaki XML oluşturulur:  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A>, Olarak ayarlanmış olarak `true` , aşağıdaki XML oluşturulur:  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 Ancak, <xref:System.Runtime.Serialization.XsdDataContractExporter> `id` `ref` özelliği olarak ayarlanmış olsa bile, şema içindeki ve özniteliklerini tanımlamaz `preserveObjectReferences` `true` .  
  
## <a name="using-isreference"></a>IsReference kullanma  

 Tanımlayan şemaya göre geçerli olan nesne başvuru bilgileri oluşturmak için, <xref:System.Runtime.Serialization.DataContractAttribute> özniteliğini bir türe uygulayın ve <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> bayrağını olarak ayarlayın `true` . Aşağıdaki örnek, bir `X` önceki örnekteki sınıfını şunu ekleyerek değiştirir `IsReference` :  
  
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
  
 Kullanma, `IsReference` iletinin gidiş dönüşü üzerinde uyumluluğu güvence altına alır. Bu olmadan, şemadan bir tür oluşturulduğunda, bu tür için XML çıktısı, özgün olarak kabul edilen şemayla uyumlu değildir. Diğer bir deyişle, `id` ve `ref` öznitelikleri serileştirildiği halde, özgün şema bu özniteliklerin (veya tüm ÖZNITELIKLERIN) XML 'de oluşmasını önlemiş olabilir. `IsReference`Bir veri üyesine uygulandığında, üye, yuvarlama sırasında *başvurulabilir* olarak tanınmaya devam eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
