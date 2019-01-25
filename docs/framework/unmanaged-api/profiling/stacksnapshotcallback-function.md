---
title: StackSnapshotCallback İşlevi
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e73afa7ef33e12d6bc658c944c79ce1bc4f94f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572435"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="1b9e7-102">StackSnapshotCallback İşlevi</span><span class="sxs-lookup"><span data-stu-id="1b9e7-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="1b9e7-103">Profil Oluşturucu yönetilen her çerçeve ve her bir çalıştırmanın yönetilmeyen çerçeveler hakkında tarafından başlatılan bir yığın ilerlemesi sırasında bilgileri yığında sağlar [Icorprofilerınfo2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b9e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b9e7-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1b9e7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b9e7-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="1b9e7-106">[in] Bu değer sıfır ise, bu geri çağırma bir yönetilmeyen çerçeveler çalıştırma için olan; Aksi takdirde, yönetilen bir işlevin tanımlayıcısıdır ve bu geri çağırma için yönetilen bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="1b9e7-107">[in] Yerel kod yönerge işaretçisini çerçevesinde değeri.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="1b9e7-108">[in] A `COR_PRF_FRAME_INFO` yığın çerçevesi hakkında bilgi başvuran değeri.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="1b9e7-109">Bu değer yalnızca bu geri çağırma sırasında kullanım için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="1b9e7-110">[in] Boyutu `CONTEXT` tarafından başvurulan yapısını `context` parametresi.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="1b9e7-111">[in] Bir Win32 işaretçisi `CONTEXT` bu çerçevesi için CPU durumunu temsil eden yapısı.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="1b9e7-112">`context` Parametredir COR_PRF_SNAPSHOT_CONTEXT bayrağı yalnızca geçirilen geçerli `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="1b9e7-113">[in] Doğrudan gelen geçirilen istemci verilerini bir işaretçiye `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b9e7-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b9e7-114">Remarks</span></span>  
 <span data-ttu-id="1b9e7-115">`StackSnapshotCallback` İşlevi, profil oluşturucu yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="1b9e7-116">Gerçekleştirilen iş karmaşıklığını sınırlaması gerekir `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="1b9e7-117">Örneğin, kullanırken `ICorProfilerInfo2::DoStackSnapshot` zaman uyumsuz olarak hedef iş parçacığının kilitler tutabilir.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="1b9e7-118">Varsa içinde kod `StackSnapshotCallback` aynı kilitler gerektirir ardından bir kilitlenme.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="1b9e7-119">`ICorProfilerInfo2::DoStackSnapshot` Yöntem çağrılarını `StackSnapshotCallback` işlevi yönetilen çerçeve başına bir kere veya çalışma yönetilmeyen çerçeve başına bir kez.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="1b9e7-120">Varsa `StackSnapshotCallback` çağrılır yönetilmeyen çerçeveler çalıştırma için profil oluşturucu kayıt bağlam kullanabilir (tarafından başvurulan `context` parametresi) kendi yönetilmeyen yığın ilerlemesi gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="1b9e7-121">Bu durumda, Win32 `CONTEXT` yapısı yönetilmeyen çerçeveler yürütülmesi en yakın zamanda gönderilen çerçevesinde CPU durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="1b9e7-122">Olsa da Win32 `CONTEXT` yapısı tüm kayıtları için değerler içeriyorsa, yığın işaretçisi kaydı, çerçeve işaretçisi kaydı, yönerge işaretçisi kaydı ve (yani korunur) kalıcı değerlerine yalnızca yararlanmalıdır tamsayı kaydeder.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b9e7-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b9e7-123">Requirements</span></span>  
 <span data-ttu-id="1b9e7-124">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b9e7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b9e7-125">**Üst bilgi:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="1b9e7-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1b9e7-126">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b9e7-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b9e7-127">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b9e7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b9e7-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b9e7-128">See also</span></span>
- [<span data-ttu-id="1b9e7-129">DoStackSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b9e7-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="1b9e7-130">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1b9e7-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
