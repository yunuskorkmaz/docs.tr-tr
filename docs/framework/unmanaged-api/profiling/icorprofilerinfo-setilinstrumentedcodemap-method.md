---
description: ': ICorProfilerInfo:: Setilınstrumentedcodemap yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0cf3b4ccf31076c2d1ea2df581003e3a07f0e795
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737356"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="e1c36-103">ICorProfilerInfo::SetILInstrumentedCodeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e1c36-103">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="e1c36-104">Belirtilen Microsoft ara dili (MSIL) eşleme girdilerini kullanarak belirtilen işlev için bir kod Haritası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e1c36-104">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>

> [!NOTE]
> <span data-ttu-id="e1c36-105">.NET Framework sürüm 2,0 ' de, `SetILInstrumentedCodeMap` `FunctionID` belirli bir uygulama etki alanında genel bir işlevi temsil eden bir üzerinde çağırmak, uygulama etki alanındaki bu işlevin tüm örneklerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="e1c36-105">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>

## <a name="syntax"></a><span data-ttu-id="e1c36-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e1c36-106">Syntax</span></span>

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a><span data-ttu-id="e1c36-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e1c36-107">Parameters</span></span>

`functionId`\
<span data-ttu-id="e1c36-108">'ndaki Kod eşlemesi ayarlanacak işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e1c36-108">[in] The ID of the function for which to set the code map.</span></span>

`fStartJit`\
<span data-ttu-id="e1c36-109">'ndaki Yöntemine yapılan çağrının `SetILInstrumentedCodeMap` , belirli bir için ilk değeri olup olmadığını belirten bir Boolean değer `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="e1c36-109">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="e1c36-110">`fStartJit`Verilen için `true` ilk çağrıda ve daha sonra öğesine ayarlanır `SetILInstrumentedCodeMap` `FunctionID` `false` .</span><span class="sxs-lookup"><span data-stu-id="e1c36-110">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>

`cILMapEntries`\
<span data-ttu-id="e1c36-111">'ndaki Dizideki öğelerin sayısı `cILMapEntries` .</span><span class="sxs-lookup"><span data-stu-id="e1c36-111">[in] The number of elements in the `cILMapEntries` array.</span></span>

`rgILMapEntries`\
<span data-ttu-id="e1c36-112">'ndaki Her biri bir MSIL sapmasını belirten COR_IL_MAP yapıları dizisi.</span><span class="sxs-lookup"><span data-stu-id="e1c36-112">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1c36-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e1c36-113">Remarks</span></span>

<span data-ttu-id="e1c36-114">Profil Oluşturucu genellikle bu yöntemi işaretlemek için (örneğin, belirli bir kaynak satırına ulaşıldığında bildirmek üzere) bir yöntemin kaynak koduna deyimler ekler.</span><span class="sxs-lookup"><span data-stu-id="e1c36-114">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="e1c36-115">`SetILInstrumentedCodeMap` profil oluşturucunun özgün MSIL talimatlarını yeni konumlarına eşlemesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e1c36-115">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="e1c36-116">Bir profil oluşturucu, belirli bir yerel kenar için özgün MSIL sapmasını almak üzere [ICorProfilerInfo:: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) metodunu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e1c36-116">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>

<span data-ttu-id="e1c36-117">Hata ayıklayıcı, her bir eski kaydırın orijinal, değiştirilmemiş MSIL kodu içindeki bir MSIL denkleşeceğini ve her yeni kaydırın yeni, belgelenmiş koddaki MSIL denkleşeceğini varsayacaktır.</span><span class="sxs-lookup"><span data-stu-id="e1c36-117">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="e1c36-118">Haritanın artan sırada sıralanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e1c36-118">The map should be sorted in increasing order.</span></span> <span data-ttu-id="e1c36-119">Adımlamayı düzgün şekilde çalışmak için aşağıdaki yönergeleri izleyin:</span><span class="sxs-lookup"><span data-stu-id="e1c36-119">For stepping to work properly, follow these guidelines:</span></span>

- <span data-ttu-id="e1c36-120">Belgelenmiş MSIL kodunu yeniden düzenleme.</span><span class="sxs-lookup"><span data-stu-id="e1c36-120">Do not reorder instrumented MSIL code.</span></span>

- <span data-ttu-id="e1c36-121">Özgün MSIL kodunu kaldırmayın.</span><span class="sxs-lookup"><span data-stu-id="e1c36-121">Do not remove the original MSIL code.</span></span>

- <span data-ttu-id="e1c36-122">Haritadaki program veritabanı (PDB) dosyasındaki tüm sıra noktalarına ait girişleri dahil edin.</span><span class="sxs-lookup"><span data-stu-id="e1c36-122">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="e1c36-123">Eşleme, eksik girişleri enterpolamıyor.</span><span class="sxs-lookup"><span data-stu-id="e1c36-123">The map does not interpolate missing entries.</span></span> <span data-ttu-id="e1c36-124">Bu nedenle, aşağıdaki haritada verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e1c36-124">So, given the following map:</span></span>

  <span data-ttu-id="e1c36-125">(0 eski, 0 yeni)</span><span class="sxs-lookup"><span data-stu-id="e1c36-125">(0 old, 0 new)</span></span>

  <span data-ttu-id="e1c36-126">(5 eski, 10 yeni)</span><span class="sxs-lookup"><span data-stu-id="e1c36-126">(5 old, 10 new)</span></span>

  <span data-ttu-id="e1c36-127">(9 eski, 20 yeni)</span><span class="sxs-lookup"><span data-stu-id="e1c36-127">(9 old, 20 new)</span></span>

  - <span data-ttu-id="e1c36-128">0, 1, 2, 3 veya 4 ' ün eski bir kayması, 0 ' dan yeni bir uzaklığa eşlenecek.</span><span class="sxs-lookup"><span data-stu-id="e1c36-128">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>

  - <span data-ttu-id="e1c36-129">5, 6, 7 veya 8 ' in eski bir kayması, yeni %10 ' a eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e1c36-129">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>

  - <span data-ttu-id="e1c36-130">Daha eski bir 9 veya üzeri fark, 20. yeni uzaklığa eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e1c36-130">An old offset of 9 or higher will be mapped to new offset 20.</span></span>

  - <span data-ttu-id="e1c36-131">0, 1, 2, 3, 4, 5, 6, 7, 8 ya da 9 ' un yeni bir kayması, 0 ' dan eski uzaklığa eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e1c36-131">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>

  - <span data-ttu-id="e1c36-132">10, 11, 12, 13, 14, 15, 16, 17, 18 veya 19 ' un yeni bir kayması, 5 eski uzaklığa eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e1c36-132">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>

  - <span data-ttu-id="e1c36-133">20 veya üzeri yeni bir konum, eski konum 9 ' A eşlenir.</span><span class="sxs-lookup"><span data-stu-id="e1c36-133">A new offset of 20 or higher will be mapped to old offset 9.</span></span>

<span data-ttu-id="e1c36-134">.NET Framework 3,5 ve önceki sürümlerde, `rgILMapEntries` [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) yöntemini çağırarak diziyi ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e1c36-134">In the .NET Framework 3.5 and previous versions, you allocate the `rgILMapEntries` array by calling the [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) method.</span></span> <span data-ttu-id="e1c36-135">Çalışma zamanı bu belleğin sahipliğini aldığı için profil oluşturucu onu serbest bırakmayı denememelidir.</span><span class="sxs-lookup"><span data-stu-id="e1c36-135">Because the runtime takes ownership of this memory, the profiler should not attempt to free it.</span></span>

## <a name="requirements"></a><span data-ttu-id="e1c36-136">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e1c36-136">Requirements</span></span>

<span data-ttu-id="e1c36-137">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1c36-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="e1c36-138">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e1c36-138">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="e1c36-139">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e1c36-139">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e1c36-140">**.NET Framework sürümleri:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1c36-140">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e1c36-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e1c36-141">See also</span></span>

- [<span data-ttu-id="e1c36-142">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e1c36-142">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
