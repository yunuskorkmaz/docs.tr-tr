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
ms.openlocfilehash: 534e0672820cc2509f32765274ad970fda69ec5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866513"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>ICorProfilerCallback::ExceptionCatcherEnter Yöntemi
Profil oluşturucuyu denetimin uygun `catch` bloğuna geçtiğini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a>Parametreler

- `functionId`

  \[içinde] `catch` bloğunu içeren işlevin tanımlayıcısı.
  
- `objectId`

  \[içinde] işlenmekte olan özel durumun tanımlayıcısı.

## <a name="remarks"></a>Açıklamalar  
 `ExceptionCatcherEnter` yöntemi, yalnızca catch noktası tam zamanında (JıT) derleyici ile derlenmişse çağrılır. Yönetilmeyen kodda veya çalışma zamanının iç kodunda yakalanan bir özel durum, bu bildirimi çağırmaz. Bir çöp toplama işlemi `ExceptionThrown` bildiriminden bu yana nesneyi taşıdığından `objectId` değer tekrar geçirilir.  
  
 Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez. Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.  
  
 Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ExceptionCatcherLeave Yöntemi](icorprofilercallback-exceptioncatcherleave-method.md)
