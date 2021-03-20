---
description: ': ICorProfilerCallback:: ExceptionCatcherEnter yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f9ea2b44e7a783f9b21f4aa385585dfebc48b1d4
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760528"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a>ICorProfilerCallback::ExceptionCatcherEnter Yöntemi

Profil oluşturucuyu denetimin uygun bloğa geçtiğini bildirir `catch` .  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a>Parametreler

`functionId` 'ndaki Bloğu içeren işlevin tanımlayıcısı `catch` .
  
`objectId` 'ndaki İşlenmekte olan özel durumun tanımlayıcısı.

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
