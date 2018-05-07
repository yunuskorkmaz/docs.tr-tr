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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 07606bf58709f088db486e0263e5cb519ab5b4cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Metodu
Özel durum yan tümcesi için yerel adres ve çerçeve bilgilerini alır (`catch`/`finally`/`filter`) hakkında çalıştırılacak veya yalnızca çalıştırın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pinfo`  
 [out] Bir işaretçi bir [cor_prf_ex_clause_ınfo](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) geçerli özel durumun yan tümcesi örneği ve ilişkili çerçevesini açıklayan yapısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir özel durum bildirimi alındığında `GetNotifiedExceptionClauseInfo` özel durum yan tümcesinin yerel adres ve çerçeve bilgilerini almak için kullanılan (`catch`/`finally`/`filter`) (hakkındaçalıştırılacakolan[ Icorprofilercallback::exceptioncatcherenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [Icorprofilercallback::exceptionunwindfinallyenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), veya [Icorprofilercallback::exceptionsearchfilterenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)geri çağırma Profil Oluşturucu tarafından alındığında) veya yalnızca çalıştırın ([Icorprofilercallback::exceptioncatcherleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [Icorprofilercallback::exceptionunwindfinallyleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), veya [ Icorprofilercallback::exceptionsearchfilterleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) geri çağırma Profil Oluşturucu tarafından alındığında).  
  
 Bu çağrı herhangi bir zamanda Enter geri çağırmaları yukarıdaki birini sonra eşleşen bırakın geri alındığında veya bir iç içe geçmiş özel durumu var. Bu yan tümcesinin bırakın bildirim olduğu geçerli yan tümcesinde durum kadar yapılabilir. Kaçınmak oluşturulan bir özel durum için mümkün olmadığını göz önünde bulundurun bir `filter` ; böylece her zaman izin bildirim bu durumda özel durum yan tümcesi.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerInfo Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
