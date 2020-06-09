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
# <a name="data-member-order"></a><span data-ttu-id="e8183-102">Veri Üye Sırası</span><span class="sxs-lookup"><span data-stu-id="e8183-102">Data Member Order</span></span>
<span data-ttu-id="e8183-103">Bazı uygulamalarda, çeşitli veri üyelerinden gelen verilerin gönderilme sırasını veya alınması beklenmekte olan (örneğin, serileştirilmiş XML 'de verilerin bulunduğu sıra) veya alınması beklenen sırayı bilmek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="e8183-103">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="e8183-104">Bazen bu sıranın değiştirilmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e8183-104">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="e8183-105">Bu konuda sıralama kuralları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e8183-105">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="e8183-106">Temel kurallar</span><span class="sxs-lookup"><span data-stu-id="e8183-106">Basic Rules</span></span>  
 <span data-ttu-id="e8183-107">Veri sıralamasına yönelik temel kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e8183-107">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="e8183-108">Bir veri anlaşması türü, devralma hiyerarşisinin bir parçasıysa, temel türlerinin veri üyeleri her zaman sırayla ilk kez olur.</span><span class="sxs-lookup"><span data-stu-id="e8183-108">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="e8183-109">Sırasıyla bir sonraki, öznitelik kümesi özelliğine sahip olmayan geçerli türün veri üyeleridir <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> ( <xref:System.Runtime.Serialization.DataMemberAttribute> alfabetik sırada).</span><span class="sxs-lookup"><span data-stu-id="e8183-109">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="e8183-110">Next, <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> öznitelik kümesi özelliğine sahip herhangi bir veri üyesidir <xref:System.Runtime.Serialization.DataMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="e8183-110">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="e8183-111">Bunlar, ilk olarak özelliğin değerine göre sıralanır `Order` ve belirli bir değerin birden fazla üyesi varsa alfabetik olarak `Order` .</span><span class="sxs-lookup"><span data-stu-id="e8183-111">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="e8183-112">Sıra değerleri atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e8183-112">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="e8183-113">Alfabetik sıralama yöntemi çağırarak belirlenir <xref:System.String.CompareOrdinal%2A> .</span><span class="sxs-lookup"><span data-stu-id="e8183-113">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e8183-114">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e8183-114">Examples</span></span>  
 <span data-ttu-id="e8183-115">Aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e8183-115">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="e8183-116">Oluşturulan XML aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="e8183-116">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e8183-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8183-117">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="e8183-118">Veri Sözleşmesi Eşitliği</span><span class="sxs-lookup"><span data-stu-id="e8183-118">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="e8183-119">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="e8183-119">Using Data Contracts</span></span>](using-data-contracts.md)
