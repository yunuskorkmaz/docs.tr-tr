---
title: ICorProfilerInfo2::GetGenerationBounds Yöntemi
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
ms.openlocfilehash: 310bde2889f8a383fde88cb1bbffce9bad157399
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267997"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="fd23f-102">ICorProfilerInfo2::GetGenerationBounds Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd23f-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="fd23f-103">Çeşitli çöp toplama kuşakları ' kılan yığın segmentler bellek bölgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="fd23f-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd23f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd23f-104">Syntax</span></span>  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd23f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd23f-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="fd23f-106">[in] Öğe için çağırıcı tarafından ayrılan sayısı `ranges` dizisi.</span><span class="sxs-lookup"><span data-stu-id="fd23f-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="fd23f-107">[out] Bazı belirten aralıkları, toplam sayısı veya her biri, döndürülecek tamsayı işaretçisi `ranges` dizisi.</span><span class="sxs-lookup"><span data-stu-id="fd23f-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="fd23f-108">[out] Bir dizi [cor_prf_gc_generatıon_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapıları, çöp toplama aşamasında nesil içinde her biri açıklanmaktadır bellek aralığı (yani, blok).</span><span class="sxs-lookup"><span data-stu-id="fd23f-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd23f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd23f-109">Remarks</span></span>  
 <span data-ttu-id="fd23f-110">`GetGenerationBounds` Yöntemi koşuluyla atık toplama devam ederken değil herhangi bir profil oluşturucu geri çağrısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd23f-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span>

 <span data-ttu-id="fd23f-111">Çoğu kaydırma nesil atık toplama sırasında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="fd23f-111">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="fd23f-112">Nesil koleksiyonlar arasında büyüyebilir ancak genel olarak değiştirmemiz değil.</span><span class="sxs-lookup"><span data-stu-id="fd23f-112">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="fd23f-113">Bu nedenle, en ilginç yerleri çağrılacak `GetGenerationBounds` bulunan `ICorProfilerCallback2::GarbageCollectionStarted` ve `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="fd23f-113">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="fd23f-114">Program açılışında, bazı nesneler ortak dil çalışma zamanı tarafından (CLR) kendisi, genellikle 3 ve 0 nesillerdeki ayrılır.</span><span class="sxs-lookup"><span data-stu-id="fd23f-114">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="fd23f-115">Bu nedenle, yönetilen kod yürütülmeye başlamadan zaman, bu nesiller zaten nesnelerini içerecektir.</span><span class="sxs-lookup"><span data-stu-id="fd23f-115">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="fd23f-116">Nesil 1 ve 2 normal çöp toplayıcısı tarafından oluşturulan işlevsiz nesneler dışında boş olur.</span><span class="sxs-lookup"><span data-stu-id="fd23f-116">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="fd23f-117">(CLR'nin 32-bit uygulamalarında işlevsiz nesnelerin boyutunu 12 bayttır; 64-bit uygulamalarında boyutu büyük.) Native Image Generator (NGen.exe) tarafından üretilen modülleri içinde 2. nesil aralıklarını da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd23f-117">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="fd23f-118">Bu durumda, 2. nesil nesneler olan *donmuş nesneler*, hangi ayrılır NGen.exe çalışırken yerine atık toplayıcı tarafından.</span><span class="sxs-lookup"><span data-stu-id="fd23f-118">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="fd23f-119">Bu işlev, arayana ayrılan arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd23f-119">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd23f-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd23f-120">Requirements</span></span>  
 <span data-ttu-id="fd23f-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd23f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd23f-122">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fd23f-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd23f-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd23f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd23f-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd23f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd23f-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd23f-125">See also</span></span>

- [<span data-ttu-id="fd23f-126">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd23f-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="fd23f-127">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd23f-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="fd23f-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fd23f-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="fd23f-129">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd23f-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
