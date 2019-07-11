---
title: ICorProfilerCallback::ModuleUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8dd5e2ecf22ce14765df8972611f1f95109f76ed
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769204"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="dce10-102">ICorProfilerCallback::ModuleUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dce10-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="dce10-103">Profil Oluşturucu, bir modül kaldırma işleminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="dce10-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dce10-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dce10-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dce10-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dce10-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="dce10-106">[in] Kaldırılmış olan modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="dce10-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="dce10-107">[in] Modül başarıyla kaldırılmış olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="dce10-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dce10-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dce10-108">Remarks</span></span>  
 <span data-ttu-id="dce10-109">Değerini `moduleId` sonra bir bilgi isteği için geçerli değil [Icorprofilercallback::moduleunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="dce10-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="dce10-110">Sınıf kaldırılması, bazı bölümleri sonra devam edebilir `ModuleUnloadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="dce10-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="dce10-111">Bir hata HRESULT içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="dce10-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="dce10-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk parçası modül kaldırma işleminin başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="dce10-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dce10-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dce10-113">Requirements</span></span>  
 <span data-ttu-id="dce10-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dce10-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dce10-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dce10-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dce10-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dce10-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dce10-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dce10-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce10-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dce10-118">See also</span></span>

- [<span data-ttu-id="dce10-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dce10-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
