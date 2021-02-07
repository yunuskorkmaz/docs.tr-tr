---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: üye çakışma bilgilerini alma'
title: 'Nasıl yapılır: Üye Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
ms.openlocfilehash: 2a33aba1a113bdfd66bdc341bfc9ae59406f2c40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723406"
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="bc70d-103">Nasıl yapılır: Üye Çakışma Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="bc70d-103">How to: Retrieve Member Conflict Information</span></span>

<span data-ttu-id="bc70d-104"><xref:System.Data.Linq.MemberChangeConflict>Çakışan ayrı Üyeler hakkında bilgi almak için sınıfını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc70d-104">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="bc70d-105">Aynı bağlamda, her üye için çakışmayı özel olarak işleme sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bc70d-105">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="bc70d-106">Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bc70d-106">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc70d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="bc70d-107">Example</span></span>  

 <span data-ttu-id="bc70d-108">Aşağıdaki kod nesneler boyunca yinelenir <xref:System.Data.Linq.ObjectChangeConflict> .</span><span class="sxs-lookup"><span data-stu-id="bc70d-108">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="bc70d-109">Her nesne için, daha sonra nesneler boyunca yinelenir <xref:System.Data.Linq.MemberChangeConflict> .</span><span class="sxs-lookup"><span data-stu-id="bc70d-109">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc70d-110"><xref:System.Reflection>Bilgi sağlamak için dahil edin <xref:System.Data.Linq.MemberChangeConflict.Member%2A> .</span><span class="sxs-lookup"><span data-stu-id="bc70d-110">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bc70d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bc70d-111">See also</span></span>

- [<span data-ttu-id="bc70d-112">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="bc70d-112">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
