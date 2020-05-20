---
title: COR_GC_STAT_TYPES Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: cca393ae34144787ab7800baec7c58209394f30e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616724"
---
# <a name="cor_gc_stat_types-enumeration"></a><span data-ttu-id="b2a42-102">COR_GC_STAT_TYPES Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="b2a42-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="b2a42-103">Çöp toplama için kaydedilecek istatistikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2a42-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2a42-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b2a42-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="b2a42-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2a42-105">Remarks</span></span>  
 <span data-ttu-id="b2a42-106">Bu numaralandırma, [cor_gc_stats](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) yapısındaki hangi Istatistiklerin [ICLRGCManager:: GetStats](iclrgcmanager-getstats-method.md) yöntemi tarafından ayarlanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b2a42-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="b2a42-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="b2a42-107">Members</span></span>  
  
|<span data-ttu-id="b2a42-108">Üye</span><span class="sxs-lookup"><span data-stu-id="b2a42-108">Member</span></span>|<span data-ttu-id="b2a42-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2a42-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="b2a42-110">Her nesil için gerçekleştirilen çöp koleksiyonlarının sayısını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b2a42-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="b2a42-111">Bellek kullanımını ve çöp toplama boyutu istatistiklerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="b2a42-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2a42-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2a42-112">Requirements</span></span>  
 <span data-ttu-id="b2a42-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2a42-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2a42-114">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="b2a42-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="b2a42-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2a42-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a42-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2a42-116">See also</span></span>

- [<span data-ttu-id="b2a42-117">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="b2a42-117">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="b2a42-118">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="b2a42-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
