---
title: 'Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 1da2abcbbb3b87d44aa99016112d9ef2674912c6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781724"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="2c1dd-102">Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="2c1dd-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="2c1dd-103">Değişikliklerinizi yeniden göndermeye çalışmadan önce beklenen ve gerçek veritabanı değerleri arasındaki farkları mutabık kılmak için, veritabanı değerlerinin üzerine yazmak <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="2c1dd-104">Daha fazla bilgi için bkz [. iyimser eşzamanlılık: Genel](optimistic-concurrency-overview.md)bakış.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c1dd-105">Her durumda, istemcideki kayıt, veritabanındaki güncelleştirilmiş verileri alarak yenilenir.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="2c1dd-106">Bu eylem, sonraki güncelleştirme denemasının aynı eşzamanlılık denetimlerinde başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c1dd-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c1dd-107">Example</span></span>  
 <span data-ttu-id="2c1dd-108">Bu senaryoda, Kullanıcı1 değişiklikleri <xref:System.Data.Linq.ChangeConflictException> göndermeye çalıştığında bir özel durum oluşur, çünkü kullanıcı2 bu arada yardımcı ve departman sütunlarını değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="2c1dd-109">Aşağıdaki tabloda durum gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="2c1dd-110">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="2c1dd-110">Manager</span></span>|<span data-ttu-id="2c1dd-111">Yardımc</span><span class="sxs-lookup"><span data-stu-id="2c1dd-111">Assistant</span></span>|<span data-ttu-id="2c1dd-112">Bölüm</span><span class="sxs-lookup"><span data-stu-id="2c1dd-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="2c1dd-113">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında özgün veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="2c1dd-114">Alfrelar</span><span class="sxs-lookup"><span data-stu-id="2c1dd-114">Alfreds</span></span>|<span data-ttu-id="2c1dd-115">Maria</span><span class="sxs-lookup"><span data-stu-id="2c1dd-115">Maria</span></span>|<span data-ttu-id="2c1dd-116">Satış</span><span class="sxs-lookup"><span data-stu-id="2c1dd-116">Sales</span></span>|  
|<span data-ttu-id="2c1dd-117">Kullanıcı1 bu değişiklikleri göndermeye hazırlar.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="2c1dd-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="2c1dd-118">Alfred</span></span>||<span data-ttu-id="2c1dd-119">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="2c1dd-119">Marketing</span></span>|  
|<span data-ttu-id="2c1dd-120">Kullanıcı2 bu değişiklikleri zaten gönderdi.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="2c1dd-121">Mary</span><span class="sxs-lookup"><span data-stu-id="2c1dd-121">Mary</span></span>|<span data-ttu-id="2c1dd-122">Hizmet</span><span class="sxs-lookup"><span data-stu-id="2c1dd-122">Service</span></span>|  
  
 <span data-ttu-id="2c1dd-123">Kullanıcı1, geçerli istemci üyesi değerleri ile veritabanı değerlerinin üzerine yazarak bu çakışmayı çözmeye karar verir.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="2c1dd-124">Kullanıcı1 kullanarak <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>çakışmayı çözdüğünde, veritabanındaki sonuç aşağıdaki tabloda olur:</span><span class="sxs-lookup"><span data-stu-id="2c1dd-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="2c1dd-125">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="2c1dd-125">Manager</span></span>|<span data-ttu-id="2c1dd-126">Yardımc</span><span class="sxs-lookup"><span data-stu-id="2c1dd-126">Assistant</span></span>|<span data-ttu-id="2c1dd-127">Bölüm</span><span class="sxs-lookup"><span data-stu-id="2c1dd-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="2c1dd-128">Çakışma çözümünden sonra yeni durum.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-128">New state after conflict resolution.</span></span>|<span data-ttu-id="2c1dd-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="2c1dd-129">Alfred</span></span><br /><br /> <span data-ttu-id="2c1dd-130">(Kullanıcı1 'ten)</span><span class="sxs-lookup"><span data-stu-id="2c1dd-130">(from User1)</span></span>|<span data-ttu-id="2c1dd-131">Maria</span><span class="sxs-lookup"><span data-stu-id="2c1dd-131">Maria</span></span><br /><br /> <span data-ttu-id="2c1dd-132">orijinale</span><span class="sxs-lookup"><span data-stu-id="2c1dd-132">(original)</span></span>|<span data-ttu-id="2c1dd-133">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="2c1dd-133">Marketing</span></span><br /><br /> <span data-ttu-id="2c1dd-134">(Kullanıcı1 'ten)</span><span class="sxs-lookup"><span data-stu-id="2c1dd-134">(from User1)</span></span>|  
  
 <span data-ttu-id="2c1dd-135">Aşağıdaki örnek kod, geçerli istemci üyesi değerleri ile veritabanı değerlerinin üzerine yazmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="2c1dd-136">(Bireysel üye çakışmalarının denetimi veya özel işlenmesi gerçekleşmez.)</span><span class="sxs-lookup"><span data-stu-id="2c1dd-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2c1dd-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c1dd-137">See also</span></span>

- [<span data-ttu-id="2c1dd-138">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="2c1dd-138">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
