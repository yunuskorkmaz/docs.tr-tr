---
title: Veri Üye Sırası
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 2a5d7430953bdc31644e92b9207cd2865209cce5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185194"
---
# <a name="data-member-order"></a>Veri Üye Sırası
Bazı uygulamalarda, çeşitli veri üyelerinden gelen verilerin gönderilme veya alınmasının beklendiği (serileştirilmiş XML'de verilerin göründüğü sıra gibi) sırasını bilmek yararlıdır. Bazen bu sırayı değiştirmek gerekebilir. Bu konu, sıralama kurallarını açıklar.  
  
## <a name="basic-rules"></a>Temel Kurallar  
 Veri sıralama için temel kurallar şunlardır:  
  
- Bir veri sözleşmesi türü devralma hiyerarşisinin bir parçasıysa, temel türlerinin veri üyeleri her zaman sırada ilk sıradadır.  
  
- Sırada, alfabetik sırada öznitelik kümesi özelliği <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> <xref:System.Runtime.Serialization.DataMemberAttribute> olmayan geçerli tür veri üyeleri yer alıyor.  
  
- Sonraki öznitelik kümesi özelliği <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> <xref:System.Runtime.Serialization.DataMemberAttribute> olan tüm veri üyeleri vardır. Bunlar, belirli `Order` bir değerin `Order` birden fazla üyesi varsa, önce özelliğin değerine, sonra da alfabetik olarak sıralanır. Sipariş değerleri atlanabilir.  
  
 Alfabetik sıra <xref:System.String.CompareOrdinal%2A> yöntemi çağırarak kurulur.  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki kodu göz önünde bulundurun.  
  
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
- [Veri Sözleşmesi Eşitliği](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
