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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8db6912700b199c64d2ebf0f7bd2ccd8939af9b6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484712"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="43769-102">ICorProfilerInfo::GetFunctionInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="43769-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="43769-103">Belirtilen işlev için üst sınıf ve meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="43769-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43769-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43769-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43769-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43769-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="43769-106">[in] Üst sınıf ve meta veri belirteci almak işlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="43769-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="43769-107">[out] İşlevin üst sınıfı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43769-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="43769-108">[out] İşlevin üst sınıfı içinde tanımlandığı modül için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43769-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="43769-109">[out] Meta veri belirteci işlevine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43769-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43769-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43769-110">Remarks</span></span>  
 <span data-ttu-id="43769-111">Profil Oluşturucu kodu çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) belirli bir modül için bir meta veri arabirimi elde edilir.</span><span class="sxs-lookup"><span data-stu-id="43769-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="43769-112">Tarafından başvurulan konuma döndürülen meta veri belirteci `pToken` işlevi için meta veriler erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="43769-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="43769-113">`ClassID` Genel sınıfta bir işlevin hakkında daha fazla bağlamsal bilgi işlevi kullanımı elde edilebilir olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="43769-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="43769-114">Bu durumda, `pClassId` 0 olur.</span><span class="sxs-lookup"><span data-stu-id="43769-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="43769-115">Profiler kod kullanması gereken [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) daha fazla bağlam sağlamak için COR_PRF_FRAME_INFO değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="43769-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43769-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43769-116">Requirements</span></span>  
 <span data-ttu-id="43769-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43769-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43769-118">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="43769-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="43769-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43769-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43769-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43769-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43769-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43769-121">See also</span></span>
- [<span data-ttu-id="43769-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43769-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
