---
title: ICorProfilerCallback2::ThreadNameChanged Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.ThreadNameChanged
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::ThreadNameChanged
helpviewer_keywords:
- ThreadNameChanged method [.NET Framework profiling]
- ICorProfilerCallback2::ThreadNameChanged method [.NET Framework profiling]
ms.assetid: c8bbd76d-a9ff-44f2-87a6-be052819da36
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dbd9374decdce171d45e57512470c652abc24882
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782635"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="1613c-102">ICorProfilerCallback2::ThreadNameChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1613c-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="1613c-103">Kod profil oluşturucu, bir iş parçacığı adı değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="1613c-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1613c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1613c-104">Syntax</span></span>  
  
```  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1613c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1613c-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="1613c-106">[in] İş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="1613c-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1613c-107">[in] Yeni iş parçacığının adı uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="1613c-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="1613c-108">[in] Yeni iş parçacığı adı.</span><span class="sxs-lookup"><span data-stu-id="1613c-108">[in] The new name of the thread.</span></span> <span data-ttu-id="1613c-109">Ad null ile sonlanmıyor.</span><span class="sxs-lookup"><span data-stu-id="1613c-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1613c-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1613c-110">Requirements</span></span>  
 <span data-ttu-id="1613c-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1613c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1613c-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1613c-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1613c-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1613c-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1613c-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1613c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1613c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1613c-115">See also</span></span>

- [<span data-ttu-id="1613c-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1613c-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="1613c-117">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1613c-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
