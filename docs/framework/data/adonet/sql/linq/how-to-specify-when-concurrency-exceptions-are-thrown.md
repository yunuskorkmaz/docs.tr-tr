---
title: 'Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: 9d71ca82c3fe1abd23a82d952d38c3ea23a7f1c0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197124"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="ee552-102">Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme</span><span class="sxs-lookup"><span data-stu-id="ee552-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>

<span data-ttu-id="ee552-103">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , <xref:System.Data.Linq.ChangeConflictException> iyimser eşzamanlılık çakışmaları nedeniyle nesneler güncelleştirmediği zaman bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ee552-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="ee552-104">Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ee552-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="ee552-105">Değişikliklerinizi veritabanına göndermeden önce, eşzamanlılık özel durumlarının ne zaman oluşturulması gerektiğini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ee552-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
- <span data-ttu-id="ee552-106">İlk hatada () özel durumu oluşturur <xref:System.Data.Linq.ConflictMode.FailOnFirstConflict> .</span><span class="sxs-lookup"><span data-stu-id="ee552-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
- <span data-ttu-id="ee552-107">Tüm güncelleştirme denemelerinden sonuna kadar tüm sorunları biriktir ve özel durum () içinde birikmiş sorunları bildirin <xref:System.Data.Linq.ConflictMode.ContinueOnConflict> .</span><span class="sxs-lookup"><span data-stu-id="ee552-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="ee552-108">Oluştuğunda, <xref:System.Data.Linq.ChangeConflictException> özel durum bir koleksiyona erişim sağlar <xref:System.Data.Linq.ChangeConflictCollection> .</span><span class="sxs-lookup"><span data-stu-id="ee552-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="ee552-109">Bu koleksiyon, koleksiyona erişim de dahil olmak üzere her bir çakışmaya ilişkin ayrıntıları (tek bir başarısız güncelleştirme denemeye eşlenir) sağlar <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> .</span><span class="sxs-lookup"><span data-stu-id="ee552-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="ee552-110">Her üye çakışması, güncelleştirmede eşzamanlılık denetimini başarısız olan tek bir üyeye eşlenir.</span><span class="sxs-lookup"><span data-stu-id="ee552-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee552-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee552-111">Example</span></span>  

 <span data-ttu-id="ee552-112">Aşağıdaki kod her iki değerin örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ee552-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ee552-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee552-113">See also</span></span>

- [<span data-ttu-id="ee552-114">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="ee552-114">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="ee552-115">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="ee552-115">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
