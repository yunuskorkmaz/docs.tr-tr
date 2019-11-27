---
title: ICorProfilerCallback::JITInlining Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 62035d623d56f7521e0a599a13bc20778e3f18d1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449905"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="d8ed6-102">ICorProfilerCallback::JITInlining Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8ed6-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="d8ed6-103">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin başka bir işlevle satıra bir işlev eklemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="d8ed6-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8ed6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8ed6-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8ed6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8ed6-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="d8ed6-106">'ndaki `calleeId` işlevinin ekleneceği işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d8ed6-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="d8ed6-107">'ndaki Eklenecek işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="d8ed6-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="d8ed6-108">[out] ekleme işleminin oluşmasına izin vermek için `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="d8ed6-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8ed6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8ed6-109">Remarks</span></span>  
 <span data-ttu-id="d8ed6-110">Profil Oluşturucu, `calleeId` işlevinin `callerId` işlevine eklenmesini engellemek için `pfShouldInline` `false` ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="d8ed6-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="d8ed6-111">Ayrıca, profil oluşturucu, [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) numaralandırmanın COR_PRF_DISABLE_INLINING değerini kullanarak satır içi ekleme işlemini genel olarak devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="d8ed6-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="d8ed6-112">Satır içi yerleştirilen işlevler girme veya bırakma için olay oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="d8ed6-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="d8ed6-113">Bu nedenle, profil oluşturucunun doğru bir callgraph oluşturmak için `false` `pfShouldInline` ayarlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8ed6-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="d8ed6-114">Satır içi ekleme genellikle hızı arttığından ve eklenen metodun ayrı JıT derleme olaylarının sayısını azalttığından `pfShouldInline` `false` olarak ayarlanması performansı etkiler.</span><span class="sxs-lookup"><span data-stu-id="d8ed6-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8ed6-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8ed6-115">Requirements</span></span>  
 <span data-ttu-id="d8ed6-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8ed6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8ed6-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d8ed6-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8ed6-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d8ed6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8ed6-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8ed6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8ed6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8ed6-120">See also</span></span>

- [<span data-ttu-id="d8ed6-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8ed6-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
