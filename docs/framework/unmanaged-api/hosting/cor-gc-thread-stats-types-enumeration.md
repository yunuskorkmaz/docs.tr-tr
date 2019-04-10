---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c631a0a3abb3cb2a342dfd44fdffb147b742ae3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212472"
---
# <a name="corgcthreadstatstypes-enumeration"></a><span data-ttu-id="ae1c3-102">COR_GC_THREAD_STATS_TYPES Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="ae1c3-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="ae1c3-103">Bir iş parçacığı çöp toplama istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="ae1c3-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae1c3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae1c3-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="ae1c3-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="ae1c3-105">Members</span></span>  
  
|<span data-ttu-id="ae1c3-106">Üye</span><span class="sxs-lookup"><span data-stu-id="ae1c3-106">Member</span></span>|<span data-ttu-id="ae1c3-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ae1c3-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="ae1c3-108">İş parçacığı en son çöp toplamada yükseltilen bayt vardır.</span><span class="sxs-lookup"><span data-stu-id="ae1c3-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ae1c3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae1c3-109">Requirements</span></span>  
 <span data-ttu-id="ae1c3-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae1c3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae1c3-111">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="ae1c3-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 **<span data-ttu-id="ae1c3-112">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ae1c3-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ae1c3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae1c3-113">See also</span></span>

- [<span data-ttu-id="ae1c3-114">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="ae1c3-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
