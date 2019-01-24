---
title: ICorProfilerCallback::ExceptionUnwindFinallyEnter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyEnter method [.NET Framework profiling]
- ExceptionUnwindFinallyEnter method [.NET Framework profiling]
ms.assetid: c7fab986-b69f-4ec8-b7b7-91dcfc239cd0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e6109796d633c5facf5c0b07e0793cb8f7dc77e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54549817"
---
# <a name="icorprofilercallbackexceptionunwindfinallyenter-method"></a>ICorProfilerCallback::ExceptionUnwindFinallyEnter Yöntemi
İşleme özel durumu geriye doğru izleme aşamasına giriyor profil oluşturucu bildirir bir `finally` belirtilen işlevinde yan tümcesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ExceptionUnwindFinallyEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `functionId`  
 [in] İçeren işlev kimliği `finally` yan tümcesi.  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın atık toplama izin veren bir durumda olmayabilir çünkü profil oluşturucu bu yöntemin uygulanması Engellemesi gereken değil ve bu nedenle preemptive çöp toplama etkinleştirilemez. Burada profil oluşturucu engellerse ve çöp toplama denenir, çalışma zamanı, bu geri dönene kadar engeller.  
  
 Bu yöntemin uygulanmasını profil oluşturucunun yönetilen koda veya herhangi bir yönetilen bellek ayırma yol neden çağırmalıdır değil.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [GetNotifiedExceptionClauseInfo Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)
- [ExceptionUnwindFinallyLeave Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)
