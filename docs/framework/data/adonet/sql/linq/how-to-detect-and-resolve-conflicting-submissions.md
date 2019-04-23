---
title: 'Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 606231449263f1c26596ca8606a88053c6aded8e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138131"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="743a5-102">Nasıl yapılır: Çakışan Gönderimleri Algılama ve Çözümleme</span><span class="sxs-lookup"><span data-stu-id="743a5-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="743a5-103">birden çok kullanıcı değişiklikleri veritabanına kökü çakışmaları algılama ve çözümleme için çok sayıda kaynak sağlar.</span><span class="sxs-lookup"><span data-stu-id="743a5-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="743a5-104">Daha fazla bilgi için [nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="743a5-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="743a5-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="743a5-105">Example</span></span>  
 <span data-ttu-id="743a5-106">Aşağıdaki örnekte gösterildiği bir `try` / `catch` yakalayan blok bir <xref:System.Data.Linq.ChangeConflictException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="743a5-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="743a5-107">Her çakışma için varlık ve üye bilgileri, konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="743a5-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="743a5-108">Eklemelisiniz `using System.Reflection` yönergesi (`Imports System.Reflection` Visual Basic'te) bilgi alma desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="743a5-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="743a5-109">Daha fazla bilgi için bkz. <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="743a5-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="743a5-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="743a5-110">See also</span></span>

- [<span data-ttu-id="743a5-111">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="743a5-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="743a5-112">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="743a5-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
