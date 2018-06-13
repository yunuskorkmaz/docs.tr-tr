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
ms.openlocfilehash: df70041497f000bfd4f6dcac2713e8d5e4eb33f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450950"
---
# <a name="icorprofilercallbackclassloadstarted-method"></a><span data-ttu-id="80ef1-102">ICorProfilerCallback::ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80ef1-102">ICorProfilerCallback::ClassLoadStarted Method</span></span>
<span data-ttu-id="80ef1-103">Profil Oluşturucu bir sınıf yüklü olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="80ef1-103">Notifies the profiler that a class is being loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ef1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80ef1-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80ef1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80ef1-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="80ef1-106">[in] Yüklenmekte sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="80ef1-106">[in] Identifies the class that is being loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80ef1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80ef1-107">Remarks</span></span>  
 <span data-ttu-id="80ef1-108">Değeri `classId` kadar bilgi isteği için geçerli değil [Icorprofilercallback::classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="80ef1-108">The value of `classId` is not valid for an information request until the [ICorProfilerCallback::ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80ef1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80ef1-109">Requirements</span></span>  
 <span data-ttu-id="80ef1-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80ef1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80ef1-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="80ef1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="80ef1-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80ef1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80ef1-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80ef1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ef1-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="80ef1-114">See Also</span></span>  
 [<span data-ttu-id="80ef1-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80ef1-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
