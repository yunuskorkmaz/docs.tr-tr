---
description: ': ICorProfilerInfo:: GetThreadInfo yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 5514b1c4860067a07bf922e9d9a8bfab8c05e218
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760556"
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="39203-103">ICorProfilerInfo::GetThreadInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39203-103">ICorProfilerInfo::GetThreadInfo Method</span></span>

<span data-ttu-id="39203-104">Belirtilen iş parçacığı için geçerli Win32 iş parçacığı kimliğini alır.</span><span class="sxs-lookup"><span data-stu-id="39203-104">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39203-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39203-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39203-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="39203-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="39203-107">'ndaki Geçerli Win32 KIMLIĞI alınacak iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="39203-107">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="39203-108">dışı Belirtilen iş parçacığının geçerli Win32 iş parçacığı KIMLIĞINE yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="39203-108">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39203-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39203-109">Requirements</span></span>  

 <span data-ttu-id="39203-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39203-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39203-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="39203-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="39203-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="39203-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39203-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39203-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39203-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39203-114">See also</span></span>

- [<span data-ttu-id="39203-115">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39203-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
