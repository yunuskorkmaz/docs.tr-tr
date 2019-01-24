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
# <a name="data-member-order"></a><span data-ttu-id="b3722-102">Veri Üye Sırası</span><span class="sxs-lookup"><span data-stu-id="b3722-102">Data Member Order</span></span>
<span data-ttu-id="b3722-103">Bazı uygulamalarda, verileri çeşitli veri üyeleri'nın gönderilir veya (örneğin, veri serileştirilmiş XML'de görünme sırasını) alınabilmesi için beklenen sırasını bilmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b3722-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="b3722-104">Bazen bu sırayı değiştirmek gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="b3722-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="b3722-105">Bu konu, sıralama kuralları açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3722-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="b3722-106">Temel kurallar</span><span class="sxs-lookup"><span data-stu-id="b3722-106">Basic Rules</span></span>  
 <span data-ttu-id="b3722-107">Verileri sıralama için temel kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b3722-107">The basic rules for data ordering include:</span></span>  
  
-   <span data-ttu-id="b3722-108">Bir veri anlaşması türü devralma hiyerarşisinin bir parçasıysa, veri üyeleri temel türlerinden her zaman sırayla ilk.</span><span class="sxs-lookup"><span data-stu-id="b3722-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
-   <span data-ttu-id="b3722-109">Sonraki sırayla sahip olmayan geçerli türün veri üyesi <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik kümesi, alfabetik olarak sıralayın.</span><span class="sxs-lookup"><span data-stu-id="b3722-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
-   <span data-ttu-id="b3722-110">Sonraki sahip herhangi bir veri üyesi olan <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> öznitelik kümesi.</span><span class="sxs-lookup"><span data-stu-id="b3722-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="b3722-111">Bu değeri tarafından sıralanan `Order` özelliği ilk ve alfabetik olarak birden fazla belirli bir üyesi ise `Order` değeri.</span><span class="sxs-lookup"><span data-stu-id="b3722-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="b3722-112">Sipariş değerleri atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="b3722-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="b3722-113">Alfabetik çağırarak kurulduğunda <xref:System.String.CompareOrdinal%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b3722-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="b3722-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b3722-114">Examples</span></span>  
 <span data-ttu-id="b3722-115">Aşağıdaki kodu düşünün.</span><span class="sxs-lookup"><span data-stu-id="b3722-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="b3722-116">Üretilen XML aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="b3722-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b3722-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3722-117">See also</span></span>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="b3722-118">Veri Anlaşması Eşitliği</span><span class="sxs-lookup"><span data-stu-id="b3722-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="b3722-119">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="b3722-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
