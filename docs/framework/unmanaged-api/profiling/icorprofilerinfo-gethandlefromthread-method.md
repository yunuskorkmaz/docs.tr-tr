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
ms.openlocfilehash: 632a9070eab227bc48ce76c51ea08f98060d680d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722551"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="a7fef-102">ICorProfilerInfo::GetHandleFromThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7fef-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>

<span data-ttu-id="a7fef-103">Bir iş parçacığının KIMLIĞINI bir Win32 iş parçacığı tanıtıcısına eşler.</span><span class="sxs-lookup"><span data-stu-id="a7fef-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7fef-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a7fef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7fef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7fef-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="a7fef-106">'ndaki Eşleştirilecek iş parçacığı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="a7fef-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="a7fef-107">dışı Win32 iş parçacığı tanıtıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a7fef-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7fef-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a7fef-108">Remarks</span></span>  

 <span data-ttu-id="a7fef-109">Profil oluşturucunun kullanılmadan `DuplicateHandle` önce tanıtıcıda Win32 işlevini çağırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="a7fef-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7fef-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7fef-110">Requirements</span></span>  

 <span data-ttu-id="a7fef-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7fef-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7fef-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a7fef-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a7fef-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a7fef-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7fef-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7fef-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7fef-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7fef-115">See also</span></span>

- [<span data-ttu-id="a7fef-116">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7fef-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
