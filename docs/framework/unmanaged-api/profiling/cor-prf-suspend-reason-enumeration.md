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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21533b5173bcd91d0c944fbde4eafc9817de8315
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598993"
---
# <a name="corprfsuspendreason-enumeration"></a><span data-ttu-id="64eb4-102">COR_PRF_SUSPEND_REASON Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="64eb4-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="64eb4-103">Çalışma zamanı askıya alındığından nedenini gösterir.</span><span class="sxs-lookup"><span data-stu-id="64eb4-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64eb4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64eb4-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="64eb4-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="64eb4-105">Members</span></span>  
  
|<span data-ttu-id="64eb4-106">Üye</span><span class="sxs-lookup"><span data-stu-id="64eb4-106">Member</span></span>|<span data-ttu-id="64eb4-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="64eb4-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="64eb4-108">Çalışma zamanı belirlenemeyen bir nedenden dolayı askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="64eb4-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="64eb4-109">Çalışma zamanı, çöp toplama isteğine hizmet askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="64eb4-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="64eb4-110">Çöp toplama ile ilgili geri çağırmalar arasında oluşan [Icorprofilercallback::runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) ve [Icorprofilercallback::runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) geri çağırmalar.</span><span class="sxs-lookup"><span data-stu-id="64eb4-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="64eb4-111">Çalışma zamanı askıya böylece bir `AppDomain` kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="64eb4-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="64eb4-112">Çalışma zamanı askıya alındı, ancak çalışma zamanının hangi iş parçacığı bulunan belirleyecek `AppDomain` diğer bir deyişle kapatmalı ve bunlar devam edince iptal etmek için bunları ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="64eb4-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="64eb4-113">Var olan hiçbir `AppDomain`-bu askıya alma sırasında belirli geri çağırmalar.</span><span class="sxs-lookup"><span data-stu-id="64eb4-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="64eb4-114">Kod pitching gerçekleştirilmesi, çalışma zamanı askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="64eb4-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="64eb4-115">Kod pitching yalnızca just-ın-time (JIT) derleyici etkin kod pitching ile etkin olduğunda ensues.</span><span class="sxs-lookup"><span data-stu-id="64eb4-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="64eb4-116">Pitching geri çağırmaları ortaya arasında kod `ICorProfilerCallback::RuntimeSuspendFinished` ve `ICorProfilerCallback::RuntimeResumeStarted` geri çağırmalar.</span><span class="sxs-lookup"><span data-stu-id="64eb4-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="64eb4-117">**Not:**  Bu değer, 2. 0'kullanılmaması CLR JIT işlevleri .NET Framework sürüm 2.0, aralık değil.</span><span class="sxs-lookup"><span data-stu-id="64eb4-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="64eb4-118">Böylece kapanabilir çalışma zamanı askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="64eb4-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="64eb4-119">İşlemi tamamlamak için tüm iş parçacıkları askıya gerekir.</span><span class="sxs-lookup"><span data-stu-id="64eb4-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="64eb4-120">Çalışma zamanı, işlemdeki hata ayıklama için askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="64eb4-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="64eb4-121">Çalışma zamanı, çöp toplama işlemi için hazırlamak üzere askıya alınır.</span><span class="sxs-lookup"><span data-stu-id="64eb4-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="64eb4-122">Çalışma zamanı JIT yeniden derlemesi için askıya alındı.</span><span class="sxs-lookup"><span data-stu-id="64eb4-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64eb4-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="64eb4-123">Remarks</span></span>  
 <span data-ttu-id="64eb4-124">Yönetilmeyen kodda olan tüm çalışma zamanı iş parçacığı, çalışma zamanı yeniden devam edene dek bu noktada, ayrıca askıya alınır ve çalışma zamanının yeniden girmeyi deneyin kadar çalışmaya devam etmesine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="64eb4-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="64eb4-125">Bu, çalışma zamanı girin yeni iş parçacıkları için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="64eb4-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="64eb4-126">Çalışma zamanı içinde tüm iş parçacıkları kesilebilir kodda olmaları durumunda hemen askıya veya kesilebilir kod ulaşmadan zaman askıya istenir.</span><span class="sxs-lookup"><span data-stu-id="64eb4-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64eb4-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64eb4-127">Requirements</span></span>  
 <span data-ttu-id="64eb4-128">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64eb4-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64eb4-129">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64eb4-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64eb4-130">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64eb4-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64eb4-131">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64eb4-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64eb4-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64eb4-132">See also</span></span>

- [<span data-ttu-id="64eb4-133">Profil Oluşturma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="64eb4-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
