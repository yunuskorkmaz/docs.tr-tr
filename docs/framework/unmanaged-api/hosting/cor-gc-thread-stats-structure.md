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
ms.openlocfilehash: 37da471aaa8e9f802a8430d7b3289b375ff1b40a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136981"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="3a195-102">COR_GC_THREAD_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="3a195-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="3a195-103">Çöp toplamadan ilgili iş parçacığı başına istatistikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3a195-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a195-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a195-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="3a195-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3a195-105">Members</span></span>  
  
|<span data-ttu-id="3a195-106">Üye</span><span class="sxs-lookup"><span data-stu-id="3a195-106">Member</span></span>|<span data-ttu-id="3a195-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3a195-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="3a195-108">Geçerli `COR_GC_THREAD_STATS` örneğiyle ilişkili iş parçacığı üzerinde ayrılan bellek bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="3a195-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="3a195-109">Her nesil sıfır atık toplama gerçekleştiğinde bu sayı sıfır olarak temizlenir.</span><span class="sxs-lookup"><span data-stu-id="3a195-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="3a195-110">En son atık toplamada daha yüksek bir oluşturmaya yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="3a195-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a195-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a195-111">Remarks</span></span>  
 <span data-ttu-id="3a195-112">[ICLRTask:: GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) `COR_GC_THREAD_STATS`türünde bir çıkış parametresi alır.</span><span class="sxs-lookup"><span data-stu-id="3a195-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a195-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a195-113">Requirements</span></span>  
 <span data-ttu-id="3a195-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a195-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a195-115">**Üst bilgi:** GCHost. IDL</span><span class="sxs-lookup"><span data-stu-id="3a195-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="3a195-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="3a195-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a195-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a195-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a195-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3a195-118">See also</span></span>

- [<span data-ttu-id="3a195-119">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="3a195-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="3a195-120">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3a195-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
