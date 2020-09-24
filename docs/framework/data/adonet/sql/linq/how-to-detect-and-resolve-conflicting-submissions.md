---
title: 'Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 96e96208d9bb28092701164e6cd5943ef81515a5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147729"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="a1d8f-102">Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme</span><span class="sxs-lookup"><span data-stu-id="a1d8f-102">How to: Detect and Resolve Conflicting Submissions</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a1d8f-103">, çok kullanıcılı değişikliklerden oluşan çakışmaları saptamak ve çözmek için çok sayıda kaynak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a1d8f-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="a1d8f-104">Daha fazla bilgi için bkz. [nasıl yapılır: değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="a1d8f-104">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1d8f-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1d8f-105">Example</span></span>  

 <span data-ttu-id="a1d8f-106">Aşağıdaki örnek `try` / `catch` bir özel durumu yakalayan bir bloğu gösterir <xref:System.Data.Linq.ChangeConflictException> .</span><span class="sxs-lookup"><span data-stu-id="a1d8f-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="a1d8f-107">Her çakışma için varlık ve üye bilgileri konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a1d8f-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1d8f-108">`using System.Reflection` `Imports System.Reflection` Bilgi alımını desteklemek için yönergesini (Visual Basic) eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a1d8f-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="a1d8f-109">Daha fazla bilgi için bkz. <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="a1d8f-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="a1d8f-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1d8f-110">See also</span></span>

- [<span data-ttu-id="a1d8f-111">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="a1d8f-111">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="a1d8f-112">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="a1d8f-112">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
