---
title: ICorProfilerCallback::ClassUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadFinished
helpviewer_keywords:
- ICorProfilerCallback::ClassUnloadFinished method [.NET Framework profiling]
- ClassUnloadFinished method [.NET Framework profiling]
ms.assetid: 55674b68-678a-4747-ae06-4e91519c7305
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d01f3d7485b19c076d9cd3e83aeccbcf5e728f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597986"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="84991-102">ICorProfilerCallback::ClassUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84991-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="84991-103">Profil Oluşturucu, bir sınıf kaldırma işleminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="84991-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84991-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="84991-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84991-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="84991-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="84991-106">[in] Kaldırılmış olan bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="84991-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="84991-107">[in] Sınıf başarıyla kaldırılmış olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="84991-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84991-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="84991-108">Remarks</span></span>  
 <span data-ttu-id="84991-109">Sınıf kaldırılması, bazı bölümleri sonra devam edebilir `ClassUnloadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="84991-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="84991-110">Bir hata HRESULT içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="84991-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="84991-111">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk parçası sınıfı kaldırma işleminin başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="84991-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84991-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="84991-112">Requirements</span></span>  
 <span data-ttu-id="84991-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84991-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84991-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="84991-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="84991-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84991-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84991-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84991-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84991-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="84991-117">See also</span></span>

- [<span data-ttu-id="84991-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="84991-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="84991-119">ClassUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="84991-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
