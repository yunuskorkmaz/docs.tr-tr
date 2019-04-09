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
ms.openlocfilehash: c8aa46e869d50fc7aa65c1d4244ad4ff71657bad
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186400"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="2fb88-102">ICorProfilerCallback::JITFunctionPitched Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2fb88-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="2fb88-103">Profil Oluşturucu bildirir, just-in-time (JIT) yapılmış bir işlev-derlenmiş bellekten kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="2fb88-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fb88-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2fb88-104">Syntax</span></span>  
  
```  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fb88-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2fb88-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="2fb88-106">[in] Kaldırılan işlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="2fb88-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fb88-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fb88-107">Remarks</span></span>  
 <span data-ttu-id="2fb88-108">Kaldırılan işlev çağrılırsa, profil oluşturucu işlevi yeniden derlendiğinde yeni JIT derleme olaylarını alacaksınız.</span><span class="sxs-lookup"><span data-stu-id="2fb88-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="2fb88-109">Şu anda, ortak dil çalışma zamanı (CLR) JIT derleyicisi bu geri arama şu anda kullanılmaz ve Profil Oluşturucu tarafından alınmaz bellekten işlevleri kaldırmaz.</span><span class="sxs-lookup"><span data-stu-id="2fb88-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="2fb88-110">Değerini `functionId` işlevi yeniden derlenen kadar geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="2fb88-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="2fb88-111">İşlev derlendiğinde, aynı `functionId` değeri kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="2fb88-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fb88-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2fb88-112">Requirements</span></span>  
 <span data-ttu-id="2fb88-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fb88-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fb88-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2fb88-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2fb88-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fb88-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2fb88-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2fb88-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2fb88-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fb88-117">See also</span></span>

- [<span data-ttu-id="2fb88-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2fb88-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
