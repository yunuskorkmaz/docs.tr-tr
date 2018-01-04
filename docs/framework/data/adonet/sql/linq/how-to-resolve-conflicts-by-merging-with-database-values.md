---
title: "Nasıl yapılır: çakışmaları veritabanı değerlerle birleştirerek"
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
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: ee1016a6dc20e58bfafc434617a36f8f8703a3bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a><span data-ttu-id="d2bec-102">Nasıl yapılır: çakışmaları veritabanı değerlerle birleştirerek</span><span class="sxs-lookup"><span data-stu-id="d2bec-102">How to: Resolve Conflicts by Merging with Database Values</span></span>
<span data-ttu-id="d2bec-103">Değişikliklerinizi yeniden denemeden önce beklenen ve mevcut veritabanı değerleri arasındaki farkları bağdaştırma için kullanabileceğiniz <xref:System.Data.Linq.RefreshMode.KeepChanges> geçerli istemci üye değerlerle veritabanı değerleri birleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="d2bec-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepChanges> to merge database values with the current client member values.</span></span> <span data-ttu-id="d2bec-104">Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d2bec-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2bec-105">Her durumda, istemci kaydını veritabanından güncelleştirilmiş verileri alarak ilk yenilenir.</span><span class="sxs-lookup"><span data-stu-id="d2bec-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="d2bec-106">Bu eylem sonraki güncelleştirme deneyin üzerinde aynı tutarlılık denetimleri başarısız olmayan emin olur.</span><span class="sxs-lookup"><span data-stu-id="d2bec-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2bec-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d2bec-107">Example</span></span>  
 <span data-ttu-id="d2bec-108">Bu senaryoda, bir <xref:System.Data.Linq.ChangeConflictException> kullanıcı2 zarfında Yardımcısı ve bölüm sütunları değiştiği için değişiklikleri göndermek Kullanıcı1 çalıştığında özel durum.</span><span class="sxs-lookup"><span data-stu-id="d2bec-108">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="d2bec-109">Aşağıdaki tabloda durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d2bec-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="d2bec-110">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="d2bec-110">Manager</span></span>|<span data-ttu-id="d2bec-111">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="d2bec-111">Assistant</span></span>|<span data-ttu-id="d2bec-112">Bölüm</span><span class="sxs-lookup"><span data-stu-id="d2bec-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="d2bec-113">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında, orijinal veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="d2bec-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="d2bec-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="d2bec-114">Alfreds</span></span>|<span data-ttu-id="d2bec-115">Maria</span><span class="sxs-lookup"><span data-stu-id="d2bec-115">Maria</span></span>|<span data-ttu-id="d2bec-116">Satış</span><span class="sxs-lookup"><span data-stu-id="d2bec-116">Sales</span></span>|  
|<span data-ttu-id="d2bec-117">Bu değişiklikleri göndermek Kullanıcı1 hazırlar.</span><span class="sxs-lookup"><span data-stu-id="d2bec-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="d2bec-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="d2bec-118">Alfred</span></span>||<span data-ttu-id="d2bec-119">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="d2bec-119">Marketing</span></span>|  
|<span data-ttu-id="d2bec-120">Kullanıcı2 zaten bu değişiklikleri gönderdi.</span><span class="sxs-lookup"><span data-stu-id="d2bec-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="d2bec-121">Mary</span><span class="sxs-lookup"><span data-stu-id="d2bec-121">Mary</span></span>|<span data-ttu-id="d2bec-122">Hizmet</span><span class="sxs-lookup"><span data-stu-id="d2bec-122">Service</span></span>|  
  
 <span data-ttu-id="d2bec-123">Kullanıcı1 veritabanı değerlerini geçerli istemci üye değerlerle birleştirerek Bu çakışmayı karar verir.</span><span class="sxs-lookup"><span data-stu-id="d2bec-123">User1 decides to resolve this conflict by merging database values with the current client member values.</span></span> <span data-ttu-id="d2bec-124">Sonucu, geçerli değişiklik kümesi de değiştirilmiş bu değer yalnızca değerleri üzerine yazılır veritabanının olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d2bec-124">The result will be that database values are overwritten only when the current changeset has also modified that value.</span></span>  
  
 <span data-ttu-id="d2bec-125">Ne zaman Kullanıcı1 çözümler çakışma kullanarak <xref:System.Data.Linq.RefreshMode.KeepChanges>, sonuç veritabanında olduğu gibi aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d2bec-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepChanges>, the result in the database is as in the following table:</span></span>  
  
||<span data-ttu-id="d2bec-126">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="d2bec-126">Manager</span></span>|<span data-ttu-id="d2bec-127">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="d2bec-127">Assistant</span></span>|<span data-ttu-id="d2bec-128">Bölüm</span><span class="sxs-lookup"><span data-stu-id="d2bec-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="d2bec-129">Yeni durum çakışma çözümü sonra.</span><span class="sxs-lookup"><span data-stu-id="d2bec-129">New state after conflict resolution.</span></span>|<span data-ttu-id="d2bec-130">Alfred</span><span class="sxs-lookup"><span data-stu-id="d2bec-130">Alfred</span></span><br /><br /> <span data-ttu-id="d2bec-131">(kullanıcı1)</span><span class="sxs-lookup"><span data-stu-id="d2bec-131">(from User1)</span></span>|<span data-ttu-id="d2bec-132">Mary</span><span class="sxs-lookup"><span data-stu-id="d2bec-132">Mary</span></span><br /><br /> <span data-ttu-id="d2bec-133">(kullanıcı2)</span><span class="sxs-lookup"><span data-stu-id="d2bec-133">(from User2)</span></span>|<span data-ttu-id="d2bec-134">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="d2bec-134">Marketing</span></span><br /><br /> <span data-ttu-id="d2bec-135">(kullanıcı1)</span><span class="sxs-lookup"><span data-stu-id="d2bec-135">(from User1)</span></span>|  
  
 <span data-ttu-id="d2bec-136">Aşağıdaki örnek, geçerli istemci üye değerlerle veritabanı değerleri (istemci de bu değeri değiştirilmediği sürece) birleştirmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d2bec-136">The following example shows how to merge database values with the current client member values (unless the client has also changed that value).</span></span> <span data-ttu-id="d2bec-137">Hiçbir denetleme veya tek tek üye çakışmalarını özel işleme oluşur.</span><span class="sxs-lookup"><span data-stu-id="d2bec-137">No inspection or custom handling of individual member conflicts occurs.</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="d2bec-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d2bec-138">See Also</span></span>  
 [<span data-ttu-id="d2bec-139">Nasıl yapılır: Veritabanı Değerlerinin Üzerine Yazarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="d2bec-139">How to: Resolve Conflicts by Overwriting Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-overwriting-database-values.md)  
 [<span data-ttu-id="d2bec-140">Nasıl yapılır: Veritabanı Değerlerini Tutarak Çakışmaları Çözümleme</span><span class="sxs-lookup"><span data-stu-id="d2bec-140">How to: Resolve Conflicts by Retaining Database Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-resolve-conflicts-by-retaining-database-values.md)  
 [<span data-ttu-id="d2bec-141">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="d2bec-141">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
