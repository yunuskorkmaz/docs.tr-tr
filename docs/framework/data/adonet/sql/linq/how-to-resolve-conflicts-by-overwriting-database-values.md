---
description: 'Daha fazla bilgi edinin: nasıl yapılır: veritabanı değerlerinin üzerine yazarak çakışmaları çözme'
title: 'Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 4eaa66b4bb49706bb1ca6449d24c688a89f2750b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723510"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="1e79d-103">Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="1e79d-103">How to: Resolve Conflicts by Overwriting Database Values</span></span>

<span data-ttu-id="1e79d-104">Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> veritabanı değerlerinin üzerine yazmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-104">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="1e79d-105">Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1e79d-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e79d-106">Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="1e79d-107">Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="1e79d-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e79d-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e79d-108">Example</span></span>  

 <span data-ttu-id="1e79d-109">Bu senaryoda, <xref:System.Data.Linq.ChangeConflictException> kullanıcı1 değişiklikleri göndermeye çalıştığında bir özel durum oluşur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="1e79d-109">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="1e79d-110">Aşağıdaki tabloda durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="1e79d-111">Yönetici</span><span class="sxs-lookup"><span data-stu-id="1e79d-111">Manager</span></span>|<span data-ttu-id="1e79d-112">Yardımc</span><span class="sxs-lookup"><span data-stu-id="1e79d-112">Assistant</span></span>|<span data-ttu-id="1e79d-113">Bölüm</span><span class="sxs-lookup"><span data-stu-id="1e79d-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="1e79d-114">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="1e79d-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="1e79d-115">Alfrelar</span><span class="sxs-lookup"><span data-stu-id="1e79d-115">Alfreds</span></span>|<span data-ttu-id="1e79d-116">Maria</span><span class="sxs-lookup"><span data-stu-id="1e79d-116">Maria</span></span>|<span data-ttu-id="1e79d-117">Sales</span><span class="sxs-lookup"><span data-stu-id="1e79d-117">Sales</span></span>|  
|<span data-ttu-id="1e79d-118">Kullanıcı1 bu değişiklikleri göndermeye hazırlar.</span><span class="sxs-lookup"><span data-stu-id="1e79d-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="1e79d-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="1e79d-119">Alfred</span></span>||<span data-ttu-id="1e79d-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="1e79d-120">Marketing</span></span>|  
|<span data-ttu-id="1e79d-121">Kullanıcı2 bu değişiklikleri zaten gönderdi.</span><span class="sxs-lookup"><span data-stu-id="1e79d-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="1e79d-122">Mary</span><span class="sxs-lookup"><span data-stu-id="1e79d-122">Mary</span></span>|<span data-ttu-id="1e79d-123">Hizmet</span><span class="sxs-lookup"><span data-stu-id="1e79d-123">Service</span></span>|  
  
 <span data-ttu-id="1e79d-124">Kullanıcı1, geçerli istemci üyesi değerleri ile veritabanı değerlerinin üzerine yazarak bu çakışmayı çözmeye karar verir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-124">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="1e79d-125">Kullanıcı1 kullanarak çakışmayı çözdüğünde <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> , veritabanındaki sonuç aşağıdaki tabloda olur:</span><span class="sxs-lookup"><span data-stu-id="1e79d-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="1e79d-126">Yönetici</span><span class="sxs-lookup"><span data-stu-id="1e79d-126">Manager</span></span>|<span data-ttu-id="1e79d-127">Yardımc</span><span class="sxs-lookup"><span data-stu-id="1e79d-127">Assistant</span></span>|<span data-ttu-id="1e79d-128">Bölüm</span><span class="sxs-lookup"><span data-stu-id="1e79d-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="1e79d-129">Çakışma çözümünden sonra yeni durum.</span><span class="sxs-lookup"><span data-stu-id="1e79d-129">New state after conflict resolution.</span></span>|<span data-ttu-id="1e79d-130">Alfred</span><span class="sxs-lookup"><span data-stu-id="1e79d-130">Alfred</span></span><br /><br /> <span data-ttu-id="1e79d-131">(Kullanıcı1 'ten)</span><span class="sxs-lookup"><span data-stu-id="1e79d-131">(from User1)</span></span>|<span data-ttu-id="1e79d-132">Maria</span><span class="sxs-lookup"><span data-stu-id="1e79d-132">Maria</span></span><br /><br /> <span data-ttu-id="1e79d-133">orijinale</span><span class="sxs-lookup"><span data-stu-id="1e79d-133">(original)</span></span>|<span data-ttu-id="1e79d-134">Marketing</span><span class="sxs-lookup"><span data-stu-id="1e79d-134">Marketing</span></span><br /><br /> <span data-ttu-id="1e79d-135">(Kullanıcı1 'ten)</span><span class="sxs-lookup"><span data-stu-id="1e79d-135">(from User1)</span></span>|  
  
 <span data-ttu-id="1e79d-136">Aşağıdaki örnek kod, geçerli istemci üyesi değerleri ile veritabanı değerlerinin üzerine yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e79d-136">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="1e79d-137">(Bireysel üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.)</span><span class="sxs-lookup"><span data-stu-id="1e79d-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1e79d-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e79d-138">See also</span></span>

- [<span data-ttu-id="1e79d-139">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="1e79d-139">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
