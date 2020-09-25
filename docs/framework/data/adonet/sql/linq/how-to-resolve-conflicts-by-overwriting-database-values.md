---
title: 'Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 1dc112350451bde28d27c63961733b96f6fc84be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191716"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="95755-102">Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="95755-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>

<span data-ttu-id="95755-103">Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> veritabanı değerlerinin üzerine yazmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95755-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="95755-104">Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="95755-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95755-105">Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir.</span><span class="sxs-lookup"><span data-stu-id="95755-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="95755-106">Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="95755-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95755-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="95755-107">Example</span></span>  

 <span data-ttu-id="95755-108">Bu senaryoda, <xref:System.Data.Linq.ChangeConflictException> kullanıcı1 değişiklikleri göndermeye çalıştığında bir özel durum oluşur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="95755-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="95755-109">Aşağıdaki tabloda durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="95755-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="95755-110">Yönetici</span><span class="sxs-lookup"><span data-stu-id="95755-110">Manager</span></span>|<span data-ttu-id="95755-111">Yardımc</span><span class="sxs-lookup"><span data-stu-id="95755-111">Assistant</span></span>|<span data-ttu-id="95755-112">Bölüm</span><span class="sxs-lookup"><span data-stu-id="95755-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="95755-113">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="95755-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="95755-114">Alfrelar</span><span class="sxs-lookup"><span data-stu-id="95755-114">Alfreds</span></span>|<span data-ttu-id="95755-115">Maria</span><span class="sxs-lookup"><span data-stu-id="95755-115">Maria</span></span>|<span data-ttu-id="95755-116">Sales</span><span class="sxs-lookup"><span data-stu-id="95755-116">Sales</span></span>|  
|<span data-ttu-id="95755-117">Kullanıcı1 bu değişiklikleri göndermeye hazırlar.</span><span class="sxs-lookup"><span data-stu-id="95755-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="95755-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="95755-118">Alfred</span></span>||<span data-ttu-id="95755-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="95755-119">Marketing</span></span>|  
|<span data-ttu-id="95755-120">Kullanıcı2 bu değişiklikleri zaten gönderdi.</span><span class="sxs-lookup"><span data-stu-id="95755-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="95755-121">Mary</span><span class="sxs-lookup"><span data-stu-id="95755-121">Mary</span></span>|<span data-ttu-id="95755-122">Hizmet</span><span class="sxs-lookup"><span data-stu-id="95755-122">Service</span></span>|  
  
 <span data-ttu-id="95755-123">Kullanıcı1, geçerli istemci üyesi değerleri ile veritabanı değerlerinin üzerine yazarak bu çakışmayı çözmeye karar verir.</span><span class="sxs-lookup"><span data-stu-id="95755-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="95755-124">Kullanıcı1 kullanarak çakışmayı çözdüğünde <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> , veritabanındaki sonuç aşağıdaki tabloda olur:</span><span class="sxs-lookup"><span data-stu-id="95755-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="95755-125">Yönetici</span><span class="sxs-lookup"><span data-stu-id="95755-125">Manager</span></span>|<span data-ttu-id="95755-126">Yardımc</span><span class="sxs-lookup"><span data-stu-id="95755-126">Assistant</span></span>|<span data-ttu-id="95755-127">Bölüm</span><span class="sxs-lookup"><span data-stu-id="95755-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="95755-128">Çakışma çözümünden sonra yeni durum.</span><span class="sxs-lookup"><span data-stu-id="95755-128">New state after conflict resolution.</span></span>|<span data-ttu-id="95755-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="95755-129">Alfred</span></span><br /><br /> <span data-ttu-id="95755-130">(Kullanıcı1 'ten)</span><span class="sxs-lookup"><span data-stu-id="95755-130">(from User1)</span></span>|<span data-ttu-id="95755-131">Maria</span><span class="sxs-lookup"><span data-stu-id="95755-131">Maria</span></span><br /><br /> <span data-ttu-id="95755-132">orijinale</span><span class="sxs-lookup"><span data-stu-id="95755-132">(original)</span></span>|<span data-ttu-id="95755-133">Marketing</span><span class="sxs-lookup"><span data-stu-id="95755-133">Marketing</span></span><br /><br /> <span data-ttu-id="95755-134">(Kullanıcı1 'ten)</span><span class="sxs-lookup"><span data-stu-id="95755-134">(from User1)</span></span>|  
  
 <span data-ttu-id="95755-135">Aşağıdaki örnek kod, geçerli istemci üyesi değerleri ile veritabanı değerlerinin üzerine yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="95755-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="95755-136">(Bireysel üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.)</span><span class="sxs-lookup"><span data-stu-id="95755-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="95755-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95755-137">See also</span></span>

- [<span data-ttu-id="95755-138">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="95755-138">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
