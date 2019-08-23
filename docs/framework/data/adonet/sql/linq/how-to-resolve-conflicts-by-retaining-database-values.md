---
title: 'Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: 828f0a21ca1ea4155f31dfbc87b01dc8c4b81e40
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928732"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="40a4a-102">Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="40a4a-102">How to: Resolve Conflicts by Retaining Database Values</span></span>
<span data-ttu-id="40a4a-103">Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, veritabanında bulunan değerleri bekletmek için kullanabilirsiniz <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> .</span><span class="sxs-lookup"><span data-stu-id="40a4a-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="40a4a-104">Nesne modelindeki geçerli değerlerin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="40a4a-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="40a4a-105">Daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md)bakış.</span><span class="sxs-lookup"><span data-stu-id="40a4a-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40a4a-106">Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir.</span><span class="sxs-lookup"><span data-stu-id="40a4a-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="40a4a-107">Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="40a4a-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40a4a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="40a4a-108">Example</span></span>  
 <span data-ttu-id="40a4a-109">Bu senaryoda, Kullanıcı1 değişiklikleri <xref:System.Data.Linq.ChangeConflictException> göndermeye çalıştığında bir özel durum oluşturulur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="40a4a-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="40a4a-110">Aşağıdaki tabloda durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="40a4a-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="40a4a-111">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="40a4a-111">Manager</span></span>|<span data-ttu-id="40a4a-112">Yardımc</span><span class="sxs-lookup"><span data-stu-id="40a4a-112">Assistant</span></span>|<span data-ttu-id="40a4a-113">Bölüm</span><span class="sxs-lookup"><span data-stu-id="40a4a-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="40a4a-114">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="40a4a-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="40a4a-115">Alfrelar</span><span class="sxs-lookup"><span data-stu-id="40a4a-115">Alfreds</span></span>|<span data-ttu-id="40a4a-116">Maria</span><span class="sxs-lookup"><span data-stu-id="40a4a-116">Maria</span></span>|<span data-ttu-id="40a4a-117">Satış</span><span class="sxs-lookup"><span data-stu-id="40a4a-117">Sales</span></span>|  
|<span data-ttu-id="40a4a-118">Kullanıcı1 bu değişiklikleri göndermeye hazırlar.</span><span class="sxs-lookup"><span data-stu-id="40a4a-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="40a4a-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="40a4a-119">Alfred</span></span>||<span data-ttu-id="40a4a-120">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="40a4a-120">Marketing</span></span>|  
|<span data-ttu-id="40a4a-121">Kullanıcı2 bu değişiklikleri zaten gönderdi.</span><span class="sxs-lookup"><span data-stu-id="40a4a-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="40a4a-122">Mary</span><span class="sxs-lookup"><span data-stu-id="40a4a-122">Mary</span></span>|<span data-ttu-id="40a4a-123">Hizmet</span><span class="sxs-lookup"><span data-stu-id="40a4a-123">Service</span></span>|  
  
 <span data-ttu-id="40a4a-124">Kullanıcı1, daha yeni veritabanı değerlerini nesne modelindeki geçerli değerlerin üzerine yazarak bu çakışmayı çözmeye karar verir.</span><span class="sxs-lookup"><span data-stu-id="40a4a-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="40a4a-125">Kullanıcı1 kullanarak <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>çakışmayı çözdüğünde, veritabanındaki sonuç tabloda aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="40a4a-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="40a4a-126">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="40a4a-126">Manager</span></span>|<span data-ttu-id="40a4a-127">Yardımc</span><span class="sxs-lookup"><span data-stu-id="40a4a-127">Assistant</span></span>|<span data-ttu-id="40a4a-128">Bölüm</span><span class="sxs-lookup"><span data-stu-id="40a4a-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="40a4a-129">Çakışma çözümünden sonra yeni durum.</span><span class="sxs-lookup"><span data-stu-id="40a4a-129">New state after conflict resolution.</span></span>|<span data-ttu-id="40a4a-130">Alfrelar</span><span class="sxs-lookup"><span data-stu-id="40a4a-130">Alfreds</span></span><br /><br /> <span data-ttu-id="40a4a-131">orijinale</span><span class="sxs-lookup"><span data-stu-id="40a4a-131">(original)</span></span>|<span data-ttu-id="40a4a-132">Mary</span><span class="sxs-lookup"><span data-stu-id="40a4a-132">Mary</span></span><br /><br /> <span data-ttu-id="40a4a-133">(kullanıcı2 'ten)</span><span class="sxs-lookup"><span data-stu-id="40a4a-133">(from User2)</span></span>|<span data-ttu-id="40a4a-134">Hizmet</span><span class="sxs-lookup"><span data-stu-id="40a4a-134">Service</span></span><br /><br /> <span data-ttu-id="40a4a-135">(kullanıcı2 'ten)</span><span class="sxs-lookup"><span data-stu-id="40a4a-135">(from User2)</span></span>|  
  
 <span data-ttu-id="40a4a-136">Aşağıdaki örnek kod, veritabanı değerleriyle nesne modelindeki geçerli değerlerin üzerine yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="40a4a-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="40a4a-137">(Bireysel üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.)</span><span class="sxs-lookup"><span data-stu-id="40a4a-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="40a4a-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40a4a-138">See also</span></span>

- [<span data-ttu-id="40a4a-139">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="40a4a-139">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
