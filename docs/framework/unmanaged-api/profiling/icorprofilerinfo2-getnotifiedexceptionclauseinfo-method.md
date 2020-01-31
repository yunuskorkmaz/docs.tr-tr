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
ms.openlocfilehash: a430631948230d16e5d04c869625b4c670faaf02
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868648"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="a9bed-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="a9bed-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="a9bed-103">Çalıştırılmak üzere olan veya yalnızca çalıştırılmış olan Exception yan tümcesinin (`catch`/`finally`/`filter`) yerel adresini ve çerçeve bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="a9bed-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9bed-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9bed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9bed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9bed-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="a9bed-106">dışı Geçerli özel durum yan tümcesi örneğini ve ilişkili çerçevesini açıklayan [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a9bed-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9bed-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9bed-107">Remarks</span></span>  
 <span data-ttu-id="a9bed-108">Bir özel durum bildirimi alındığında `GetNotifiedExceptionClauseInfo`, çalıştırmak üzere özel durum yan tümcesinin (`catch`/`finally`/`filter`) yerel adres ve çerçeve bilgilerini almak için kullanılabilir ([ICorProfilerCallback:: ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback:: Exceptionunwıniyenter](icorprofilercallback-exceptionunwindfinallyenter-method.md)veya [ICorProfilerCallback:: ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) geri çağırması profil oluşturucu tarafından alındı ya da yalnızca çalıştırıldı ([ICorProfilerCallback:: exceptioncatch erleave ](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback:: Exceptionunbir finallyleave](icorprofilercallback-exceptionunwindfinallyleave-method.md)veya [ICorProfilerCallback:: Profiler tarafından bir ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md) geri araması alındı.</span><span class="sxs-lookup"><span data-stu-id="a9bed-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="a9bed-109">Bu çağrı, herhangi bir zamanda, eşleşen bırakma geri çağırması alınana veya geçerli yan tümcesinde iç içe geçmiş bir özel duruma gelene kadar herhangi bir zamanda ENTER geri çağırmaları yapıldıktan sonra yapılabilir. Bu durumda, bu yan tümce için bildirim yok.</span><span class="sxs-lookup"><span data-stu-id="a9bed-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="a9bed-110">Oluşan bir özel durum `filter` özel durum yan tümcesini kaçış için mümkün olmadığını unutmayın. bu nedenle, bu durumda her zaman bir Izin bildirimi vardır.</span><span class="sxs-lookup"><span data-stu-id="a9bed-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9bed-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9bed-111">Requirements</span></span>  
 <span data-ttu-id="a9bed-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9bed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9bed-113">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a9bed-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9bed-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a9bed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9bed-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9bed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9bed-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9bed-116">See also</span></span>

- [<span data-ttu-id="a9bed-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9bed-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="a9bed-118">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9bed-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
