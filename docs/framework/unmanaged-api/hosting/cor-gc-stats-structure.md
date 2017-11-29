---
title: "COR_GC_STATS Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STATS
helpviewer_keywords: COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e7c620c4a33032711abc0d7b82af908018bd44cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="corgcstats-structure"></a><span data-ttu-id="0d679-102">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="0d679-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="0d679-103">Ortak dil çalışma zamanı (CLR) atık toplama mekanizmasını ilgili istatistikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="0d679-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d679-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0d679-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;   
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;   
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="0d679-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="0d679-105">Members</span></span>  
  
|<span data-ttu-id="0d679-106">Üye</span><span class="sxs-lookup"><span data-stu-id="0d679-106">Member</span></span>|<span data-ttu-id="0d679-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0d679-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="0d679-108">Hangi alan değerlerini hesaplanır ve döndürülen gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d679-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="0d679-109">Dış istek tarafından zorlanan çöp koleksiyonlarının sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d679-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="0d679-110">Her oluşturulmasında gerçekleştirilen çöp koleksiyonlarının sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0d679-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="0d679-111">Tüm yığın kaydedilen kilobayt toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="0d679-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="0d679-112">Tüm yığın ayrılmış kilobayt toplam sayısı.</span><span class="sxs-lookup"><span data-stu-id="0d679-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="0d679-113">Kilobayt cinsinden nesil sıfır yığın boyutu.</span><span class="sxs-lookup"><span data-stu-id="0d679-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="0d679-114">Kilobayt cinsinden oluşturma-bir yığın boyutu.</span><span class="sxs-lookup"><span data-stu-id="0d679-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="0d679-115">Kilobayt cinsinden nesil iki yığın boyutu.</span><span class="sxs-lookup"><span data-stu-id="0d679-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="0d679-116">Kilobayt cinsinden büyük nesne yığın boyutu.</span><span class="sxs-lookup"><span data-stu-id="0d679-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="0d679-117">Nesil biri sıfır kuşaktan yükseltilen nesnelerin kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0d679-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="0d679-118">Nesil iki kuşaktan bir yükseltilmiş nesnelerin kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0d679-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d679-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d679-119">Remarks</span></span>  
 <span data-ttu-id="0d679-120">[Iclrgcmanager::getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) gerektirdiğine `Flags` alanını `COR_GC_STATS` yapısı bir veya daha fazla değerlere ayarlamak için [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) belirtmek için numaralandırması İstatistikleri ayarlanması üzeresiniz.</span><span class="sxs-lookup"><span data-stu-id="0d679-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="0d679-121">Aşağıdaki tabloda bu iki yapısına tarafından sağlanan istatistikleri eşleyen [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) numaralandırma değerlerinin `COR_GC_COUNTS` ve `COR_GC_MEMORYUSAGE`.</span><span class="sxs-lookup"><span data-stu-id="0d679-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="0d679-122">COR_GC_COUNTS tarafından belirtilen</span><span class="sxs-lookup"><span data-stu-id="0d679-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="0d679-123">COR_GC_MEMORYUSAGE tarafından belirtilen</span><span class="sxs-lookup"><span data-stu-id="0d679-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="0d679-124">Kullanım örneği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="0d679-124">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0d679-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d679-125">Requirements</span></span>  
 <span data-ttu-id="0d679-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d679-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d679-127">**Başlık:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="0d679-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="0d679-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0d679-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d679-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d679-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d679-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d679-130">See Also</span></span>  
 [<span data-ttu-id="0d679-131">Barındırma yapıları</span><span class="sxs-lookup"><span data-stu-id="0d679-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="0d679-132">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="0d679-132">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="0d679-133">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="0d679-133">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
