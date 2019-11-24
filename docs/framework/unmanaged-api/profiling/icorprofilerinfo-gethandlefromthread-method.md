---
title: ICorProfilerInfo::GetHandleFromThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: e508ccd81d25aa3d303456fa88554903ec71d633
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439059"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="d8426-102">ICorProfilerInfo::GetHandleFromThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8426-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="d8426-103">Maps the ID of a thread to a Win32 thread handle.</span><span class="sxs-lookup"><span data-stu-id="d8426-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8426-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8426-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8426-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8426-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="d8426-106">[in] The thread ID to be mapped.</span><span class="sxs-lookup"><span data-stu-id="d8426-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="d8426-107">[out] A pointer to a Win32 thread handle.</span><span class="sxs-lookup"><span data-stu-id="d8426-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8426-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8426-108">Remarks</span></span>  
 <span data-ttu-id="d8426-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span><span class="sxs-lookup"><span data-stu-id="d8426-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8426-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8426-110">Requirements</span></span>  
 <span data-ttu-id="d8426-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8426-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8426-112">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d8426-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d8426-113">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8426-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8426-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8426-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8426-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8426-115">See also</span></span>

- [<span data-ttu-id="d8426-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8426-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
