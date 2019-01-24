---
title: 'Nasıl yapılır: Veritabanı değerlerinin üzerine yazarak çakışmaları'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 38129996949bcfbd938038743897d1db5910fdfe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653914"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="f3227-102">Nasıl yapılır: Veritabanı değerlerinin üzerine yazarak çakışmaları</span><span class="sxs-lookup"><span data-stu-id="f3227-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="f3227-103">Değişikliklerinizi yeniden denemeden önce veritabanı beklenen ve gerçek değerler arasındaki farkları bağdaştırma için kullanabileceğiniz <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> veritabanı değerlerinin üzerine yazmak için.</span><span class="sxs-lookup"><span data-stu-id="f3227-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="f3227-104">Daha fazla bilgi için [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f3227-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3227-105">Her durumda, istemci kaydını veritabanından güncelleştirilmiş verileri alarak önce yenilenir.</span><span class="sxs-lookup"><span data-stu-id="f3227-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="f3227-106">Bu eylem, İleri güncelleştirmeyi deneyin üzerinde aynı eşzamanlılık denetimlerinin dönmüyor emin olur.</span><span class="sxs-lookup"><span data-stu-id="f3227-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3227-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f3227-107">Example</span></span>  
 <span data-ttu-id="f3227-108">Bu senaryoda, bir <xref:System.Data.Linq.ChangeConflictException> kullanıcı2 sırada Yardımcısı ve bölüm sütunları değiştiğinden, değişiklikleri göndermek User1 çalıştığında özel durum harekete geçirilir.</span><span class="sxs-lookup"><span data-stu-id="f3227-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="f3227-109">Aşağıdaki tablo, durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3227-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="f3227-110">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="f3227-110">Manager</span></span>|<span data-ttu-id="f3227-111">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="f3227-111">Assistant</span></span>|<span data-ttu-id="f3227-112">Bölüm</span><span class="sxs-lookup"><span data-stu-id="f3227-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="f3227-113">User1 ve kullanıcı2 tarafından sorgulandığında, özgün veritabanının durumu.</span><span class="sxs-lookup"><span data-stu-id="f3227-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="f3227-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="f3227-114">Alfreds</span></span>|<span data-ttu-id="f3227-115">Maria</span><span class="sxs-lookup"><span data-stu-id="f3227-115">Maria</span></span>|<span data-ttu-id="f3227-116">Satış</span><span class="sxs-lookup"><span data-stu-id="f3227-116">Sales</span></span>|  
|<span data-ttu-id="f3227-117">Kullanıcı1, bu değişiklikleri göndermek hazırlar.</span><span class="sxs-lookup"><span data-stu-id="f3227-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="f3227-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="f3227-118">Alfred</span></span>||<span data-ttu-id="f3227-119">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="f3227-119">Marketing</span></span>|  
|<span data-ttu-id="f3227-120">Kullanıcı2 bu değişiklikleri zaten gönderildi.</span><span class="sxs-lookup"><span data-stu-id="f3227-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="f3227-121">Mary</span><span class="sxs-lookup"><span data-stu-id="f3227-121">Mary</span></span>|<span data-ttu-id="f3227-122">Hizmet</span><span class="sxs-lookup"><span data-stu-id="f3227-122">Service</span></span>|  
  
 <span data-ttu-id="f3227-123">User1 geçerli istemci üye değerlerle veritabanı değerlerinin üzerine yazarak bu çakışmayı karar verir.</span><span class="sxs-lookup"><span data-stu-id="f3227-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="f3227-124">Ne zaman User1 çözümlenen çakışması kullanarak <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, sonuç veritabanında olduğu gibi aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f3227-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="f3227-125">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="f3227-125">Manager</span></span>|<span data-ttu-id="f3227-126">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="f3227-126">Assistant</span></span>|<span data-ttu-id="f3227-127">Bölüm</span><span class="sxs-lookup"><span data-stu-id="f3227-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="f3227-128">Çakışma çözümü sonra yeni durumu.</span><span class="sxs-lookup"><span data-stu-id="f3227-128">New state after conflict resolution.</span></span>|<span data-ttu-id="f3227-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="f3227-129">Alfred</span></span><br /><br /> <span data-ttu-id="f3227-130">(kullanıcı1)</span><span class="sxs-lookup"><span data-stu-id="f3227-130">(from User1)</span></span>|<span data-ttu-id="f3227-131">Maria</span><span class="sxs-lookup"><span data-stu-id="f3227-131">Maria</span></span><br /><br /> <span data-ttu-id="f3227-132">(özgün)</span><span class="sxs-lookup"><span data-stu-id="f3227-132">(original)</span></span>|<span data-ttu-id="f3227-133">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="f3227-133">Marketing</span></span><br /><br /> <span data-ttu-id="f3227-134">(kullanıcı1)</span><span class="sxs-lookup"><span data-stu-id="f3227-134">(from User1)</span></span>|  
  
 <span data-ttu-id="f3227-135">Aşağıdaki kod örneği, geçerli istemci üye değerlerle veritabanı değerlerinin üzerine gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f3227-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="f3227-136">(Herhangi bir inceleme veya tek tek üye çakışıyor özel işleme gerçekleşir.)</span><span class="sxs-lookup"><span data-stu-id="f3227-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f3227-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f3227-137">See also</span></span>
- [<span data-ttu-id="f3227-138">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="f3227-138">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
