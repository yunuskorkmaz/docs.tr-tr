---
title: ICorProfilerInfo::SetILInstrumentedCodeMap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4780242dc34f31ecd0ff0dc2c339cdaa30278a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54721168"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="95eee-102">ICorProfilerInfo::SetILInstrumentedCodeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="95eee-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="95eee-103">Belirtilen Microsoft Ara dil (MSIL) map girişleri kullanarak belirtilen işlev için kod Haritası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="95eee-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95eee-104">Çağırma .NET Framework sürüm 2.0 `SetILInstrumentedCodeMap` üzerinde bir `FunctionID` genel işlev belirli uygulama etki alanında temsil eder, bu işlevin uygulama etki alanındaki tüm örnekleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="95eee-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95eee-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95eee-105">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95eee-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95eee-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="95eee-107">[in] Kod Haritası ayarlanacağı işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="95eee-107">[in] The ID of the function for which to set the code map.</span></span>  
  
 `fStartJit`  
 <span data-ttu-id="95eee-108">[in] Belirten Boolean bir değer olup olmadığını çağrısı `SetILInstrumentedCodeMap` yöntemidir, belirli bir ilk `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="95eee-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="95eee-109">Ayarlama `fStartJit` için `true` yapılan ilk çağrıda `SetILInstrumentedCodeMap` için bir verilen `FunctionID`ve `false` tutarında ücret alınır.</span><span class="sxs-lookup"><span data-stu-id="95eee-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>  
  
 `cILMapEntries`  
 <span data-ttu-id="95eee-110">[in] İçindeki öğelerin sayısını `cILMapEntries` dizisi.</span><span class="sxs-lookup"><span data-stu-id="95eee-110">[in] The number of elements in the `cILMapEntries` array.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="95eee-111">[in] Bir dizi cor_ıl_map yapılarının her biri bir MSIL uzaklığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="95eee-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95eee-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95eee-112">Remarks</span></span>  
 <span data-ttu-id="95eee-113">Bir profil oluşturucu, kaynak kodundaki deyimleri bir yöntemin genellikle bu yöntem (örneğin, belirtilen kaynak satırı ulaşıldığında bildirmek için) izleme için ekler.</span><span class="sxs-lookup"><span data-stu-id="95eee-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="95eee-114">`SetILInstrumentedCodeMap` özgün MSIL yönergeleri yeni konumlarına eşlemek bir profil oluşturucunun sağlar.</span><span class="sxs-lookup"><span data-stu-id="95eee-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="95eee-115">Bir profil oluşturucu kullanabilirsiniz [Icorprofilerınfo::getıltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) özgün MSIL uzaklığı için belirli bir yerel uzaklık almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95eee-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>  
  
 <span data-ttu-id="95eee-116">Hata ayıklayıcı, her eski uzaklığı bir MSIL içindeki özgün, değiştirilmemiş MSIL kod uzaklığı için ifade eder ve her yeni uzaklık yeni, izleme eklenmiş kod içinde MSIL uzaklığı başvurduğu varsayar.</span><span class="sxs-lookup"><span data-stu-id="95eee-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="95eee-117">Harita, artan düzende sıralanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="95eee-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="95eee-118">Düzgün çalışması için atlamak için aşağıdaki yönergeleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="95eee-118">For stepping to work properly, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="95eee-119">İzleme eklenmiş MSIL kodu yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="95eee-119">Do not reorder instrumented MSIL code.</span></span>  
  
-   <span data-ttu-id="95eee-120">Özgün MSIL kodunu kaldırmayın.</span><span class="sxs-lookup"><span data-stu-id="95eee-120">Do not remove the original MSIL code.</span></span>  
  
-   <span data-ttu-id="95eee-121">Program veritabanı (PDB) dosyasındaki dizi noktalarını girişlerinde haritada içerir.</span><span class="sxs-lookup"><span data-stu-id="95eee-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="95eee-122">Harita eksik girdiler enterpolasyon değil.</span><span class="sxs-lookup"><span data-stu-id="95eee-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="95eee-123">Bu nedenle, aşağıdaki harita verilen:</span><span class="sxs-lookup"><span data-stu-id="95eee-123">So, given the following map:</span></span>  
  
     <span data-ttu-id="95eee-124">(0 eski, 0 yeni)</span><span class="sxs-lookup"><span data-stu-id="95eee-124">(0 old, 0 new)</span></span>  
  
     <span data-ttu-id="95eee-125">(5 eski, 10 yeni)</span><span class="sxs-lookup"><span data-stu-id="95eee-125">(5 old, 10 new)</span></span>  
  
     <span data-ttu-id="95eee-126">(9 eski, 20 yeni)</span><span class="sxs-lookup"><span data-stu-id="95eee-126">(9 old, 20 new)</span></span>  
  
    -   <span data-ttu-id="95eee-127">Yeni Uzaklık 0, 0, 1, 2, 3 veya 4 eski bir uzaklık eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="95eee-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>  
  
    -   <span data-ttu-id="95eee-128">Eski bir uzaklık 5, 6, 7 veya 8, 10 yeni uzaklık eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="95eee-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
    -   <span data-ttu-id="95eee-129">9 veya daha eski bir uzaklık yeni uzaklık 20 eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="95eee-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
    -   <span data-ttu-id="95eee-130">Yeni bir uzaklığı 0, 1, 2, 3, 4, 5, 6, 7, 8 veya 9 eski uzaklığı 0 eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="95eee-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
    -   <span data-ttu-id="95eee-131">Yeni bir uzaklık 10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 eski uzaklığı 5 eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="95eee-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
    -   <span data-ttu-id="95eee-132">20 veya üzeri bir yeni uzaklığı eski uzaklığı 9 eşleştirilir.</span><span class="sxs-lookup"><span data-stu-id="95eee-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95eee-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95eee-133">Requirements</span></span>  
 <span data-ttu-id="95eee-134">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95eee-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95eee-135">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="95eee-135">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="95eee-136">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95eee-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95eee-137">**.NET framework sürümleri:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95eee-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95eee-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95eee-138">See also</span></span>
- [<span data-ttu-id="95eee-139">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95eee-139">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
