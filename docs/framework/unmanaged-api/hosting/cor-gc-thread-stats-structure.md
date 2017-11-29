---
title: "COR_GC_THREAD_STATS Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_THREAD_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_THREAD_STATS
helpviewer_keywords: COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10366d183ed7fd7386609e4c5726df0cea4e29a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="bc1f9-102">COR_GC_THREAD_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="bc1f9-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="bc1f9-103">Çöp toplama için ilgili iş parçacığı başına istatistikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bc1f9-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc1f9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc1f9-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="bc1f9-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bc1f9-105">Members</span></span>  
  
|<span data-ttu-id="bc1f9-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bc1f9-106">Member</span></span>|<span data-ttu-id="bc1f9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc1f9-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="bc1f9-108">Geçerli ilişkili iş parçacığında ayrılan belleği bayt sayısı `COR_GC_THREAD_STATS` örneği.</span><span class="sxs-lookup"><span data-stu-id="bc1f9-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="bc1f9-109">Bu sayı sıfıra nesil sıfır çöp toplama her gerçekleştiğinde temizlenir.</span><span class="sxs-lookup"><span data-stu-id="bc1f9-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="bc1f9-110">Bayt sayısı, en son çöp toplama için daha yüksek kuşaklı yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="bc1f9-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc1f9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bc1f9-111">Remarks</span></span>  
 <span data-ttu-id="bc1f9-112">[Iclrtask::getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) bir çıktı parametresi türü alan `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="bc1f9-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc1f9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc1f9-113">Requirements</span></span>  
 <span data-ttu-id="bc1f9-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc1f9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc1f9-115">**Başlık:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="bc1f9-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="bc1f9-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="bc1f9-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bc1f9-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc1f9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1f9-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc1f9-118">See Also</span></span>  
 [<span data-ttu-id="bc1f9-119">Barındırma yapıları</span><span class="sxs-lookup"><span data-stu-id="bc1f9-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="bc1f9-120">Ihosttask arabirimi</span><span class="sxs-lookup"><span data-stu-id="bc1f9-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
