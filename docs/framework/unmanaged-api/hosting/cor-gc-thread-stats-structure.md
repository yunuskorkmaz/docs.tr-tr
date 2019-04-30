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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696726"
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="fe5e4-102">COR_GC_THREAD_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="fe5e4-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="fe5e4-103">Çöp toplama için ilgili iş parçacığı başına istatistikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fe5e4-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe5e4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fe5e4-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="fe5e4-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="fe5e4-105">Members</span></span>  
  
|<span data-ttu-id="fe5e4-106">Üye</span><span class="sxs-lookup"><span data-stu-id="fe5e4-106">Member</span></span>|<span data-ttu-id="fe5e4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe5e4-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="fe5e4-108">Geçerli iş parçacığı üzerinde ayrılmış bellek bayt sayısı `COR_GC_THREAD_STATS` örneği.</span><span class="sxs-lookup"><span data-stu-id="fe5e4-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="fe5e4-109">Bu sayı her zaman sıfır nesil atık toplama işlemi gerçekleştiğinde sıfır olarak temizlenir.</span><span class="sxs-lookup"><span data-stu-id="fe5e4-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="fe5e4-110">Bayt sayısı, en son çöp toplama daha yüksek bir nesle yükseltilir.</span><span class="sxs-lookup"><span data-stu-id="fe5e4-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe5e4-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fe5e4-111">Remarks</span></span>  
 <span data-ttu-id="fe5e4-112">[Iclrtask::getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) çıkış parametresi türü alan `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="fe5e4-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe5e4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe5e4-113">Requirements</span></span>  
 <span data-ttu-id="fe5e4-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe5e4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe5e4-115">**Üst bilgi:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="fe5e4-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="fe5e4-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fe5e4-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe5e4-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe5e4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe5e4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe5e4-118">See also</span></span>

- [<span data-ttu-id="fe5e4-119">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="fe5e4-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="fe5e4-120">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe5e4-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
