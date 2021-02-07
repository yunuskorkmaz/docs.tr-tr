---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo yöntemi'
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
ms.openlocfilehash: f297689ccdd1b600fe86db16940434c990e4b084
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716490"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="7f2ec-103">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="7f2ec-103">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>

<span data-ttu-id="7f2ec-104">`catch` / `finally` / `filter` Çalıştırılmak üzere olan veya yalnızca çalıştırılmış olan özel durum yan tümcesinin () yerel adresini ve çerçeve bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="7f2ec-104">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f2ec-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f2ec-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f2ec-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f2ec-106">Parameters</span></span>  

 `pinfo`  
 <span data-ttu-id="7f2ec-107">dışı Geçerli özel durum yan tümcesi örneğini ve ilişkili çerçevesini açıklayan [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7f2ec-107">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f2ec-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7f2ec-108">Remarks</span></span>  

 <span data-ttu-id="7f2ec-109">Bir özel durum bildirimi alındığında, `GetNotifiedExceptionClauseInfo` `catch` / `finally` / `filter` çalıştırılmak üzere olan ([ICorProfilerCallback:: ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback:: exceptionunwıniyenter](icorprofilercallback-exceptionunwindfinallyenter-method.md)) için yerel adres ve çerçeve bilgilerini almak üzere kullanılabilir. ya da [ICorProfilerCallback:: ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) geri çağırması profil oluşturucu tarafından alındı ya da yalnızca çalıştırılmış ([ICorProfilerCallback:: exceptioncatch erleave](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback:: exceptionunwıncallback](icorprofilercallback-exceptionunwindfinallyleave-method.md) [](icorprofilercallback-exceptionsearchfilterleave-method.md)</span><span class="sxs-lookup"><span data-stu-id="7f2ec-109">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="7f2ec-110">Bu çağrı, herhangi bir zamanda, eşleşen bırakma geri çağırması alınana veya geçerli yan tümcesinde iç içe geçmiş bir özel duruma gelene kadar herhangi bir zamanda ENTER geri çağırmaları yapıldıktan sonra yapılabilir. Bu durumda, bu yan tümce için bildirim yok.</span><span class="sxs-lookup"><span data-stu-id="7f2ec-110">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="7f2ec-111">Oluşan bir özel durum yan tümcesini kaçış için mümkün olmadığını unutmayın `filter` , bu nedenle bu durumda her zaman bir izin bildirimi vardır.</span><span class="sxs-lookup"><span data-stu-id="7f2ec-111">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f2ec-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f2ec-112">Requirements</span></span>  

 <span data-ttu-id="7f2ec-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f2ec-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f2ec-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7f2ec-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7f2ec-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7f2ec-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f2ec-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f2ec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f2ec-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f2ec-117">See also</span></span>

- [<span data-ttu-id="7f2ec-118">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f2ec-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="7f2ec-119">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f2ec-119">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
