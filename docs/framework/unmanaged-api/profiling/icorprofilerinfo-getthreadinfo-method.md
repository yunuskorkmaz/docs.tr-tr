---
title: ICorProfilerInfo::GetThreadInfo Yöntemi
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
ms.openlocfilehash: 405d5ff49ba7bc2e5204f00cf50c30822354e56d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775590"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="f2cfc-102">ICorProfilerInfo::GetThreadInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2cfc-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="f2cfc-103">Belirtilen iş parçacığı için geçerli bir Win32 iş parçacığı kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="f2cfc-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2cfc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2cfc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2cfc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2cfc-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="f2cfc-106">[in] Geçerli Win32 kimliği alınacağı iş parçacığının kimliği</span><span class="sxs-lookup"><span data-stu-id="f2cfc-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="f2cfc-107">[out] Bir işaretçi belirtilen iş parçacığının geçerli Win32 iş parçacığı kimliği</span><span class="sxs-lookup"><span data-stu-id="f2cfc-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2cfc-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2cfc-108">Requirements</span></span>  
 <span data-ttu-id="f2cfc-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2cfc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2cfc-110">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2cfc-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2cfc-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2cfc-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2cfc-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2cfc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2cfc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2cfc-113">See also</span></span>

- [<span data-ttu-id="f2cfc-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2cfc-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
