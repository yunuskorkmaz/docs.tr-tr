---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: veritabanı değerleriyle birleştirerek çakışmaları çözme'
title: 'Nasıl yapılır: Veritabanı Değerleri ile Birleştirerek Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: 83cae4c98fdd2e51065c66d36ef04202bdc86c9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99767771"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a><span data-ttu-id="c6716-103">Nasıl yapılır: Veritabanı Değerleri ile Birleştirerek Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="c6716-103">How to: Resolve Conflicts by Merging with Database Values</span></span>

<span data-ttu-id="c6716-104">Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, <xref:System.Data.Linq.RefreshMode.KeepChanges> veritabanı değerlerini geçerli istemci üye değerleriyle birleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c6716-104">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepChanges> to merge database values with the current client member values.</span></span> <span data-ttu-id="c6716-105">Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c6716-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6716-106">Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir.</span><span class="sxs-lookup"><span data-stu-id="c6716-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="c6716-107">Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c6716-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6716-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="c6716-108">Example</span></span>  

 <span data-ttu-id="c6716-109">Bu senaryoda, <xref:System.Data.Linq.ChangeConflictException> kullanıcı1 değişiklikleri göndermeye çalıştığında bir özel durum oluşturulur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="c6716-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="c6716-110">Aşağıdaki tabloda durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c6716-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="c6716-111">Yönetici</span><span class="sxs-lookup"><span data-stu-id="c6716-111">Manager</span></span>|<span data-ttu-id="c6716-112">Yardımc</span><span class="sxs-lookup"><span data-stu-id="c6716-112">Assistant</span></span>|<span data-ttu-id="c6716-113">Bölüm</span><span class="sxs-lookup"><span data-stu-id="c6716-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="c6716-114">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="c6716-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="c6716-115">Alfrelar</span><span class="sxs-lookup"><span data-stu-id="c6716-115">Alfreds</span></span>|<span data-ttu-id="c6716-116">Maria</span><span class="sxs-lookup"><span data-stu-id="c6716-116">Maria</span></span>|<span data-ttu-id="c6716-117">Sales</span><span class="sxs-lookup"><span data-stu-id="c6716-117">Sales</span></span>|  
|<span data-ttu-id="c6716-118">Kullanıcı1 bu değişiklikleri göndermeye hazırlar.</span><span class="sxs-lookup"><span data-stu-id="c6716-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="c6716-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="c6716-119">Alfred</span></span>||<span data-ttu-id="c6716-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="c6716-120">Marketing</span></span>|  
|<span data-ttu-id="c6716-121">Kullanıcı2 bu değişiklikleri zaten gönderdi.</span><span class="sxs-lookup"><span data-stu-id="c6716-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="c6716-122">Mary</span><span class="sxs-lookup"><span data-stu-id="c6716-122">Mary</span></span>|<span data-ttu-id="c6716-123">Hizmet</span><span class="sxs-lookup"><span data-stu-id="c6716-123">Service</span></span>|  
  
 <span data-ttu-id="c6716-124">Kullanıcı1, veritabanı değerlerini geçerli istemci üyesi değerleriyle birleştirerek bu çakışmayı çözmeye karar verir.</span><span class="sxs-lookup"><span data-stu-id="c6716-124">User1 decides to resolve this conflict by merging database values with the current client member values.</span></span> <span data-ttu-id="c6716-125">Sonuç veritabanı değerlerinin üzerine yazılır ve yalnızca geçerli değişiklik kümesi de o değeri de değiştirmiş olur.</span><span class="sxs-lookup"><span data-stu-id="c6716-125">The result will be that database values are overwritten only when the current changeset has also modified that value.</span></span>  
  
 <span data-ttu-id="c6716-126">Kullanıcı1 kullanarak çakışmayı çözdüğünde <xref:System.Data.Linq.RefreshMode.KeepChanges> , veritabanındaki sonuç aşağıdaki tabloda olur:</span><span class="sxs-lookup"><span data-stu-id="c6716-126">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepChanges>, the result in the database is as in the following table:</span></span>  
  
||<span data-ttu-id="c6716-127">Yönetici</span><span class="sxs-lookup"><span data-stu-id="c6716-127">Manager</span></span>|<span data-ttu-id="c6716-128">Yardımc</span><span class="sxs-lookup"><span data-stu-id="c6716-128">Assistant</span></span>|<span data-ttu-id="c6716-129">Bölüm</span><span class="sxs-lookup"><span data-stu-id="c6716-129">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="c6716-130">Çakışma çözümünden sonra yeni durum.</span><span class="sxs-lookup"><span data-stu-id="c6716-130">New state after conflict resolution.</span></span>|<span data-ttu-id="c6716-131">Alfred</span><span class="sxs-lookup"><span data-stu-id="c6716-131">Alfred</span></span><br /><br /> <span data-ttu-id="c6716-132">(Kullanıcı1 'ten)</span><span class="sxs-lookup"><span data-stu-id="c6716-132">(from User1)</span></span>|<span data-ttu-id="c6716-133">Mary</span><span class="sxs-lookup"><span data-stu-id="c6716-133">Mary</span></span><br /><br /> <span data-ttu-id="c6716-134">(kullanıcı2 'ten)</span><span class="sxs-lookup"><span data-stu-id="c6716-134">(from User2)</span></span>|<span data-ttu-id="c6716-135">Marketing</span><span class="sxs-lookup"><span data-stu-id="c6716-135">Marketing</span></span><br /><br /> <span data-ttu-id="c6716-136">(Kullanıcı1 'ten)</span><span class="sxs-lookup"><span data-stu-id="c6716-136">(from User1)</span></span>|  
  
 <span data-ttu-id="c6716-137">Aşağıdaki örnekte, veritabanı değerlerinin geçerli istemci üye değerleriyle nasıl birleştiriyapılacağı gösterilmektedir (istemci bu değeri de değiştirmediği durumlar dışında).</span><span class="sxs-lookup"><span data-stu-id="c6716-137">The following example shows how to merge database values with the current client member values (unless the client has also changed that value).</span></span> <span data-ttu-id="c6716-138">Tek tek üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="c6716-138">No inspection or custom handling of individual member conflicts occurs.</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c6716-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6716-139">See also</span></span>

- [<span data-ttu-id="c6716-140">Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="c6716-140">How to: Resolve Conflicts by Overwriting Database Values</span></span>](how-to-resolve-conflicts-by-overwriting-database-values.md)
- [<span data-ttu-id="c6716-141">Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="c6716-141">How to: Resolve Conflicts by Retaining Database Values</span></span>](how-to-resolve-conflicts-by-retaining-database-values.md)
- [<span data-ttu-id="c6716-142">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="c6716-142">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
