---
description: ': ICorProfilerCallback:: Jınkıtıl yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 2bd6c48180b9484ef90b6afb505c8171aff57aa4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705648"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="9d2be-103">ICorProfilerCallback::JITInlining Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d2be-103">ICorProfilerCallback::JITInlining Method</span></span>

<span data-ttu-id="9d2be-104">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin başka bir işlevle satıra bir işlev eklemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="9d2be-104">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d2be-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d2be-105">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d2be-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d2be-106">Parameters</span></span>  

 `callerId`  
 <span data-ttu-id="9d2be-107">'ndaki `calleeId` İşlevin ekleneceği IŞLEVIN kimliği.</span><span class="sxs-lookup"><span data-stu-id="9d2be-107">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="9d2be-108">'ndaki Eklenecek işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9d2be-108">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="9d2be-109">[out] `true` ekleme işleminin oluşmasına izin vermek için; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="9d2be-109">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d2be-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9d2be-110">Remarks</span></span>  

 <span data-ttu-id="9d2be-111">Profil Oluşturucu `pfShouldInline` `false` işlevin işleve eklenmesini engellemek için olarak ayarlanabilir `calleeId` `callerId` .</span><span class="sxs-lookup"><span data-stu-id="9d2be-111">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="9d2be-112">Ayrıca, profil oluşturucu, [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmanın COR_PRF_DISABLE_INLINING değerini kullanarak satır içi ekleme işlemini genel olarak devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="9d2be-112">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="9d2be-113">Satır içi yerleştirilen işlevler girme veya bırakma için olay oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="9d2be-113">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="9d2be-114">Bu nedenle, profil oluşturucunun `pfShouldInline` `false` doğru bir callgraph oluşturmak için olarak ayarlanmış olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9d2be-114">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="9d2be-115">`pfShouldInline`İçin ayarı `false` , satır içi ekleme genellikle hızı arttığından ve eklenen METODUN ayrı JIT derleme olaylarının sayısını azalttığından, performansı etkileyecek şekilde değişir.</span><span class="sxs-lookup"><span data-stu-id="9d2be-115">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d2be-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d2be-116">Requirements</span></span>  

 <span data-ttu-id="9d2be-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d2be-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d2be-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9d2be-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d2be-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9d2be-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d2be-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d2be-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d2be-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d2be-121">See also</span></span>

- [<span data-ttu-id="9d2be-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d2be-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
