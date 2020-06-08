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
ms.openlocfilehash: 2715a5b6b03a5ad33a6f18fb736fce3911bfbef0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500032"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="2d755-102">ICorProfilerCallback::JITFunctionPitched Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d755-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="2d755-103">Profiler öğesine, tam zamanında (JıT) derlenmiş bir işlevin bellekten kaldırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="2d755-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d755-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2d755-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d755-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d755-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="2d755-106">'ndaki Kaldırılan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2d755-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d755-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d755-107">Remarks</span></span>  
 <span data-ttu-id="2d755-108">Kaldırılan işlev çağrılırsa, işlev yeniden derlenmeye başlatıldığında profil Oluşturucu yeni JıT derleme olayları alır.</span><span class="sxs-lookup"><span data-stu-id="2d755-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="2d755-109">Şu anda, ortak dil çalışma zamanı (CLR) JıT derleyicisi, işlevleri bellekten kaldırmaz, bu nedenle bu geri çağırma Şu anda kullanılmıyor ve profil oluşturucu tarafından alınmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="2d755-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="2d755-110">Değeri, `functionId` işlev yeniden derlenene kadar geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="2d755-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="2d755-111">İşlev yeniden `functionId` derlenme sırasında aynı değer kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="2d755-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d755-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d755-112">Requirements</span></span>  
 <span data-ttu-id="2d755-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d755-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d755-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2d755-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2d755-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2d755-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d755-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d755-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d755-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d755-117">See also</span></span>

- [<span data-ttu-id="2d755-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d755-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
