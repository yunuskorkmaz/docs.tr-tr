---
title: Veri Üye Sırası
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 717d7014f4c4a56249ead0c839cf05f4f83a6f5f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593470"
---
# <a name="data-member-order"></a>Veri Üye Sırası
Bazı uygulamalarda, çeşitli veri üyelerinden gelen verilerin gönderilme sırasını veya alınması beklenmekte olan (örneğin, serileştirilmiş XML 'de verilerin bulunduğu sıra) veya alınması beklenen sırayı bilmek yararlı olur. Bazen bu sıranın değiştirilmesi gerekebilir. Bu konuda sıralama kuralları açıklanmaktadır.  
  
## <a name="basic-rules"></a>Temel kurallar  
 Veri sıralamasına yönelik temel kurallar şunlardır:  
  
- Bir veri anlaşması türü, devralma hiyerarşisinin bir parçasıysa, temel türlerinin veri üyeleri her zaman sırayla ilk kez olur.  
  
- Sırasıyla bir sonraki, öznitelik kümesi özelliğine sahip olmayan geçerli türün veri üyeleridir <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> ( <xref:System.Runtime.Serialization.DataMemberAttribute> alfabetik sırada).  
  
- Next, <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> öznitelik kümesi özelliğine sahip herhangi bir veri üyesidir <xref:System.Runtime.Serialization.DataMemberAttribute> . Bunlar, ilk olarak özelliğin değerine göre sıralanır `Order` ve belirli bir değerin birden fazla üyesi varsa alfabetik olarak `Order` . Sıra değerleri atlanabilir.  
  
 Alfabetik sıralama yöntemi çağırarak belirlenir <xref:System.String.CompareOrdinal%2A> .  
  
## <a name="examples"></a>Örnekler  
 Aşağıdaki kodu göz önünde bulundurun.  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 Oluşturulan XML aşağıdaki gibidir.  
  
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
- [Veri Sözleşmesi Eşitliği](data-contract-equivalence.md)
- [Veri Anlaşmalarını Kullanma](using-data-contracts.md)
