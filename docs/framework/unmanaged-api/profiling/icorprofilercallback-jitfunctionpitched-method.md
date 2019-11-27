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
ms.openlocfilehash: 9bb3934be4a2f4de4a3a235a00522c801331e1eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448422"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="5bdd3-102">ICorProfilerCallback::JITFunctionPitched Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5bdd3-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="5bdd3-103">Profiler öğesine, tam zamanında (JıT) derlenmiş bir işlevin bellekten kaldırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bdd3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bdd3-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bdd3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5bdd3-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5bdd3-106">'ndaki Kaldırılan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bdd3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5bdd3-107">Remarks</span></span>  
 <span data-ttu-id="5bdd3-108">Kaldırılan işlev çağrılırsa, işlev yeniden derlenmeye başlatıldığında profil Oluşturucu yeni JıT derleme olayları alır.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="5bdd3-109">Şu anda, ortak dil çalışma zamanı (CLR) JıT derleyicisi, işlevleri bellekten kaldırmaz, bu nedenle bu geri çağırma Şu anda kullanılmıyor ve profil oluşturucu tarafından alınmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="5bdd3-110">`functionId` değeri, işlev yeniden derlenene kadar geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="5bdd3-111">İşlev yeniden derlenme sırasında aynı `functionId` değeri kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bdd3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5bdd3-112">Requirements</span></span>  
 <span data-ttu-id="5bdd3-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bdd3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bdd3-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5bdd3-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5bdd3-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5bdd3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bdd3-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bdd3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bdd3-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bdd3-117">See also</span></span>

- [<span data-ttu-id="5bdd3-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bdd3-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
