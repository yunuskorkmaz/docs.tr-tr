---
title: 'Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: b6f9b0308bcbf53a89ae0690ed44db0a364aef0c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191703"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="ff549-102">Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="ff549-102">How to: Resolve Conflicts by Retaining Database Values</span></span>

<span data-ttu-id="ff549-103">Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> veritabanında bulunan değerleri bekletmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff549-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="ff549-104">Nesne modelindeki geçerli değerlerin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="ff549-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="ff549-105">Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ff549-105">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ff549-106">Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir.</span><span class="sxs-lookup"><span data-stu-id="ff549-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="ff549-107">Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="ff549-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff549-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="ff549-108">Example</span></span>  

 <span data-ttu-id="ff549-109">Bu senaryoda, <xref:System.Data.Linq.ChangeConflictException> kullanıcı1 değişiklikleri göndermeye çalıştığında bir özel durum oluşturulur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="ff549-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="ff549-110">Aşağıdaki tabloda durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ff549-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="ff549-111">Yönetici</span><span class="sxs-lookup"><span data-stu-id="ff549-111">Manager</span></span>|<span data-ttu-id="ff549-112">Yardımc</span><span class="sxs-lookup"><span data-stu-id="ff549-112">Assistant</span></span>|<span data-ttu-id="ff549-113">Bölüm</span><span class="sxs-lookup"><span data-stu-id="ff549-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="ff549-114">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="ff549-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="ff549-115">Alfrelar</span><span class="sxs-lookup"><span data-stu-id="ff549-115">Alfreds</span></span>|<span data-ttu-id="ff549-116">Maria</span><span class="sxs-lookup"><span data-stu-id="ff549-116">Maria</span></span>|<span data-ttu-id="ff549-117">Sales</span><span class="sxs-lookup"><span data-stu-id="ff549-117">Sales</span></span>|  
|<span data-ttu-id="ff549-118">Kullanıcı1 bu değişiklikleri göndermeye hazırlar.</span><span class="sxs-lookup"><span data-stu-id="ff549-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="ff549-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="ff549-119">Alfred</span></span>||<span data-ttu-id="ff549-120">Marketing</span><span class="sxs-lookup"><span data-stu-id="ff549-120">Marketing</span></span>|  
|<span data-ttu-id="ff549-121">Kullanıcı2 bu değişiklikleri zaten gönderdi.</span><span class="sxs-lookup"><span data-stu-id="ff549-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="ff549-122">Mary</span><span class="sxs-lookup"><span data-stu-id="ff549-122">Mary</span></span>|<span data-ttu-id="ff549-123">Hizmet</span><span class="sxs-lookup"><span data-stu-id="ff549-123">Service</span></span>|  
  
 <span data-ttu-id="ff549-124">Kullanıcı1, daha yeni veritabanı değerlerini nesne modelindeki geçerli değerlerin üzerine yazarak bu çakışmayı çözmeye karar verir.</span><span class="sxs-lookup"><span data-stu-id="ff549-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="ff549-125">Kullanıcı1 kullanarak çakışmayı çözdüğünde <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> , veritabanındaki sonuç tabloda aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="ff549-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="ff549-126">Yönetici</span><span class="sxs-lookup"><span data-stu-id="ff549-126">Manager</span></span>|<span data-ttu-id="ff549-127">Yardımc</span><span class="sxs-lookup"><span data-stu-id="ff549-127">Assistant</span></span>|<span data-ttu-id="ff549-128">Bölüm</span><span class="sxs-lookup"><span data-stu-id="ff549-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="ff549-129">Çakışma çözümünden sonra yeni durum.</span><span class="sxs-lookup"><span data-stu-id="ff549-129">New state after conflict resolution.</span></span>|<span data-ttu-id="ff549-130">Alfrelar</span><span class="sxs-lookup"><span data-stu-id="ff549-130">Alfreds</span></span><br /><br /> <span data-ttu-id="ff549-131">orijinale</span><span class="sxs-lookup"><span data-stu-id="ff549-131">(original)</span></span>|<span data-ttu-id="ff549-132">Mary</span><span class="sxs-lookup"><span data-stu-id="ff549-132">Mary</span></span><br /><br /> <span data-ttu-id="ff549-133">(kullanıcı2 'ten)</span><span class="sxs-lookup"><span data-stu-id="ff549-133">(from User2)</span></span>|<span data-ttu-id="ff549-134">Hizmet</span><span class="sxs-lookup"><span data-stu-id="ff549-134">Service</span></span><br /><br /> <span data-ttu-id="ff549-135">(kullanıcı2 'ten)</span><span class="sxs-lookup"><span data-stu-id="ff549-135">(from User2)</span></span>|  
  
 <span data-ttu-id="ff549-136">Aşağıdaki örnek kod, veritabanı değerleriyle nesne modelindeki geçerli değerlerin üzerine yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff549-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="ff549-137">(Bireysel üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.)</span><span class="sxs-lookup"><span data-stu-id="ff549-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ff549-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff549-138">See also</span></span>

- [<span data-ttu-id="ff549-139">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="ff549-139">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
