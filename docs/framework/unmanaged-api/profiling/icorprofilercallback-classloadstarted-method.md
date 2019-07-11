---
title: ICorProfilerCallback::ClassLoadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadStarted
helpviewer_keywords:
- ICorProfilerCallback::ClassLoadStarted method [.NET Framework profiling]
- ClassLoadStarted method [.NET Framework profiling]
ms.assetid: 9f728de8-45c2-45a5-ac4a-45660bd36ecf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84ff6cb79abdb60a3c01c66580ed6fc10f6c137e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762940"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="4734f-102">ICorProfilerCallback::ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4734f-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="4734f-103">Profil Oluşturucu, bir sınıf yüklü olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="4734f-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4734f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4734f-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4734f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4734f-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4734f-106">[in] Yüklenmekte sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4734f-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4734f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4734f-107">Remarks</span></span>  
 <span data-ttu-id="4734f-108">Değerini `classId` kadar bir bilgi isteği için geçerli değil [Icorprofilercallback::classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="4734f-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4734f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4734f-109">Requirements</span></span>  
 <span data-ttu-id="4734f-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4734f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4734f-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4734f-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4734f-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4734f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4734f-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4734f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4734f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4734f-114">See also</span></span>

- [<span data-ttu-id="4734f-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4734f-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
