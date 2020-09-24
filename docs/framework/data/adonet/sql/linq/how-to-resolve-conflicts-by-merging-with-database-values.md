---
title: 'Nasıl yapılır: Veritabanı Değerleri ile Birleştirerek Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: fb77c4a23a4c4fa93dc55e63858ee41783c197ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166189"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a><span data-ttu-id="8b583-102">Nasıl yapılır: Veritabanı Değerleri ile Birleştirerek Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="8b583-102">How to: Resolve Conflicts by Merging with Database Values</span></span>

<span data-ttu-id="8b583-103">Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, <xref:System.Data.Linq.RefreshMode.KeepChanges> veritabanı değerlerini geçerli istemci üye değerleriyle birleştirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8b583-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepChanges> to merge database values with the current client member values.</span></span> <span data-ttu-id="8b583-104">Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8b583-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b583-105">Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir.</span><span class="sxs-lookup"><span data-stu-id="8b583-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="8b583-106">Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8b583-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b583-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="8b583-107">Example</span></span>  

 <span data-ttu-id="8b583-108">Bu senaryoda, <xref:System.Data.Linq.ChangeConflictException> kullanıcı1 değişiklikleri göndermeye çalıştığında bir özel durum oluşturulur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="8b583-108">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="8b583-109">Aşağıdaki tabloda durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8b583-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="8b583-110">Yönetici</span><span class="sxs-lookup"><span data-stu-id="8b583-110">Manager</span></span>|<span data-ttu-id="8b583-111">Yardımc</span><span class="sxs-lookup"><span data-stu-id="8b583-111">Assistant</span></span>|<span data-ttu-id="8b583-112">Bölüm</span><span class="sxs-lookup"><span data-stu-id="8b583-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="8b583-113">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="8b583-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="8b583-114">Alfrelar</span><span class="sxs-lookup"><span data-stu-id="8b583-114">Alfreds</span></span>|<span data-ttu-id="8b583-115">Maria</span><span class="sxs-lookup"><span data-stu-id="8b583-115">Maria</span></span>|<span data-ttu-id="8b583-116">Sales</span><span class="sxs-lookup"><span data-stu-id="8b583-116">Sales</span></span>|  
|<span data-ttu-id="8b583-117">Kullanıcı1 bu değişiklikleri göndermeye hazırlar.</span><span class="sxs-lookup"><span data-stu-id="8b583-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="8b583-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="8b583-118">Alfred</span></span>||<span data-ttu-id="8b583-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="8b583-119">Marketing</span></span>|  
|<span data-ttu-id="8b583-120">Kullanıcı2 bu değişiklikleri zaten gönderdi.</span><span class="sxs-lookup"><span data-stu-id="8b583-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="8b583-121">Mary</span><span class="sxs-lookup"><span data-stu-id="8b583-121">Mary</span></span>|<span data-ttu-id="8b583-122">Hizmet</span><span class="sxs-lookup"><span data-stu-id="8b583-122">Service</span></span>|  
  
 <span data-ttu-id="8b583-123">Kullanıcı1, veritabanı değerlerini geçerli istemci üyesi değerleriyle birleştirerek bu çakışmayı çözmeye karar verir.</span><span class="sxs-lookup"><span data-stu-id="8b583-123">User1 decides to resolve this conflict by merging database values with the current client member values.</span></span> <span data-ttu-id="8b583-124">Sonuç veritabanı değerlerinin üzerine yazılır ve yalnızca geçerli değişiklik kümesi de o değeri de değiştirmiş olur.</span><span class="sxs-lookup"><span data-stu-id="8b583-124">The result will be that database values are overwritten only when the current changeset has also modified that value.</span></span>  
  
 <span data-ttu-id="8b583-125">Kullanıcı1 kullanarak çakışmayı çözdüğünde <xref:System.Data.Linq.RefreshMode.KeepChanges> , veritabanındaki sonuç aşağıdaki tabloda olur:</span><span class="sxs-lookup"><span data-stu-id="8b583-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepChanges>, the result in the database is as in the following table:</span></span>  
  
||<span data-ttu-id="8b583-126">Yönetici</span><span class="sxs-lookup"><span data-stu-id="8b583-126">Manager</span></span>|<span data-ttu-id="8b583-127">Yardımc</span><span class="sxs-lookup"><span data-stu-id="8b583-127">Assistant</span></span>|<span data-ttu-id="8b583-128">Bölüm</span><span class="sxs-lookup"><span data-stu-id="8b583-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="8b583-129">Çakışma çözümünden sonra yeni durum.</span><span class="sxs-lookup"><span data-stu-id="8b583-129">New state after conflict resolution.</span></span>|<span data-ttu-id="8b583-130">Alfred</span><span class="sxs-lookup"><span data-stu-id="8b583-130">Alfred</span></span><br /><br /> <span data-ttu-id="8b583-131">(Kullanıcı1 'ten)</span><span class="sxs-lookup"><span data-stu-id="8b583-131">(from User1)</span></span>|<span data-ttu-id="8b583-132">Mary</span><span class="sxs-lookup"><span data-stu-id="8b583-132">Mary</span></span><br /><br /> <span data-ttu-id="8b583-133">(kullanıcı2 'ten)</span><span class="sxs-lookup"><span data-stu-id="8b583-133">(from User2)</span></span>|<span data-ttu-id="8b583-134">Marketing</span><span class="sxs-lookup"><span data-stu-id="8b583-134">Marketing</span></span><br /><br /> <span data-ttu-id="8b583-135">(Kullanıcı1 'ten)</span><span class="sxs-lookup"><span data-stu-id="8b583-135">(from User1)</span></span>|  
  
 <span data-ttu-id="8b583-136">Aşağıdaki örnekte, veritabanı değerlerinin geçerli istemci üye değerleriyle nasıl birleştiriyapılacağı gösterilmektedir (istemci bu değeri de değiştirmediği durumlar dışında).</span><span class="sxs-lookup"><span data-stu-id="8b583-136">The following example shows how to merge database values with the current client member values (unless the client has also changed that value).</span></span> <span data-ttu-id="8b583-137">Tek tek üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.</span><span class="sxs-lookup"><span data-stu-id="8b583-137">No inspection or custom handling of individual member conflicts occurs.</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="8b583-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b583-138">See also</span></span>

- [<span data-ttu-id="8b583-139">Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="8b583-139">How to: Resolve Conflicts by Overwriting Database Values</span></span>](how-to-resolve-conflicts-by-overwriting-database-values.md)
- [<span data-ttu-id="8b583-140">Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="8b583-140">How to: Resolve Conflicts by Retaining Database Values</span></span>](how-to-resolve-conflicts-by-retaining-database-values.md)
- [<span data-ttu-id="8b583-141">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="8b583-141">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
