---
title: 'Nasıl yapılır: Üye Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 40caa07488cb40ca8e9e3eb3a570c325b92de491
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793298"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="a23f2-102">Nasıl yapılır: Üye Çakışma Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="a23f2-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="a23f2-103">Çakışan ayrı Üyeler hakkında <xref:System.Data.Linq.MemberChangeConflict> bilgi almak için sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a23f2-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="a23f2-104">Aynı bağlamda, her üye için çakışmayı özel olarak işleme sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a23f2-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="a23f2-105">Daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](optimistic-concurrency-overview.md)bakış.</span><span class="sxs-lookup"><span data-stu-id="a23f2-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a23f2-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="a23f2-106">Example</span></span>  
 <span data-ttu-id="a23f2-107">Aşağıdaki kod <xref:System.Data.Linq.ObjectChangeConflict> nesneler boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="a23f2-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="a23f2-108">Her nesne için, daha sonra <xref:System.Data.Linq.MemberChangeConflict> nesneler boyunca yinelenir.</span><span class="sxs-lookup"><span data-stu-id="a23f2-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a23f2-109">Bilgi <xref:System.Reflection> sağlamak<xref:System.Data.Linq.MemberChangeConflict.Member%2A> için dahil edin.</span><span class="sxs-lookup"><span data-stu-id="a23f2-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a23f2-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a23f2-110">See also</span></span>

- [<span data-ttu-id="a23f2-111">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="a23f2-111">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
