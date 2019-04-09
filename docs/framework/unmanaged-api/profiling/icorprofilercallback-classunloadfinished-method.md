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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160712"
---
# <a name="icorprofilercallbackclassunloadfinished-method"></a><span data-ttu-id="abfac-102">ICorProfilerCallback::ClassUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="abfac-102">ICorProfilerCallback::ClassUnloadFinished Method</span></span>
<span data-ttu-id="abfac-103">Profil Oluşturucu, bir sınıf kaldırma işleminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="abfac-103">Notifies the profiler that a class has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abfac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="abfac-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abfac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="abfac-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="abfac-106">[in] Kaldırılmış olan bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="abfac-106">[in] Identifies the class that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="abfac-107">[in] Sınıf başarıyla kaldırılmış olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="abfac-107">[in] An HRESULT that indicates whether the class was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abfac-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="abfac-108">Remarks</span></span>  
 <span data-ttu-id="abfac-109">Sınıf kaldırılması, bazı bölümleri sonra devam edebilir `ClassUnloadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="abfac-109">Some parts of unloading the class might continue after the `ClassUnloadFinished` callback.</span></span> <span data-ttu-id="abfac-110">Bir hata HRESULT içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="abfac-110">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="abfac-111">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk parçası sınıfı kaldırma işleminin başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="abfac-111">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abfac-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abfac-112">Requirements</span></span>  
 <span data-ttu-id="abfac-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abfac-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abfac-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="abfac-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="abfac-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abfac-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="abfac-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="abfac-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="abfac-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abfac-117">See also</span></span>

- [<span data-ttu-id="abfac-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abfac-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="abfac-119">ClassUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="abfac-119">ClassUnloadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)
