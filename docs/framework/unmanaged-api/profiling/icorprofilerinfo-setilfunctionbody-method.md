---
description: ': ICorProfilerInfo:: SetILFunctionBody yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 38e7907080065dc96d72a3d38a67227414637a70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647173"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="32b1b-103">ICorProfilerInfo::SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="32b1b-103">ICorProfilerInfo::SetILFunctionBody Method</span></span>

<span data-ttu-id="32b1b-104">Belirtilen modüldeki belirtilen işlevin gövdesini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="32b1b-104">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32b1b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32b1b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32b1b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32b1b-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="32b1b-107">'ndaki İşlevin bulunduğu modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="32b1b-107">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="32b1b-108">'ndaki Gövdesinin yerine geçecek işlevin belirteci.</span><span class="sxs-lookup"><span data-stu-id="32b1b-108">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="32b1b-109">'ndaki İşlevin yeni üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="32b1b-109">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32b1b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32b1b-110">Remarks</span></span>  

 <span data-ttu-id="32b1b-111">`SetILFunctionBody`Yöntemi, Meta verilerdeki işlevin göreli sanal adresini değiştirir, böylece yeni işlev gövdesine işaret eder ve tüm iç veri yapılarını gerektiği şekilde ayarlar.</span><span class="sxs-lookup"><span data-stu-id="32b1b-111">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="32b1b-112">`SetILFunctionBody`Yöntemi yalnızca bir tam zamanında (JIT) derleyici tarafından derlenmediği işlevlerde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="32b1b-112">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="32b1b-113">Arabelleğin uyumlu olduğundan emin olmak için yeni yönteme alan ayırmak üzere [ICorProfilerInfo:: GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md) metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="32b1b-113">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32b1b-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32b1b-114">Requirements</span></span>  

 <span data-ttu-id="32b1b-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32b1b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32b1b-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="32b1b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32b1b-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="32b1b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32b1b-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32b1b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b1b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32b1b-119">See also</span></span>

- [<span data-ttu-id="32b1b-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32b1b-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
