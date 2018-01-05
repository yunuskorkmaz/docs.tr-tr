---
title: "Barındırma Yapıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- hosting structures [.NET Framework]
- unmanaged structures [.NET Framework], hosting
- structures [.NET Framework hosting]
ms.assetid: 492e010f-7493-4134-9505-f7008ccdaae6
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e59353272856525b7d72f322694d15a42ab7b32
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-structures"></a><span data-ttu-id="6c724-102">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="6c724-102">Hosting Structures</span></span>
<span data-ttu-id="6c724-103">Bu bölümde barındırma API'sini kullanır yönetilmeyen yapılar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6c724-103">This section describes the unmanaged structures that the hosting API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6c724-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6c724-104">In This Section</span></span>  
 [<span data-ttu-id="6c724-105">AssemblyBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="6c724-105">AssemblyBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/assemblybindinfo-structure.md)  
 <span data-ttu-id="6c724-106">Başvurulan derlemeyi hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c724-106">Provides detailed information about the referenced assembly.</span></span>  
  
 [<span data-ttu-id="6c724-107">BucketParameters Yapısı</span><span class="sxs-lookup"><span data-stu-id="6c724-107">BucketParameters Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/bucketparameters-structure.md)  
 <span data-ttu-id="6c724-108">Olay ve parametreleri tür adını olayla ilişkili geçerli özel durumu için depolar.</span><span class="sxs-lookup"><span data-stu-id="6c724-108">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
 [<span data-ttu-id="6c724-109">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="6c724-109">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 <span data-ttu-id="6c724-110">Ortak dil çalışma zamanı (CLR) atık toplama mekanizmasını ilgili istatistikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c724-110">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
 [<span data-ttu-id="6c724-111">COR_GC_THREAD_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="6c724-111">COR_GC_THREAD_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md)  
 <span data-ttu-id="6c724-112">Çöp toplama için ilgili iş parçacığı başına istatistikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="6c724-112">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
 [<span data-ttu-id="6c724-113">CustomDumpItem Yapısı</span><span class="sxs-lookup"><span data-stu-id="6c724-113">CustomDumpItem Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 <span data-ttu-id="6c724-114">Hata Raporlama özel bir döküm eklenmesi için bir öğe açıklar.</span><span class="sxs-lookup"><span data-stu-id="6c724-114">Describes an item to be added to a custom dump in error reporting.</span></span>  
  
 [<span data-ttu-id="6c724-115">MDAInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="6c724-115">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)  
 <span data-ttu-id="6c724-116">Hakkında ayrıntılar sağlar `Event_MDAFired` yönetilen hata ayıklama Yardımcısı (MDA) oluşturulmasını tetikleyen olayı.</span><span class="sxs-lookup"><span data-stu-id="6c724-116">Provides details about the `Event_MDAFired` event, which triggers the creation of a managed debugging assistant (MDA).</span></span>  
  
 [<span data-ttu-id="6c724-117">ModuleBindInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="6c724-117">ModuleBindInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/modulebindinfo-structure.md)  
 <span data-ttu-id="6c724-118">Başvurulan modül ve içerdiği derleme hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6c724-118">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
 [<span data-ttu-id="6c724-119">StackOverflowInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="6c724-119">StackOverflowInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/stackoverflowinfo-structure.md)  
 <span data-ttu-id="6c724-120">Taşması nedeniyle atılan özel durum oluştu Taşması ve bilgi türünü saklar.</span><span class="sxs-lookup"><span data-stu-id="6c724-120">Stores the type of overflow that occurred and information on the exception that was thrown due to the overflow.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6c724-121">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6c724-121">Related Sections</span></span>  
 [<span data-ttu-id="6c724-122">Barındırma Coclassları</span><span class="sxs-lookup"><span data-stu-id="6c724-122">Hosting Coclasses</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)  
  
 [<span data-ttu-id="6c724-123">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6c724-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
  
 [<span data-ttu-id="6c724-124">Kullanım Dışı CLR Barındırma İşlevleri</span><span class="sxs-lookup"><span data-stu-id="6c724-124">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)  
  
 [<span data-ttu-id="6c724-125">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6c724-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
