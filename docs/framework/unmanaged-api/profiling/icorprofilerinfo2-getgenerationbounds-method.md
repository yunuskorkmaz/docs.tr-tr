---
title: ICorProfilerInfo2::GetGenerationBounds Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 760c2d927409ef9f0a1f7a72c33efd3a7618f771
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678635"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="5e3ee-102">ICorProfilerInfo2::GetGenerationBounds Metodu</span><span class="sxs-lookup"><span data-stu-id="5e3ee-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="5e3ee-103">Çeşitli çöp toplama kuşakları ' kılan yığın segmentler bellek bölgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e3ee-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e3ee-104">Syntax</span></span>  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5e3ee-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e3ee-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="5e3ee-106">[in] Öğe için çağırıcı tarafından ayrılan sayısı `ranges` dizisi.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="5e3ee-107">[out] Bazı belirten aralıkları, toplam sayısı veya her biri, döndürülecek tamsayı işaretçisi `ranges` dizisi.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="5e3ee-108">[out] Bir dizi [cor_prf_gc_generatıon_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapıları, çöp toplama aşamasında nesil içinde her biri açıklanmaktadır bellek aralığı (yani, blok).</span><span class="sxs-lookup"><span data-stu-id="5e3ee-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5e3ee-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e3ee-109">Remarks</span></span>  
 <span data-ttu-id="5e3ee-110">`GetGenerationBounds` Yöntemi koşuluyla atık toplama devam ederken değil herhangi bir profil oluşturucu geri çağrısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="5e3ee-111">Diğer bir deyişle, herhangi bir geri çağırma arasında gerçekleşen hariç gelen çağrılabilir [Icorprofilercallback2::garbagecollectionstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) ve [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="5e3ee-111">That is, it can be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
 <span data-ttu-id="5e3ee-112">Çoğu kaydırma nesil atık toplama sırasında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-112">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="5e3ee-113">Nesil koleksiyonlar arasında büyüyebilir ancak genel olarak değiştirmemiz değil.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-113">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="5e3ee-114">Bu nedenle, en ilginç yerleri çağrılacak `GetGenerationBounds` bulunan `ICorProfilerCallback2::GarbageCollectionStarted` ve `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-114">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="5e3ee-115">Program açılışında, bazı nesneler ortak dil çalışma zamanı tarafından (CLR) kendisi, genellikle 3 ve 0 nesillerdeki ayrılır.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-115">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="5e3ee-116">Bu nedenle, yönetilen kod yürütülmeye başlamadan zaman, bu nesiller zaten nesnelerini içerecektir.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-116">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="5e3ee-117">Nesil 1 ve 2 normal çöp toplayıcısı tarafından oluşturulan işlevsiz nesneler dışında boş olur.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-117">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="5e3ee-118">(CLR'nin 32-bit uygulamalarında işlevsiz nesnelerin boyutunu 12 bayttır; 64-bit uygulamalarında boyutu büyük.) Native Image Generator (NGen.exe) tarafından üretilen modülleri içinde 2. nesil aralıklarını da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-118">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="5e3ee-119">Bu durumda, 2. nesil nesneler olan *donmuş nesneler*, hangi ayrılır NGen.exe çalışırken yerine atık toplayıcı tarafından.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-119">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="5e3ee-120">Bu işlev, arayana ayrılan arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-120">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e3ee-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e3ee-121">Requirements</span></span>  
 <span data-ttu-id="5e3ee-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e3ee-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e3ee-123">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5e3ee-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5e3ee-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e3ee-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e3ee-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e3ee-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e3ee-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e3ee-126">See also</span></span>
- [<span data-ttu-id="5e3ee-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e3ee-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="5e3ee-128">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e3ee-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="5e3ee-129">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5e3ee-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="5e3ee-130">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5e3ee-130">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
