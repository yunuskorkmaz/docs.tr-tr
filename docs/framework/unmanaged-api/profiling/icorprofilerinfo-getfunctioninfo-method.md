---
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
ms.openlocfilehash: 823cc5638ff3e0955aca0bd9ba5795f6b369c6b0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863627"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="8fab5-102">ICorProfilerInfo::GetFunctionInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="8fab5-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="8fab5-103">Belirtilen işlev için üst sınıfı ve meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="8fab5-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fab5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fab5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fab5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8fab5-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="8fab5-106">'ndaki Üst sınıfı ve meta veri belirtecinin alınacağı işlevin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8fab5-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="8fab5-107">dışı İşlevin üst sınıfına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8fab5-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="8fab5-108">dışı İşlevin üst sınıfının tanımlandığı modüle yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8fab5-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="8fab5-109">dışı İşlevin meta veri belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8fab5-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fab5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fab5-110">Remarks</span></span>  
 <span data-ttu-id="8fab5-111">Profil Oluşturucu kodu, belirli bir modül için meta veri arabirimi elde etmek üzere [ICorProfilerInfo:: GetModuleMetaData öğesini](icorprofilerinfo-getmodulemetadata-method.md) çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="8fab5-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="8fab5-112">`pToken` tarafından başvurulan konuma döndürülen meta veri belirteci, daha sonra işlevin meta verilerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8fab5-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="8fab5-113">Bir genel sınıftaki işlevin `ClassID`, işlevin kullanımı hakkında daha fazla bağlamsal bilgi olmadan bilgiler kişilerden olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="8fab5-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="8fab5-114">Bu durumda, `pClassId` 0 olur.</span><span class="sxs-lookup"><span data-stu-id="8fab5-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="8fab5-115">Profil Oluşturucu kodu, daha fazla bağlam sağlamak için bir COR_PRF_FRAME_INFO değeri ile [ICorProfilerInfo2:: GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8fab5-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fab5-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8fab5-116">Requirements</span></span>  
 <span data-ttu-id="8fab5-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fab5-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fab5-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8fab5-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8fab5-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8fab5-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fab5-120">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fab5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fab5-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fab5-121">See also</span></span>

- [<span data-ttu-id="8fab5-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8fab5-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
