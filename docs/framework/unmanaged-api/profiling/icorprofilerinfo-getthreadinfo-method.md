---
title: ICorProfilerInfo::GetThreadInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetThreadInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4c4657279e145dbb923c339ed0114723620e7aa7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="a438e-102">ICorProfilerInfo::GetThreadInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="a438e-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="a438e-103">Geçerli Win32 iş parçacığı kimliği için belirtilen iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="a438e-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a438e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a438e-104">Syntax</span></span>  
  
```  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a438e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a438e-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="a438e-106">[in] Win32 geçerli kimliği edinmek için iş parçacığı kimliği</span><span class="sxs-lookup"><span data-stu-id="a438e-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="a438e-107">[out] Belirtilen iş parçacığının geçerli Win32 iş parçacığı için bir işaretçi kimliği</span><span class="sxs-lookup"><span data-stu-id="a438e-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a438e-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a438e-108">Requirements</span></span>  
 <span data-ttu-id="a438e-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a438e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a438e-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a438e-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a438e-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a438e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a438e-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a438e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a438e-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a438e-113">See Also</span></span>  
 [<span data-ttu-id="a438e-114">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="a438e-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
