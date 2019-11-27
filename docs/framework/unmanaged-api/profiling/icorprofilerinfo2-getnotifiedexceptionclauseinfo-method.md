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
ms.openlocfilehash: 52ad124638a1c1ec7d39fa41b9163f3ab50ffe70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433075"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Metodu
Çalıştırılmak üzere olan veya yalnızca çalıştırılmış olan Exception yan tümcesinin (`catch`/`finally`/`filter`) yerel adresini ve çerçeve bilgilerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a>Parametreler  
 `pinfo`  
 dışı Geçerli özel durum yan tümcesi örneğini ve ilişkili çerçevesini açıklayan [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) yapısına yönelik bir işaretçi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özel durum bildirimi alındığında `GetNotifiedExceptionClauseInfo`, çalıştırmak üzere özel durum yan tümcesinin (`catch`/`finally`/`filter`) yerel adres ve çerçeve bilgilerini almak için kullanılabilir ([ICorProfilerCallback:: ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback:: Exceptionunwıniyenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)veya [ICorProfilerCallback:: ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) geri çağırması profil oluşturucu tarafından alındı ya da yalnızca çalıştırıldı ([ICorProfilerCallback:: exceptioncatch erleave ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback:: Exceptionunbir finallyleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)veya [ICorProfilerCallback:: Profiler tarafından bir ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) geri araması alındı.  
  
 Bu çağrı, herhangi bir zamanda, eşleşen bırakma geri çağırması alınana veya geçerli yan tümcesinde iç içe geçmiş bir özel duruma gelene kadar herhangi bir zamanda ENTER geri çağırmaları yapıldıktan sonra yapılabilir. Bu durumda, bu yan tümce için bildirim yok. Oluşan bir özel durum `filter` özel durum yan tümcesini kaçış için mümkün olmadığını unutmayın. bu nedenle, bu durumda her zaman bir Izin bildirimi vardır.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
