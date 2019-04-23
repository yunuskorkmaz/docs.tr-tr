---
title: 'Nasıl yapılır: Varlık Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: 825ba2a32e7c75e922ca08386b9f6efede7b2693
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154758"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="09944-102">Nasıl yapılır: Varlık Çakışma Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="09944-102">How to: Retrieve Entity Conflict Information</span></span>
<span data-ttu-id="09944-103">Nesnelerin kullanabileceğiniz <xref:System.Data.Linq.ObjectChangeConflict> tarafından ortaya çakışmalar hakkında bilgi sağlar sınıfını <xref:System.Data.Linq.ChangeConflictException> özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="09944-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="09944-104">Daha fazla bilgi için [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="09944-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09944-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="09944-105">Example</span></span>  
 <span data-ttu-id="09944-106">Aşağıdaki örnek birikmiş çakışmaları bir listesi üzerinden yinelenir.</span><span class="sxs-lookup"><span data-stu-id="09944-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="09944-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09944-107">See also</span></span>

- [<span data-ttu-id="09944-108">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="09944-108">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
