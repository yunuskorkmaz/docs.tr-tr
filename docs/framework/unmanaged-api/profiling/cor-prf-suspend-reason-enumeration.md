---
title: "COR_PRF_SUSPEND_REASON Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SUSPEND_REASON
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SUSPEND_REASON
helpviewer_keywords: COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 713360b3cdc30ce7bca3e0df115016d66e59b0df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="corprfsuspendreason-enumeration"></a><span data-ttu-id="7cdc7-102">COR_PRF_SUSPEND_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7cdc7-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="7cdc7-103">Çalışma zamanı askıya alınmış nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cdc7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7cdc7-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="7cdc7-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7cdc7-105">Members</span></span>  
  
|<span data-ttu-id="7cdc7-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7cdc7-106">Member</span></span>|<span data-ttu-id="7cdc7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7cdc7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="7cdc7-108">Çalışma zamanı belirlenemeyen bir nedenden dolayı askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="7cdc7-109">Çalışma zamanı bir atık toplama isteğine hizmet askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="7cdc7-110">Çöp toplama ile ilgili geri aramalar arasında ortaya [Icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) ve [Icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri aramalar.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="7cdc7-111">Çalışma zamanı askıya böylece bir `AppDomain` kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="7cdc7-112">Çalışma zamanı askıya alınmış durumdayken, çalışma zamanı hangi iş parçacığı bulunan belirleyecek `AppDomain` diğer bir deyişle kapatılır ve bunlar sürdürdüğünüzde iptal etmek için bunları ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="7cdc7-113">Var olan hiçbir `AppDomain`-bu askıya alma sırasında belirli geri aramalar.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="7cdc7-114">Böylece kodu pitching oluşabilir çalışma zamanı askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="7cdc7-115">Kod pitching yalnızca tam zamanında (JIT) derleyici etkin kodu pitching ile etkin olduğunda ensues.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="7cdc7-116">Kod pitching geri aramalar ortaya arasında `ICorProfilerCallback::RuntimeSuspendFinished` ve `ICorProfilerCallback::RuntimeResumeStarted` geri aramalar.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="7cdc7-117">**Not:** bu değer 2. 0'kullanılmaması CLR JIT işlevlerini .NET Framework sürüm 2.0, aralık değil.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="7cdc7-118">Böylece kapatmak, çalışma zamanı'askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="7cdc7-119">İşlemi tamamlamak için tüm iş parçacıklarını askıya alma gerekir.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="7cdc7-120">Çalışma zamanı işlemde hata ayıklamak için askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="7cdc7-121">Çöp toplama için hazırlamak için çalışma zamanı askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="7cdc7-122">Çalışma zamanı JIT yeniden derlenmek üzere askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cdc7-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7cdc7-123">Remarks</span></span>  
 <span data-ttu-id="7cdc7-124">Yönetilmeyen kodunda tüm çalışma zamanı iş parçacıklarının bunlar çalışma zamanı yeniden devam edene dek bu noktada bunlar da askıya alınacak çalışma zamanı yeniden girmeyi deneyin kadar çalışmaya devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="7cdc7-125">Bu durum, çalışma zamanı girin yeni iş parçacığı için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="7cdc7-126">Çalışma Zamanı Modülü içindeki tüm iş parçacıklarının kesilebilir kodda olmaları durumunda hemen askıya, ya da bunlar kesilebilir kod ulaştığında askıya istenir.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cdc7-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7cdc7-127">Requirements</span></span>  
 <span data-ttu-id="7cdc7-128">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cdc7-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cdc7-129">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7cdc7-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7cdc7-130">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cdc7-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cdc7-131">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cdc7-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cdc7-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7cdc7-132">See Also</span></span>  
 [<span data-ttu-id="7cdc7-133">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7cdc7-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
