---
title: "ICorProfilerInfo::SetILFunctionBody Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.SetILFunctionBody
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::SetILFunctionBody
helpviewer_keywords:
- ICorProfilerInfo::SetILFunctionBody method [.NET Framework profiling]
- SetILFunctionBody method [.NET Framework profiling]
ms.assetid: b159c712-00f4-4fc7-a990-40bf9f642e8f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6d97827555ecefb775323fdf9dbd6577f941f1e9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="4d30a-102">ICorProfilerInfo::SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4d30a-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="4d30a-103">Belirtilen modül belirtilen işlev gövdesi yerini alır.</span><span class="sxs-lookup"><span data-stu-id="4d30a-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d30a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4d30a-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d30a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4d30a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="4d30a-106">[in] İşlev bulunduğu modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="4d30a-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="4d30a-107">[in] İşlev gövdesi değiştirmek üzere belirteci.</span><span class="sxs-lookup"><span data-stu-id="4d30a-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="4d30a-108">[in] İşlev için yeni üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="4d30a-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d30a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4d30a-109">Remarks</span></span>  
 <span data-ttu-id="4d30a-110">`SetILFunctionBody` Yöntemi, böylece işaret yeni işlev gövdesi ve iç veri yapılarını gerektiği gibi ayarlar meta verilerde işlevinin göreli sanal adres değiştirir.</span><span class="sxs-lookup"><span data-stu-id="4d30a-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="4d30a-111">`SetILFunctionBody` Yöntemi, hiçbir zaman tam zamanında (JIT) derleyicisi tarafından derlenen işlevler üzerinde çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="4d30a-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="4d30a-112">Kullanım [Icorprofilerınfo::getılfunctionbodyallocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) arabellek uyumlu olduğundan emin olmak yeni yöntemi için alan ayırmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="4d30a-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d30a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4d30a-113">Requirements</span></span>  
 <span data-ttu-id="4d30a-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d30a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d30a-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4d30a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4d30a-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d30a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d30a-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d30a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d30a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4d30a-118">See Also</span></span>  
 [<span data-ttu-id="4d30a-119">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="4d30a-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
