---
title: COR_GC_THREAD_STATS Yapısı
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60a4b56270318a05d0e5a480fdb56eb45593d5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177742"
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="2bb19-102">COR_GC_THREAD_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="2bb19-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="2bb19-103">Çöp toplama için ilgili iş parçacığı başına istatistikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2bb19-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bb19-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2bb19-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="2bb19-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2bb19-105">Members</span></span>  
  
|<span data-ttu-id="2bb19-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2bb19-106">Member</span></span>|<span data-ttu-id="2bb19-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2bb19-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="2bb19-108">Geçerli iş parçacığı üzerinde ayrılmış bellek bayt sayısı `COR_GC_THREAD_STATS` örneği.</span><span class="sxs-lookup"><span data-stu-id="2bb19-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="2bb19-109">Bu sayı her zaman sıfır nesil atık toplama işlemi gerçekleştiğinde sıfır olarak temizlenir.</span><span class="sxs-lookup"><span data-stu-id="2bb19-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="2bb19-110">Bayt sayısı, en son çöp toplama daha yüksek bir nesle yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="2bb19-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bb19-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2bb19-111">Remarks</span></span>  
 <span data-ttu-id="2bb19-112">[Iclrtask::getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) çıkış parametresi türü alan `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="2bb19-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bb19-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2bb19-113">Requirements</span></span>  
 <span data-ttu-id="2bb19-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2bb19-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bb19-115">**Üst bilgi:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="2bb19-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="2bb19-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2bb19-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="2bb19-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2bb19-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2bb19-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bb19-118">See also</span></span>

- [<span data-ttu-id="2bb19-119">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="2bb19-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="2bb19-120">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2bb19-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
