---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: f53d1d66eef0f745e1a0c51c3234ac66eec07315
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866370"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a>ICorProfilerCallback::ExceptionUnwindFinallyLeave Yöntemi
Profil oluşturucuyu, özel durum işlemenin geriye doğru izleme aşamasının bir `finally` yan tümcesi bıraktı olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu çağrı sırasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez. Profil Oluşturucu burada ve bir çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engeller.  
  
 Ayrıca, bu çağrı sırasında profil oluşturucunun yönetilen koda çağrı olmaması veya herhangi bir şekilde yönetilen bellek ayırmaya neden olması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ExceptionUnwindFinallyEnter Yöntemi](icorprofilercallback-exceptionunwindfinallyenter-method.md)
