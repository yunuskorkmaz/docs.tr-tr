---
title: ICorProfilerInfo::GetILFunctionBody Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 484fb5b8398e3ebd61d1c300afec1536ee1dc0c5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780610"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="f7159-102">ICorProfilerInfo::GetILFunctionBody Metodu</span><span class="sxs-lookup"><span data-stu-id="f7159-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="f7159-103">Bir işaretçi bir yöntem gövdesi ile başlayarak, üst bilgisi, Microsoft Ara dili (MSIL) kodu alır.</span><span class="sxs-lookup"><span data-stu-id="f7159-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7159-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f7159-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7159-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f7159-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f7159-106">[in] İşlev bulunduğu modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="f7159-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="f7159-107">[in] Yöntemi için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="f7159-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="f7159-108">[out] Yöntem üst bilgisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f7159-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="f7159-109">[out] Yönteminin boyutu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f7159-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7159-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f7159-110">Remarks</span></span>  
 <span data-ttu-id="f7159-111">Bir yöntem içinde barındırılmasından modülü tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="f7159-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="f7159-112">Çünkü `GetILFunctionBody` yöntemi, ortak dil çalışma zamanı tarafından (CLR) yüklenmiş olan önce MSIL kodu bir aracı erişim vermek için tasarlanmıştır, yöntemin meta veri belirteci istenen örnek bulmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="f7159-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="f7159-113">`GetILFunctionBody` CORPROF_E_FUNCTION_NOT_IL HRESULT verirseniz dönebilirsiniz `methodId` (soyut bir yöntem veya bir platform çağırma gibi (PInvoke) yöntemi) herhangi bir MSIL kodu olmadan bir yönteme işaret eder.</span><span class="sxs-lookup"><span data-stu-id="f7159-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7159-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f7159-114">Requirements</span></span>  
 <span data-ttu-id="f7159-115">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7159-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7159-116">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7159-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7159-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7159-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7159-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7159-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7159-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7159-119">See also</span></span>

- [<span data-ttu-id="f7159-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f7159-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
