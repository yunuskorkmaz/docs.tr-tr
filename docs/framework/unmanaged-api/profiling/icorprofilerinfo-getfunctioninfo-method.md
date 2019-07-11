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
ms.openlocfilehash: b4b39e53af7abaf25cc4a563bfbec8450b1e57d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780660"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="2f867-102">ICorProfilerInfo::GetFunctionInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="2f867-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="2f867-103">Belirtilen işlev için üst sınıf ve meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="2f867-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f867-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f867-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f867-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2f867-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="2f867-106">[in] Üst sınıf ve meta veri belirteci almak işlev kimliği.</span><span class="sxs-lookup"><span data-stu-id="2f867-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="2f867-107">[out] İşlevin üst sınıfı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2f867-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="2f867-108">[out] İşlevin üst sınıfı içinde tanımlandığı modül için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2f867-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="2f867-109">[out] Meta veri belirteci işlevine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2f867-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f867-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2f867-110">Remarks</span></span>  
 <span data-ttu-id="2f867-111">Profil Oluşturucu kodu çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) belirli bir modül için bir meta veri arabirimi elde edilir.</span><span class="sxs-lookup"><span data-stu-id="2f867-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="2f867-112">Tarafından başvurulan konuma döndürülen meta veri belirteci `pToken` işlevi için meta veriler erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2f867-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="2f867-113">`ClassID` Genel sınıfta bir işlevin hakkında daha fazla bağlamsal bilgi işlevi kullanımı elde edilebilir olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2f867-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="2f867-114">Bu durumda, `pClassId` 0 olur.</span><span class="sxs-lookup"><span data-stu-id="2f867-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="2f867-115">Profiler kod kullanması gereken [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) daha fazla bağlam sağlamak için COR_PRF_FRAME_INFO değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="2f867-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f867-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f867-116">Requirements</span></span>  
 <span data-ttu-id="2f867-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f867-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f867-118">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f867-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f867-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f867-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f867-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f867-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f867-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f867-121">See also</span></span>

- [<span data-ttu-id="2f867-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f867-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
