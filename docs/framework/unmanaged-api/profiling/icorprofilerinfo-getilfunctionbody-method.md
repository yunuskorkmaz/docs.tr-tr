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
ms.openlocfilehash: a7ec50c91ce02958d0d44643d4f79da1680532aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450361"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="87228-102">ICorProfilerInfo::GetILFunctionBody Metodu</span><span class="sxs-lookup"><span data-stu-id="87228-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="87228-103">Üst bilgisinden başlayarak, Microsoft ara dili (MSIL) kodundaki bir yöntemin gövdesine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="87228-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87228-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87228-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87228-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87228-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="87228-106">'ndaki İşlevin bulunduğu modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="87228-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="87228-107">'ndaki Yöntemi için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="87228-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="87228-108">dışı Metodun üstbilgisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="87228-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="87228-109">dışı Yöntemin boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="87228-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87228-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87228-110">Remarks</span></span>  
 <span data-ttu-id="87228-111">Bir yöntem, bulunduğu modülün kapsamına alınır.</span><span class="sxs-lookup"><span data-stu-id="87228-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="87228-112">`GetILFunctionBody` yöntemi, ortak dil çalışma zamanı (CLR) tarafından yüklenmeden önce MSIL koduna bir araç erişimi vermek üzere tasarlandığından, istenen örneği bulmak için yönteminin meta veri belirtecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="87228-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="87228-113">`GetILFunctionBody`, bir MSIL kodu (soyut bir yöntem veya platform çağırma (PInvoke) yöntemi) olmadan bir yönteme işaret ediyorsa, CORPROF_E_FUNCTION_NOT_IL HRESULT bir `methodId` döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="87228-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87228-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87228-114">Requirements</span></span>  
 <span data-ttu-id="87228-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87228-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87228-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="87228-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87228-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="87228-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87228-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87228-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87228-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87228-119">See also</span></span>

- [<span data-ttu-id="87228-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87228-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
