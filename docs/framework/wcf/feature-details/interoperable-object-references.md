---
title: Birlikte Çalışabilir Nesne Başvuruları
ms.date: 03/30/2017
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 9cbbd5a34269a7c4a5c33d72487a02df21f2f0fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222711"
---
# <a name="interoperable-object-references"></a>Birlikte Çalışabilir Nesne Başvuruları
Varsayılan olarak <xref:System.Runtime.Serialization.DataContractSerializer> nesneleri değerine göre serileştirir. Kullanabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> türe ait nesneleri serileştirilirken nesne başvuruları korumak için veri sözleşmesi serileştiricisi istemek için özellik.  
  
## <a name="generated-xml"></a>Oluşturulan XML  
 Örneğin, şu nesne göz önünde bulundurun:  
  
```  
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
   <B ref="1" />  
</X>  
```  
  
 Ancak, <xref:System.Runtime.Serialization.XsdDataContractExporter> açıklanmayan `id` ve `ref` ve şeması özniteliklerinde bile `preserveObjectReferences` özelliği `true`.  
  
## <a name="using-isreference"></a>IsReference kullanma  
 Tanımladığı şemaya göre geçerli nesne başvuru bilgisi oluşturmak için uygulama <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği bir türe ve ayarlama <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> bayrak `true`. Kullanarak `IsReference` önceki örnek sınıfında `X`:  
  
 `[DataContract(IsReference=true)] public class X`  
  
 `{`  
  
 `SomeClass someInstance = new SomeClass();`  
  
 `[DataMember]`  
  
 `public SomeClass A = someInstance;`  
  
 `[DataMember]`  
  
 `public SomeClass B = someInstance;`  
  
 `}`  
  
 `public class SomeClass`  
  
 `{`  
  
 `}`  
  
 Oluşturulan XML aşağıdaki gibidir:  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 Kullanarak `IsReference` ileti gidiş dönüşü üzerinde uyumluluğu güvence altına alır. Bir türü şemadan oluşturulduğunda bu olmadan ne için XML olarak geri türü mutlaka başlangıçta kabul şemasıyla uyumlu değil gönderilir. Diğer bir deyişle, ancak `id` ve `ref` öznitelikleri seri hale getirilmiş, özgün şema bu öznitelikler (veya tüm öznitelikler) XML'de oluşmasını barred. İle `IsReference` veri üyesi uygulanan, üye "başvurulabilir" olduğunda tanınması devam roundtripped.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
