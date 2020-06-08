---
title: COR_PRF_SUSPEND_REASON Numaralandırması
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
ms.openlocfilehash: fdbcbb2da8f449b9275d820763c2a94cca86cd1e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500760"
---
# <a name="cor_prf_suspend_reason-enumeration"></a><span data-ttu-id="f61ad-102">COR_PRF_SUSPEND_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f61ad-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="f61ad-103">Çalışma zamanının askıya alınma nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f61ad-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f61ad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f61ad-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="f61ad-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f61ad-105">Members</span></span>  
  
|<span data-ttu-id="f61ad-106">Üye</span><span class="sxs-lookup"><span data-stu-id="f61ad-106">Member</span></span>|<span data-ttu-id="f61ad-107">Description</span><span class="sxs-lookup"><span data-stu-id="f61ad-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="f61ad-108">Beklenmeyen bir nedenden dolayı çalışma zamanı askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="f61ad-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="f61ad-109">Bir çöp toplama isteğine hizmet vermek için çalışma zamanı askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="f61ad-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="f61ad-110">[ICorProfilerCallback:: RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) ve [ICorProfilerCallback:: RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) geri çağırmaları arasında çöp toplama ile ilgili geri çağırmaları meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="f61ad-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="f61ad-111">Çalışma zamanı askıya alınabilmesi için askıya alındı `AppDomain` .</span><span class="sxs-lookup"><span data-stu-id="f61ad-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="f61ad-112">Çalışma zamanı askıya alındığında, çalışma zamanı hangi iş parçacıklarının `AppDomain` kapanmakta olduğunu ve sürdürüldiklerinde onları iptal etmek üzere ayarlayaceğini belirlemektir.</span><span class="sxs-lookup"><span data-stu-id="f61ad-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="f61ad-113">`AppDomain`Bu askıya alma sırasında belirli bir geri çağırma yok.</span><span class="sxs-lookup"><span data-stu-id="f61ad-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="f61ad-114">Çalışma zamanı, kod alma işleminin gerçekleşmesi için askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="f61ad-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="f61ad-115">Kod işleme, yalnızca tam zamanında (JıT) derleyici tarafından etkin hale geldiğinde kodun etkin hale getiriliyor.</span><span class="sxs-lookup"><span data-stu-id="f61ad-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="f61ad-116">`ICorProfilerCallback::RuntimeSuspendFinished`Ve geri çağırmalar arasında kod geri çağırmaları oluşur `ICorProfilerCallback::RuntimeResumeStarted` .</span><span class="sxs-lookup"><span data-stu-id="f61ad-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="f61ad-117">**Note:**  CLR JıT, .NET Framework sürüm 2,0 ' deki işlevleri göstermez, bu nedenle bu değer 2,0 ' de kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="f61ad-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="f61ad-118">Çalışma zamanı, kapanması için askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="f61ad-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="f61ad-119">İşlemi gerçekleştirmek için tüm iş parçacıklarını askıya almalıdır.</span><span class="sxs-lookup"><span data-stu-id="f61ad-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="f61ad-120">Çalışma zamanı, işlem içi hata ayıklama için askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="f61ad-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="f61ad-121">Bir çöp toplama işlemine hazırlanmak için çalışma zamanı askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="f61ad-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="f61ad-122">Çalışma zamanı, JıT yeniden derleme için askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="f61ad-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f61ad-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f61ad-123">Remarks</span></span>  
 <span data-ttu-id="f61ad-124">Yönetilmeyen koddaki tüm çalışma zamanı iş parçacıklarının çalışmaya devam etmesine izin verilir, çalışma zamanı yeniden girmeye çalışır ve bu noktada çalışma zamanı sürdürülene kadar da askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="f61ad-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="f61ad-125">Bu, çalışma zamanını belirten yeni iş parçacıkları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f61ad-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="f61ad-126">Çalışma zamanının içindeki tüm iş parçacıkları, kesilebilir kodunda olmaları durumunda veya kesilebilir koduna ulaştığında askıya alınması isteniyorsa hemen askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="f61ad-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f61ad-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f61ad-127">Requirements</span></span>  
 <span data-ttu-id="f61ad-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f61ad-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f61ad-129">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f61ad-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f61ad-130">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f61ad-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f61ad-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f61ad-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f61ad-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f61ad-132">See also</span></span>

- [<span data-ttu-id="f61ad-133">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f61ad-133">Profiling Enumerations</span></span>](profiling-enumerations.md)
