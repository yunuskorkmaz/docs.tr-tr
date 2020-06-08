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
ms.openlocfilehash: fa0fe827300a86a906a254292434e2a56ebb4a47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498407"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="1bcaa-102">ICorProfilerInfo::GetCurrentThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="1bcaa-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="1bcaa-103">Yönetilen bir iş parçacığı ise, geçerli iş parçacığının KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="1bcaa-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bcaa-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1bcaa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bcaa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1bcaa-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="1bcaa-106">dışı Yönetilen iş parçacığının döndürülen KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1bcaa-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bcaa-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bcaa-107">Remarks</span></span>  
 <span data-ttu-id="1bcaa-108">Geçerli iş parçacığı bir iç çalışma zamanı iş parçacığı veya diğer yönetilmeyen iş parçacığıdır, `GetCurrentThreadID` hresult olarak CORPROF_E_NOT_MANAGED_THREAD döndürür ve parametre döndürülen değeri `pThreadId` null olur.</span><span class="sxs-lookup"><span data-stu-id="1bcaa-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bcaa-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1bcaa-109">Requirements</span></span>  
 <span data-ttu-id="1bcaa-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bcaa-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bcaa-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1bcaa-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1bcaa-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1bcaa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bcaa-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bcaa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bcaa-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bcaa-114">See also</span></span>

- [<span data-ttu-id="1bcaa-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bcaa-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
