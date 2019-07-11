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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 630c365c8710388ae3e913bedece0fb710da7cd9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768142"
---
# <a name="corgcstats-structure"></a><span data-ttu-id="af78e-102">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="af78e-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="af78e-103">Ortak dil çalışma zamanı (CLR) çöp toplama mekanizması hakkında istatistikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="af78e-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af78e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af78e-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="af78e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="af78e-105">Members</span></span>  
  
|<span data-ttu-id="af78e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="af78e-106">Member</span></span>|<span data-ttu-id="af78e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="af78e-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="af78e-108">Hangi alan değerlerini hesaplanır ve döndürülen gösterir.</span><span class="sxs-lookup"><span data-stu-id="af78e-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="af78e-109">Dış istek tarafından zorlanan çöp koleksiyonları sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af78e-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="af78e-110">Her bir oluşturmada gerçekleştirilen çöp koleksiyonları sayısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af78e-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="af78e-111">Tüm yığınlara kaydedilen kilobayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="af78e-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="af78e-112">Tüm yığınlara ayrılmış kilobayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="af78e-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="af78e-113">Nesil sıfır yığın kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="af78e-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="af78e-114">Oluşturma bir yığın kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="af78e-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="af78e-115">Nesil iki yığın kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="af78e-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="af78e-116">Büyük nesne yığının kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="af78e-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="af78e-117">Oluşturma bir sıfır kuşaktan yükseltilen nesnelerin kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="af78e-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="af78e-118">Oluşturma bir nesle iki yükseltilir nesnelerin kilobayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="af78e-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af78e-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="af78e-119">Remarks</span></span>  
 <span data-ttu-id="af78e-120">[Iclrgcmanager::getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) gerektirdiğine `Flags` alanını `COR_GC_STATS` yapısı bir veya daha fazla değere ayarlanacak [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) belirtmek için sabit listesi Ayarlanacak istatistikleri şunlardır.</span><span class="sxs-lookup"><span data-stu-id="af78e-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="af78e-121">Aşağıdaki tabloda bu yapı için iki tarafından sağlanan istatistikleri eşler [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) numaralandırma değerlerinin `COR_GC_COUNTS` ve `COR_GC_MEMORYUSAGE`.</span><span class="sxs-lookup"><span data-stu-id="af78e-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="af78e-122">COR_GC_COUNTS tarafından belirtilen</span><span class="sxs-lookup"><span data-stu-id="af78e-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="af78e-123">COR_GC_MEMORYUSAGE tarafından belirtilen</span><span class="sxs-lookup"><span data-stu-id="af78e-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="af78e-124">Kullanım örneği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="af78e-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="af78e-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af78e-125">Requirements</span></span>  
 <span data-ttu-id="af78e-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af78e-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af78e-127">**Üst bilgi:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="af78e-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="af78e-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="af78e-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af78e-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af78e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af78e-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af78e-130">See also</span></span>

- [<span data-ttu-id="af78e-131">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="af78e-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="af78e-132">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="af78e-132">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="af78e-133">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="af78e-133">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
