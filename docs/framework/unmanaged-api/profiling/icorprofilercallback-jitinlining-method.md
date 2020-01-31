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
ms.openlocfilehash: 3e13b17fb03530730a78f6889309f1993419574b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866223"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="98cc8-102">ICorProfilerCallback::JITInlining Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98cc8-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="98cc8-103">Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin başka bir işlevle satıra bir işlev eklemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="98cc8-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98cc8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98cc8-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98cc8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98cc8-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="98cc8-106">'ndaki `calleeId` işlevinin ekleneceği işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="98cc8-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="98cc8-107">'ndaki Eklenecek işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="98cc8-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="98cc8-108">[out] ekleme işleminin oluşmasına izin vermek için `true`; Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="98cc8-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98cc8-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98cc8-109">Remarks</span></span>  
 <span data-ttu-id="98cc8-110">Profil Oluşturucu, `calleeId` işlevinin `callerId` işlevine eklenmesini engellemek için `pfShouldInline` `false` ayarlayabilir.</span><span class="sxs-lookup"><span data-stu-id="98cc8-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="98cc8-111">Ayrıca, profil oluşturucu, [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) numaralandırmanın COR_PRF_DISABLE_INLINING değerini kullanarak satır içi ekleme işlemini genel olarak devre dışı bırakabilir.</span><span class="sxs-lookup"><span data-stu-id="98cc8-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="98cc8-112">Satır içi yerleştirilen işlevler girme veya bırakma için olay oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="98cc8-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="98cc8-113">Bu nedenle, profil oluşturucunun doğru bir callgraph oluşturmak için `false` `pfShouldInline` ayarlaması gerekir.</span><span class="sxs-lookup"><span data-stu-id="98cc8-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="98cc8-114">Satır içi ekleme genellikle hızı arttığından ve eklenen metodun ayrı JıT derleme olaylarının sayısını azalttığından `pfShouldInline` `false` olarak ayarlanması performansı etkiler.</span><span class="sxs-lookup"><span data-stu-id="98cc8-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98cc8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98cc8-115">Requirements</span></span>  
 <span data-ttu-id="98cc8-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98cc8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98cc8-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="98cc8-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="98cc8-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="98cc8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98cc8-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98cc8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98cc8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98cc8-120">See also</span></span>

- [<span data-ttu-id="98cc8-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98cc8-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
