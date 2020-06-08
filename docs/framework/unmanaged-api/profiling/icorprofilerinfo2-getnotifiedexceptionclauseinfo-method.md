---
title: ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type:
- apiref
ms.openlocfilehash: 08337a118a80d213f16e2a16f744b96f5dde2e7f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497012"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="fd1c4-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="fd1c4-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="fd1c4-103">`catch` / `finally` / `filter` Çalıştırılmak üzere olan veya yalnızca çalıştırılmış olan özel durum yan tümcesinin () yerel adresini ve çerçeve bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="fd1c4-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd1c4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fd1c4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd1c4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd1c4-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="fd1c4-106">dışı Geçerli özel durum yan tümcesi örneğini ve ilişkili çerçevesini açıklayan [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fd1c4-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd1c4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd1c4-107">Remarks</span></span>  
 <span data-ttu-id="fd1c4-108">Bir özel durum bildirimi alındığında, `GetNotifiedExceptionClauseInfo` `catch` / `finally` / `filter` çalıştırılmak üzere olan ([ICorProfilerCallback:: ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback:: exceptionunwıniyenter](icorprofilercallback-exceptionunwindfinallyenter-method.md)) için yerel adres ve çerçeve bilgilerini almak üzere kullanılabilir. ya da [ICorProfilerCallback:: ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) geri çağırması profil oluşturucu tarafından alındı ya da yalnızca çalıştırılmış ([ICorProfilerCallback:: exceptioncatch erleave](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback:: exceptionunwıncallback](icorprofilercallback-exceptionunwindfinallyleave-method.md) [ICorProfilerCallback::ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md)</span><span class="sxs-lookup"><span data-stu-id="fd1c4-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="fd1c4-109">Bu çağrı, herhangi bir zamanda, eşleşen bırakma geri çağırması alınana veya geçerli yan tümcesinde iç içe geçmiş bir özel duruma gelene kadar herhangi bir zamanda ENTER geri çağırmaları yapıldıktan sonra yapılabilir. Bu durumda, bu yan tümce için bildirim yok.</span><span class="sxs-lookup"><span data-stu-id="fd1c4-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="fd1c4-110">Oluşan bir özel durum yan tümcesini kaçış için mümkün olmadığını unutmayın `filter` , bu nedenle bu durumda her zaman bir izin bildirimi vardır.</span><span class="sxs-lookup"><span data-stu-id="fd1c4-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd1c4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd1c4-111">Requirements</span></span>  
 <span data-ttu-id="fd1c4-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd1c4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd1c4-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fd1c4-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd1c4-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fd1c4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd1c4-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd1c4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd1c4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd1c4-116">See also</span></span>

- [<span data-ttu-id="fd1c4-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd1c4-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="fd1c4-118">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd1c4-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
