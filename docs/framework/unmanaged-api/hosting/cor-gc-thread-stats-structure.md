---
description: 'Daha fazla bilgi edinin: COR_GC_THREAD_STATS yapısı'
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
ms.openlocfilehash: 179eb335e9f8c118ee98d4b777c347f3758ee0c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799791"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="4a0b7-103">COR_GC_THREAD_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="4a0b7-103">COR_GC_THREAD_STATS Structure</span></span>

<span data-ttu-id="4a0b7-104">Çöp toplamadan ilgili iş parçacığı başına istatistikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4a0b7-104">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a0b7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4a0b7-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="4a0b7-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="4a0b7-106">Members</span></span>  
  
|<span data-ttu-id="4a0b7-107">Üye</span><span class="sxs-lookup"><span data-stu-id="4a0b7-107">Member</span></span>|<span data-ttu-id="4a0b7-108">Description</span><span class="sxs-lookup"><span data-stu-id="4a0b7-108">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="4a0b7-109">Geçerli örnekle ilişkili iş parçacığı üzerinde ayrılan bellek bayt sayısı `COR_GC_THREAD_STATS` .</span><span class="sxs-lookup"><span data-stu-id="4a0b7-109">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="4a0b7-110">Her nesil sıfır atık toplama gerçekleştiğinde bu sayı sıfır olarak temizlenir.</span><span class="sxs-lookup"><span data-stu-id="4a0b7-110">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="4a0b7-111">En son atık toplamada daha yüksek bir oluşturmaya yükseltilen bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="4a0b7-111">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a0b7-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a0b7-112">Remarks</span></span>  

 <span data-ttu-id="4a0b7-113">[ICLRTask:: GetMemStats](iclrtask-getmemstats-method.md) , türünde bir çıkış parametresi alır `COR_GC_THREAD_STATS` .</span><span class="sxs-lookup"><span data-stu-id="4a0b7-113">[ICLRTask::GetMemStats](iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a0b7-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a0b7-114">Requirements</span></span>  

 <span data-ttu-id="4a0b7-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a0b7-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a0b7-116">**Üst bilgi:** GCHost. IDL</span><span class="sxs-lookup"><span data-stu-id="4a0b7-116">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="4a0b7-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="4a0b7-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4a0b7-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a0b7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a0b7-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a0b7-119">See also</span></span>

- [<span data-ttu-id="4a0b7-120">Barındırma Yapıları</span><span class="sxs-lookup"><span data-stu-id="4a0b7-120">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="4a0b7-121">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4a0b7-121">IHostTask Interface</span></span>](ihosttask-interface.md)
