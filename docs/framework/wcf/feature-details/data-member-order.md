---
title: Veri Üye Sırası
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: c78cc682c0776bfb0ce09dec7ba1ff8cab504285
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198575"
---
# <a name="data-member-order"></a><span data-ttu-id="8dacf-102">Veri Üye Sırası</span><span class="sxs-lookup"><span data-stu-id="8dacf-102">Data Member Order</span></span>
<span data-ttu-id="8dacf-103">Bazı uygulamalarda, verileri çeşitli veri üyeleri'nın gönderilir veya (örneğin, veri serileştirilmiş XML'de görünme sırasını) alınabilmesi için beklenen sırasını bilmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="8dacf-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="8dacf-104">Bazen bu sırayı değiştirmek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="8dacf-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="8dacf-105">Bu konu, sıralama kuralları açıklar.</span><span class="sxs-lookup"><span data-stu-id="8dacf-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="8dacf-106">Temel kurallar</span><span class="sxs-lookup"><span data-stu-id="8dacf-106">Basic Rules</span></span>  
 <span data-ttu-id="8dacf-107">Verileri sıralama için temel kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8dacf-107">The basic rules for data ordering include:</span></span>  
  
-   <span data-ttu-id="8dacf-108">Bir veri anlaşması türü devralma hiyerarşisinin bir parçasıysa, veri üyeleri temel türlerinden her zaman sırayla ilk.</span><span class="sxs-lookup"><span data-stu-id="8dacf-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
-   <span data-ttu-id="8dacf-109">Sonraki sırayla sahip olmayan geçerli türün veri üyesi <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik kümesi, alfabetik olarak sıralayın.</span><span class="sxs-lookup"><span data-stu-id="8dacf-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
-   <span data-ttu-id="8dacf-110">Sonraki sahip herhangi bir veri üyesi olan <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik kümesi.</span><span class="sxs-lookup"><span data-stu-id="8dacf-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="8dacf-111">Bu değeri tarafından sıralanan `Order` özelliği ilk ve alfabetik olarak birden fazla belirli bir üyesi ise `Order` değeri.</span><span class="sxs-lookup"><span data-stu-id="8dacf-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="8dacf-112">Sipariş değerleri atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="8dacf-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="8dacf-113">Alfabetik çağırarak kurulduğunda <xref:System.String.CompareOrdinal%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8dacf-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8dacf-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8dacf-114">Examples</span></span>  
 <span data-ttu-id="8dacf-115">Aşağıdaki kodu düşünün.</span><span class="sxs-lookup"><span data-stu-id="8dacf-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="8dacf-116">Üretilen XML aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="8dacf-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8dacf-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8dacf-117">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="8dacf-118">Veri Sözleşmesi Eşitliği</span><span class="sxs-lookup"><span data-stu-id="8dacf-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="8dacf-119">Veri Sözleşmelerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="8dacf-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
