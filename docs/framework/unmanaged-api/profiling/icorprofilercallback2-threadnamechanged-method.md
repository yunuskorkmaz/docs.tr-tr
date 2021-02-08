---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback2:: ThreadNameChanged yöntemi'
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
ms.openlocfilehash: 161247f9692d1307d063e244b200eb0d8f739e9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799050"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="46454-103">ICorProfilerCallback2::ThreadNameChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="46454-103">ICorProfilerCallback2::ThreadNameChanged Method</span></span>

<span data-ttu-id="46454-104">Kod Profilcisi bir iş parçacığı adının değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="46454-104">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46454-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46454-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46454-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="46454-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="46454-107">'ndaki İş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="46454-107">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="46454-108">'ndaki İş parçacığının yeni adının uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="46454-108">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="46454-109">'ndaki İş parçacığının yeni adı.</span><span class="sxs-lookup"><span data-stu-id="46454-109">[in] The new name of the thread.</span></span> <span data-ttu-id="46454-110">Ad, null ile Sonlandırılmamış.</span><span class="sxs-lookup"><span data-stu-id="46454-110">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46454-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46454-111">Requirements</span></span>  

 <span data-ttu-id="46454-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46454-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46454-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="46454-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46454-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="46454-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46454-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46454-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46454-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46454-116">See also</span></span>

- [<span data-ttu-id="46454-117">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46454-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="46454-118">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="46454-118">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
