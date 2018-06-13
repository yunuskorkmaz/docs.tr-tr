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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c30fb5d5576a7bed403f48504ead923df212de9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450381"
---
# <a name="icorprofilercallbackclassunloadstarted-method"></a><span data-ttu-id="52371-102">ICorProfilerCallback::ClassUnloadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52371-102">ICorProfilerCallback::ClassUnloadStarted Method</span></span>
<span data-ttu-id="52371-103">Profil Oluşturucu bir sınıf yüklenmemiş olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="52371-103">Notifies the profiler that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52371-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52371-104">Syntax</span></span>  
  
```  
HRESULT ClassUnloadStarted(  
    [in] ClassID classId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52371-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52371-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="52371-106">[in] Boşaltılıyor sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="52371-106">[in] Identifies the class that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52371-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52371-107">Remarks</span></span>  
 <span data-ttu-id="52371-108">Değeri `classId` sonra bir bilgi isteği için geçerli değil `ClassUnloadStarted` yöntemi döndürür — bu bu sınıfı hakkında bilgi edinmek için Profil Oluşturucu'nın son şansınızdır.</span><span class="sxs-lookup"><span data-stu-id="52371-108">The value of `classId` is not valid for an information request after the `ClassUnloadStarted` method returns — this is the profiler's last chance to obtain information about this class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52371-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52371-109">Requirements</span></span>  
 <span data-ttu-id="52371-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52371-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52371-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="52371-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52371-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52371-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52371-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52371-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52371-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="52371-114">See Also</span></span>  
 [<span data-ttu-id="52371-115">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="52371-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="52371-116">ClassUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="52371-116">ClassUnloadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)
