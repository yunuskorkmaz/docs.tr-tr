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
ms.openlocfilehash: 5984c63f0e1a1859dd5cc2550d6dc37c963affb3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503009"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="13c36-102">ICorProfilerInfo::GetILFunctionBody Metodu</span><span class="sxs-lookup"><span data-stu-id="13c36-102">ICorProfilerInfo::GetILFunctionBody Method</span></span>
<span data-ttu-id="13c36-103">Üst bilgisinden başlayarak, Microsoft ara dili (MSIL) kodundaki bir yöntemin gövdesine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="13c36-103">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c36-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="13c36-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13c36-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13c36-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="13c36-106">'ndaki İşlevin bulunduğu modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="13c36-106">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="13c36-107">'ndaki Yöntemi için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="13c36-107">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="13c36-108">dışı Metodun üstbilgisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="13c36-108">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="13c36-109">dışı Yöntemin boyutunu belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="13c36-109">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13c36-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13c36-110">Remarks</span></span>  
 <span data-ttu-id="13c36-111">Bir yöntem, bulunduğu modülün kapsamına alınır.</span><span class="sxs-lookup"><span data-stu-id="13c36-111">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="13c36-112">Yöntemi, `GetILFunctionBody` ortak dil çalışma zamanı (CLR) tarafından yüklenmeden önce MSIL koduna bir araç erişimi vermek üzere tasarlandığından, istenen örneği bulmak için yönteminin meta veri belirtecini kullanır.</span><span class="sxs-lookup"><span data-stu-id="13c36-112">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="13c36-113">`GetILFunctionBody``methodId`herhangi BIR MSIL kodu (soyut bir yöntem veya platform çağırma (PInvoke) yöntemi) olmadan bir yönteme işaret ediyorsa, bir CORPROF_E_FUNCTION_NOT_IL hresult döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="13c36-113">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c36-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13c36-114">Requirements</span></span>  
 <span data-ttu-id="13c36-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13c36-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c36-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="13c36-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="13c36-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="13c36-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13c36-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13c36-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c36-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13c36-119">See also</span></span>

- [<span data-ttu-id="13c36-120">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13c36-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
