---
description: ': ICorProfilerInfo:: GetFunctionInfo metodu hakkında daha fazla bilgi edinin'
title: ICorProfilerInfo::GetFunctionInfo Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
ms.openlocfilehash: e6ad1112f0e6938fc6de549d3a1d2f0901150025
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647560"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="1997e-103">ICorProfilerInfo::GetFunctionInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="1997e-103">ICorProfilerInfo::GetFunctionInfo Method</span></span>

<span data-ttu-id="1997e-104">Belirtilen işlev için üst sınıfı ve meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="1997e-104">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1997e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1997e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1997e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1997e-106">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="1997e-107">'ndaki Üst sınıfı ve meta veri belirtecinin alınacağı işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1997e-107">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="1997e-108">dışı İşlevin üst sınıfına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1997e-108">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="1997e-109">dışı İşlevin üst sınıfının tanımlandığı modüle yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1997e-109">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="1997e-110">dışı İşlevin meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1997e-110">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1997e-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1997e-111">Remarks</span></span>  

 <span data-ttu-id="1997e-112">Profil Oluşturucu kodu, belirli bir modül için meta veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](icorprofilerinfo-getmodulemetadata-method.md) çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="1997e-112">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="1997e-113">Tarafından başvurulan konuma döndürülen meta veri belirteci, `pToken` daha sonra işlevin meta verilerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1997e-113">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="1997e-114">`ClassID`Bir genel sınıftaki işlevin kullanımı, işlevin kullanımıyla ilgili daha fazla bağlamsal bilgi olmadan bilgiler kişilerden olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1997e-114">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="1997e-115">Bu durumda `pClassId` 0 olur.</span><span class="sxs-lookup"><span data-stu-id="1997e-115">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="1997e-116">Profil Oluşturucu kodu, daha fazla bağlam sağlamak için bir COR_PRF_FRAME_INFO değeri ile [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1997e-116">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1997e-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1997e-117">Requirements</span></span>  

 <span data-ttu-id="1997e-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1997e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1997e-119">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1997e-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1997e-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1997e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1997e-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1997e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1997e-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1997e-122">See also</span></span>

- [<span data-ttu-id="1997e-123">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1997e-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
