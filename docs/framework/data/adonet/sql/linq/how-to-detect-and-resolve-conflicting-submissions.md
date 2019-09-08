---
title: 'Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 2de0182cc0b87768a9cff553b7ec6e77f8ccc7b8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793767"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="e106d-102">Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme</span><span class="sxs-lookup"><span data-stu-id="e106d-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="e106d-103">, çok kullanıcılı değişikliklerden oluşan çakışmaları saptamak ve çözmek için çok sayıda kaynak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e106d-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="e106d-104">Daha fazla bilgi için [nasıl yapılır: Değişiklik çakışmalarını](how-to-manage-change-conflicts.md)yönetin.</span><span class="sxs-lookup"><span data-stu-id="e106d-104">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e106d-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e106d-105">Example</span></span>  
 <span data-ttu-id="e106d-106">Aşağıdaki örnek bir `try` `catch` / özeldurumuyakalayanbirbloğugösterir<xref:System.Data.Linq.ChangeConflictException> .</span><span class="sxs-lookup"><span data-stu-id="e106d-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="e106d-107">Her çakışma için varlık ve üye bilgileri konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e106d-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e106d-108">Bilgi alımını desteklemek için `using System.Reflection` yönergesini (`Imports System.Reflection` Visual Basic) eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e106d-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="e106d-109">Daha fazla bilgi için bkz. <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="e106d-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e106d-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e106d-110">See also</span></span>

- [<span data-ttu-id="e106d-111">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="e106d-111">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="e106d-112">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="e106d-112">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
