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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e228cfbdade420c4d5248ffd417c6131083ee74
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110423"
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="dbadf-102">COR_GC_STAT_TYPES Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="dbadf-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="dbadf-103">Bir çöp toplama için kaydedilecek istatistikleri belirtir.</span><span class="sxs-lookup"><span data-stu-id="dbadf-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbadf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbadf-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="dbadf-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dbadf-105">Remarks</span></span>  
 <span data-ttu-id="dbadf-106">Bu numaralandırma, hangi istatistikleri belirtir [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) yapısı olan ayarlanması [Iclrgcmanager::getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dbadf-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="dbadf-107">Üyeler</span><span class="sxs-lookup"><span data-stu-id="dbadf-107">Members</span></span>  
  
|<span data-ttu-id="dbadf-108">Üye</span><span class="sxs-lookup"><span data-stu-id="dbadf-108">Member</span></span>|<span data-ttu-id="dbadf-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dbadf-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="dbadf-110">Kayıtları atık toplamaları sayısı için her bir oluşturmada gerçekleştirdi.</span><span class="sxs-lookup"><span data-stu-id="dbadf-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="dbadf-111">Kayıtları bellek kullanımı ve çöp toplama boyutu istatistikleri.</span><span class="sxs-lookup"><span data-stu-id="dbadf-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dbadf-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dbadf-112">Requirements</span></span>  
 <span data-ttu-id="dbadf-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbadf-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbadf-114">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="dbadf-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="dbadf-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbadf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbadf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbadf-116">See also</span></span>

- [<span data-ttu-id="dbadf-117">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="dbadf-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="dbadf-118">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="dbadf-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
