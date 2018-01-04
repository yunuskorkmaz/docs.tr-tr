---
title: "Birlikte Çalışabilir Nesne Başvuruları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d74c54d29f7da085d9d87bf37cc93078726f308
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="interoperable-object-references"></a>Birlikte Çalışabilir Nesne Başvuruları
Varsayılan olarak <xref:System.Runtime.Serialization.DataContractSerializer> değeriyle nesneleri serileştirir. Kullanabileceğiniz <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> nesne başvuruları türündeki nesneleri serileştirirken korumak için veri sözleşmesi seri hale getirici istemek üzere özelliği.  
  
## <a name="generated-xml"></a>Oluşturulan XML  
 Örnek olarak, aşağıdaki nesne göz önünde bulundurun:  
  
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
  
 Ancak, <xref:System.Runtime.Serialization.XsdDataContractExporter> açıklanmayan `id` ve `ref` ve şeması öznitelikleri bile `preserveObjectReferences` özelliği ayarlanmış `true`.  
  
## <a name="using-isreference"></a>IsReference kullanma  
 Açıklayan şemaya göre geçerli nesne başvuru bilgileri oluşturmak için geçerli <xref:System.Runtime.Serialization.DataContractAttribute> bir türüne ve ayarlayın <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> bayrağını `true`. Kullanarak `IsReference` önceki örnek sınıfında `X`:  
  
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
  
 Kullanarak `IsReference` ileti gidiş uyumluluk sağlar. Bir türü şemadan oluşturulduğunda bu olmadan ne için XML olarak geri türü mutlaka ilk olarak kabul şemasıyla uyumlu değil gönderilir. Diğer bir deyişle, ancak `id` ve `ref` öznitelikleri seri, özgün şema bu öznitelikleri (veya tüm) XML'de oluşmasını barred. İle `IsReference` veri üyesi uygulanan, üye "önerilebilir" olduğunda kabul edilecek devam roundtripped.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
