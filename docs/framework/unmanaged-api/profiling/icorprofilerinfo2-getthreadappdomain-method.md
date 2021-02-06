---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerInfo2:: GetThreadAppDomain Yöntemi'
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
ms.openlocfilehash: b480388254a6ee84db9f6c3e8d44b7358246502a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647069"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="b1ac5-103">ICorProfilerInfo2::GetThreadAppDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b1ac5-103">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>

<span data-ttu-id="b1ac5-104">Belirtilen iş parçacığının kodu çalıştırmakta olduğu uygulama etki alanının KIMLIĞINI alır.</span><span class="sxs-lookup"><span data-stu-id="b1ac5-104">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1ac5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b1ac5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1ac5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b1ac5-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="b1ac5-107">'ndaki İş parçacığını belirten KIMLIK.</span><span class="sxs-lookup"><span data-stu-id="b1ac5-107">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="b1ac5-108">dışı Uygulama etki alanının KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b1ac5-108">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1ac5-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b1ac5-109">Requirements</span></span>  

 <span data-ttu-id="b1ac5-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1ac5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1ac5-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b1ac5-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b1ac5-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b1ac5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1ac5-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1ac5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1ac5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1ac5-114">See also</span></span>

- [<span data-ttu-id="b1ac5-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1ac5-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="b1ac5-116">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b1ac5-116">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
