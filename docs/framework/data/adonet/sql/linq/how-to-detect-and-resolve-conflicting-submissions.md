---
title: "Nasıl yapılır: algılamak ve çakışan gönderimlerini gidermek"
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
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8eb2e27ab034d464ba6978d9ddc063e623812619
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="e326a-102">Nasıl yapılır: algılamak ve çakışan gönderimlerini gidermek</span><span class="sxs-lookup"><span data-stu-id="e326a-102">How to: Detect and Resolve Conflicting Submissions</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="e326a-103">Algılama ve birden çok kullanıcı değişiklikleri veritabanına gövdesi çakışmalarını çözme için birçok kaynaklar sağlar.</span><span class="sxs-lookup"><span data-stu-id="e326a-103"> provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="e326a-104">Daha fazla bilgi için bkz: [nasıl yapılır: yönetmek değişiklik çakışmaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span><span class="sxs-lookup"><span data-stu-id="e326a-104">For more information, see [How to: Manage Change Conflicts](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e326a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="e326a-105">Example</span></span>  
 <span data-ttu-id="e326a-106">Aşağıdaki örnekte gösterildiği bir `try` / `catch` yakalar blok bir <xref:System.Data.Linq.ChangeConflictException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="e326a-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="e326a-107">Varlık ve üye bilgilerini her çakışma için konsol penceresinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e326a-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e326a-108">Eklemelisiniz `using System.Reflection` yönergesi (`Imports System.Reflection` Visual Basic'te) bilgi alma desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="e326a-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="e326a-109">Daha fazla bilgi için bkz. <xref:System.Reflection>.</span><span class="sxs-lookup"><span data-stu-id="e326a-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e326a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e326a-110">See Also</span></span>  
 [<span data-ttu-id="e326a-111">Sağlama ve veri değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="e326a-111">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 [<span data-ttu-id="e326a-112">Nasıl yapılır: değişiklik çakışmalarını yönetin</span><span class="sxs-lookup"><span data-stu-id="e326a-112">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
