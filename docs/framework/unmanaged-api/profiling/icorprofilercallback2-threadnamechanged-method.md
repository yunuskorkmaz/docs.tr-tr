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
ms.openlocfilehash: 3eb108ed20d0fd1287cb82eb4d552206aeae15d4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499733"
---
# <a name="icorprofilercallback2threadnamechanged-method"></a><span data-ttu-id="cd93d-102">ICorProfilerCallback2::ThreadNameChanged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cd93d-102">ICorProfilerCallback2::ThreadNameChanged Method</span></span>
<span data-ttu-id="cd93d-103">Kod Profilcisi bir iş parçacığı adının değiştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="cd93d-103">Notifies the code profiler that the name of a thread has changed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd93d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="cd93d-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadNameChanged(  
    [in] ThreadID threadId,  
    [in] ULONG cchName,  
    [in] WCHAR name[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd93d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cd93d-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="cd93d-106">'ndaki İş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="cd93d-106">[in] The ID of the thread.</span></span>  
  
 `cchName`  
 <span data-ttu-id="cd93d-107">'ndaki İş parçacığının yeni adının uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="cd93d-107">[in] The length of the new name of the thread.</span></span>  
  
 `name`  
 <span data-ttu-id="cd93d-108">'ndaki İş parçacığının yeni adı.</span><span class="sxs-lookup"><span data-stu-id="cd93d-108">[in] The new name of the thread.</span></span> <span data-ttu-id="cd93d-109">Ad, null ile Sonlandırılmamış.</span><span class="sxs-lookup"><span data-stu-id="cd93d-109">The name is not null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd93d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cd93d-110">Requirements</span></span>  
 <span data-ttu-id="cd93d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd93d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd93d-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cd93d-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd93d-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cd93d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd93d-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd93d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd93d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cd93d-115">See also</span></span>

- [<span data-ttu-id="cd93d-116">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd93d-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="cd93d-117">ICorProfilerCallback2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cd93d-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
