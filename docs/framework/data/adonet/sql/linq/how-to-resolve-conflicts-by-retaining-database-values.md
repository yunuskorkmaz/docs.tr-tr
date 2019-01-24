---
title: 'Nasıl yapılır: Veritabanı değerlerini tutarak çakışmaları'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
ms.openlocfilehash: f647dad951acfbc309257212018db32e655169df
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531271"
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="1300e-102">Nasıl yapılır: Veritabanı değerlerini tutarak çakışmaları</span><span class="sxs-lookup"><span data-stu-id="1300e-102">How to: Resolve Conflicts by Retaining Database Values</span></span>
<span data-ttu-id="1300e-103">Değişikliklerinizi yeniden denemeden önce veritabanı beklenen ve gerçek değerler arasındaki farkları bağdaştırma için kullanabileceğiniz <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> veritabanında bulunan değerlerini korumak için.</span><span class="sxs-lookup"><span data-stu-id="1300e-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="1300e-104">Nesne modelinde geçerli değerlerin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="1300e-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="1300e-105">Daha fazla bilgi için [iyimser eşzamanlılık: Genel Bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1300e-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1300e-106">Her durumda, istemci kaydını veritabanından güncelleştirilmiş verileri alarak önce yenilenir.</span><span class="sxs-lookup"><span data-stu-id="1300e-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="1300e-107">Bu eylem, İleri güncelleştirmeyi deneyin üzerinde aynı eşzamanlılık denetimlerinin dönmüyor emin olur.</span><span class="sxs-lookup"><span data-stu-id="1300e-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1300e-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="1300e-108">Example</span></span>  
 <span data-ttu-id="1300e-109">Bu senaryoda, bir <xref:System.Data.Linq.ChangeConflictException> kullanıcı2 sırada Yardımcısı ve bölüm sütunları değiştiğinden, değişiklikleri göndermek User1 çalıştığında özel durum harekete geçirilir.</span><span class="sxs-lookup"><span data-stu-id="1300e-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="1300e-110">Aşağıdaki tablo, durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1300e-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="1300e-111">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="1300e-111">Manager</span></span>|<span data-ttu-id="1300e-112">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="1300e-112">Assistant</span></span>|<span data-ttu-id="1300e-113">Bölüm</span><span class="sxs-lookup"><span data-stu-id="1300e-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="1300e-114">User1 ve kullanıcı2 tarafından sorgulandığında, özgün veritabanının durumu.</span><span class="sxs-lookup"><span data-stu-id="1300e-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="1300e-115">Alfreds</span><span class="sxs-lookup"><span data-stu-id="1300e-115">Alfreds</span></span>|<span data-ttu-id="1300e-116">Maria</span><span class="sxs-lookup"><span data-stu-id="1300e-116">Maria</span></span>|<span data-ttu-id="1300e-117">Satış</span><span class="sxs-lookup"><span data-stu-id="1300e-117">Sales</span></span>|  
|<span data-ttu-id="1300e-118">Kullanıcı1, bu değişiklikleri göndermek hazırlar.</span><span class="sxs-lookup"><span data-stu-id="1300e-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="1300e-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="1300e-119">Alfred</span></span>||<span data-ttu-id="1300e-120">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="1300e-120">Marketing</span></span>|  
|<span data-ttu-id="1300e-121">Kullanıcı2 bu değişiklikleri zaten gönderildi.</span><span class="sxs-lookup"><span data-stu-id="1300e-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="1300e-122">Mary</span><span class="sxs-lookup"><span data-stu-id="1300e-122">Mary</span></span>|<span data-ttu-id="1300e-123">Hizmet</span><span class="sxs-lookup"><span data-stu-id="1300e-123">Service</span></span>|  
  
 <span data-ttu-id="1300e-124">User1 nesne modelinde geçerli değerlerin üzerine daha yeni veritabanı değerleri sağlayarak bu çakışmayı karar verir.</span><span class="sxs-lookup"><span data-stu-id="1300e-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="1300e-125">Ne zaman User1 çözümlenen çakışması kullanarak <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, sonuç veritabanındaki tabloda aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="1300e-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="1300e-126">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="1300e-126">Manager</span></span>|<span data-ttu-id="1300e-127">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="1300e-127">Assistant</span></span>|<span data-ttu-id="1300e-128">Bölüm</span><span class="sxs-lookup"><span data-stu-id="1300e-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="1300e-129">Çakışma çözümü sonra yeni durumu.</span><span class="sxs-lookup"><span data-stu-id="1300e-129">New state after conflict resolution.</span></span>|<span data-ttu-id="1300e-130">Alfreds</span><span class="sxs-lookup"><span data-stu-id="1300e-130">Alfreds</span></span><br /><br /> <span data-ttu-id="1300e-131">(özgün)</span><span class="sxs-lookup"><span data-stu-id="1300e-131">(original)</span></span>|<span data-ttu-id="1300e-132">Mary</span><span class="sxs-lookup"><span data-stu-id="1300e-132">Mary</span></span><br /><br /> <span data-ttu-id="1300e-133">(kullanıcı2)</span><span class="sxs-lookup"><span data-stu-id="1300e-133">(from User2)</span></span>|<span data-ttu-id="1300e-134">Hizmet</span><span class="sxs-lookup"><span data-stu-id="1300e-134">Service</span></span><br /><br /> <span data-ttu-id="1300e-135">(kullanıcı2)</span><span class="sxs-lookup"><span data-stu-id="1300e-135">(from User2)</span></span>|  
  
 <span data-ttu-id="1300e-136">Aşağıdaki kod örneği, veritabanı değerleri ile nesne modelinde geçerli değerlerin üzerine gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1300e-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="1300e-137">(Herhangi bir inceleme veya tek tek üye çakışıyor özel işleme gerçekleşir.)</span><span class="sxs-lookup"><span data-stu-id="1300e-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="1300e-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1300e-138">See also</span></span>
- [<span data-ttu-id="1300e-139">Nasıl yapılır: Değişiklik çakışmalarını yönetme</span><span class="sxs-lookup"><span data-stu-id="1300e-139">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
