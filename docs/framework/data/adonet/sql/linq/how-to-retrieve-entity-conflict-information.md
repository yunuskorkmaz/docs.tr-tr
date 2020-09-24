---
title: 'Nasıl yapılır: Varlık Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: e8c548ac632454d9c488ebd5f7b471f6759418fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155880"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="b20fd-102">Nasıl yapılır: Varlık Çakışma Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="b20fd-102">How to: Retrieve Entity Conflict Information</span></span>

<span data-ttu-id="b20fd-103"><xref:System.Data.Linq.ObjectChangeConflict>Özel durumlar tarafından ortaya çıkan çakışmalar hakkında bilgi sağlamak için sınıfının nesnelerini kullanabilirsiniz <xref:System.Data.Linq.ChangeConflictException> .</span><span class="sxs-lookup"><span data-stu-id="b20fd-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="b20fd-104">Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b20fd-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b20fd-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="b20fd-105">Example</span></span>  

 <span data-ttu-id="b20fd-106">Aşağıdaki örnek, birikmiş çakışmaların bir listesi üzerinden yinelenir.</span><span class="sxs-lookup"><span data-stu-id="b20fd-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b20fd-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b20fd-107">See also</span></span>

- [<span data-ttu-id="b20fd-108">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="b20fd-108">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
