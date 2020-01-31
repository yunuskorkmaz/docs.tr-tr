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
ms.openlocfilehash: 8160bb5b9ca5e0a4e22a1a831e978eaf125e7605
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76870498"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="90fce-102">ICorProfilerInfo::GetILFunctionBody Metodu</span><span class="sxs-lookup"><span data-stu-id="90fce-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="90fce-103">Üst bilgisinden başlayarak, Microsoft ara dili (MSIL) kodundaki bir yöntemin gövdesine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="90fce-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90fce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="90fce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90fce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="90fce-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="90fce-106">'ndaki İşlevin bulunduğu modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="90fce-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="90fce-107">'ndaki Yöntemi için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="90fce-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="90fce-108">dışı Metodun üstbilgisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="90fce-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="90fce-109">dışı Yöntemin boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="90fce-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90fce-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="90fce-110">Remarks</span></span>  
 <span data-ttu-id="90fce-111">Bir yöntem, bulunduğu modülün kapsamına alınır.</span><span class="sxs-lookup"><span data-stu-id="90fce-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="90fce-112">`GetILFunctionBody` yöntemi, ortak dil çalışma zamanı (CLR) tarafından yüklenmeden önce MSIL koduna bir araç erişimi vermek üzere tasarlandığından, istenen örneği bulmak için yönteminin meta veri belirtecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="90fce-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="90fce-113">`GetILFunctionBody`, bir MSIL kodu (soyut bir yöntem veya platform çağırma (PInvoke) yöntemi) olmadan bir yönteme işaret ediyorsa, CORPROF_E_FUNCTION_NOT_IL HRESULT bir `methodId` döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="90fce-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90fce-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="90fce-114">Requirements</span></span>  
 <span data-ttu-id="90fce-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90fce-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90fce-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="90fce-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90fce-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="90fce-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90fce-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90fce-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90fce-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="90fce-119">See also</span></span>

- [<span data-ttu-id="90fce-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="90fce-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
