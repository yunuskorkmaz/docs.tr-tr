---
title: 'Nasıl yapılır: Üye Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: fae1513e7a7ead98318d907b220b7510758c9ffe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115095"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="28f10-102">Nasıl yapılır: Üye Çakışma Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="28f10-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="28f10-103">Kullanabileceğiniz <xref:System.Data.Linq.MemberChangeConflict> çakışan tek tek üyeleri hakkında bilgi almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="28f10-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="28f10-104">Bu aynı bağlamda herhangi bir üyesi için özel işleme çakışmanın sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="28f10-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="28f10-105">Daha fazla bilgi için [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="28f10-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="28f10-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="28f10-106">Example</span></span>  
 <span data-ttu-id="28f10-107">Aşağıdaki kod gezinir <xref:System.Data.Linq.ObjectChangeConflict> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="28f10-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="28f10-108">Her bir nesne için ardından gezinir <xref:System.Data.Linq.MemberChangeConflict> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="28f10-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28f10-109">Dahil <xref:System.Reflection> sağlamak amacıyla <xref:System.Data.Linq.MemberChangeConflict.Member%2A> bilgileri.</span><span class="sxs-lookup"><span data-stu-id="28f10-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="28f10-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28f10-110">See also</span></span>

- [<span data-ttu-id="28f10-111">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="28f10-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
