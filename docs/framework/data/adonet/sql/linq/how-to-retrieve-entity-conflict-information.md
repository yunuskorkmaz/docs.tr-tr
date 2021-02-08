---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: varlık çakışma bilgilerini alma'
title: 'Nasıl yapılır: Varlık Çakışma Bilgilerini Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9a02b608-e7bb-4041-a452-a7fed26fd008
ms.openlocfilehash: dde11a431ae977595b9845444e48705a4552fb23
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767758"
---
# <a name="how-to-retrieve-entity-conflict-information"></a><span data-ttu-id="de171-103">Nasıl yapılır: Varlık Çakışma Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="de171-103">How to: Retrieve Entity Conflict Information</span></span>

<span data-ttu-id="de171-104"><xref:System.Data.Linq.ObjectChangeConflict>Özel durumlar tarafından ortaya çıkan çakışmalar hakkında bilgi sağlamak için sınıfının nesnelerini kullanabilirsiniz <xref:System.Data.Linq.ChangeConflictException> .</span><span class="sxs-lookup"><span data-stu-id="de171-104">You can use objects of the <xref:System.Data.Linq.ObjectChangeConflict> class to provide information about conflicts revealed by <xref:System.Data.Linq.ChangeConflictException> exceptions.</span></span> <span data-ttu-id="de171-105">Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="de171-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de171-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="de171-106">Example</span></span>  

 <span data-ttu-id="de171-107">Aşağıdaki örnek, birikmiş çakışmaların bir listesi üzerinden yinelenir.</span><span class="sxs-lookup"><span data-stu-id="de171-107">The following example iterates through a list of accumulated conflicts.</span></span>  
  
 [!code-csharp[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.objectchangeconflict/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ObjectChangeConflict#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.objectchangeconflict/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="de171-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de171-108">See also</span></span>

- [<span data-ttu-id="de171-109">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="de171-109">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
