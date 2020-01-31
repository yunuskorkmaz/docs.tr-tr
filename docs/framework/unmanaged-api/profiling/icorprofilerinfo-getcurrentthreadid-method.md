---
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
ms.openlocfilehash: e70d8ee40e16e37a12f8ed4033d2aa7489f0f25e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863967"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="f9c25-102">ICorProfilerInfo::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="f9c25-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="f9c25-103">Yönetilen bir iş parçacığı ise, geçerli iş parçacığının KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="f9c25-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9c25-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f9c25-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9c25-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f9c25-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="f9c25-106">dışı Yönetilen iş parçacığının döndürülen KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f9c25-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9c25-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9c25-107">Remarks</span></span>  
 <span data-ttu-id="f9c25-108">Geçerli iş parçacığı bir iç çalışma zamanı iş parçacığı veya diğer yönetilmeyen iş parçacığıdır, `GetCurrentThreadID` HRESULT olarak CORPROF_E_NOT_MANAGED_THREAD döndürür ve `pThreadId` parametresinin döndürülen değeri null olur.</span><span class="sxs-lookup"><span data-stu-id="f9c25-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9c25-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f9c25-109">Requirements</span></span>  
 <span data-ttu-id="f9c25-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9c25-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9c25-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f9c25-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9c25-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f9c25-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9c25-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9c25-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9c25-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9c25-114">See also</span></span>

- [<span data-ttu-id="f9c25-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9c25-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
