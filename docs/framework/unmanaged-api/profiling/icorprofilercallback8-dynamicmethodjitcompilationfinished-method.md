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
ms.openlocfilehash: addaf6333914c9f0ea36d67e3eb96577fef79e1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497924"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationFinished yöntemi
[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]  
  
Dinamik bir yöntem JIT derlemesi tamamlandı zaman profil oluşturucu bildirir.  
  
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
Bellek içi işlev için hangi JIT derleme başlatıldığında tanımlayıcısı.   

[in] `hrStatus`   
JIT derlemesi başarılı olup olmadığını belirten bir değer.

[in] `fIsSafeToBlock`   
`true` Bu geri çağrısından döndürmek çağıran iş parçacığını beklemek çalışma zamanı engelleme neden olabileceğini göstermek için; `false` engelleme zamanının işlemi etkilemez belirtmek için.  

## <a name="remarks"></a>Açıklamalar  

Bu geri çağırma dinamik bir yöntem JIT derlemesi Tamamlandı olduğunda tetiklenir. Bu, çeşitli IL saptamalar ve LCG yöntemleri içerir. Profil Oluşturucu yazarları kullanıcılara derlenmiş yöntemi tanımlamak için yeterli bilgi sağlamak için hedefi sağlamaktır.

> [!NOTE]
> `functionId` dinamik yöntemler meta veri olduğundan değerleri kendi meta veri belirteçleri için çözümlemek için kullanılamaz.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [DynamicMethodJITCompilationStarted Metodu](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8 Arabirimi](icorprofilercallback8-interface.md)
