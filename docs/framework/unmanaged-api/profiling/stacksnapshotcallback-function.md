---
title: "StackSnapshotCallback İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackSnapshotCallback
api_location: mscorwks.dll
api_type: COM
f1_keywords: StackSnapshotCallback
helpviewer_keywords: StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 92f7071ebcf7664b3622c180b9f1bade50909cea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="48b48-102">StackSnapshotCallback İşlevi</span><span class="sxs-lookup"><span data-stu-id="48b48-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="48b48-103">Profil Oluşturucu bilgiler her yönetilen çerçeve ve her çalışma yönetilmeyen çerçeve yığında tarafından başlatılan bir yığın ilerlemesi sırasında verir [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="48b48-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48b48-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48b48-104">Syntax</span></span>  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48b48-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48b48-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="48b48-106">[in] Bu değer sıfır ise, bu geri çağırma bir yönetilmeyen çerçeveler çalıştırması için yeterli; Aksi takdirde, yönetilen bir işlevin tanımlayıcısıdır ve bu geri çağırma için yönetilen bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="48b48-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="48b48-107">[in] Yerel kod yönerge işaretçisi çerçevesinde değeri.</span><span class="sxs-lookup"><span data-stu-id="48b48-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="48b48-108">[in] A `COR_PRF_FRAME_INFO` yığın çerçevesi hakkında bilgi başvuran değeri.</span><span class="sxs-lookup"><span data-stu-id="48b48-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="48b48-109">Bu değer yalnızca bu geri çağırma sırasında kullanım için geçerli olur.</span><span class="sxs-lookup"><span data-stu-id="48b48-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="48b48-110">[in] Boyutunu `CONTEXT` tarafından başvurulan yapısı `context` parametresi.</span><span class="sxs-lookup"><span data-stu-id="48b48-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="48b48-111">[in] Bir işaretçi bir Win32 `CONTEXT` yapısı bu çerçeve CPU durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="48b48-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="48b48-112">`context` Parametredir COR_PRF_SNAPSHOT_CONTEXT bayrağı yalnızca geçildi geçerli `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="48b48-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="48b48-113">[in] Doğrudan gelen geçirilir istemci verilerini gösteren bir işaretçi `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="48b48-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48b48-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48b48-114">Remarks</span></span>  
 <span data-ttu-id="48b48-115">`StackSnapshotCallback` İşlevi profil oluşturucu yazıcı tarafından gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="48b48-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="48b48-116">İşlerini karmaşıklığını sınırlamak `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="48b48-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="48b48-117">Örneğin, kullanırken `ICorProfilerInfo2::DoStackSnapshot` zaman uyumsuz bir şekilde hedef iş parçacığı kilitleri tutabilir.</span><span class="sxs-lookup"><span data-stu-id="48b48-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="48b48-118">Varsa içindeki kod `StackSnapshotCallback` aynı kilitler gerektirir kilitlenme olun.</span><span class="sxs-lookup"><span data-stu-id="48b48-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="48b48-119">`ICorProfilerInfo2::DoStackSnapshot` Yöntem çağrılarını `StackSnapshotCallback` yönetilen çerçeve başına bir kez veya bir kez çalıştır yönetilmeyen çerçeve başına işlevi.</span><span class="sxs-lookup"><span data-stu-id="48b48-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="48b48-120">Varsa `StackSnapshotCallback` çağrılır yönetilmeyen çerçeveler çalıştırma için profil oluşturucu kayıt bağlam kullanabilir (tarafından başvurulan `context` parametresi) kendi yönetilmeyen yığın ilerlemesi gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="48b48-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="48b48-121">Bu durumda, Win32 `CONTEXT` yapısı yönetilmeyen çerçeveler Çalıştır en yakın zamanda basılmış çerçevesinde CPU ili temsil eder.</span><span class="sxs-lookup"><span data-stu-id="48b48-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="48b48-122">Ancak Win32 `CONTEXT` yapısı tüm kayıtları için değerleri içerir, yığın işaretçi kaydı, çerçeve işaretçisi kaydı, yönerge işaretçisi kaydı ve (yani korundu) kalıcı değerlerine yalnızca yararlanmalıdır tamsayı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="48b48-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48b48-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48b48-123">Requirements</span></span>  
 <span data-ttu-id="48b48-124">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48b48-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48b48-125">**Başlık:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="48b48-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="48b48-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48b48-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48b48-127">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48b48-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48b48-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="48b48-128">See Also</span></span>  
 [<span data-ttu-id="48b48-129">DoStackSnapshot yöntemi</span><span class="sxs-lookup"><span data-stu-id="48b48-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="48b48-130">Profil oluşturma genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="48b48-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
