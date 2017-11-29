---
title: "Nasıl yapılır: çakışmaları veritabanı değerlerini koruyarak"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: b475cf72-9e64-4f6e-99c1-af7737bc85ef
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1c2abc3f5ddd2daf9befc93e4469bd0e785fa6f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-resolve-conflicts-by-retaining-database-values"></a><span data-ttu-id="bd714-102">Nasıl yapılır: çakışmaları veritabanı değerlerini koruyarak</span><span class="sxs-lookup"><span data-stu-id="bd714-102">How to: Resolve Conflicts by Retaining Database Values</span></span>
<span data-ttu-id="bd714-103">Değişikliklerinizi yeniden denemeden önce beklenen ve mevcut veritabanı değerleri arasındaki farkları bağdaştırma için kullanabileceğiniz <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> veritabanında bulunan değerleri korumak için.</span><span class="sxs-lookup"><span data-stu-id="bd714-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues> to retain the values found in the database.</span></span> <span data-ttu-id="bd714-104">Nesne modeli geçerli değerleri ardından üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="bd714-104">The current values in the object model are then overwritten.</span></span> <span data-ttu-id="bd714-105">Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bd714-105">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd714-106">Her durumda, istemci kaydını veritabanından güncelleştirilmiş verileri alarak ilk yenilenir.</span><span class="sxs-lookup"><span data-stu-id="bd714-106">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="bd714-107">Bu eylem sonraki güncelleştirme deneyin üzerinde aynı tutarlılık denetimleri başarısız olmayan emin olur.</span><span class="sxs-lookup"><span data-stu-id="bd714-107">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd714-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd714-108">Example</span></span>  
 <span data-ttu-id="bd714-109">Bu senaryoda, bir <xref:System.Data.Linq.ChangeConflictException> kullanıcı2 zarfında Yardımcısı ve bölüm sütunları değiştiği için değişiklikleri göndermek Kullanıcı1 çalıştığında özel durum.</span><span class="sxs-lookup"><span data-stu-id="bd714-109">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="bd714-110">Aşağıdaki tabloda durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd714-110">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="bd714-111">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="bd714-111">Manager</span></span>|<span data-ttu-id="bd714-112">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="bd714-112">Assistant</span></span>|<span data-ttu-id="bd714-113">Bölüm</span><span class="sxs-lookup"><span data-stu-id="bd714-113">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="bd714-114">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında, orijinal veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="bd714-114">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="bd714-115">Alfreds</span><span class="sxs-lookup"><span data-stu-id="bd714-115">Alfreds</span></span>|<span data-ttu-id="bd714-116">Maria</span><span class="sxs-lookup"><span data-stu-id="bd714-116">Maria</span></span>|<span data-ttu-id="bd714-117">Satış</span><span class="sxs-lookup"><span data-stu-id="bd714-117">Sales</span></span>|  
|<span data-ttu-id="bd714-118">Bu değişiklikleri göndermek Kullanıcı1 hazırlar.</span><span class="sxs-lookup"><span data-stu-id="bd714-118">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="bd714-119">Alfred</span><span class="sxs-lookup"><span data-stu-id="bd714-119">Alfred</span></span>||<span data-ttu-id="bd714-120">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="bd714-120">Marketing</span></span>|  
|<span data-ttu-id="bd714-121">Kullanıcı2 zaten bu değişiklikleri gönderdi.</span><span class="sxs-lookup"><span data-stu-id="bd714-121">User2 has already submitted these changes.</span></span>||<span data-ttu-id="bd714-122">Mary</span><span class="sxs-lookup"><span data-stu-id="bd714-122">Mary</span></span>|<span data-ttu-id="bd714-123">Hizmet</span><span class="sxs-lookup"><span data-stu-id="bd714-123">Service</span></span>|  
  
 <span data-ttu-id="bd714-124">Kullanıcı1 nesne modeli geçerli değerleri üzerine daha yeni veritabanı değerlerini sağlayarak bu çakışmayı karar verir.</span><span class="sxs-lookup"><span data-stu-id="bd714-124">User1 decides to resolve this conflict by having the newer database values overwrite the current values in the object model.</span></span>  
  
 <span data-ttu-id="bd714-125">Ne zaman Kullanıcı1 çözümler çakışma kullanarak <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, veritabanı sonucunda tabloda aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="bd714-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.OverwriteCurrentValues>, the result in the database is as follows in the table:</span></span>  
  
||<span data-ttu-id="bd714-126">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="bd714-126">Manager</span></span>|<span data-ttu-id="bd714-127">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="bd714-127">Assistant</span></span>|<span data-ttu-id="bd714-128">Bölüm</span><span class="sxs-lookup"><span data-stu-id="bd714-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="bd714-129">Yeni durum çakışma çözümü sonra.</span><span class="sxs-lookup"><span data-stu-id="bd714-129">New state after conflict resolution.</span></span>|<span data-ttu-id="bd714-130">Alfreds</span><span class="sxs-lookup"><span data-stu-id="bd714-130">Alfreds</span></span><br /><br /> <span data-ttu-id="bd714-131">(orijinal)</span><span class="sxs-lookup"><span data-stu-id="bd714-131">(original)</span></span>|<span data-ttu-id="bd714-132">Mary</span><span class="sxs-lookup"><span data-stu-id="bd714-132">Mary</span></span><br /><br /> <span data-ttu-id="bd714-133">(kullanıcı2)</span><span class="sxs-lookup"><span data-stu-id="bd714-133">(from User2)</span></span>|<span data-ttu-id="bd714-134">Hizmet</span><span class="sxs-lookup"><span data-stu-id="bd714-134">Service</span></span><br /><br /> <span data-ttu-id="bd714-135">(kullanıcı2)</span><span class="sxs-lookup"><span data-stu-id="bd714-135">(from User2)</span></span>|  
  
 <span data-ttu-id="bd714-136">Aşağıdaki kod örneği, nesne modelinde geçerli değerleri veritabanı değerlerle üzerine gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="bd714-136">The following example code shows how to overwrite current values in the object model with the database values.</span></span> <span data-ttu-id="bd714-137">(Hiçbir denetleme veya tek tek üye çakışmalarını özel işleme gerçekleşir.)</span><span class="sxs-lookup"><span data-stu-id="bd714-137">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.RefreshMode#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bd714-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd714-138">See Also</span></span>  
 [<span data-ttu-id="bd714-139">Nasıl yapılır: değişiklik çakışmalarını yönetin</span><span class="sxs-lookup"><span data-stu-id="bd714-139">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
