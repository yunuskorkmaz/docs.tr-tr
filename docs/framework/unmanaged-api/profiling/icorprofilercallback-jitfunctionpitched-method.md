---
title: "ICorProfilerCallback::JITFunctionPitched Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITFunctionPitched
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a5b14bc5735c83897e818ca2038455e0c6510e27
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="2a8b3-102">ICorProfilerCallback::JITFunctionPitched Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a8b3-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="2a8b3-103">Profil Oluşturucu bildirir, tam zamanında (JIT) boyunca işlevi-derlenmiş bellekten kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="2a8b3-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a8b3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a8b3-104">Syntax</span></span>  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2a8b3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a8b3-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="2a8b3-106">[in] Kaldırıldı işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="2a8b3-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a8b3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a8b3-107">Remarks</span></span>  
 <span data-ttu-id="2a8b3-108">Kaldırılan işlevi çağrıldıysa profil oluşturucu işlevi derlenmiştir yeni JIT derleme olayları alır.</span><span class="sxs-lookup"><span data-stu-id="2a8b3-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="2a8b3-109">Şu anda, böylece bu geri çağırma şu anda kullanılmaz ve Profil Oluşturucu tarafından alınan olmayan ortak dil çalışma zamanı (CLR) JIT Derleyici işlevleri bellekten kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="2a8b3-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="2a8b3-110">Değeri `functionId` işlevi derlenmiştir kadar geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="2a8b3-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="2a8b3-111">İşlev derlenmiştir, aynı `functionId` değeri kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="2a8b3-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a8b3-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a8b3-112">Requirements</span></span>  
 <span data-ttu-id="2a8b3-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a8b3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a8b3-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2a8b3-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a8b3-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a8b3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a8b3-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a8b3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a8b3-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a8b3-117">See Also</span></span>  
 [<span data-ttu-id="2a8b3-118">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a8b3-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
