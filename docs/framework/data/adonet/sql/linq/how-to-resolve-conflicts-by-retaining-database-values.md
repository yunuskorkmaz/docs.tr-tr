---
description: 'Daha fazla bilgi edinin: nasıl yapılır: veritabanı değerlerini koruyarak çakışmaları çözme'
title: 'Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: ef47370768ce474ccb6d941bcec0e66807290599
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723497"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="10d5e-103">Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="10d5e-103">How to: Resolve Conflicts by Retaining Database Values</span></span>

<span data-ttu-id="10d5e-104">Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> veritabanında bulunan değerleri bekletmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10d5e-104">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="10d5e-105">Nesne modelindeki geçerli değerlerin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="10d5e-105">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="10d5e-106">Daha fazla bilgi için bkz. [Iyimser eşzamanlılık: genel bakış](optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="10d5e-106">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10d5e-107">Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir.</span><span class="sxs-lookup"><span data-stu-id="10d5e-107">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="10d5e-108">Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="10d5e-108">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10d5e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="10d5e-109">Example</span></span>  

 <span data-ttu-id="10d5e-110">Bu senaryoda, <xref:System.Data.Linq.ChangeConflictException> kullanıcı1 değişiklikleri göndermeye çalıştığında bir özel durum oluşturulur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="10d5e-110">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="10d5e-111">Aşağıdaki tabloda durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="10d5e-111">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="10d5e-112">Yönetici</span><span class="sxs-lookup"><span data-stu-id="10d5e-112">Manager</span></span>|<span data-ttu-id="10d5e-113">Yardımc</span><span class="sxs-lookup"><span data-stu-id="10d5e-113">Assistant</span></span>|<span data-ttu-id="10d5e-114">Bölüm</span><span class="sxs-lookup"><span data-stu-id="10d5e-114">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="10d5e-115">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="10d5e-115">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="10d5e-116">Alfrelar</span><span class="sxs-lookup"><span data-stu-id="10d5e-116">Alfreds</span></span>|<span data-ttu-id="10d5e-117">Maria</span><span class="sxs-lookup"><span data-stu-id="10d5e-117">Maria</span></span>|<span data-ttu-id="10d5e-118">Sales</span><span class="sxs-lookup"><span data-stu-id="10d5e-118">Sales</span></span>|  
|<span data-ttu-id="10d5e-119">Kullanıcı1 bu değişiklikleri göndermeye hazırlar.</span><span class="sxs-lookup"><span data-stu-id="10d5e-119">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="10d5e-120">Alfred</span><span class="sxs-lookup"><span data-stu-id="10d5e-120">Alfred</span></span>||<span data-ttu-id="10d5e-121">Marketing</span><span class="sxs-lookup"><span data-stu-id="10d5e-121">Marketing</span></span>|  
|<span data-ttu-id="10d5e-122">Kullanıcı2 bu değişiklikleri zaten gönderdi.</span><span class="sxs-lookup"><span data-stu-id="10d5e-122">User2 has already submitted these changes.</span></span>||<span data-ttu-id="10d5e-123">Mary</span><span class="sxs-lookup"><span data-stu-id="10d5e-123">Mary</span></span>|<span data-ttu-id="10d5e-124">Hizmet</span><span class="sxs-lookup"><span data-stu-id="10d5e-124">Service</span></span>|  
  
 <span data-ttu-id="10d5e-125">Kullanıcı1, daha yeni veritabanı değerlerini nesne modelindeki geçerli değerlerin üzerine yazarak bu çakışmayı çözmeye karar verir.</span><span class="sxs-lookup"><span data-stu-id="10d5e-125">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="10d5e-126">Kullanıcı1 kullanarak çakışmayı çözdüğünde <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> , veritabanındaki sonuç tabloda aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="10d5e-126">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="10d5e-127">Yönetici</span><span class="sxs-lookup"><span data-stu-id="10d5e-127">Manager</span></span>|<span data-ttu-id="10d5e-128">Yardımc</span><span class="sxs-lookup"><span data-stu-id="10d5e-128">Assistant</span></span>|<span data-ttu-id="10d5e-129">Bölüm</span><span class="sxs-lookup"><span data-stu-id="10d5e-129">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="10d5e-130">Çakışma çözümünden sonra yeni durum.</span><span class="sxs-lookup"><span data-stu-id="10d5e-130">New state after conflict resolution.</span></span>|<span data-ttu-id="10d5e-131">Alfrelar</span><span class="sxs-lookup"><span data-stu-id="10d5e-131">Alfreds</span></span><br /><br /> <span data-ttu-id="10d5e-132">orijinale</span><span class="sxs-lookup"><span data-stu-id="10d5e-132">(original)</span></span>|<span data-ttu-id="10d5e-133">Mary</span><span class="sxs-lookup"><span data-stu-id="10d5e-133">Mary</span></span><br /><br /> <span data-ttu-id="10d5e-134">(kullanıcı2 'ten)</span><span class="sxs-lookup"><span data-stu-id="10d5e-134">(from User2)</span></span>|<span data-ttu-id="10d5e-135">Hizmet</span><span class="sxs-lookup"><span data-stu-id="10d5e-135">Service</span></span><br /><br /> <span data-ttu-id="10d5e-136">(kullanıcı2 'ten)</span><span class="sxs-lookup"><span data-stu-id="10d5e-136">(from User2)</span></span>|  
  
 <span data-ttu-id="10d5e-137">Aşağıdaki örnek kod, veritabanı değerleriyle nesne modelindeki geçerli değerlerin üzerine yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="10d5e-137">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="10d5e-138">(Bireysel üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.)</span><span class="sxs-lookup"><span data-stu-id="10d5e-138">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="10d5e-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10d5e-139">See also</span></span>

- [<span data-ttu-id="10d5e-140">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="10d5e-140">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
