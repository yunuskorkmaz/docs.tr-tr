---
description: ': ICorProfilerInfo:: GetThreadContext metodu hakkında daha fazla bilgi edinin'
title: ICorProfilerInfo::GetThreadContext Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
ms.openlocfilehash: b2970da90250819cc68eee55b70188d4830113a6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687280"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="899a9-103">ICorProfilerInfo::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="899a9-103">ICorProfilerInfo::GetThreadContext Method</span></span>

<span data-ttu-id="899a9-104">Belirtilen iş parçacığıyla Şu anda ilişkili olan bağlam Kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="899a9-104">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="899a9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="899a9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="899a9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="899a9-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="899a9-107">'ndaki İş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="899a9-107">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="899a9-108">dışı Şu anda belirtilen iş parçacığıyla ilişkilendirilen bağlam KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="899a9-108">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="899a9-109">İş parçacığında şu anda ilişkili bir bağlam yoksa, bu işlev CORPROF_E_DATAINCOMPLETE döndürür.</span><span class="sxs-lookup"><span data-stu-id="899a9-109">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="899a9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="899a9-110">Requirements</span></span>  

 <span data-ttu-id="899a9-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="899a9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="899a9-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="899a9-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="899a9-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="899a9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="899a9-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="899a9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="899a9-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="899a9-115">See also</span></span>

- [<span data-ttu-id="899a9-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="899a9-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
