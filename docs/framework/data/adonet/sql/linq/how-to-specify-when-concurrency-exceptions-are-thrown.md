---
title: "Nasıl yapılır: zaman eşzamanlılık özel durumlar belirtin"
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
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8af833574544410977b9f881f9b2db4e6d88aa73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a><span data-ttu-id="65770-102">Nasıl yapılır: zaman eşzamanlılık özel durumlar belirtin</span><span class="sxs-lookup"><span data-stu-id="65770-102">How to: Specify When Concurrency Exceptions are Thrown</span></span>
<span data-ttu-id="65770-103">İçinde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], <xref:System.Data.Linq.ChangeConflictException> nesneleri iyimser eşzamanlılık çakışmaları nedeniyle güncelleştirdiğinizde değil, özel durum.</span><span class="sxs-lookup"><span data-stu-id="65770-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when objects do not update because of optimistic concurrency conflicts.</span></span> <span data-ttu-id="65770-104">Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="65770-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
 <span data-ttu-id="65770-105">Değişiklikler veritabanına göndermeden önce eşzamanlılık özel durum olduğunda belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="65770-105">Before you submit your changes to the database, you can specify when concurrency exceptions should be thrown:</span></span>  
  
-   <span data-ttu-id="65770-106">İlk hata özel durum (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span><span class="sxs-lookup"><span data-stu-id="65770-106">Throw the exception at the first failure (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).</span></span>  
  
-   <span data-ttu-id="65770-107">Tüm güncelleştirme çalıştığında son, tüm hataları biriktirmesi ve özel durum birikmiş hataları rapor (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span><span class="sxs-lookup"><span data-stu-id="65770-107">Finish all update tries, accumulate all failures, and report the accumulated failures in the exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).</span></span>  
  
 <span data-ttu-id="65770-108">Oluştuğunda, <xref:System.Data.Linq.ChangeConflictException> özel durum erişim sağlayan bir <xref:System.Data.Linq.ChangeConflictCollection> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="65770-108">When thrown, the <xref:System.Data.Linq.ChangeConflictException> exception provides access to a <xref:System.Data.Linq.ChangeConflictCollection> collection.</span></span> <span data-ttu-id="65770-109">Bu koleksiyon (bir tek başarısız güncelleştirme try eşlenen) her çakışma dahil olmak üzere ayrıntılarını sağlar <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="65770-109">This collection provides details for each conflict (mapped to a single failed update try), including access to the <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A> collection.</span></span> <span data-ttu-id="65770-110">Tek bir üye olarak tutarlılık denetimi başarısız güncelleştirme her üye çakışma eşler.</span><span class="sxs-lookup"><span data-stu-id="65770-110">Each member conflict maps to a single member in the update that failed the concurrency check.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65770-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="65770-111">Example</span></span>  
 <span data-ttu-id="65770-112">Aşağıdaki kod iki değer örnekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="65770-112">The following code shows examples of both values.</span></span>  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="65770-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65770-113">See Also</span></span>  
 [<span data-ttu-id="65770-114">Nasıl yapılır: değişiklik çakışmalarını yönetin</span><span class="sxs-lookup"><span data-stu-id="65770-114">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [<span data-ttu-id="65770-115">Sağlama ve veri değişiklikleri gönderme</span><span class="sxs-lookup"><span data-stu-id="65770-115">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
