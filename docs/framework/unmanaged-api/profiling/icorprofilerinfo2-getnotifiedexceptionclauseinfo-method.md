---
title: ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 170aad39710f6e945495e9988921eddde5d9ba6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="501e9-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="501e9-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="501e9-103">Özel durum yan tümcesi için yerel adres ve çerçeve bilgilerini alır (`catch`/`finally`/`filter`) hakkında çalıştırılacak veya yalnızca çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="501e9-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="501e9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="501e9-104">Syntax</span></span>  
  
```  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="501e9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="501e9-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="501e9-106">[out] Bir işaretçi bir [cor_prf_ex_clause_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) geçerli özel durumun yan tümcesi örneği ve ilişkili çerçevesini açıklayan yapısı.</span><span class="sxs-lookup"><span data-stu-id="501e9-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="501e9-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="501e9-107">Remarks</span></span>  
 <span data-ttu-id="501e9-108">Bir özel durum bildirimi alındığında `GetNotifiedExceptionClauseInfo` özel durum yan tümcesinin yerel adres ve çerçeve bilgilerini almak için kullanılan (`catch`/`finally`/`filter`) (hakkındaçalıştırılacakolan[ Icorprofilercallback::exceptioncatcherenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [Icorprofilercallback::exceptionunwindfinallyenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), veya [Icorprofilercallback::exceptionsearchfilterenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)geri çağırma Profil Oluşturucu tarafından alındığında) veya yalnızca çalıştırın ([Icorprofilercallback::exceptioncatcherleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [Icorprofilercallback::exceptionunwindfinallyleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), veya [ Icorprofilercallback::exceptionsearchfilterleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) geri çağırma Profil Oluşturucu tarafından alındığında).</span><span class="sxs-lookup"><span data-stu-id="501e9-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="501e9-109">Bu çağrı herhangi bir zamanda Enter geri çağırmaları yukarıdaki birini sonra eşleşen bırakın geri alındığında veya bir iç içe geçmiş özel durumu var. Bu yan tümcesinin bırakın bildirim olduğu geçerli yan tümcesinde durum kadar yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="501e9-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="501e9-110">Kaçınmak oluşturulan bir özel durum için mümkün olmadığını göz önünde bulundurun bir `filter` ; böylece her zaman izin bildirim bu durumda özel durum yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="501e9-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="501e9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="501e9-111">Requirements</span></span>  
 <span data-ttu-id="501e9-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="501e9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="501e9-113">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="501e9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="501e9-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="501e9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="501e9-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="501e9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="501e9-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="501e9-116">See Also</span></span>  
 [<span data-ttu-id="501e9-117">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="501e9-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="501e9-118">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="501e9-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
