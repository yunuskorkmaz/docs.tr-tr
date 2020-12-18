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
ms.openlocfilehash: 94c2c6e01e4188f1fa13c3b6a9f638d4b79a502f
ms.sourcegitcommit: 4b79862c5b41fbd86cf38f926f6a49516059f6f2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2020
ms.locfileid: "97678185"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="05dab-102">ICorProfilerInfo::GetHandleFromThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05dab-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>

<span data-ttu-id="05dab-103">Bir iş parçacığının KIMLIĞINI bir Win32 iş parçacığı tanıtıcısına eşler.</span><span class="sxs-lookup"><span data-stu-id="05dab-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05dab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05dab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05dab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05dab-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="05dab-106">'ndaki Eşleştirilecek iş parçacığı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="05dab-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="05dab-107">dışı Win32 iş parçacığı tanıtıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="05dab-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05dab-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="05dab-108">Remarks</span></span>  

 <span data-ttu-id="05dab-109">Profil oluşturucunun kullanılmadan `DuplicateHandle` önce tanıtıcıda Win32 işlevini çağırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="05dab-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  

 <span data-ttu-id="05dab-110">Bu yöntemden döndürülen tanıtıcı çalışma zamanına aittir ve profil oluşturucu hiç kapanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="05dab-110">The handle returned from this method is owned by the runtime and the profiler should never close it.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="05dab-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05dab-111">Requirements</span></span>  

 <span data-ttu-id="05dab-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05dab-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05dab-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="05dab-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="05dab-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="05dab-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05dab-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05dab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05dab-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05dab-116">See also</span></span>

- [<span data-ttu-id="05dab-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="05dab-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
