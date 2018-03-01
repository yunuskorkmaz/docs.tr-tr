---
title: "COR_GC_THREAD_STATS Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 266352984cf50dc906e77598e8dcc9216526ce17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="f8978-102">COR_GC_THREAD_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="f8978-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="f8978-103">Çöp toplama için ilgili iş parçacığı başına istatistikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="f8978-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8978-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f8978-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="f8978-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f8978-105">Members</span></span>  
  
|<span data-ttu-id="f8978-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f8978-106">Member</span></span>|<span data-ttu-id="f8978-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8978-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="f8978-108">Geçerli ilişkili iş parçacığında ayrılan belleği bayt sayısı `COR_GC_THREAD_STATS` örneği.</span><span class="sxs-lookup"><span data-stu-id="f8978-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="f8978-109">Bu sayı sıfıra nesil sıfır çöp toplama her gerçekleştiğinde temizlenir.</span><span class="sxs-lookup"><span data-stu-id="f8978-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="f8978-110">Bayt sayısı, en son çöp toplama için daha yüksek kuşaklı yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="f8978-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8978-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8978-111">Remarks</span></span>  
 <span data-ttu-id="f8978-112">[Iclrtask::getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) bir çıktı parametresi türü alan `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="f8978-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8978-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8978-113">Requirements</span></span>  
 <span data-ttu-id="f8978-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8978-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8978-115">**Başlık:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="f8978-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="f8978-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f8978-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8978-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8978-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8978-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f8978-118">See Also</span></span>  
 [<span data-ttu-id="f8978-119">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="f8978-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="f8978-120">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8978-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
