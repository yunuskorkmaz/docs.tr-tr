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
# <a name="data-member-order"></a><span data-ttu-id="f4950-102">Veri Üye Sırası</span><span class="sxs-lookup"><span data-stu-id="f4950-102">Data Member Order</span></span>
<span data-ttu-id="f4950-103">Bazı uygulamalarda, çeşitli veri üyelerinden gelen verilerin gönderilme veya alınmasının beklendiği (serileştirilmiş XML'de verilerin göründüğü sıra gibi) sırasını bilmek yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f4950-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="f4950-104">Bazen bu sırayı değiştirmek gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="f4950-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="f4950-105">Bu konu, sıralama kurallarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="f4950-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="f4950-106">Temel Kurallar</span><span class="sxs-lookup"><span data-stu-id="f4950-106">Basic Rules</span></span>  
 <span data-ttu-id="f4950-107">Veri sıralama için temel kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="f4950-107">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="f4950-108">Bir veri sözleşmesi türü devralma hiyerarşisinin bir parçasıysa, temel türlerinin veri üyeleri her zaman sırada ilk sıradadır.</span><span class="sxs-lookup"><span data-stu-id="f4950-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="f4950-109">Sırada, alfabetik sırada öznitelik kümesi özelliği <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> <xref:System.Runtime.Serialization.DataMemberAttribute> olmayan geçerli tür veri üyeleri yer alıyor.</span><span class="sxs-lookup"><span data-stu-id="f4950-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="f4950-110">Sonraki öznitelik kümesi özelliği <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> <xref:System.Runtime.Serialization.DataMemberAttribute> olan tüm veri üyeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="f4950-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="f4950-111">Bunlar, belirli `Order` bir değerin `Order` birden fazla üyesi varsa, önce özelliğin değerine, sonra da alfabetik olarak sıralanır.</span><span class="sxs-lookup"><span data-stu-id="f4950-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="f4950-112">Sipariş değerleri atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f4950-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="f4950-113">Alfabetik sıra <xref:System.String.CompareOrdinal%2A> yöntemi çağırarak kurulur.</span><span class="sxs-lookup"><span data-stu-id="f4950-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="f4950-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f4950-114">Examples</span></span>  
 <span data-ttu-id="f4950-115">Aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="f4950-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="f4950-116">Üretilen XML aşağıdakine benzer.</span><span class="sxs-lookup"><span data-stu-id="f4950-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f4950-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4950-117">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="f4950-118">Veri Sözleşmesi Eşitliği</span><span class="sxs-lookup"><span data-stu-id="f4950-118">Data Contract Equivalence</span></span>](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [<span data-ttu-id="f4950-119">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="f4950-119">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
