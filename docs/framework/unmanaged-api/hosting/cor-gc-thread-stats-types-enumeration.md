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
ms.openlocfilehash: a984e8645bec0f58d8a31965b762e0a3a190ba59
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768022"
---
# <a name="corgcthreadstatstypes-enumeration"></a><span data-ttu-id="7e47e-102">COR_GC_THREAD_STATS_TYPES Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7e47e-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="7e47e-103">Bir iş parçacığı çöp toplama istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7e47e-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e47e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7e47e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="7e47e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7e47e-105">Members</span></span>  
  
|<span data-ttu-id="7e47e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7e47e-106">Member</span></span>|<span data-ttu-id="7e47e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7e47e-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="7e47e-108">İş parçacığı en son çöp toplamada yükseltilen bayt vardır.</span><span class="sxs-lookup"><span data-stu-id="7e47e-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7e47e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e47e-109">Requirements</span></span>  
 <span data-ttu-id="7e47e-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e47e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e47e-111">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="7e47e-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="7e47e-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e47e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e47e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e47e-113">See also</span></span>

- [<span data-ttu-id="7e47e-114">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7e47e-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
