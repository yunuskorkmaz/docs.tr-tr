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
ms.openlocfilehash: 81880f5f97d1c8f16c80f3e3cb2a1be506d44e2d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571041"
---
# <a name="icorprofilerfunctioncontrolsetilinstrumentedcodemap-method"></a><span data-ttu-id="abe96-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="abe96-102">ICorProfilerFunctionControl::SetILInstrumentedCodeMap Method</span></span>
<span data-ttu-id="abe96-103">Belirtilen işlev için kod haritası, belirtilen ortak Ara dil (CIL) map girişlerini kullanarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="abe96-103">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe96-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abe96-104">Syntax</span></span>  
  
```  
HRESULT SetILInstrumentedCodeMap(  
    [in]   ULONG      cILMapEntries,  
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abe96-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="abe96-105">Parameters</span></span>  
 `cILMapEntries`  
 <span data-ttu-id="abe96-106">[in] Eşleme girişleri sayısı.</span><span class="sxs-lookup"><span data-stu-id="abe96-106">[in] The number of entries in the map.</span></span>  
  
 `rgILMapEntries`  
 <span data-ttu-id="abe96-107">[in] Cor_ıl_map girişleri arayan tarafından ayrılmış dizi.</span><span class="sxs-lookup"><span data-stu-id="abe96-107">[in] The caller-allocated array of COR_IL_MAP  entries.</span></span> <span data-ttu-id="abe96-108">Bu girişlerin aynı yorumlamasıdır [Icorprofilerınfo::setılınstrumentedcodemap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="abe96-108">The interpretation of these entries is the same as for the [ICorProfilerInfo::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abe96-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abe96-109">Remarks</span></span>  
 <span data-ttu-id="abe96-110">Bu yöntemi çağırarak eşlemeyi ayarlamaya izin verir çağırarak eşlemesini almak hata ayıklayıcı [Icordebugılcode2::getınstrumentedılmap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span><span class="sxs-lookup"><span data-stu-id="abe96-110">Setting the mapping by calling this method allows the debugger to retrieve the mapping by calling [ICorDebugILCode2::GetInstrumentedILMap](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md).</span></span> <span data-ttu-id="abe96-111">Yığın izlemeleri ve değişken yaşam süreleri için hesaplama IL kaydırır eşleme dahili olarak kullanılacak hata ayıklayıcı ayrıca sağlar.</span><span class="sxs-lookup"><span data-stu-id="abe96-111">It also allows the debugger to use the mapping internally when calculating IL offsets for stack traces and variable lifetimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe96-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abe96-112">Requirements</span></span>  
 <span data-ttu-id="abe96-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abe96-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe96-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="abe96-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="abe96-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abe96-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abe96-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe96-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe96-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abe96-117">See also</span></span>
- [<span data-ttu-id="abe96-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abe96-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
