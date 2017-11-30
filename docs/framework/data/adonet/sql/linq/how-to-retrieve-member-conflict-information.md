---
title: "Nasıl yapılır: üye çakışma bilgisi alma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7dd6829e-79a5-4480-9023-9e588cb0bf2e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a6766e40b842675cbe37ba1ebeb1a956c19e6318
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-member-conflict-information"></a><span data-ttu-id="c903f-102">Nasıl yapılır: üye çakışma bilgisi alma</span><span class="sxs-lookup"><span data-stu-id="c903f-102">How to: Retrieve Member Conflict Information</span></span>
<span data-ttu-id="c903f-103">Kullanabileceğiniz <xref:System.Data.Linq.MemberChangeConflict> çakışan tek tek üyeleri hakkında bilgi almak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="c903f-103">You can use the <xref:System.Data.Linq.MemberChangeConflict> class to retrieve information about individual members in conflict.</span></span> <span data-ttu-id="c903f-104">Aynı bu bağlamda herhangi bir üyesi için özel işleme çakışmanın sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="c903f-104">In this same context you can provide for custom handling of the conflict for any member.</span></span> <span data-ttu-id="c903f-105">Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c903f-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c903f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="c903f-106">Example</span></span>  
 <span data-ttu-id="c903f-107">Aşağıdaki kod dolaşır <xref:System.Data.Linq.ObjectChangeConflict> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c903f-107">The following code iterates through the <xref:System.Data.Linq.ObjectChangeConflict> objects.</span></span> <span data-ttu-id="c903f-108">Her bir nesne için ardından dolaşır <xref:System.Data.Linq.MemberChangeConflict> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c903f-108">For each object, it then iterates through the <xref:System.Data.Linq.MemberChangeConflict> objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c903f-109">Dahil <xref:System.Reflection> sağlamak amacıyla <xref:System.Data.Linq.MemberChangeConflict.Member%2A> bilgi.</span><span class="sxs-lookup"><span data-stu-id="c903f-109">Include <xref:System.Reflection> in order to provide <xref:System.Data.Linq.MemberChangeConflict.Member%2A> information.</span></span>  
  
 [!code-csharp[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.memberchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.MemberChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.memberchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c903f-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c903f-110">See Also</span></span>  
 [<span data-ttu-id="c903f-111">Nasıl yapılır: değişiklik çakışmalarını yönetin</span><span class="sxs-lookup"><span data-stu-id="c903f-111">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
