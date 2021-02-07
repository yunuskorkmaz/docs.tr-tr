---
description: ': ICorProfilerCallback:: Jfunctionlintiz yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 11729de2188fe2f2cec7ec16ff7a5d1928cbd75d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705726"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="fa159-103">ICorProfilerCallback::JITFunctionPitched Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa159-103">ICorProfilerCallback::JITFunctionPitched Method</span></span>

<span data-ttu-id="fa159-104">Profiler öğesine, tam zamanında (JıT) derlenmiş bir işlevin bellekten kaldırıldığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="fa159-104">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa159-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa159-105">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa159-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa159-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="fa159-107">'ndaki Kaldırılan işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="fa159-107">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa159-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa159-108">Remarks</span></span>  

 <span data-ttu-id="fa159-109">Kaldırılan işlev çağrılırsa, işlev yeniden derlenmeye başlatıldığında profil Oluşturucu yeni JıT derleme olayları alır.</span><span class="sxs-lookup"><span data-stu-id="fa159-109">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="fa159-110">Şu anda, ortak dil çalışma zamanı (CLR) JıT derleyicisi, işlevleri bellekten kaldırmaz, bu nedenle bu geri çağırma Şu anda kullanılmıyor ve profil oluşturucu tarafından alınmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="fa159-110">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="fa159-111">Değeri, `functionId` işlev yeniden derlenene kadar geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="fa159-111">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="fa159-112">İşlev yeniden `functionId` derlenme sırasında aynı değer kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="fa159-112">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa159-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa159-113">Requirements</span></span>  

 <span data-ttu-id="fa159-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa159-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa159-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fa159-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa159-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fa159-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa159-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa159-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa159-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa159-118">See also</span></span>

- [<span data-ttu-id="fa159-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa159-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
