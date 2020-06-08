---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
ms.openlocfilehash: 8694a2d19c3b98487b86da4273eb0c68fb9d9ace
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500123"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a>ICorProfilerCallback::ExceptionUnwindFunctionLeave Yöntemi
Profil oluşturucuyu, özel durum işlemenin geri sarma aşamasının bir işlevi geriye doğru izlemeyi tamamladığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 `ExceptionUnwindFunctionLeave`Yöntemi çağrıldığında, işlev örneği ve yığın verileri yığından kaldırılır.  
  
 Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu çağrı sırasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez. Profil Oluşturucu burada ve bir çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engeller.  
  
 Ayrıca, bu çağrı sırasında profil oluşturucunun yönetilen koda çağrı olmaması veya herhangi bir şekilde yönetilen bellek ayırmaya neden olması gerekir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ExceptionUnwindFunctionEnter Yöntemi](icorprofilercallback-exceptionunwindfunctionenter-method.md)
