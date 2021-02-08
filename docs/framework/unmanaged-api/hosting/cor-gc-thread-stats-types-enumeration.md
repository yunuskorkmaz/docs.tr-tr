---
description: 'Hakkında daha fazla bilgi edinin: COR_GC_THREAD_STATS_TYPES numaralandırması'
title: COR_GC_THREAD_STATS_TYPES Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS_TYPES
helpviewer_keywords:
- COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type:
- apiref
ms.openlocfilehash: 04bc4e11c527b83cf5f1384b1092cc0d084008a3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799778"
---
# <a name="cor_gc_thread_stats_types-enumeration"></a><span data-ttu-id="27571-103">COR_GC_THREAD_STATS_TYPES Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="27571-103">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>

<span data-ttu-id="27571-104">Bir iş parçacığının çöp toplama istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="27571-104">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27571-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="27571-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="27571-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="27571-106">Members</span></span>  
  
|<span data-ttu-id="27571-107">Üye</span><span class="sxs-lookup"><span data-stu-id="27571-107">Member</span></span>|<span data-ttu-id="27571-108">Description</span><span class="sxs-lookup"><span data-stu-id="27571-108">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="27571-109">İş parçacığında en son çöp toplamada yükseltilen baytlar vardır.</span><span class="sxs-lookup"><span data-stu-id="27571-109">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27571-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27571-110">Requirements</span></span>  

 <span data-ttu-id="27571-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27571-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27571-112">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="27571-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="27571-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27571-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27571-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27571-114">See also</span></span>

- [<span data-ttu-id="27571-115">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="27571-115">Hosting Enumerations</span></span>](hosting-enumerations.md)
