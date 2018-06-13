---
title: ICorProfilerInfo::GetThreadInfo Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f68565977551a54244f3caf6a0250f67005a6ecf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452888"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="dc27d-102">ICorProfilerInfo::GetThreadInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="dc27d-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="dc27d-103">Geçerli Win32 iş parçacığı kimliği için belirtilen iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="dc27d-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc27d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc27d-104">Syntax</span></span>  
  
```  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dc27d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc27d-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="dc27d-106">[in] Win32 geçerli kimliği edinmek için iş parçacığı kimliği</span><span class="sxs-lookup"><span data-stu-id="dc27d-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="dc27d-107">[out] Belirtilen iş parçacığının geçerli Win32 iş parçacığı için bir işaretçi kimliği</span><span class="sxs-lookup"><span data-stu-id="dc27d-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc27d-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc27d-108">Requirements</span></span>  
 <span data-ttu-id="dc27d-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc27d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc27d-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dc27d-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc27d-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dc27d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc27d-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc27d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc27d-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc27d-113">See Also</span></span>  
 [<span data-ttu-id="dc27d-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc27d-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
