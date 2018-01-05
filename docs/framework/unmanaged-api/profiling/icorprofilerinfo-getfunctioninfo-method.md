---
title: ICorProfilerInfo::GetFunctionInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetFunctionInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17512077ef7a8ca45fa76c00f93612015948d083
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="e07d4-102">ICorProfilerInfo::GetFunctionInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="e07d4-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="e07d4-103">Üst sınıf ve meta verileri belirtilen işlevi için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="e07d4-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e07d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e07d4-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e07d4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e07d4-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e07d4-106">[in] İşlevi için meta verileri ve üst sınıf belirteci almak istediğiniz kimliği.</span><span class="sxs-lookup"><span data-stu-id="e07d4-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="e07d4-107">[out] İşlev üst sınıfı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e07d4-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="e07d4-108">[out] İşlevin üst sınıf tanımlandığı modül için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e07d4-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="e07d4-109">[out] İşlev için meta veri simgesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e07d4-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e07d4-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e07d4-110">Remarks</span></span>  
 <span data-ttu-id="e07d4-111">Profil Oluşturucu kod çağırabilir [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) belirli bir modül için bir meta veri arabirimi elde edilir.</span><span class="sxs-lookup"><span data-stu-id="e07d4-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="e07d4-112">Tarafından başvurulan konuma döndürülen meta veri simgesi `pToken` işlevi için meta verilerine erişmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e07d4-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="e07d4-113">`ClassID` İşlevinin genel bir sınıf üzerinde daha fazla bağlamsal işlevinin kullanımı hakkında bilgi elde edilebilir olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e07d4-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="e07d4-114">Bu durumda, `pClassId` 0 olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e07d4-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="e07d4-115">Profil Oluşturucu kodu kullanması gereken [Icorprofilerınfo2::getfunctionınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) daha fazla içerik sağlamak için COR_PRF_FRAME_INFO değerine sahip.</span><span class="sxs-lookup"><span data-stu-id="e07d4-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e07d4-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e07d4-116">Requirements</span></span>  
 <span data-ttu-id="e07d4-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e07d4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e07d4-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e07d4-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e07d4-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e07d4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e07d4-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e07d4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e07d4-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e07d4-121">See Also</span></span>  
 [<span data-ttu-id="e07d4-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e07d4-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
