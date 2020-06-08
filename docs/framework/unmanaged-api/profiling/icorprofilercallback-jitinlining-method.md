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
ms.openlocfilehash: 13ce44c9c7a04b870278bc8926dd9fe5daf10bc3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500019"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="90f47-102">ICorProfilerCallback::JITInlining Yöntemi</span><span class="sxs-lookup"><span data-stu-id="90f47-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="90f47-103">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin başka bir işlevle satıra bir işlev eklemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="90f47-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90f47-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="90f47-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90f47-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="90f47-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="90f47-106">'ndaki `calleeId`İşlevin ekleneceği IŞLEVIN kimliği.</span><span class="sxs-lookup"><span data-stu-id="90f47-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="90f47-107">'ndaki Eklenecek işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="90f47-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="90f47-108">[out] `true` ekleme işleminin oluşmasına izin vermek için; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="90f47-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90f47-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90f47-109">Remarks</span></span>  
 <span data-ttu-id="90f47-110">Profil Oluşturucu `pfShouldInline` `false` işlevin işleve eklenmesini engellemek için olarak ayarlanabilir `calleeId` `callerId` .</span><span class="sxs-lookup"><span data-stu-id="90f47-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="90f47-111">Ayrıca, profil oluşturucu, [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmanın COR_PRF_DISABLE_INLINING değerini kullanarak satır içi ekleme işlemini genel olarak devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="90f47-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="90f47-112">Satır içi yerleştirilen işlevler girme veya bırakma için olay oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="90f47-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="90f47-113">Bu nedenle, profil oluşturucunun `pfShouldInline` `false` doğru bir callgraph oluşturmak için olarak ayarlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="90f47-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="90f47-114">`pfShouldInline`İçin ayarı `false` , satır içi ekleme genellikle hızı arttığından ve eklenen METODUN ayrı JIT derleme olaylarının sayısını azalttığından, performansı etkileyecek şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="90f47-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90f47-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90f47-115">Requirements</span></span>  
 <span data-ttu-id="90f47-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90f47-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90f47-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="90f47-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90f47-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="90f47-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90f47-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90f47-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f47-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90f47-120">See also</span></span>

- [<span data-ttu-id="90f47-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="90f47-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
