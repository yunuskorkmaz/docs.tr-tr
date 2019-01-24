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
ms.openlocfilehash: 60cbc6f6649db28d06321b59c26c45668628d9ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712226"
---
# <a name="corgcthreadstatstypes-enumeration"></a><span data-ttu-id="6691f-102">COR_GC_THREAD_STATS_TYPES Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="6691f-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="6691f-103">Bir iş parçacığı çöp toplama istatistiklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="6691f-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6691f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6691f-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="6691f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="6691f-105">Members</span></span>  
  
|<span data-ttu-id="6691f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="6691f-106">Member</span></span>|<span data-ttu-id="6691f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6691f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="6691f-108">İş parçacığı en son çöp toplamada yükseltilen bayt vardır.</span><span class="sxs-lookup"><span data-stu-id="6691f-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6691f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6691f-109">Requirements</span></span>  
 <span data-ttu-id="6691f-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6691f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6691f-111">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="6691f-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="6691f-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6691f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6691f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6691f-113">See also</span></span>
- [<span data-ttu-id="6691f-114">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="6691f-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
