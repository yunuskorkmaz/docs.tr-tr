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
ms.openlocfilehash: 7318d7d1494b0cf4db54b92ff09775be5500bdb1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869588"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="f1eb7-102">ICorProfilerInfo::GetThreadInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1eb7-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="f1eb7-103">Belirtilen iş parçacığı için geçerli Win32 iş parçacığı kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1eb7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1eb7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1eb7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1eb7-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="f1eb7-106">'ndaki Geçerli Win32 KIMLIĞI alınacak iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="f1eb7-107">dışı Belirtilen iş parçacığının geçerli Win32 iş parçacığı KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1eb7-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1eb7-108">Requirements</span></span>  
 <span data-ttu-id="f1eb7-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1eb7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1eb7-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f1eb7-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f1eb7-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f1eb7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1eb7-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1eb7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1eb7-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1eb7-113">See also</span></span>

- [<span data-ttu-id="f1eb7-114">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1eb7-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
