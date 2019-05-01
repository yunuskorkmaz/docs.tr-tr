---
title: Birlikte çalışabilir nesne başvuruları
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: ada9084f6ac3c97dc641571c0cb8379a2fac68a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918976"
---
# <a name="interoperable-object-references"></a>Birlikte çalışabilir nesne başvuruları
Varsayılan olarak, <xref:System.Runtime.Serialization.DataContractSerializer> nesneleri değerine göre serileştirir. Kullanabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> bildirmesine nesne serileştirilirken nesne başvuruları korumak için veri sözleşmesi serileştiricisi özelliği.  
  
## <a name="generated-xml"></a>Oluşturulan XML  
 Örneğin, şu nesne göz önünde bulundurun:  
  
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
  
 İle <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> kümesine `false` (varsayılan), aşağıdaki XML oluşturulur:  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 İle <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> kümesine `true`, aşağıdaki XML oluşturulur:  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 Ancak, <xref:System.Runtime.Serialization.XsdDataContractExporter> açıklanmamaktadır `id` ve `ref` ve şeması özniteliklerinde bile `preserveObjectReferences` özelliği `true`.  
  
## <a name="using-isreference"></a>IsReference kullanma  
 Tanımladığı şemaya göre geçerli nesne başvuru bilgisi oluşturmak için uygulama <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği bir türe ve ayarlama <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> bayrak `true`. Aşağıdaki örnek, sınıf değiştirir `X` ekleyerek önceki örnekte `IsReference`:  
  
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
  
 Kullanarak `IsReference` ileti gidiş dönüşü üzerinde uyumluluğu güvence altına alır. Bir türü şemadan oluşturulduğunda bu olmadan XML için türü mutlaka başlangıçta kabul şemasıyla uyumlu değil çıktı. Diğer bir deyişle, ancak `id` ve `ref` öznitelikleri seri hale getirilmiş, özgün şema bu öznitelikler (veya tüm öznitelikler) XML'de oluşmasını barred. İle `IsReference` veri üyesi uygulanan, üye olarak tanınması devam *başvurulabilir* olduğunda gidiş dönüşlü.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
