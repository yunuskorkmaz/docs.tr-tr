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
ms.openlocfilehash: c0cec9eb7bb8bbc94b255152a9b4d79108bdd1b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427072"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="66913-102">StackSnapshotCallback İşlevi</span><span class="sxs-lookup"><span data-stu-id="66913-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="66913-103">, Profil oluşturucuyu her yönetilen çerçeve ve yığın üzerinde her yönetilmeyen çerçeve, [ICorProfilerInfo2::D oStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yöntemi tarafından başlatılan bir yığın ilerleme durumuyla ilgili bilgilerle birlikte sağlar.</span><span class="sxs-lookup"><span data-stu-id="66913-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66913-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="66913-104">Syntax</span></span>  
  
```cpp  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66913-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="66913-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="66913-106">'ndaki Bu değer sıfırsa, bu geri çağırma, yönetilmeyen çerçevelerin çalıştırılması içindir; Aksi takdirde, yönetilen bir işlevin tanımlayıcısıdır ve bu geri çağırma yönetilen bir çerçeve içindir.</span><span class="sxs-lookup"><span data-stu-id="66913-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="66913-107">'ndaki Çerçevede yerel kod yönerge işaretçisinin değeri.</span><span class="sxs-lookup"><span data-stu-id="66913-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="66913-108">'ndaki Yığın çerçevesiyle ilgili bilgilere başvuran bir `COR_PRF_FRAME_INFO` değeri.</span><span class="sxs-lookup"><span data-stu-id="66913-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="66913-109">Bu değer yalnızca bu geri çağırma sırasında kullanım için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="66913-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="66913-110">'ndaki `context` parametresi tarafından başvurulan `CONTEXT` yapısının boyutu.</span><span class="sxs-lookup"><span data-stu-id="66913-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="66913-111">'ndaki Bu çerçevenin CPU durumunu temsil eden bir Win32 `CONTEXT` yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="66913-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="66913-112">`context` parametresi yalnızca COR_PRF_SNAPSHOT_CONTEXT bayrağı `ICorProfilerInfo2::DoStackSnapshot`geçirildiğinde geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="66913-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="66913-113">'ndaki `ICorProfilerInfo2::DoStackSnapshot`'den doğrudan geçirilen istemci verilerine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="66913-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66913-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="66913-114">Remarks</span></span>  
 <span data-ttu-id="66913-115">`StackSnapshotCallback` işlevi, profil oluşturucu yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="66913-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="66913-116">`StackSnapshotCallback`yapılan çalışmanın karmaşıklığını sınırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="66913-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="66913-117">Örneğin, zaman uyumsuz bir şekilde `ICorProfilerInfo2::DoStackSnapshot` kullanırken, hedef iş parçacığı kilitleri tutuyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="66913-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="66913-118">`StackSnapshotCallback` içindeki kod aynı kilitleri gerektiriyorsa, bir kilitlenme olabilir.</span><span class="sxs-lookup"><span data-stu-id="66913-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="66913-119">`ICorProfilerInfo2::DoStackSnapshot` yöntemi, yönetilen çerçeveye veya yönetilmeyen çerçevelerin her biri için bir kez `StackSnapshotCallback` işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="66913-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="66913-120">Yönetilmeyen çerçevelerin bir çalıştırması için `StackSnapshotCallback` çağrılırsa, profil oluşturucu kendi yönetilmeyen yığın ilerlemesini gerçekleştirmek için Register bağlamını (`context` parametresi tarafından başvurulan) kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="66913-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="66913-121">Bu durumda, Win32 `CONTEXT` yapısı yönetilmeyen çerçevelerin çalıştırılmasındaki en son gönderilen çerçevenin CPU durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="66913-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="66913-122">Win32 `CONTEXT` yapısı tüm yazmaçların değerlerini içerse de, yalnızca yığın işaretçisi yazmacı, çerçeve işaretçisi kaydı, yönerge işaretçisi kaydı ve kalıcı (yani korunan) tamsayı Yazmaçları değerlerini de bilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="66913-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66913-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="66913-123">Requirements</span></span>  
 <span data-ttu-id="66913-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66913-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66913-125">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="66913-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="66913-126">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="66913-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66913-127">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66913-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66913-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="66913-128">See also</span></span>

- [<span data-ttu-id="66913-129">DoStackSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="66913-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="66913-130">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="66913-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
