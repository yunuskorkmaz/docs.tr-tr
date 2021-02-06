---
description: ': ICorProfilerInfo:: GetCurrentThreadID yöntemi hakkında daha fazla bilgi edinin'
title: ICorProfilerInfo::GetCurrentThreadID Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
ms.openlocfilehash: 562c6cb61f13e9ab568d18c7d179872cbc7cdb06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647650"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="29eeb-103">ICorProfilerInfo::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="29eeb-103">ICorProfilerInfo::GetCurrentThreadID Method</span></span>

<span data-ttu-id="29eeb-104">Yönetilen bir iş parçacığı ise, geçerli iş parçacığının KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="29eeb-104">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29eeb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29eeb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29eeb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29eeb-106">Parameters</span></span>  

 `pThreadId`  
 <span data-ttu-id="29eeb-107">dışı Yönetilen iş parçacığının döndürülen KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="29eeb-107">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29eeb-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29eeb-108">Remarks</span></span>  

 <span data-ttu-id="29eeb-109">Geçerli iş parçacığı bir iç çalışma zamanı iş parçacığı veya diğer yönetilmeyen iş parçacığıdır, `GetCurrentThreadID` hresult olarak CORPROF_E_NOT_MANAGED_THREAD döndürür ve parametre döndürülen değeri `pThreadId` null olur.</span><span class="sxs-lookup"><span data-stu-id="29eeb-109">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29eeb-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29eeb-110">Requirements</span></span>  

 <span data-ttu-id="29eeb-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29eeb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29eeb-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="29eeb-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="29eeb-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="29eeb-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29eeb-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29eeb-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29eeb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29eeb-115">See also</span></span>

- [<span data-ttu-id="29eeb-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29eeb-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
