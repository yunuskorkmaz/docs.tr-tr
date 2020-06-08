---
title: ICorProfilerInfo2::GetThreadAppDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
ms.openlocfilehash: 70535f8bcee95c2596c43617eb5893e2d92a355b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496787"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="500a6-102">ICorProfilerInfo2::GetThreadAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="500a6-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="500a6-103">Belirtilen iş parçacığının kodu çalıştırmakta olduğu uygulama etki alanının KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="500a6-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="500a6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="500a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="500a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="500a6-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="500a6-106">'ndaki İş parçacığını belirten KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="500a6-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="500a6-107">dışı Uygulama etki alanının KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="500a6-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="500a6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="500a6-108">Requirements</span></span>  
 <span data-ttu-id="500a6-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="500a6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="500a6-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="500a6-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="500a6-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="500a6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="500a6-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="500a6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="500a6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="500a6-113">See also</span></span>

- [<span data-ttu-id="500a6-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="500a6-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="500a6-115">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="500a6-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
