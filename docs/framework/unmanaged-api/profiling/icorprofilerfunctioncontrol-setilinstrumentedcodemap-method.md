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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3cb4bfdf90099719e2584c3767965a53186ca8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453264"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="87914-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87914-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="87914-103">Kod Haritası belirtilen işlev için belirtilen ortak Ara dili (CIL) eşleme girdilerini kullanarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="87914-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87914-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87914-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87914-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87914-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="87914-106">[in] Harita giriş sayısı.</span><span class="sxs-lookup"><span data-stu-id="87914-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="87914-107">[in] Cor_ıl_map girişleri arayana ayrılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="87914-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="87914-108">Bu girişler yorumu olarak aynıdır [Icorprofilerınfo::setılınstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="87914-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87914-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87914-109">Remarks</span></span>  
 <span data-ttu-id="87914-110">Bu yöntemi çağrılarak eşleme ayarlamayı sağlar çağırarak eşleme almak hata ayıklayıcı [Icordebugılcode2::getınstrumentedılmap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="87914-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="87914-111">Yığın izlemeleri ve değişken yaşam süreleri için hesaplama IL kaydırır eşleme dahili olarak kullanılacak hata ayıklayıcı de sağlar.</span><span class="sxs-lookup"><span data-stu-id="87914-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87914-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87914-112">Requirements</span></span>  
 <span data-ttu-id="87914-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87914-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87914-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87914-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87914-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87914-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87914-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87914-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87914-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="87914-117">See Also</span></span>  
 [<span data-ttu-id="87914-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87914-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
