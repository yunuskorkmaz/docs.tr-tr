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
ms.openlocfilehash: bde194023ff6913db9a56e30eddaad8d7abc5ad1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452813"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="fab81-102">ICorProfilerInfo::GetILFunctionBody Metodu</span><span class="sxs-lookup"><span data-stu-id="fab81-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="fab81-103">Bir işaretçi bir yöntemin gövdesi Microsoft Ara dili (MSIL) kodda, kendi üst bilgisi başlangıç alır.</span><span class="sxs-lookup"><span data-stu-id="fab81-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fab81-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fab81-104">Syntax</span></span>  
  
```  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fab81-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fab81-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="fab81-106">[in] İşlev bulunduğu modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="fab81-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="fab81-107">[in] Meta veri simgesi yöntemi.</span><span class="sxs-lookup"><span data-stu-id="fab81-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="fab81-108">[out] Yöntemin üst bilgisi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fab81-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="fab81-109">[out] Yöntem boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="fab81-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fab81-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fab81-110">Remarks</span></span>  
 <span data-ttu-id="fab81-111">Bir yöntemi, yaşadığı modülü tarafından kapsamlıdır.</span><span class="sxs-lookup"><span data-stu-id="fab81-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="fab81-112">Çünkü `GetILFunctionBody` yöntemi ortak dil çalışma zamanı tarafından (CLR) yüklenen önce MSIL koda bir aracı erişmesini sağlamak için tasarlanmıştır, istenen örneği bulmak için meta veri simgesi yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fab81-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="fab81-113">`GetILFunctionBody` CORPROF_E_FUNCTION_NOT_IL HRESULT varsa döndürebilir `methodId` herhangi MSIL kodu olmadan (soyut bir yöntem ya da bir platform çağırma gibi (PInvoke) yöntemi) bir yönteme işaret eder.</span><span class="sxs-lookup"><span data-stu-id="fab81-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fab81-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fab81-114">Requirements</span></span>  
 <span data-ttu-id="fab81-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fab81-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fab81-116">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fab81-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fab81-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fab81-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fab81-118">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fab81-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fab81-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fab81-119">See Also</span></span>  
 [<span data-ttu-id="fab81-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fab81-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
