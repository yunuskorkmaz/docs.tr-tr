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
ms.openlocfilehash: c4b8bffeb71497a7dd8e2ed25b833f9216d8017e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049745"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted yöntemi
[.NET Framework 4.7 ve sonraki sürümlerinde desteklenen]  
  
Dinamik bir yöntem JIT derlemesi başladı zaman profil oluşturucu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a>Parametreler  
[in] `functionId`  
Bellek içi işlev için hangi JIT derleme başlatıldığında tanımlayıcısı.   

[in] `fIsSafeToBlock`   
`true` Bu geri çağrısından döndürmek çağıran iş parçacığını beklemek çalışma zamanı engelleme neden olabileceğini göstermek için; `false` engelleme zamanının işlemi etkilemez belirtmek için.  

[in] `pILHeader`    
Yöntemin IL üstbilgi ilk baytına bir işaretçi.   

[in] `cbILHeader`    
IL üst bilgisindeki bayt sayısı. 

## <a name="remarks"></a>Açıklamalar  

Bu geri çağırma JIT olarak derlenmiş bir dinamik yöntem olduğunda tetiklenir. Bu, çeşitli IL saptamalar ve LCG yöntemleri içerir. Profil Oluşturucu yazarları kullanıcılara derlenmiş yöntemi tanımlamak için yeterli bilgi sağlamak için hedefi sağlamaktır.

> [!NOTE]
> `functionId` dinamik yöntemler meta veri olduğundan değerleri kendi meta veri belirteçleri için çözümlemek için kullanılamaz.

`pILHeader` İşaretçisi, yalnızca geçerli sırasında geri çağırma.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DynamicMethodJITCompilationFinished Metodu](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8 Arabirimi](icorprofilercallback8-interface.md)
