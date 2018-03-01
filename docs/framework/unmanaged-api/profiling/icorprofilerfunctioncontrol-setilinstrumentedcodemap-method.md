---
title: "ICorProfilerFunctionControl::SetILInstrumentedCodeMap Yöntemi"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 580d60fe0a6348a163fef9e215cddfc1bc4302b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="9963b-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9963b-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="9963b-103">Kod Haritası belirtilen işlev için belirtilen ortak Ara dili (CIL) eşleme girdilerini kullanarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9963b-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9963b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9963b-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9963b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9963b-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="9963b-106">[in] Harita giriş sayısı.</span><span class="sxs-lookup"><span data-stu-id="9963b-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="9963b-107">[in] Cor_ıl_map girişleri arayana ayrılan dizisi.</span><span class="sxs-lookup"><span data-stu-id="9963b-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="9963b-108">Bu girişler yorumu olarak aynıdır [Icorprofilerınfo::setılınstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9963b-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9963b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9963b-109">Remarks</span></span>  
 <span data-ttu-id="9963b-110">Bu yöntemi çağrılarak eşleme ayarlamayı sağlar çağırarak eşleme almak hata ayıklayıcı [Icordebugılcode2::getınstrumentedılmap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="9963b-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="9963b-111">Yığın izlemeleri ve değişken yaşam süreleri için hesaplama IL kaydırır eşleme dahili olarak kullanılacak hata ayıklayıcı de sağlar.</span><span class="sxs-lookup"><span data-stu-id="9963b-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9963b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9963b-112">Requirements</span></span>  
 <span data-ttu-id="9963b-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9963b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9963b-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9963b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9963b-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9963b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9963b-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9963b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9963b-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9963b-117">See Also</span></span>  
 [<span data-ttu-id="9963b-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9963b-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
