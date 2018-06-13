---
title: ICorProfilerCallback::FunctionUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e28aef4916d06218953236e3b29e19c68822bd6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451194"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="1b012-102">ICorProfilerCallback::FunctionUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b012-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="1b012-103">Profil oluşturucu işlevi kaldırmak çalışma zamanı başlatıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="1b012-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b012-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b012-104">Syntax</span></span>  
  
```  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b012-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b012-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="1b012-106">[in] Boşaltılıyor işlevi kimliği.</span><span class="sxs-lookup"><span data-stu-id="1b012-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b012-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1b012-107">Remarks</span></span>  
 <span data-ttu-id="1b012-108">Değeri `functionId` parametresi geçerli artık bu metodu çağıran döndükten sonra.</span><span class="sxs-lookup"><span data-stu-id="1b012-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b012-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b012-109">Requirements</span></span>  
 <span data-ttu-id="1b012-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b012-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b012-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1b012-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b012-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b012-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b012-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b012-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b012-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1b012-114">See Also</span></span>  
 [<span data-ttu-id="1b012-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b012-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
