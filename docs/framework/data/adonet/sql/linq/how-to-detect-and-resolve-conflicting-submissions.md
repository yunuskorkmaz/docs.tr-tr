---
title: 'Nasıl yapılır: Algılamak ve çözmek çakışan gönderimleri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: ab1b56d409a3b185be15ebc8dc119a57038d55bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54510513"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="bb51a-102">Nasıl yapılır: Algılamak ve çözmek çakışan gönderimleri</span><span class="sxs-lookup"><span data-stu-id="bb51a-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="bb51a-103">birden çok kullanıcı değişiklikleri veritabanına kökü çakışmaları algılama ve çözümleme için çok sayıda kaynak sağlar.</span><span class="sxs-lookup"><span data-stu-id="bb51a-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="bb51a-104">Daha fazla bilgi için [nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="bb51a-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb51a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="bb51a-105">Example</span></span>  
 <span data-ttu-id="bb51a-106">Aşağıdaki örnekte gösterildiği bir `try` / `catch` yakalayan blok bir <xref:System.Data.Linq.ChangeConflictException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="bb51a-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="bb51a-107">Her çakışma için varlık ve üye bilgileri, konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="bb51a-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb51a-108">Eklemelisiniz `using System.Reflection` yönergesi (`Imports System.Reflection` Visual Basic'te) bilgi alma desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="bb51a-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="bb51a-109">Daha fazla bilgi için bkz. <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="bb51a-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bb51a-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb51a-110">See also</span></span>
- [<span data-ttu-id="bb51a-111">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="bb51a-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
- [<span data-ttu-id="bb51a-112">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="bb51a-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
