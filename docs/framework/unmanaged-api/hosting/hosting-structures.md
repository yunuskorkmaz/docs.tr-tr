---
title: Barındırma Yapıları
ms.date: 03/30/2017
helpviewer_keywords:
- hosting structures [.NET Framework]
- unmanaged structures [.NET Framework], hosting
- structures [.NET Framework hosting]
ms.assetid: 492e010f-7493-4134-9505-f7008ccdaae6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01b12af8c3c3a2f834827ff14665050e07b31467
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985601"
---
# <a name="hosting-structures"></a><span data-ttu-id="c2c91-102">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="c2c91-102">Hosting Structures</span></span>
<span data-ttu-id="c2c91-103">Bu bölümde barındırma API'SİNİN kullandığı yönetilmeyen yapıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2c91-103">This section describes the unmanaged structures that the hosting API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2c91-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c2c91-104">In This Section</span></span>  
 [<span data-ttu-id="c2c91-105">AssemblyBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="c2c91-105">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 <span data-ttu-id="c2c91-106">Başvurulan derleme hakkında ayrıntılı bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2c91-106">Provides detailed information about the referenced assembly.</span></span>  
  
 [<span data-ttu-id="c2c91-107">BucketParameters Yapısı</span><span class="sxs-lookup"><span data-stu-id="c2c91-107">BucketParameters Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)  
 <span data-ttu-id="c2c91-108">Olay ile ilişkili olan geçerli bir özel durum için bir olay ve parametreleri türü adını depolar.</span><span class="sxs-lookup"><span data-stu-id="c2c91-108">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
 [<span data-ttu-id="c2c91-109">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="c2c91-109">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 <span data-ttu-id="c2c91-110">Ortak dil çalışma zamanı (CLR) çöp toplama mekanizması hakkında istatistikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2c91-110">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
 [<span data-ttu-id="c2c91-111">COR_GC_THREAD_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="c2c91-111">COR_GC_THREAD_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)  
 <span data-ttu-id="c2c91-112">Çöp toplama için ilgili iş parçacığı başına istatistikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="c2c91-112">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
 [<span data-ttu-id="c2c91-113">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="c2c91-113">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 <span data-ttu-id="c2c91-114">Hata Raporlama özel bir döküm eklenmesi için bir öğe açıklar.</span><span class="sxs-lookup"><span data-stu-id="c2c91-114">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
 [<span data-ttu-id="c2c91-115">MDAInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="c2c91-115">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)  
 <span data-ttu-id="c2c91-116">Hakkında ayrıntılar sağlar `Event_MDAFired` olayı yönetilen hata ayıklama Yardımcısı (MDA) oluşturulmasını tetikler.</span><span class="sxs-lookup"><span data-stu-id="c2c91-116">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
 [<span data-ttu-id="c2c91-117">ModuleBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="c2c91-117">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)  
 <span data-ttu-id="c2c91-118">Başvurulan modül ve onu içeren derleme hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c2c91-118">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
 [<span data-ttu-id="c2c91-119">StackOverflowInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="c2c91-119">StackOverflowInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/stackoverflowinfo-structure.md)  
 <span data-ttu-id="c2c91-120">Taşması nedeniyle oluşturulan özel durum oluştu taşma ve bilgi türünü saklar.</span><span class="sxs-lookup"><span data-stu-id="c2c91-120">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c2c91-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c2c91-121">Related Sections</span></span>  
 [<span data-ttu-id="c2c91-122">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="c2c91-122">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="c2c91-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c2c91-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [<span data-ttu-id="c2c91-124">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c2c91-124">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="c2c91-125">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c2c91-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
