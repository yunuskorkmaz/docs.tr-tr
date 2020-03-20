---
title: COR_GC_STATS Yapısı
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
ms.openlocfilehash: 2ab0c38645a8e5fbd9e71b3c1787e88bfe2c0604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176532"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="e8f8d-102">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="e8f8d-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="e8f8d-103">Ortak dil çalışma zamanının (CLR) çöp toplama mekanizması hakkında istatistikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8f8d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8f8d-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="e8f8d-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="e8f8d-105">Members</span></span>  
  
|<span data-ttu-id="e8f8d-106">Üye</span><span class="sxs-lookup"><span data-stu-id="e8f8d-106">Member</span></span>|<span data-ttu-id="e8f8d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e8f8d-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="e8f8d-108">Hangi alan değerlerinin hesaplanıp döndürülmesi gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="e8f8d-109">Dış istek tarafından zorlanan çöp toplama sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="e8f8d-110">Her nesil için gerçekleştirilen çöp toplama sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="e8f8d-111">Tüm yığınlarda işlenen toplam kilobayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="e8f8d-112">Tüm yığınlarda ayrılmış toplam kilobayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="e8f8d-113">Kilobaytlıklarda, sıfır kuşağının büyüklüğü.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="e8f8d-114">Kilobaytlıklarda, nesil-bir yığının büyüklüğü.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="e8f8d-115">Kilobaytlıkboyutu, nesil-iki yığın.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="e8f8d-116">Büyük nesne yığınının büyüklüğü, kilobaytlar halinde.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="e8f8d-117">Kilobaytlarda, sıfır kuşağından nesil bire yükseltilen nesnelerin boyutu.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="e8f8d-118">Kilobaytlarda, birinci nesilden ikinci nesile terfi eden nesnelerin boyutu.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8f8d-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8f8d-119">Remarks</span></span>  
 <span data-ttu-id="e8f8d-120">[ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) yöntemi, `Flags` hangi istatistiklerin ayarlaneceğini belirtmek için `COR_GC_STATS` yapıalanının [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) numaralandırmanın bir veya daha fazla değerine ayarlanmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="e8f8d-121">Aşağıdaki tablo, bu yapı tarafından sağlanan istatistikleri iki [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) numaralandırma değeri `COR_GC_COUNTS` ile eşler ve. `COR_GC_MEMORYUSAGE`</span><span class="sxs-lookup"><span data-stu-id="e8f8d-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="e8f8d-122">COR_GC_COUNTS tarafından belirtilir</span><span class="sxs-lookup"><span data-stu-id="e8f8d-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="e8f8d-123">COR_GC_MEMORYUSAGE tarafından belirtilir</span><span class="sxs-lookup"><span data-stu-id="e8f8d-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="e8f8d-124">Kullanıma bir örnek aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="e8f8d-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e8f8d-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8f8d-125">Requirements</span></span>  
 <span data-ttu-id="e8f8d-126">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8f8d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8f8d-127">**Üstbilgi:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="e8f8d-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="e8f8d-128">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="e8f8d-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e8f8d-129">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8f8d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f8d-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8f8d-130">See also</span></span>

- [<span data-ttu-id="e8f8d-131">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="e8f8d-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="e8f8d-132">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="e8f8d-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="e8f8d-133">Çöp Toplama</span><span class="sxs-lookup"><span data-stu-id="e8f8d-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
