---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad74eeb4deeae73be40b3a0bc0f6a18ec2299780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted yöntemi
[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]  
  
Profil Oluşturucu JIT derleme dinamik yönteminin başlatıldı her bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
#### <a name="parameters"></a>Parametreler  
[in] `functionId`  
Bellek içi işlevi için hangi JIT derleme başladı tanımlayıcısı.   

[in] `fIsSafeToBlock`   
`true` engelleme ten bu geri dönmek çağıran iş parçacığı beklemek çalışma zamanı yaratabilir belirtmek için; `false` engelleme işlemi çalışma zamanının etkilemez belirtmek için.  

[in] `pILHeader`    
Bir işaretçi yöntemin IL üstbilgisinin ilk bayta.   

[in] `cbILHeader`    
IL üstbilgisinde bayt sayısı. 

## <a name="remarks"></a>Açıklamalar  

Dinamik bir yöntem JIT derlenmiş olduğunda bu geri çağırma tetiklenir. Bu, çeşitli IL saplamalar ve LCG yöntemleri içerir. Profil Oluşturucu yazıcılarının kullanıcılara derlenmiş yöntemini belirlemek için yeterli bilgi sağlamak için kendi hedeftir.

> [!NOTE]
> `functionId` dinamik yöntemler meta verisi yok olduğundan değerleri kendi meta veri simgesi çözümlemek için kullanılamaz.

`pILHeader` İşaretçidir yalnızca geçerli sırasında geri çağırma.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DynamicMethodJITCompilationFinished yöntemi](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
 [ICorProfilerCallback8 arabirimi](icorprofilercallback8-interface.md)
