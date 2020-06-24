---
title: Veri Üye Sırası
description: WCF 'de veri üye sıralaması hakkında bilgi edinin. Uygulamaların veri üyelerinin gönderilme veya beklenme sırasını bilmesi veya değiştirmesi gerekebilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: 5c192d3bda65a7364345df4310dccd96cbe04056
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247370"
---
# <a name="data-member-order"></a><span data-ttu-id="892a6-104">Veri Üye Sırası</span><span class="sxs-lookup"><span data-stu-id="892a6-104">Data Member Order</span></span>
<span data-ttu-id="892a6-105">Bazı uygulamalarda, çeşitli veri üyelerinden gelen verilerin gönderilme sırasını veya alınması beklenmekte olan (örneğin, serileştirilmiş XML 'de verilerin bulunduğu sıra) veya alınması beklenen sırayı bilmek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="892a6-105">In some applications, it is useful to know the order in which data from the various data members is sent or is expected to be received (such as the order in which data appears in the serialized XML).</span></span> <span data-ttu-id="892a6-106">Bazen bu sıranın değiştirilmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="892a6-106">Sometimes it may be necessary to change this order.</span></span> <span data-ttu-id="892a6-107">Bu konuda sıralama kuralları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="892a6-107">This topic explains the ordering rules.</span></span>  
  
## <a name="basic-rules"></a><span data-ttu-id="892a6-108">Temel kurallar</span><span class="sxs-lookup"><span data-stu-id="892a6-108">Basic Rules</span></span>  
 <span data-ttu-id="892a6-109">Veri sıralamasına yönelik temel kurallar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="892a6-109">The basic rules for data ordering include:</span></span>  
  
- <span data-ttu-id="892a6-110">Bir veri anlaşması türü, devralma hiyerarşisinin bir parçasıysa, temel türlerinin veri üyeleri her zaman sırayla ilk kez olur.</span><span class="sxs-lookup"><span data-stu-id="892a6-110">If a data contract type is a part of an inheritance hierarchy, data members of its base types are always first in the order.</span></span>  
  
- <span data-ttu-id="892a6-111">Sırasıyla bir sonraki, öznitelik kümesi özelliğine sahip olmayan geçerli türün veri üyeleridir <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> ( <xref:System.Runtime.Serialization.DataMemberAttribute> alfabetik sırada).</span><span class="sxs-lookup"><span data-stu-id="892a6-111">Next in order are the current type’s data members that do not have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set, in alphabetical order.</span></span>  
  
- <span data-ttu-id="892a6-112">Next, <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> öznitelik kümesi özelliğine sahip herhangi bir veri üyesidir <xref:System.Runtime.Serialization.DataMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="892a6-112">Next are any data members that have the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> property of the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute set.</span></span> <span data-ttu-id="892a6-113">Bunlar, ilk olarak özelliğin değerine göre sıralanır `Order` ve belirli bir değerin birden fazla üyesi varsa alfabetik olarak `Order` .</span><span class="sxs-lookup"><span data-stu-id="892a6-113">These are ordered by the value of the `Order` property first and then alphabetically if there is more than one member of a certain `Order` value.</span></span> <span data-ttu-id="892a6-114">Sıra değerleri atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="892a6-114">Order values may be skipped.</span></span>  
  
 <span data-ttu-id="892a6-115">Alfabetik sıralama yöntemi çağırarak belirlenir <xref:System.String.CompareOrdinal%2A> .</span><span class="sxs-lookup"><span data-stu-id="892a6-115">Alphabetical order is established by calling the <xref:System.String.CompareOrdinal%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="892a6-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="892a6-116">Examples</span></span>  
 <span data-ttu-id="892a6-117">Aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="892a6-117">Consider the following code.</span></span>  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 <span data-ttu-id="892a6-118">Oluşturulan XML aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="892a6-118">The XML produced is similar to the following.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="892a6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="892a6-119">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [<span data-ttu-id="892a6-120">Veri Sözleşmesi Eşitliği</span><span class="sxs-lookup"><span data-stu-id="892a6-120">Data Contract Equivalence</span></span>](data-contract-equivalence.md)
- [<span data-ttu-id="892a6-121">Veri Anlaşmalarını Kullanma</span><span class="sxs-lookup"><span data-stu-id="892a6-121">Using Data Contracts</span></span>](using-data-contracts.md)
