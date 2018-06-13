---
title: 'Nasıl yapılır: çakışmaları veritabanı değerlerin üzerine yazar tarafından'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fd6db0b8-c29c-48ff-b768-31d28e7a148c
ms.openlocfilehash: 2e15f69e724365ea01d53c4c329511dcbebb3a4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358582"
---
# <a name="how-to-resolve-conflicts-by-overwriting-database-values"></a><span data-ttu-id="3233d-102">Nasıl yapılır: çakışmaları veritabanı değerlerin üzerine yazar tarafından</span><span class="sxs-lookup"><span data-stu-id="3233d-102">How to: Resolve Conflicts by Overwriting Database Values</span></span>
<span data-ttu-id="3233d-103">Değişikliklerinizi yeniden denemeden önce beklenen ve mevcut veritabanı değerleri arasındaki farkları bağdaştırma için kullanabileceğiniz <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> veritabanı değerlerini üzerine yazmak için.</span><span class="sxs-lookup"><span data-stu-id="3233d-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepCurrentValues> to overwrite database values.</span></span> <span data-ttu-id="3233d-104">Daha fazla bilgi için bkz: [iyimser eşzamanlılık: genel bakış](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3233d-104">For more information, see [Optimistic Concurrency: Overview](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3233d-105">Her durumda, istemci kaydını veritabanından güncelleştirilmiş verileri alarak ilk yenilenir.</span><span class="sxs-lookup"><span data-stu-id="3233d-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="3233d-106">Bu eylem sonraki güncelleştirme deneyin üzerinde aynı tutarlılık denetimleri başarısız olmayan emin olur.</span><span class="sxs-lookup"><span data-stu-id="3233d-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3233d-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="3233d-107">Example</span></span>  
 <span data-ttu-id="3233d-108">Bu senaryoda, bir <xref:System.Data.Linq.ChangeConflictException> kullanıcı2 zarfında Yardımcısı ve bölüm sütunları değiştiği için değişiklikleri göndermek Kullanıcı1 çalıştığında özel durum.</span><span class="sxs-lookup"><span data-stu-id="3233d-108">In this scenario, an <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="3233d-109">Aşağıdaki tabloda durumu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3233d-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="3233d-110">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="3233d-110">Manager</span></span>|<span data-ttu-id="3233d-111">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="3233d-111">Assistant</span></span>|<span data-ttu-id="3233d-112">Bölüm</span><span class="sxs-lookup"><span data-stu-id="3233d-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="3233d-113">Kullanıcı1 ve kullanıcı2 tarafından sorgulandığında, orijinal veritabanı durumu.</span><span class="sxs-lookup"><span data-stu-id="3233d-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="3233d-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="3233d-114">Alfreds</span></span>|<span data-ttu-id="3233d-115">Maria</span><span class="sxs-lookup"><span data-stu-id="3233d-115">Maria</span></span>|<span data-ttu-id="3233d-116">Satış</span><span class="sxs-lookup"><span data-stu-id="3233d-116">Sales</span></span>|  
|<span data-ttu-id="3233d-117">Bu değişiklikleri göndermek Kullanıcı1 hazırlar.</span><span class="sxs-lookup"><span data-stu-id="3233d-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="3233d-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="3233d-118">Alfred</span></span>||<span data-ttu-id="3233d-119">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="3233d-119">Marketing</span></span>|  
|<span data-ttu-id="3233d-120">Kullanıcı2 zaten bu değişiklikleri gönderdi.</span><span class="sxs-lookup"><span data-stu-id="3233d-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="3233d-121">Mary</span><span class="sxs-lookup"><span data-stu-id="3233d-121">Mary</span></span>|<span data-ttu-id="3233d-122">Hizmet</span><span class="sxs-lookup"><span data-stu-id="3233d-122">Service</span></span>|  
  
 <span data-ttu-id="3233d-123">Kullanıcı1 geçerli istemci üye değerlerle veritabanı değerlerini yazarak bu çakışmayı karar verir.</span><span class="sxs-lookup"><span data-stu-id="3233d-123">User1 decides to resolve this conflict by overwriting database values with the current client member values.</span></span>  
  
 <span data-ttu-id="3233d-124">Ne zaman Kullanıcı1 çözümler çakışma kullanarak <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, sonuç veritabanında olduğu gibi aşağıdaki tabloda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3233d-124">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepCurrentValues>, the result in the database is as in following table:</span></span>  
  
||<span data-ttu-id="3233d-125">Yöneticisi</span><span class="sxs-lookup"><span data-stu-id="3233d-125">Manager</span></span>|<span data-ttu-id="3233d-126">Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="3233d-126">Assistant</span></span>|<span data-ttu-id="3233d-127">Bölüm</span><span class="sxs-lookup"><span data-stu-id="3233d-127">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="3233d-128">Yeni durum çakışma çözümü sonra.</span><span class="sxs-lookup"><span data-stu-id="3233d-128">New state after conflict resolution.</span></span>|<span data-ttu-id="3233d-129">Alfred</span><span class="sxs-lookup"><span data-stu-id="3233d-129">Alfred</span></span><br /><br /> <span data-ttu-id="3233d-130">(kullanıcı1)</span><span class="sxs-lookup"><span data-stu-id="3233d-130">(from User1)</span></span>|<span data-ttu-id="3233d-131">Maria</span><span class="sxs-lookup"><span data-stu-id="3233d-131">Maria</span></span><br /><br /> <span data-ttu-id="3233d-132">(orijinal)</span><span class="sxs-lookup"><span data-stu-id="3233d-132">(original)</span></span>|<span data-ttu-id="3233d-133">Pazarlama</span><span class="sxs-lookup"><span data-stu-id="3233d-133">Marketing</span></span><br /><br /> <span data-ttu-id="3233d-134">(kullanıcı1)</span><span class="sxs-lookup"><span data-stu-id="3233d-134">(from User1)</span></span>|  
  
 <span data-ttu-id="3233d-135">Aşağıdaki kod örneği, veritabanı değerlerini geçerli istemci üye değerlerle üzerine gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3233d-135">The following example code shows how to overwrite database values with the current client member values.</span></span> <span data-ttu-id="3233d-136">(Hiçbir denetleme veya tek tek üye çakışmalarını özel işleme gerçekleşir.)</span><span class="sxs-lookup"><span data-stu-id="3233d-136">(No inspection or custom handling of individual member conflicts occurs.)</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.RefreshMode#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3233d-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3233d-137">See Also</span></span>  
 [<span data-ttu-id="3233d-138">Nasıl yapılır: Değişiklik Çakışmalarını Yönetme</span><span class="sxs-lookup"><span data-stu-id="3233d-138">How to: Manage Change Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)
