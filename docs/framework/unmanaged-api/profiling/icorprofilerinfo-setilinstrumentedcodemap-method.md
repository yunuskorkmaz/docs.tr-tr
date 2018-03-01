---
title: "ICorProfilerInfo::SetILInstrumentedCodeMap Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 127f6d76e85ed30f1407d16f8d81c93dd2941960
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="04ec2-102">ICorProfilerInfo::SetILInstrumentedCodeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="04ec2-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="04ec2-103">Kod Haritası belirtilen Microsoft Ara dili (MSIL) harita girişleri kullanarak belirtilen işlev için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="04ec2-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04ec2-104">Çağırma .NET Framework sürüm 2.0, `SetILInstrumentedCodeMap` üzerinde bir `FunctionID` genel bir belirli uygulama etki alanı işlev temsil eder Bu işlev uygulama etki alanındaki tüm örneklerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="04ec2-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ec2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04ec2-105">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]  FunctionID functionId,  
    [in]  BOOL       fStartJit,  
    [in]  ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04ec2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04ec2-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="04ec2-107">[in] Kod Haritası ayarlanacak işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="04ec2-107">[in] The ID of the function for which to set the code map.</span></span>  
  
 `fStartJit`  
 <span data-ttu-id="04ec2-108">[in] Gösteren bir Boole değeri olup olmadığını çağrısı `SetILInstrumentedCodeMap` yöntemdir belirli bir ilk `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="04ec2-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="04ec2-109">Ayarlama `fStartJit` için `true` yapılan ilk çağrıda `SetILInstrumentedCodeMap` için bir verilen `FunctionID`ve `false` bundan sonra.</span><span class="sxs-lookup"><span data-stu-id="04ec2-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>  
  
 `cILMapEntries`  
 <span data-ttu-id="04ec2-110">[in] Öğe sayısı `cILMapEntries` dizi.</span><span class="sxs-lookup"><span data-stu-id="04ec2-110">[in] The number of elements in the `cILMapEntries` array.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="04ec2-111">[in] Her biri bir MSIL uzaklığını belirtir dizisi cor_ıl_map yapıların.</span><span class="sxs-lookup"><span data-stu-id="04ec2-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04ec2-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04ec2-112">Remarks</span></span>  
 <span data-ttu-id="04ec2-113">Bir profil oluşturucu kaynak kodundaki deyimleri yönteminin bu yöntem (örneğin, belirtilen kaynak satırı ulaşıldığında bildirmek için) izlemek için genellikle ekler.</span><span class="sxs-lookup"><span data-stu-id="04ec2-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="04ec2-114">`SetILInstrumentedCodeMap`Yeni konumlarını özgün MSIL yönergeleri eşlemek bir profil oluşturucu sağlar.</span><span class="sxs-lookup"><span data-stu-id="04ec2-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="04ec2-115">Bir profil oluşturucu kullanabilirsiniz [Icorprofilerınfo::getıltonativemapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) özgün MSIL uzaklığı için belirli bir yerel uzaklığı almak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="04ec2-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>  
  
 <span data-ttu-id="04ec2-116">Hata ayıklayıcı her eski uzaklığı içindeki özgün, değiştirilmemiş MSIL kod uzaklığı MSIL başvurduğu ve her yeni uzaklığı yeni, Araçlı kodundaki MSIL uzaklığı başvurduğu varsayar.</span><span class="sxs-lookup"><span data-stu-id="04ec2-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="04ec2-117">Harita artan düzende sıralanmış.</span><span class="sxs-lookup"><span data-stu-id="04ec2-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="04ec2-118">Atlama için düzgün çalışması için aşağıdaki yönergeleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="04ec2-118">For stepping to work properly, follow these guidelines:</span></span>  
  
-   <span data-ttu-id="04ec2-119">İzleme eklenmiş MSIL kodu yeniden değil.</span><span class="sxs-lookup"><span data-stu-id="04ec2-119">Do not reorder instrumented MSIL code.</span></span>  
  
-   <span data-ttu-id="04ec2-120">Özgün MSIL kodunu kaldırmayın.</span><span class="sxs-lookup"><span data-stu-id="04ec2-120">Do not remove the original MSIL code.</span></span>  
  
-   <span data-ttu-id="04ec2-121">Program veritabanı (PDB) dosyasından tüm sıralama noktaları girişlerinde eşlemesinde içerir.</span><span class="sxs-lookup"><span data-stu-id="04ec2-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="04ec2-122">Harita eksik girdiler kesinti değil.</span><span class="sxs-lookup"><span data-stu-id="04ec2-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="04ec2-123">Bu nedenle, aşağıdaki harita verilen:</span><span class="sxs-lookup"><span data-stu-id="04ec2-123">So, given the following map:</span></span>  
  
     <span data-ttu-id="04ec2-124">(0 eski, 0 yeni)</span><span class="sxs-lookup"><span data-stu-id="04ec2-124">(0 old, 0 new)</span></span>  
  
     <span data-ttu-id="04ec2-125">(5 eski, 10 yeni)</span><span class="sxs-lookup"><span data-stu-id="04ec2-125">(5 old, 10 new)</span></span>  
  
     <span data-ttu-id="04ec2-126">(9 eski, 20 yeni)</span><span class="sxs-lookup"><span data-stu-id="04ec2-126">(9 old, 20 new)</span></span>  
  
    -   <span data-ttu-id="04ec2-127">0, 1, 2, 3 veya 4 eski uzaklığı yeni uzaklığı 0 eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="04ec2-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>  
  
    -   <span data-ttu-id="04ec2-128">5, 6, 7 veya 8 eski uzaklığı yeni uzaklık 10 eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="04ec2-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>  
  
    -   <span data-ttu-id="04ec2-129">9 veya üzeri eski uzaklığı yeni uzaklık 20 eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="04ec2-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>  
  
    -   <span data-ttu-id="04ec2-130">Yeni bir uzaklığı 0, 1, 2, 3, 4, 5, 6, 7, 8 veya 9 eski uzaklığı 0 eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="04ec2-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>  
  
    -   <span data-ttu-id="04ec2-131">Yeni uzaklığını 10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 eski uzaklık 5 eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="04ec2-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>  
  
    -   <span data-ttu-id="04ec2-132">Yeni bir uzaklık 20 veya daha yüksek eski uzaklık 9 eşleşecektir.</span><span class="sxs-lookup"><span data-stu-id="04ec2-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04ec2-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04ec2-133">Requirements</span></span>  
 <span data-ttu-id="04ec2-134">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04ec2-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04ec2-135">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="04ec2-135">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="04ec2-136">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04ec2-136">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04ec2-137">**.NET framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04ec2-137">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ec2-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="04ec2-138">See Also</span></span>  
 [<span data-ttu-id="04ec2-139">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04ec2-139">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
