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
ms.openlocfilehash: cda629b7a6560ca5d731cd88cffc2cffd3486d8a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866227"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="45659-102">ICorProfilerCallback::JITFunctionPitched Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45659-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="45659-103">Profiler öğesine, tam zamanında (JıT) derlenmiş bir işlevin bellekten kaldırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="45659-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45659-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45659-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45659-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45659-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="45659-106">'ndaki Kaldırılan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="45659-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45659-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45659-107">Remarks</span></span>  
 <span data-ttu-id="45659-108">Kaldırılan işlev çağrılırsa, işlev yeniden derlenmeye başlatıldığında profil Oluşturucu yeni JıT derleme olayları alır.</span><span class="sxs-lookup"><span data-stu-id="45659-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="45659-109">Şu anda, ortak dil çalışma zamanı (CLR) JıT derleyicisi, işlevleri bellekten kaldırmaz, bu nedenle bu geri çağırma Şu anda kullanılmıyor ve profil oluşturucu tarafından alınmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="45659-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="45659-110">`functionId` değeri, işlev yeniden derlenene kadar geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="45659-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="45659-111">İşlev yeniden derlenme sırasında aynı `functionId` değeri kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="45659-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45659-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45659-112">Requirements</span></span>  
 <span data-ttu-id="45659-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45659-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45659-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="45659-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45659-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="45659-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45659-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45659-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45659-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45659-117">See also</span></span>

- [<span data-ttu-id="45659-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45659-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
