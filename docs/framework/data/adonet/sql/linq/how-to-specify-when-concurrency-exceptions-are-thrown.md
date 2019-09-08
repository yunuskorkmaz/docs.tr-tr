---
title: 'Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: c0f41d23264bbe5c9130cb5a0b03686331bc92b1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781611"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="5ec4f-102">Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme</span><span class="sxs-lookup"><span data-stu-id="5ec4f-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="5ec4f-103">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], iyimser <xref:System.Data.Linq.ChangeConflictException> eşzamanlılık çakışmaları nedeniyle nesneler güncelleştirmediği zaman bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5ec4f-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="5ec4f-104">Daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](optimistic-concurrency-overview.md)bakış.</span><span class="sxs-lookup"><span data-stu-id="5ec4f-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="5ec4f-105">Değişikliklerinizi veritabanına göndermeden önce, eşzamanlılık özel durumlarının ne zaman oluşturulması gerektiğini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5ec4f-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
- <span data-ttu-id="5ec4f-106">İlk hatada (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>) özel durumu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5ec4f-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
- <span data-ttu-id="5ec4f-107">Tüm güncelleştirme denemelerinden sonuna kadar tüm sorunları biriktir ve özel durum (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>) içinde birikmiş sorunları bildirin.</span><span class="sxs-lookup"><span data-stu-id="5ec4f-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="5ec4f-108">Oluştuğunda, <xref:System.Data.Linq.ChangeConflictException> özel durum bir <xref:System.Data.Linq.ChangeConflictCollection> koleksiyona erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ec4f-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="5ec4f-109">Bu koleksiyon, <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> koleksiyona erişim de dahil olmak üzere her bir çakışmaya ilişkin ayrıntıları (tek bir başarısız güncelleştirme denemeye eşlenir) sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ec4f-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="5ec4f-110">Her üye çakışması, güncelleştirmede eşzamanlılık denetimini başarısız olan tek bir üyeye eşlenir.</span><span class="sxs-lookup"><span data-stu-id="5ec4f-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ec4f-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="5ec4f-111">Example</span></span>  
 <span data-ttu-id="5ec4f-112">Aşağıdaki kod her iki değerin örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ec4f-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5ec4f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ec4f-113">See also</span></span>

- [<span data-ttu-id="5ec4f-114">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="5ec4f-114">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="5ec4f-115">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="5ec4f-115">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
