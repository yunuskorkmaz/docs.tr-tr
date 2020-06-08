---
title: ICorProfilerCallback::ExceptionCatcherEnter Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 9d0ef4da4ba6c8db49bcb0b40911756f7d9db66d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500329"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>ICorProfilerCallback::ExceptionCatcherEnter Yöntemi
Profil oluşturucuyu denetimin uygun bloğa geçtiğini bildirir `catch` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a>Parametreler

- `functionId`

  \[içinde] bloğu içeren işlevin tanımlayıcısı `catch` .
  
- `objectId`

  \[' de] işlenmekte olan özel durumun tanımlayıcısı.

## <a name="remarks"></a>Açıklamalar  
 `ExceptionCatcherEnter`Yöntemi, yalnızca catch noktası tam zamanında (JIT) derleyici ile derlenmişse çağrılır. Yönetilmeyen kodda veya çalışma zamanının iç kodunda yakalanan bir özel durum, bu bildirimi çağırmaz. `objectId`Bir çöp toplama işlemi, bildirimden bu yana nesneyi taşıdığından, değer tekrar geçirilir `ExceptionThrown` .  
  
 Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez. Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.  
  
 Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ExceptionCatcherLeave Yöntemi](icorprofilercallback-exceptioncatcherleave-method.md)
