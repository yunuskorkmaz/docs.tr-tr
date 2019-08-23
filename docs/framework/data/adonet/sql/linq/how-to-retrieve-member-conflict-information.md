---
title: 'Nasıl yapılır: Üye Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 9d63b0b2c7d513d9f4db526b88a7c4e852637343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928626"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="2025e-102">Nasıl yapılır: Üye Çakışma Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="2025e-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="2025e-103">Çakışan ayrı Üyeler hakkında <xref:System.Data.Linq.MemberChangeConflict> bilgi almak için sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2025e-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="2025e-104">Aynı bağlamda, her üye için çakışmayı özel olarak işleme sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2025e-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="2025e-105">Daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)bakış.</span><span class="sxs-lookup"><span data-stu-id="2025e-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2025e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="2025e-106">Example</span></span>  
 <span data-ttu-id="2025e-107">Aşağıdaki kod <xref:System.Data.Linq.ObjectChangeConflict> nesneler boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="2025e-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="2025e-108">Her nesne için, daha sonra <xref:System.Data.Linq.MemberChangeConflict> nesneler boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="2025e-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2025e-109">Bilgi <xref:System.Reflection> sağlamak<xref:System.Data.Linq.MemberChangeConflict.Member%2A> için dahil edin.</span><span class="sxs-lookup"><span data-stu-id="2025e-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2025e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2025e-110">See also</span></span>

- [<span data-ttu-id="2025e-111">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="2025e-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
