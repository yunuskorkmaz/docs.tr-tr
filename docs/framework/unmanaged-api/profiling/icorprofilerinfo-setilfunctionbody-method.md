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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d10bb7033688efce9488078d2ef605e2a29382f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221420"
---
# <a name="icorprofilerinfosetilfunctionbody-method"></a><span data-ttu-id="17ca3-102">ICorProfilerInfo::SetILFunctionBody Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17ca3-102">ICorProfilerInfo::SetILFunctionBody Method</span></span>
<span data-ttu-id="17ca3-103">Belirtilen modüldeki belirtilen işlev gövdesinin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="17ca3-103">Replaces the body of the specified function in the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17ca3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17ca3-104">Syntax</span></span>  
  
```  
HRESULT SetILFunctionBody(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodid,  
    [in] LPCBYTE     pbNewILMethodHeader);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17ca3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17ca3-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="17ca3-106">[in] İşlev bulunduğu modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="17ca3-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodid`  
 <span data-ttu-id="17ca3-107">[in] İşlev gövdesi değiştirmek istediğiniz belirteç.</span><span class="sxs-lookup"><span data-stu-id="17ca3-107">[in] The token of the function for which to replace the body.</span></span>  
  
 `pbNewILMethodHeader`  
 <span data-ttu-id="17ca3-108">[in] İşlev için yeni üstbilgi.</span><span class="sxs-lookup"><span data-stu-id="17ca3-108">[in] The new header for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17ca3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17ca3-109">Remarks</span></span>  
 <span data-ttu-id="17ca3-110">`SetILFunctionBody` Yöntemi noktaları için yeni işlev gövdesi ve gerektiği gibi iç veri yapılarını ayarlar böylece göreli sanal adres meta verileri işlevin yerini alır.</span><span class="sxs-lookup"><span data-stu-id="17ca3-110">The `SetILFunctionBody` method replaces the relative virtual address of the function in the metadata so that it points to the new function body, and adjusts any internal data structures as required.</span></span>  
  
 <span data-ttu-id="17ca3-111">`SetILFunctionBody` Yöntemi, üzerinde hiçbir zaman just-in-time (JIT) derleyicisi tarafından derlenen işlevler çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="17ca3-111">The `SetILFunctionBody` method can be called on only those functions that have never been compiled by a just-in-time (JIT) compiler.</span></span>  
  
 <span data-ttu-id="17ca3-112">Kullanım [Icorprofilerınfo::getılfunctionbodyallocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) arabellek uyumlu olmasını sağlamak yeni yöntem için alan ayırmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="17ca3-112">Use the [ICorProfilerInfo::GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md) method to allocate space for the new method to ensure that the buffer is compatible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17ca3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17ca3-113">Requirements</span></span>  
 <span data-ttu-id="17ca3-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17ca3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17ca3-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="17ca3-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17ca3-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17ca3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17ca3-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17ca3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ca3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17ca3-118">See also</span></span>

- [<span data-ttu-id="17ca3-119">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17ca3-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
