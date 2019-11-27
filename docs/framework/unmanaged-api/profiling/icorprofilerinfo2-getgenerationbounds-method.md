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
ms.openlocfilehash: 11157bca2d0f0be2b9b9bc36c382188a43db22a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433117"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="2b0ea-102">ICorProfilerInfo2::GetGenerationBounds Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2b0ea-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="2b0ea-103">Yığın kesimleri olan bellek bölgelerini alır, bu, çeşitli çöp toplama nesilleri yapar.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b0ea-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b0ea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b0ea-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b0ea-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="2b0ea-106">'ndaki `ranges` dizisi için çağıran tarafından ayrılan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="2b0ea-107">dışı `ranges` dizisinde döndürülecek bir veya hepsi olan toplam Aralık sayısını belirten bir tamsayı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="2b0ea-108">dışı Her biri çöp toplama yapılmakta olan kuşak içindeki belleğin bir aralığını (yani bloğunu) açıklayan [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b0ea-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2b0ea-109">Remarks</span></span>  
 <span data-ttu-id="2b0ea-110">Çöp toplama işlemi devam ettiğinden, `GetGenerationBounds` yöntemi herhangi bir profil oluşturucu geri çağrısından çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span>

 <span data-ttu-id="2b0ea-111">Nesklerde en fazla kaydırma, çöp koleksiyonları sırasında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-111">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="2b0ea-112">Nesiller koleksiyonlar arasında büyüyebilir ancak genellikle hareket etmez.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-112">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="2b0ea-113">Bu nedenle, `GetGenerationBounds` çağrısı yapılacak en ilginç konumlar `ICorProfilerCallback2::GarbageCollectionStarted` ve `ICorProfilerCallback2::GarbageCollectionFinished`.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-113">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="2b0ea-114">Program başlatma sırasında bazı nesneler ortak dil çalışma zamanı (CLR) tarafından genellikle 2. nesil 3 ve 0 ' da ayrılır.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-114">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="2b0ea-115">Bu nedenle, yönetilen kodun yürütülmeye başladığı zaman, bu nesiller de nesneleri içerecektir.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-115">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="2b0ea-116">Atık toplayıcı tarafından oluşturulan kukla nesneler dışında, 1 ve 2. nesil normalde boş olur.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-116">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="2b0ea-117">(Kukla nesnelerin boyutu, CLR 'nin 32 bitlik uygulamalarında 12 bayttır; boyut 64 bit uygulamalarda daha büyüktür.) Ayrıca, yerel görüntü Oluşturucu (NGen. exe) tarafından üretilen modüller içindeki 2. nesil aralıkları görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-117">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="2b0ea-118">Bu durumda, kuşak 2 ' deki nesneler, çöp toplayıcı tarafından değil NGen. exe çalıştırıldığında ayrılan *dondurulmuş nesnelerdir*.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-118">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="2b0ea-119">Bu işlev, arayana ayrılan arabellekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-119">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b0ea-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b0ea-120">Requirements</span></span>  
 <span data-ttu-id="2b0ea-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b0ea-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b0ea-122">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2b0ea-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2b0ea-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2b0ea-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b0ea-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b0ea-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b0ea-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b0ea-125">See also</span></span>

- [<span data-ttu-id="2b0ea-126">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b0ea-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="2b0ea-127">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b0ea-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="2b0ea-128">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2b0ea-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="2b0ea-129">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2b0ea-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
