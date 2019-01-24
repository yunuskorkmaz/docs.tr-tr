---
title: Veri Üye Sırası
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 93ec81d94d8133fc5a6d71d7f1b57b2e9a6aad21
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659637"
---
# <a name="data-member-order"></a>Veri Üye Sırası
Bazı uygulamalarda, verileri çeşitli veri üyeleri'nın gönderilir veya (örneğin, veri serileştirilmiş XML'de görünme sırasını) alınabilmesi için beklenen sırasını bilmek yararlıdır. Bazen bu sırayı değiştirmek gerekli olabilir. Bu konu, sıralama kuralları açıklar.  
  
## <a name="basic-rules"></a>Temel kurallar  
 Verileri sıralama için temel kurallar şunlardır:  
  
-   Bir veri anlaşması türü devralma hiyerarşisinin bir parçasıysa, veri üyeleri temel türlerinden her zaman sırayla ilk.  
  
-   Sonraki sırayla sahip olmayan geçerli türün veri üyesi <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik kümesi, alfabetik olarak sıralayın.  
  
-   Sonraki sahip herhangi bir veri üyesi olan <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik kümesi. Bu değeri tarafından sıralanan `Order` özelliği ilk ve alfabetik olarak birden fazla belirli bir üyesi ise `Order` değeri. Sipariş değerleri atlanabilir.  
  
 Alfabetik çağırarak kurulduğunda <xref:System.String.CompareOrdinal%2A> yöntemi.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki kodu düşünün.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Veri Anlaşması Eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
