---
description: 'Aşağıdakiler hakkında daha fazla bilgi edinin: nasıl yapılır: eşzamanlılık özel durumlarının ne zaman oluşturulacağını belirtme'
title: 'Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
ms.openlocfilehash: d445cabfd2498f3599d874c2b7983a86c2c36c7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785880"
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="32f0c-103">Nasıl yapılır: Eşzamanlılık Özel Durumları Oluştuğunda Belirtme</span><span class="sxs-lookup"><span data-stu-id="32f0c-103">How to: Specify When Concurrency Exceptions are Thrown</span></span>

<span data-ttu-id="32f0c-104">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , <xref:System.Data.Linq.ChangeConflictException> iyimser eşzamanlılık çakışmaları nedeniyle nesneler güncelleştirmediği zaman bir özel durum oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="32f0c-104">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="32f0c-105">Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="32f0c-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="32f0c-106">Değişikliklerinizi veritabanına göndermeden önce, eşzamanlılık özel durumlarının ne zaman oluşturulması gerektiğini belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="32f0c-106">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
- <span data-ttu-id="32f0c-107">İlk hatada () özel durumu oluşturur <xref:System.Data.Linq.ConflictMode.FailOnFirstConflict> .</span><span class="sxs-lookup"><span data-stu-id="32f0c-107">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
- <span data-ttu-id="32f0c-108">Tüm güncelleştirme denemelerinden sonuna kadar tüm sorunları biriktir ve özel durum () içinde birikmiş sorunları bildirin <xref:System.Data.Linq.ConflictMode.ContinueOnConflict> .</span><span class="sxs-lookup"><span data-stu-id="32f0c-108">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="32f0c-109">Oluştuğunda, <xref:System.Data.Linq.ChangeConflictException> özel durum bir koleksiyona erişim sağlar <xref:System.Data.Linq.ChangeConflictCollection> .</span><span class="sxs-lookup"><span data-stu-id="32f0c-109">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="32f0c-110">Bu koleksiyon, koleksiyona erişim de dahil olmak üzere her bir çakışmaya ilişkin ayrıntıları (tek bir başarısız güncelleştirme denemeye eşlenir) sağlar <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> .</span><span class="sxs-lookup"><span data-stu-id="32f0c-110">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="32f0c-111">Her üye çakışması, güncelleştirmede eşzamanlılık denetimini başarısız olan tek bir üyeye eşlenir.</span><span class="sxs-lookup"><span data-stu-id="32f0c-111">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="32f0c-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="32f0c-112">Example</span></span>  

 <span data-ttu-id="32f0c-113">Aşağıdaki kod her iki değerin örneklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="32f0c-113">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="32f0c-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32f0c-114">See also</span></span>

- [<span data-ttu-id="32f0c-115">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="32f0c-115">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
- [<span data-ttu-id="32f0c-116">Veri Değişiklikleri Yapma ve Gönderme</span><span class="sxs-lookup"><span data-stu-id="32f0c-116">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
