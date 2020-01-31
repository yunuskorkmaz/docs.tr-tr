---
title: ICorProfilerCallback::ClassUnloadStarted Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassUnloadStarted
helpviewer_keywords:
- ClassUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::ClassUnloadStarted method [.NET Framework profiling]
ms.assetid: bc93bead-f3a9-415c-b919-ddd3ca80facc
topic_type:
- apiref
ms.openlocfilehash: 75fb92be078c40f49ddcdc6662535b2a0be7a6ad
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866565"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="83578-102">ICorProfilerCallback::ClassUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83578-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="83578-103">Profil oluşturucuyu bir sınıfın kaldırılmakta olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="83578-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83578-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83578-104">Syntax</span></span>  
  
```cpp  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83578-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83578-105">Parameters</span></span>

- `classId`

  <span data-ttu-id="83578-106">\[içindeki], bellekten kaldırılan sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="83578-106">\[in] Identifies the class that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="83578-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83578-107">Remarks</span></span>  
 <span data-ttu-id="83578-108">`classId` değeri `ClassUnloadStarted` yöntemi çağrıldıktan sonra bir bilgi isteği için geçerli değil — bu sınıf hakkında bilgi almak için profil oluşturucunun son şansı budur.</span><span class="sxs-lookup"><span data-stu-id="83578-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83578-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83578-109">Requirements</span></span>  
 <span data-ttu-id="83578-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83578-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83578-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="83578-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83578-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="83578-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83578-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83578-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83578-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83578-114">See also</span></span>

- [<span data-ttu-id="83578-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83578-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="83578-116">ClassUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83578-116">ClassUnloadFinished Method</span></span>](icorprofilercallback-classunloadfinished-method.md)
