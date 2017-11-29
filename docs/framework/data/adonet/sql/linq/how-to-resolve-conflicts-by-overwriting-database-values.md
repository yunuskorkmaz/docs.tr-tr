---
title: "Nasıl yapılır: çakışmaları veritabanı değerlerin üzerine yazar tarafından"
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
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1cb128020964955937aae3d9e477a600085d4cdb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="1d495-102">Nasıl yapılır: çakışmaları veritabanı değerlerin üzerine yazar tarafından</span><span class="sxs-lookup"><span data-stu-id="1d495-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="1d495-103">Değişikliklerinizi yeniden denemeden önce beklenen ve mevcut veritabanı değerleri arasındaki farkları bağdaştırma için kullanabileceğiniz <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> veritabanı değerlerini üzerine yazmak için.</span><span class="sxs-lookup"><span data-stu-id="1d495-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="1d495-104">Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="1d495-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d495-105">Her durumda, istemci kaydını veritabanından güncelleştirilmiş verileri alarak ilk yenilenir.</span><span class="sxs-lookup"><span data-stu-id="1d495-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="1d495-106">Bu eylem sonraki güncelleştirme deneyin üzerinde aynı tutarlılık denetimleri başarısız olmayan emin olur.</span><span class="sxs-lookup"><span data-stu-id="1d495-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d495-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d495-107">Example</span></span>  
 <span data-ttu-id="1d495-108">Bu senaryoda, bir <xref:System.Data.Linq.ChangeConflictException> kullanıcı2 zarfında Yardımcısı ve bölüm sütunları değiştiği için değişiklikleri göndermek Kullanıcı1 çalıştığında özel durum.</span><span class="sxs-lookup"><span data-stu-id="1d495-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="1d495-109">Aşağıdaki tabloda durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1d495-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="1d495-110">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="1d495-110">Manager</span></span>|<span data-ttu-id="1d495-111">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="1d495-111">Assistant</span></span>|<span data-ttu-id="1d495-112">Bölüm</span><span class="sxs-lookup"><span data-stu-id="1d495-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="1d495-113">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında, orijinal veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="1d495-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="1d495-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="1d495-114">Alfreds</span></span>|<span data-ttu-id="1d495-115">Maria</span><span class="sxs-lookup"><span data-stu-id="1d495-115">Maria</span></span>|<span data-ttu-id="1d495-116">Satış</span><span class="sxs-lookup"><span data-stu-id="1d495-116">Sales</span></span>|  
|<span data-ttu-id="1d495-117">Bu değişiklikleri göndermek Kullanıcı1 hazırlar.</span><span class="sxs-lookup"><span data-stu-id="1d495-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="1d495-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="1d495-118">Alfred</span></span>||<span data-ttu-id="1d495-119">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="1d495-119">Marketing</span></span>|  
|<span data-ttu-id="1d495-120">Kullanıcı2 zaten bu değişiklikleri gönderdi.</span><span class="sxs-lookup"><span data-stu-id="1d495-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="1d495-121">Mary</span><span class="sxs-lookup"><span data-stu-id="1d495-121">Mary</span></span>|<span data-ttu-id="1d495-122">Hizmet</span><span class="sxs-lookup"><span data-stu-id="1d495-122">Service</span></span>|  
  
 <span data-ttu-id="1d495-123">Kullanıcı1 geçerli istemci üye değerlerle veritabanı değerlerini yazarak bu çakışmayı karar verir.</span><span class="sxs-lookup"><span data-stu-id="1d495-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="1d495-124">Ne zaman Kullanıcı1 çözümler çakışma kullanarak <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, sonuç veritabanında olduğu gibi aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="1d495-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="1d495-125">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="1d495-125">Manager</span></span>|<span data-ttu-id="1d495-126">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="1d495-126">Assistant</span></span>|<span data-ttu-id="1d495-127">Bölüm</span><span class="sxs-lookup"><span data-stu-id="1d495-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="1d495-128">Yeni durum çakışma çözümü sonra.</span><span class="sxs-lookup"><span data-stu-id="1d495-128">New state after conflict resolution.</span></span>|<span data-ttu-id="1d495-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="1d495-129">Alfred</span></span><br /><br /> <span data-ttu-id="1d495-130">(kullanıcı1)</span><span class="sxs-lookup"><span data-stu-id="1d495-130">(from User1)</span></span>|<span data-ttu-id="1d495-131">Maria</span><span class="sxs-lookup"><span data-stu-id="1d495-131">Maria</span></span><br /><br /> <span data-ttu-id="1d495-132">(orijinal)</span><span class="sxs-lookup"><span data-stu-id="1d495-132">(original)</span></span>|<span data-ttu-id="1d495-133">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="1d495-133">Marketing</span></span><br /><br /> <span data-ttu-id="1d495-134">(kullanıcı1)</span><span class="sxs-lookup"><span data-stu-id="1d495-134">(from User1)</span></span>|  
  
 <span data-ttu-id="1d495-135">Aşağıdaki kod örneği, veritabanı değerlerini geçerli istemci üye değerlerle üzerine gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1d495-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="1d495-136">(Hiçbir denetleme veya tek tek üye çakışmalarını özel işleme gerçekleşir.)</span><span class="sxs-lookup"><span data-stu-id="1d495-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1d495-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1d495-137">See Also</span></span>  
 [<span data-ttu-id="1d495-138">Nasıl yapılır: değişiklik çakışmalarını yönetin</span><span class="sxs-lookup"><span data-stu-id="1d495-138">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
