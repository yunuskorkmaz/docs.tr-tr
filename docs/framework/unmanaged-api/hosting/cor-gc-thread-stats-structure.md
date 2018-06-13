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
ms.openlocfilehash: 24a386fe82bbd004954924a573c090af7f58824a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431834"
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="d8a1b-102">COR_GC_THREAD_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="d8a1b-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="d8a1b-103">Çöp toplama için ilgili iş parçacığı başına istatistikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d8a1b-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8a1b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8a1b-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="d8a1b-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d8a1b-105">Members</span></span>  
  
|<span data-ttu-id="d8a1b-106">Üye</span><span class="sxs-lookup"><span data-stu-id="d8a1b-106">Member</span></span>|<span data-ttu-id="d8a1b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d8a1b-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="d8a1b-108">Geçerli ilişkili iş parçacığında ayrılan belleği bayt sayısı `COR_GC_THREAD_STATS` örneği.</span><span class="sxs-lookup"><span data-stu-id="d8a1b-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="d8a1b-109">Bu sayı sıfıra nesil sıfır çöp toplama her gerçekleştiğinde temizlenir.</span><span class="sxs-lookup"><span data-stu-id="d8a1b-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="d8a1b-110">Bayt sayısı, en son çöp toplama için daha yüksek kuşaklı yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="d8a1b-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8a1b-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8a1b-111">Remarks</span></span>  
 <span data-ttu-id="d8a1b-112">[Iclrtask::getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) bir çıktı parametresi türü alan `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="d8a1b-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8a1b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8a1b-113">Requirements</span></span>  
 <span data-ttu-id="d8a1b-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8a1b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8a1b-115">**Başlık:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="d8a1b-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="d8a1b-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d8a1b-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d8a1b-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8a1b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a1b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8a1b-118">See Also</span></span>  
 [<span data-ttu-id="d8a1b-119">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="d8a1b-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="d8a1b-120">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8a1b-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
