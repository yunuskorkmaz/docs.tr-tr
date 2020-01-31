---
title: ICorProfilerInfo::SetILFunctionBody Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type:
- apiref
ms.openlocfilehash: 296c3973403a5b09332efa24961d7a474d814aab
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863354"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="a89a5-102">ICorProfilerInfo::SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a89a5-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="a89a5-103">Belirtilen modüldeki belirtilen işlevin gövdesini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a89a5-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a89a5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a89a5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a89a5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a89a5-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a89a5-106">'ndaki İşlevin bulunduğu modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a89a5-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="a89a5-107">'ndaki Gövdesinin yerine geçecek işlevin belirteci.</span><span class="sxs-lookup"><span data-stu-id="a89a5-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="a89a5-108">'ndaki İşlevin yeni üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="a89a5-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a89a5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a89a5-109">Remarks</span></span>  
 <span data-ttu-id="a89a5-110">`SetILFunctionBody` yöntemi, Meta verilerdeki işlevin göreli sanal adresini değiştirir, böylece yeni işlev gövdesine işaret eder ve tüm iç veri yapılarını gerektiği şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a89a5-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="a89a5-111">`SetILFunctionBody` yöntemi, yalnızca bir tam zamanında (JıT) derleyici tarafından derlenmediği işlevlerde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="a89a5-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="a89a5-112">Arabelleğin uyumlu olduğundan emin olmak için yeni yönteme alan ayırmak üzere [ICorProfilerInfo:: GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="a89a5-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a89a5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a89a5-113">Requirements</span></span>  
 <span data-ttu-id="a89a5-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a89a5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a89a5-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a89a5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a89a5-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a89a5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a89a5-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a89a5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a89a5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a89a5-118">See also</span></span>

- [<span data-ttu-id="a89a5-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a89a5-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
