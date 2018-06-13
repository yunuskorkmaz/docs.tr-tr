---
title: Veri Üye Sırası
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: e286b900d7647bcd5bc99b78164e6820c1417a63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489550"
---
# <a name="data-member-order"></a>Veri Üye Sırası
Bazı uygulamalarda, verileri çeşitli veri üyelerinden gönderilir veya (örneğin, veri seri hale getirilmiş XML'de gösterilen sırada) alınabilmesi için beklenen sırasını bilmek yararlıdır. Bazen bu sırayı değiştirmek gerekli olabilir. Bu konuda sıralama kuralları açıklanır.  
  
## <a name="basic-rules"></a>Temel kurallar  
 Verileri sıralama için temel kurallar şunlardır:  
  
-   Bir veri sözleşmesi türü bir devralma hiyerarşisini bir parçası ise, veri temel türlerinden her zaman sırayla ilk üyeleridir.  
  
-   Sonraki sırada olmayan geçerli tür veri üyesi <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik alfabetik sırada kümesi.  
  
-   Sonraki sahip herhangi bir veri üyesi olan <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik kümesi. Bu değeri tarafından sıralanır `Order` özelliği ilk ardından alfabetik olarak birden fazla belirli bir üyesi ise `Order` değeri. Sırası değerlerinin atlanabilir.  
  
 Alfabetik çağırarak kurulduğunda <xref:System.String.CompareOrdinal%2A> yöntemi.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki kod göz önünde bulundurun.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 Üretilen XML aşağıdakine benzer.  
  
```xml  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>   
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>   
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>   
</DerivedType>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 [Veri Anlaşması Eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
