---
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acb4d67f41b1434fe8052a74e976907f24fecd31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453583"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="1e41e-102">ICorProfilerInfo::GetThreadContext Metodu</span><span class="sxs-lookup"><span data-stu-id="1e41e-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="1e41e-103">Şu anda belirtilen iş parçacığı ile ilişkili bağlam kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="1e41e-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e41e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e41e-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e41e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e41e-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="1e41e-106">[in] İş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="1e41e-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="1e41e-107">[out] Şu anda belirtilen iş parçacığı ile ilişkili içerik kimliği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e41e-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="1e41e-108">İş parçacığı şu anda ilişkili bağlam varsa, bu işlev CORPROF_E_DATAINCOMPLETE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1e41e-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e41e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e41e-109">Requirements</span></span>  
 <span data-ttu-id="1e41e-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e41e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e41e-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1e41e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1e41e-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e41e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e41e-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e41e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e41e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e41e-114">See Also</span></span>  
 [<span data-ttu-id="1e41e-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e41e-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
