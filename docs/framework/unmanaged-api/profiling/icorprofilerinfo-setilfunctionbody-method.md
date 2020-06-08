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
ms.openlocfilehash: 462fc7222243f8cad4e1d03d1717eedace549836
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502944"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="87425-102">ICorProfilerInfo::SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87425-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="87425-103">Belirtilen modüldeki belirtilen işlevin gövdesini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="87425-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87425-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="87425-104">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87425-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87425-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="87425-106">'ndaki İşlevin bulunduğu modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="87425-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="87425-107">'ndaki Gövdesinin yerine geçecek işlevin belirteci.</span><span class="sxs-lookup"><span data-stu-id="87425-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="87425-108">'ndaki İşlevin yeni üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="87425-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87425-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87425-109">Remarks</span></span>  
 <span data-ttu-id="87425-110">`SetILFunctionBody`Yöntemi, Meta verilerdeki işlevin göreli sanal adresini değiştirir, böylece yeni işlev gövdesine işaret eder ve tüm iç veri yapılarını gerektiği şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="87425-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="87425-111">`SetILFunctionBody`Yöntemi yalnızca bir tam zamanında (JIT) derleyici tarafından derlenmediği işlevlerde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="87425-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="87425-112">Arabelleğin uyumlu olduğundan emin olmak için yeni yönteme alan ayırmak üzere [ICorProfilerInfo:: GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="87425-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87425-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87425-113">Requirements</span></span>  
 <span data-ttu-id="87425-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87425-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87425-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="87425-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87425-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="87425-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87425-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87425-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87425-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87425-118">See also</span></span>

- [<span data-ttu-id="87425-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87425-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
