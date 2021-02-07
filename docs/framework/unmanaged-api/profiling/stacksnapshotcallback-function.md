---
description: 'Daha fazla bilgi edinin: StackSnapshotCallback Işlevi'
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
ms.openlocfilehash: a49588bc3277956acad612afd0fcab3fa7edffbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736862"
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="14968-103">StackSnapshotCallback İşlevi</span><span class="sxs-lookup"><span data-stu-id="14968-103">StackSnapshotCallback Function</span></span>

<span data-ttu-id="14968-104">, Profil oluşturucuyu her yönetilen çerçeve ve yığın üzerinde her yönetilmeyen çerçeve, [ICorProfilerInfo2::D oStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) yöntemi tarafından başlatılan bir yığın ilerleme durumuyla ilgili bilgilerle birlikte sağlar.</span><span class="sxs-lookup"><span data-stu-id="14968-104">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14968-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14968-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="14968-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14968-106">Parameters</span></span>  

 `funcId`  
 <span data-ttu-id="14968-107">'ndaki Bu değer sıfırsa, bu geri çağırma, yönetilmeyen çerçevelerin çalıştırılması içindir; Aksi takdirde, yönetilen bir işlevin tanımlayıcısıdır ve bu geri çağırma yönetilen bir çerçeve içindir.</span><span class="sxs-lookup"><span data-stu-id="14968-107">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="14968-108">'ndaki Çerçevede yerel kod yönerge işaretçisinin değeri.</span><span class="sxs-lookup"><span data-stu-id="14968-108">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="14968-109">'ndaki `COR_PRF_FRAME_INFO` Yığın çerçevesiyle ilgili bilgilere başvuran bir değer.</span><span class="sxs-lookup"><span data-stu-id="14968-109">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="14968-110">Bu değer yalnızca bu geri çağırma sırasında kullanım için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="14968-110">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="14968-111">'ndaki `CONTEXT` Parametrenin başvurduğu yapının boyutu `context` .</span><span class="sxs-lookup"><span data-stu-id="14968-111">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="14968-112">'ndaki `CONTEXT` Bu ÇERÇEVENIN CPU durumunu temsil eden Win32 yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="14968-112">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="14968-113">`context`Parametresi yalnızca COR_PRF_SNAPSHOT_CONTEXT bayrağının geçirilmesi durumunda geçerlidir `ICorProfilerInfo2::DoStackSnapshot` .</span><span class="sxs-lookup"><span data-stu-id="14968-113">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="14968-114">'ndaki İstemci verilerine yönelik bir işaretçi, ' den doğrudan geçirilir `ICorProfilerInfo2::DoStackSnapshot` .</span><span class="sxs-lookup"><span data-stu-id="14968-114">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14968-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="14968-115">Remarks</span></span>  

 <span data-ttu-id="14968-116">`StackSnapshotCallback`İşlev, profil oluşturucu yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="14968-116">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="14968-117">' De yapılan çalışmanın karmaşıklığını sınırlamanız gerekir `StackSnapshotCallback` .</span><span class="sxs-lookup"><span data-stu-id="14968-117">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="14968-118">Örneğin, `ICorProfilerInfo2::DoStackSnapshot` zaman uyumsuz bir şekilde kullanırken, hedef iş parçacığı kilitleri tutuyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="14968-118">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="14968-119">İçindeki kod `StackSnapshotCallback` aynı kilitleri gerektiriyorsa, bir kilitlenme olabilir.</span><span class="sxs-lookup"><span data-stu-id="14968-119">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="14968-120">`ICorProfilerInfo2::DoStackSnapshot`Yöntemi `StackSnapshotCallback` yönetilen çerçeveye göre veya yönetilmeyen çerçevelerin her biri için bir kez işlevini çağırır.</span><span class="sxs-lookup"><span data-stu-id="14968-120">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="14968-121">`StackSnapshotCallback`Yönetilmeyen çerçevelerin bir çalıştırması için çağrılırsa, profil oluşturucu `context` kendi yönetilmeyen yığın yürüme işlemini gerçekleştirmek için YAZMAÇ bağlamını (parametresi tarafından başvurulan) kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="14968-121">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="14968-122">Bu durumda, Win32 `CONTEXT` yapısı yönetilmeyen çerçevelerin çalıştırılmasındaki en son gönderilen çerçeveye AIT CPU durumunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="14968-122">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="14968-123">Win32 `CONTEXT` yapısı tüm yazmaçların değerlerini içerse de, yalnızca yığın işaretçisi yazmacı, çerçeve işaretçisi kaydı, yönerge işaretçisi kaydı ve kalıcı (yani korunan) tamsayı Yazmaçları değerlerini de bilmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="14968-123">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14968-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14968-124">Requirements</span></span>  

 <span data-ttu-id="14968-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14968-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14968-126">**Üst bilgi:** CorProf. IDL</span><span class="sxs-lookup"><span data-stu-id="14968-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="14968-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="14968-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14968-128">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14968-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14968-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14968-129">See also</span></span>

- [<span data-ttu-id="14968-130">DoStackSnapshot Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14968-130">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="14968-131">Profil Oluşturma Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="14968-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
