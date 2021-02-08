---
description: 'Hakkında daha fazla bilgi edinin: COR_GC_STAT_TYPES numaralandırması'
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
ms.openlocfilehash: c4ea3175c777d49a5d6cffdf506f42e479784971
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799817"
---
# <a name="cor_gc_stat_types-enumeration"></a><span data-ttu-id="1fb99-103">COR_GC_STAT_TYPES Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1fb99-103">COR_GC_STAT_TYPES Enumeration</span></span>

<span data-ttu-id="1fb99-104">Çöp toplama için kaydedilecek istatistikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="1fb99-104">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fb99-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1fb99-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="1fb99-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1fb99-106">Remarks</span></span>  

 <span data-ttu-id="1fb99-107">Bu numaralandırma, [cor_gc_stats](cor-gc-stats-structure.md) yapısındaki hangi Istatistiklerin [ICLRGCManager:: GetStats](iclrgcmanager-getstats-method.md) yöntemi tarafından ayarlanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1fb99-107">This enumeration specifies which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="1fb99-108">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1fb99-108">Members</span></span>  
  
|<span data-ttu-id="1fb99-109">Üye</span><span class="sxs-lookup"><span data-stu-id="1fb99-109">Member</span></span>|<span data-ttu-id="1fb99-110">Description</span><span class="sxs-lookup"><span data-stu-id="1fb99-110">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="1fb99-111">Her nesil için gerçekleştirilen çöp koleksiyonlarının sayısını kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1fb99-111">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="1fb99-112">Bellek kullanımını ve çöp toplama boyutu istatistiklerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1fb99-112">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1fb99-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1fb99-113">Requirements</span></span>  

 <span data-ttu-id="1fb99-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fb99-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fb99-115">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="1fb99-115">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="1fb99-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fb99-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fb99-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fb99-117">See also</span></span>

- [<span data-ttu-id="1fb99-118">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="1fb99-118">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="1fb99-119">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="1fb99-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
