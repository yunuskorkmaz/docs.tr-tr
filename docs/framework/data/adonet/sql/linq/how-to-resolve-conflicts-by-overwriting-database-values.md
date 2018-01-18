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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1dd9a6be51ad1723aab7c3102387a42d1c24996
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="f7ef3-102">Nasıl yapılır: çakışmaları veritabanı değerlerin üzerine yazar tarafından</span><span class="sxs-lookup"><span data-stu-id="f7ef3-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="f7ef3-103">Değişikliklerinizi yeniden denemeden önce beklenen ve mevcut veritabanı değerleri arasındaki farkları bağdaştırma için kullanabileceğiniz <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> veritabanı değerlerini üzerine yazmak için.</span><span class="sxs-lookup"><span data-stu-id="f7ef3-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="f7ef3-104">Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f7ef3-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7ef3-105">Her durumda, istemci kaydını veritabanından güncelleştirilmiş verileri alarak ilk yenilenir.</span><span class="sxs-lookup"><span data-stu-id="f7ef3-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="f7ef3-106">Bu eylem sonraki güncelleştirme deneyin üzerinde aynı tutarlılık denetimleri başarısız olmayan emin olur.</span><span class="sxs-lookup"><span data-stu-id="f7ef3-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7ef3-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f7ef3-107">Example</span></span>  
 <span data-ttu-id="f7ef3-108">Bu senaryoda, bir <xref:System.Data.Linq.ChangeConflictException> kullanıcı2 zarfında Yardımcısı ve bölüm sütunları değiştiği için değişiklikleri göndermek Kullanıcı1 çalıştığında özel durum.</span><span class="sxs-lookup"><span data-stu-id="f7ef3-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="f7ef3-109">Aşağıdaki tabloda durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7ef3-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="f7ef3-110">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="f7ef3-110">Manager</span></span>|<span data-ttu-id="f7ef3-111">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="f7ef3-111">Assistant</span></span>|<span data-ttu-id="f7ef3-112">Bölüm</span><span class="sxs-lookup"><span data-stu-id="f7ef3-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="f7ef3-113">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında, orijinal veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="f7ef3-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="f7ef3-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="f7ef3-114">Alfreds</span></span>|<span data-ttu-id="f7ef3-115">Maria</span><span class="sxs-lookup"><span data-stu-id="f7ef3-115">Maria</span></span>|<span data-ttu-id="f7ef3-116">Satış</span><span class="sxs-lookup"><span data-stu-id="f7ef3-116">Sales</span></span>|  
|<span data-ttu-id="f7ef3-117">Bu değişiklikleri göndermek Kullanıcı1 hazırlar.</span><span class="sxs-lookup"><span data-stu-id="f7ef3-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="f7ef3-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="f7ef3-118">Alfred</span></span>||<span data-ttu-id="f7ef3-119">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="f7ef3-119">Marketing</span></span>|  
|<span data-ttu-id="f7ef3-120">Kullanıcı2 zaten bu değişiklikleri gönderdi.</span><span class="sxs-lookup"><span data-stu-id="f7ef3-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="f7ef3-121">Mary</span><span class="sxs-lookup"><span data-stu-id="f7ef3-121">Mary</span></span>|<span data-ttu-id="f7ef3-122">Hizmet</span><span class="sxs-lookup"><span data-stu-id="f7ef3-122">Service</span></span>|  
  
 <span data-ttu-id="f7ef3-123">Kullanıcı1 geçerli istemci üye değerlerle veritabanı değerlerini yazarak bu çakışmayı karar verir.</span><span class="sxs-lookup"><span data-stu-id="f7ef3-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="f7ef3-124">Ne zaman Kullanıcı1 çözümler çakışma kullanarak <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, sonuç veritabanında olduğu gibi aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="f7ef3-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="f7ef3-125">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="f7ef3-125">Manager</span></span>|<span data-ttu-id="f7ef3-126">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="f7ef3-126">Assistant</span></span>|<span data-ttu-id="f7ef3-127">Bölüm</span><span class="sxs-lookup"><span data-stu-id="f7ef3-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="f7ef3-128">Yeni durum çakışma çözümü sonra.</span><span class="sxs-lookup"><span data-stu-id="f7ef3-128">New state after conflict resolution.</span></span>|<span data-ttu-id="f7ef3-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="f7ef3-129">Alfred</span></span><br /><br /> <span data-ttu-id="f7ef3-130">(kullanıcı1)</span><span class="sxs-lookup"><span data-stu-id="f7ef3-130">(from User1)</span></span>|<span data-ttu-id="f7ef3-131">Maria</span><span class="sxs-lookup"><span data-stu-id="f7ef3-131">Maria</span></span><br /><br /> <span data-ttu-id="f7ef3-132">(orijinal)</span><span class="sxs-lookup"><span data-stu-id="f7ef3-132">(original)</span></span>|<span data-ttu-id="f7ef3-133">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="f7ef3-133">Marketing</span></span><br /><br /> <span data-ttu-id="f7ef3-134">(kullanıcı1)</span><span class="sxs-lookup"><span data-stu-id="f7ef3-134">(from User1)</span></span>|  
  
 <span data-ttu-id="f7ef3-135">Aşağıdaki kod örneği, veritabanı değerlerini geçerli istemci üye değerlerle üzerine gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f7ef3-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="f7ef3-136">(Hiçbir denetleme veya tek tek üye çakışmalarını özel işleme gerçekleşir.)</span><span class="sxs-lookup"><span data-stu-id="f7ef3-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f7ef3-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f7ef3-137">See Also</span></span>  
 [<span data-ttu-id="f7ef3-138">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="f7ef3-138">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
