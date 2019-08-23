---
title: 'Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: ff33196f83e2c0d8d759e4ffc3fb7442e8ba0e3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940093"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="6da8c-102">Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme</span><span class="sxs-lookup"><span data-stu-id="6da8c-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="6da8c-103">, çok kullanıcılı değişikliklerden oluşan çakışmaları saptamak ve çözmek için çok sayıda kaynak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6da8c-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="6da8c-104">Daha fazla bilgi için [nasıl yapılır: Değişiklik çakışmalarını](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)yönetin.</span><span class="sxs-lookup"><span data-stu-id="6da8c-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6da8c-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="6da8c-105">Example</span></span>  
 <span data-ttu-id="6da8c-106">Aşağıdaki örnek bir `try` `catch` / özeldurumuyakalayanbirbloğugösterir<xref:System.Data.Linq.ChangeConflictException> .</span><span class="sxs-lookup"><span data-stu-id="6da8c-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="6da8c-107">Her çakışma için varlık ve üye bilgileri konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="6da8c-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6da8c-108">Bilgi alımını desteklemek için `using System.Reflection` yönergesini (`Imports System.Reflection` Visual Basic) eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6da8c-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="6da8c-109">Daha fazla bilgi için bkz. <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="6da8c-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6da8c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6da8c-110">See also</span></span>

- [<span data-ttu-id="6da8c-111">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="6da8c-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="6da8c-112">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="6da8c-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
