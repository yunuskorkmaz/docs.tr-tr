---
title: ICorProfilerInfo2::GetGenerationBounds Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetGenerationBounds
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c84be5d7e78c348c0368e9639a470a8fc60e2ca7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="12bfd-102">ICorProfilerInfo2::GetGenerationBounds Metodu</span><span class="sxs-lookup"><span data-stu-id="12bfd-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="12bfd-103">Heap öğesinin çeşitli atık toplama nesli yapmak kesimlerin bellek bölümlerinin alır.</span><span class="sxs-lookup"><span data-stu-id="12bfd-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12bfd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12bfd-104">Syntax</span></span>  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12bfd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12bfd-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="12bfd-106">[in] İçin çağıran tarafından ayrılmış. öğe sayısı `ranges` dizi.</span><span class="sxs-lookup"><span data-stu-id="12bfd-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="12bfd-107">[out] Tamsayı aralığı, toplam sayısı bazı belirtir veya bunların tümü de döndürülecek bir işaretçi `ranges` dizi.</span><span class="sxs-lookup"><span data-stu-id="12bfd-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="12bfd-108">[out] Bir dizi [cor_prf_gc_generatıon_range](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapıları, atık toplama yapılıyor nesil içinde her biri açıklanmaktadır bellek aralığı (yani, blok).</span><span class="sxs-lookup"><span data-stu-id="12bfd-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12bfd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12bfd-109">Remarks</span></span>  
 <span data-ttu-id="12bfd-110">`GetGenerationBounds` Yöntemi koşuluyla atık toplama devam değil tüm profil oluşturucu geri aramasından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="12bfd-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="12bfd-111">Diğer bir deyişle, onu arasında oluşan olanlar dışında herhangi bir geri aramadan çağrılabilir [Icorprofilercallback2::garbagecollectionstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) ve [Icorprofilercallback2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="12bfd-111">That is, it can be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
 <span data-ttu-id="12bfd-112">Çoğu nesli kaydırma sırasında çöp koleksiyonları gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="12bfd-112">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="12bfd-113">Nesli koleksiyonları arasında büyüyebilir ancak genellikle dolaşmak değil.</span><span class="sxs-lookup"><span data-stu-id="12bfd-113">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="12bfd-114">Bu nedenle, çağırmak için en ilgi çekici yerleri `GetGenerationBounds` bulunan `ICorProfilerCallback2::GarbageCollectionStarted` ve `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="12bfd-114">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="12bfd-115">Program başlatma sırasında bazı nesneler ortak dil çalışma zamanı tarafından (CLR) kendisi, genellikle kuşakta 3 ve 0 ayrılır.</span><span class="sxs-lookup"><span data-stu-id="12bfd-115">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="12bfd-116">Bu nedenle, yönetilen kod yürütme başlatılışında tarafından bu nesli zaten nesnelerini içerecektir.</span><span class="sxs-lookup"><span data-stu-id="12bfd-116">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="12bfd-117">Nesil 1 ve 2 normalde atık toplayıcısı tarafından oluşturulan sahte nesneler dışında boş olacaktır.</span><span class="sxs-lookup"><span data-stu-id="12bfd-117">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="12bfd-118">(Sahte nesneler 12 32-bit uygulamaları CLR bayt boyutudur; boyutu 64-bit uygulamalarında daha büyüktür.) Yerel Görüntü Oluşturucu (NGen.exe) tarafından üretilen modülleri içinde olduğunda 2. nesil aralıkları da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12bfd-118">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="12bfd-119">Bu durumda, 2. nesil nesneler olan *nesneleri dondurulmuş*, hangi ayrılır NGen.exe çalıştığında yerine atık toplayıcı tarafından.</span><span class="sxs-lookup"><span data-stu-id="12bfd-119">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="12bfd-120">Bu işlev, çağıran tarafından ayrılan arabellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="12bfd-120">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12bfd-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12bfd-121">Requirements</span></span>  
 <span data-ttu-id="12bfd-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12bfd-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12bfd-123">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="12bfd-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="12bfd-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12bfd-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12bfd-125">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12bfd-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12bfd-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="12bfd-126">See Also</span></span>  
 [<span data-ttu-id="12bfd-127">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12bfd-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="12bfd-128">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12bfd-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="12bfd-129">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="12bfd-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="12bfd-130">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="12bfd-130">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
