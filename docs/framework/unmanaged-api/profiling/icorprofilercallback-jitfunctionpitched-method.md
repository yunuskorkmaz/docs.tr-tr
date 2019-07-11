---
title: ICorProfilerCallback::JITFunctionPitched Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71df3bc707099cbad06742d964881ee629216b69
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782811"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="55049-102">ICorProfilerCallback::JITFunctionPitched Yöntemi</span><span class="sxs-lookup"><span data-stu-id="55049-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="55049-103">Profil Oluşturucu bildirir, just-in-time (JIT) yapılmış bir işlev-derlenmiş bellekten kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="55049-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55049-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55049-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55049-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="55049-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="55049-106">[in] Kaldırılan işlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="55049-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55049-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="55049-107">Remarks</span></span>  
 <span data-ttu-id="55049-108">Kaldırılan işlev çağrılırsa, profil oluşturucu işlevi yeniden derlendiğinde yeni JIT derleme olaylarını alacaksınız.</span><span class="sxs-lookup"><span data-stu-id="55049-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="55049-109">Şu anda, ortak dil çalışma zamanı (CLR) JIT derleyicisi bu geri arama şu anda kullanılmaz ve Profil Oluşturucu tarafından alınmaz bellekten işlevleri kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="55049-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="55049-110">Değerini `functionId` işlevi yeniden derlenen kadar geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="55049-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="55049-111">İşlev derlendiğinde, aynı `functionId` değeri kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="55049-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55049-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="55049-112">Requirements</span></span>  
 <span data-ttu-id="55049-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55049-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55049-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55049-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="55049-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55049-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55049-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55049-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55049-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55049-117">See also</span></span>

- [<span data-ttu-id="55049-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="55049-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
