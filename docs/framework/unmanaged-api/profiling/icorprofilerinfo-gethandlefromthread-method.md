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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fc26ad9b25ad243bf868d6ef3155360509e6483
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049589"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="83c9a-102">ICorProfilerInfo::GetHandleFromThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="83c9a-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="83c9a-103">Bir iş parçacığının kimliği bir Win32 iş parçacığı tutamacı eşler.</span><span class="sxs-lookup"><span data-stu-id="83c9a-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83c9a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="83c9a-104">Syntax</span></span>  
  
```  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83c9a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="83c9a-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="83c9a-106">[in] Eşleştirilecek iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="83c9a-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="83c9a-107">[out] Bir Win32 iş parçacığı tutamacı işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="83c9a-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83c9a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="83c9a-108">Remarks</span></span>  
 <span data-ttu-id="83c9a-109">Profil Oluşturucu Win32 çağırmalıdır `DuplicateHandle` kullanmadan önce tutamacı işlevi.</span><span class="sxs-lookup"><span data-stu-id="83c9a-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83c9a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="83c9a-110">Requirements</span></span>  
 <span data-ttu-id="83c9a-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83c9a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83c9a-112">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83c9a-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83c9a-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83c9a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83c9a-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83c9a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c9a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83c9a-115">See also</span></span>

- [<span data-ttu-id="83c9a-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="83c9a-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
