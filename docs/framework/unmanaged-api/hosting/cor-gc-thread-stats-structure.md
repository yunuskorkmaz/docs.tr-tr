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
ms.openlocfilehash: 88e81779fc9c20c506f3b0aa11ac2da3958dfe86
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616703"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="1dd41-102">COR_GC_THREAD_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="1dd41-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="1dd41-103">Çöp toplamadan ilgili iş parçacığı başına istatistikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="1dd41-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd41-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1dd41-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="1dd41-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1dd41-105">Members</span></span>  
  
|<span data-ttu-id="1dd41-106">Üye</span><span class="sxs-lookup"><span data-stu-id="1dd41-106">Member</span></span>|<span data-ttu-id="1dd41-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1dd41-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="1dd41-108">Geçerli örnekle ilişkili iş parçacığı üzerinde ayrılan bellek bayt sayısı `COR_GC_THREAD_STATS` .</span><span class="sxs-lookup"><span data-stu-id="1dd41-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="1dd41-109">Her nesil sıfır atık toplama gerçekleştiğinde bu sayı sıfır olarak temizlenir.</span><span class="sxs-lookup"><span data-stu-id="1dd41-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="1dd41-110">En son atık toplamada daha yüksek bir oluşturmaya yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="1dd41-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dd41-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1dd41-111">Remarks</span></span>  
 <span data-ttu-id="1dd41-112">[ICLRTask:: GetMemStats](iclrtask-getmemstats-method.md) , türünde bir çıkış parametresi alır `COR_GC_THREAD_STATS` .</span><span class="sxs-lookup"><span data-stu-id="1dd41-112">[ICLRTask::GetMemStats](iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd41-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dd41-113">Requirements</span></span>  
 <span data-ttu-id="1dd41-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dd41-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd41-115">**Üst bilgi:** GCHost. IDL</span><span class="sxs-lookup"><span data-stu-id="1dd41-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="1dd41-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="1dd41-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dd41-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd41-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd41-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dd41-118">See also</span></span>

- [<span data-ttu-id="1dd41-119">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="1dd41-119">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="1dd41-120">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dd41-120">IHostTask Interface</span></span>](ihosttask-interface.md)
