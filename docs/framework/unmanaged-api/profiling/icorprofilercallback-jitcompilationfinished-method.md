---
title: ICorProfilerCallback::JITCompilationFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dbf447e1325b4acaa26c9bb16d7d1a736eb20a29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453557"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="62cc7-102">ICorProfilerCallback::JITCompilationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62cc7-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="62cc7-103">Profil Oluşturucu tam zamanında (JIT) derleyici bir işlev derleme tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="62cc7-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62cc7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="62cc7-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62cc7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="62cc7-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="62cc7-106">[in] Derlenen işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="62cc7-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="62cc7-107">[in] Derleme başarılı olup olmadığını belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="62cc7-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="62cc7-108">[in] Profil Oluşturucu için engelleme olup olmadığını belirten bir değer çalışma zamanının işlemi etkiler.</span><span class="sxs-lookup"><span data-stu-id="62cc7-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="62cc7-109">Değer `true` engelleme bu geri aramasından; döndürülecek çağıran iş parçacığı beklemek çalışma zamanı yaratabilir, aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="62cc7-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="62cc7-110">Değerini rağmen `true` çalışma zamanı zarar değil, profil oluşturma sonuçlarını eğme.</span><span class="sxs-lookup"><span data-stu-id="62cc7-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62cc7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="62cc7-111">Requirements</span></span>  
 <span data-ttu-id="62cc7-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62cc7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62cc7-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="62cc7-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="62cc7-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62cc7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62cc7-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62cc7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62cc7-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="62cc7-116">See Also</span></span>  
 [<span data-ttu-id="62cc7-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="62cc7-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="62cc7-118">JITCompilationStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="62cc7-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
