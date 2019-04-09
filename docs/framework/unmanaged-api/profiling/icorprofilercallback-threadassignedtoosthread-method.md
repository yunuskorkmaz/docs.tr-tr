---
title: ICorProfilerCallback::ThreadAssignedToOSThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eefcd4436a28fdf52cbe55da5d4bb7eea4449463
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158463"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="65e8e-102">ICorProfilerCallback::ThreadAssignedToOSThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65e8e-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="65e8e-103">Profil Oluşturucu, belirli bir işletim sistemi iş parçacığı kullanarak bir yönetilen iş parçacığı uygulanan olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="65e8e-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65e8e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65e8e-104">Syntax</span></span>  
  
```  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65e8e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65e8e-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="65e8e-106">[in] Yönetilen iş parçacığı tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="65e8e-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="65e8e-107">[in] İşletim sistemi iş parçacığı tanıtıcısı.</span><span class="sxs-lookup"><span data-stu-id="65e8e-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65e8e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65e8e-108">Remarks</span></span>  
 <span data-ttu-id="65e8e-109">`ThreadAssignedToOSThread` Geri çağırma profil oluşturucu iyileştirmesini işletim sistemi iş parçacığı yönetilen iş parçacıkları arasında doğru bir eşleme tutmak bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="65e8e-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65e8e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65e8e-110">Requirements</span></span>  
 <span data-ttu-id="65e8e-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65e8e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65e8e-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65e8e-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65e8e-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65e8e-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="65e8e-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="65e8e-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="65e8e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="65e8e-115">See also</span></span>

- [<span data-ttu-id="65e8e-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65e8e-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
