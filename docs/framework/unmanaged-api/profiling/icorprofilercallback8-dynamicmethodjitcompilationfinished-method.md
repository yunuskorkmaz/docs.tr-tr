---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b5ead8b5428d855b7dab81dced1de6325fd07b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455003"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationFinished yöntemi
[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]  
  
Profil Oluşturucu JIT derleme dinamik yönteminin tamamlandı her bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
#### <a name="parameters"></a>Parametreler  
[in] `functionId`  
Bellek içi işlevi için hangi JIT derleme başladı tanımlayıcısı.   

[in] `hrStatus`   
JIT derleme başarılı olup olmadığını belirten bir değer.

[in] `fIsSafeToBlock`   
`true` engelleme ten bu geri dönmek çağıran iş parçacığı beklemek çalışma zamanı yaratabilir belirtmek için; `false` engelleme işlemi çalışma zamanının etkilemez belirtmek için.  

## <a name="remarks"></a>Açıklamalar  

Bu geri çağırma JIT derleme dinamik yönteminin bitirdi tetiklenir. Bu, çeşitli IL saplamalar ve LCG yöntemleri içerir. Profil Oluşturucu yazıcılarının kullanıcılara derlenmiş yöntemini belirlemek için yeterli bilgi sağlamak için kendi hedeftir.

> [!NOTE]
> `functionId` dinamik yöntemler meta verisi yok olduğundan değerleri kendi meta veri simgesi çözümlemek için kullanılamaz.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DynamicMethodJITCompilationStarted yöntemi](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)  
 [ICorProfilerCallback8 arabirimi](icorprofilercallback8-interface.md)
