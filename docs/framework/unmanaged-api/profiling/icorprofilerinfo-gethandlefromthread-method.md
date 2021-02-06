---
description: ': ICorProfilerInfo:: GetHandleFromThread yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 541a2872bc3cbbe8233e09283b9773957b0a7daf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647563"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="e720e-103">ICorProfilerInfo::GetHandleFromThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e720e-103">ICorProfilerInfo::GetHandleFromThread Method</span></span>

<span data-ttu-id="e720e-104">Bir iş parçacığının KIMLIĞINI bir Win32 iş parçacığı tanıtıcısına eşler.</span><span class="sxs-lookup"><span data-stu-id="e720e-104">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e720e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e720e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e720e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e720e-106">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="e720e-107">'ndaki Eşleştirilecek iş parçacığı KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e720e-107">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="e720e-108">dışı Win32 iş parçacığı tanıtıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e720e-108">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e720e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e720e-109">Remarks</span></span>  

 <span data-ttu-id="e720e-110">Profil oluşturucunun kullanılmadan `DuplicateHandle` önce tanıtıcıda Win32 işlevini çağırması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e720e-110">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  

 <span data-ttu-id="e720e-111">Bu yöntemden döndürülen tanıtıcı çalışma zamanına aittir ve profil oluşturucu hiç kapanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e720e-111">The handle returned from this method is owned by the runtime and the profiler should never close it.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="e720e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e720e-112">Requirements</span></span>  

 <span data-ttu-id="e720e-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e720e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e720e-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e720e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e720e-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e720e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e720e-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e720e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e720e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e720e-117">See also</span></span>

- [<span data-ttu-id="e720e-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e720e-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
