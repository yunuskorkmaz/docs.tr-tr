---
title: ICorProfilerFunctionControl::SetILInstrumentedCodeMap Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerFunctionControl::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetIILInstrumentedCodeMap method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: ecf56646-7e5f-46c4-8340-f3a04e88920f
topic_type:
- apiref
ms.openlocfilehash: 738c98a0a37983faa71ea6e5eeaabb20639f604a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503150"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="39f8b-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39f8b-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="39f8b-103">Belirtilen ortak ara dil (CıL) eşleme girdilerini kullanarak belirtilen işlev için bir kod Haritası ayarlar.</span><span class="sxs-lookup"><span data-stu-id="39f8b-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39f8b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="39f8b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39f8b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39f8b-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="39f8b-106">'ndaki Eşlemedeki girdi sayısı.</span><span class="sxs-lookup"><span data-stu-id="39f8b-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="39f8b-107">'ndaki COR_IL_MAP girdilerinin çağıran ayrılmış dizisi.</span><span class="sxs-lookup"><span data-stu-id="39f8b-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="39f8b-108">Bu girdilerin yorumu [ICorProfilerInfo:: Setilınstrumentedcodemap](icorprofilerinfo-setilinstrumentedcodemap-method.md) yöntemi ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="39f8b-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39f8b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39f8b-109">Remarks</span></span>  
 <span data-ttu-id="39f8b-110">Bu yöntemi çağırarak eşlemenin ayarlanması, [ICorDebugILCode2:: GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md)çağırarak hata ayıklayıcının eşlemeyi almasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="39f8b-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="39f8b-111">Ayrıca, yığın izlemeleri ve değişken yaşam süreleri için Il farklarını hesaplarken hata ayıklayıcının eşlemeyi dahili olarak kullanmasına de olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="39f8b-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39f8b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39f8b-112">Requirements</span></span>  
 <span data-ttu-id="39f8b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39f8b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39f8b-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="39f8b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="39f8b-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="39f8b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39f8b-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39f8b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39f8b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39f8b-117">See also</span></span>

- [<span data-ttu-id="39f8b-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39f8b-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
