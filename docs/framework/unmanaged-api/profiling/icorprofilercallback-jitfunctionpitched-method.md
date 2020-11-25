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
ms.openlocfilehash: 51fec26837b3c7f0a0328a7b64ff4a02148283da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725522"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="0502a-102">ICorProfilerCallback::JITFunctionPitched Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0502a-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>

<span data-ttu-id="0502a-103">Profiler öğesine, tam zamanında (JıT) derlenmiş bir işlevin bellekten kaldırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="0502a-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0502a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0502a-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0502a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0502a-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="0502a-106">'ndaki Kaldırılan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0502a-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0502a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0502a-107">Remarks</span></span>  

 <span data-ttu-id="0502a-108">Kaldırılan işlev çağrılırsa, işlev yeniden derlenmeye başlatıldığında profil Oluşturucu yeni JıT derleme olayları alır.</span><span class="sxs-lookup"><span data-stu-id="0502a-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="0502a-109">Şu anda, ortak dil çalışma zamanı (CLR) JıT derleyicisi, işlevleri bellekten kaldırmaz, bu nedenle bu geri çağırma Şu anda kullanılmıyor ve profil oluşturucu tarafından alınmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="0502a-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="0502a-110">Değeri, `functionId` işlev yeniden derlenene kadar geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="0502a-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="0502a-111">İşlev yeniden `functionId` derlenme sırasında aynı değer kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="0502a-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0502a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0502a-112">Requirements</span></span>  

 <span data-ttu-id="0502a-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0502a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0502a-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0502a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0502a-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0502a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0502a-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0502a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0502a-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0502a-117">See also</span></span>

- [<span data-ttu-id="0502a-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0502a-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
