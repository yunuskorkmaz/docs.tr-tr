---
title: 'Nasıl yapılır: Varlık Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: 766ede90b14f07e2799c2715daf62aaeeeaa83f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782243"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="4d040-102">Nasıl yapılır: Varlık Çakışma Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="4d040-102">How to: Retrieve Entity Conflict Information</span></span>
<span data-ttu-id="4d040-103">Özel durumlar tarafından <xref:System.Data.Linq.ChangeConflictException> ortaya çıkan çakışmalar <xref:System.Data.Linq.ObjectChangeConflict> hakkında bilgi sağlamak için sınıfının nesnelerini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d040-103">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="4d040-104">Daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](optimistic-concurrency-overview.md)bakış.</span><span class="sxs-lookup"><span data-stu-id="4d040-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d040-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d040-105">Example</span></span>  
 <span data-ttu-id="4d040-106">Aşağıdaki örnek, birikmiş çakışmaların bir listesi üzerinden yinelenir.</span><span class="sxs-lookup"><span data-stu-id="4d040-106">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="4d040-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d040-107">See also</span></span>

- [<span data-ttu-id="4d040-108">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="4d040-108">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
