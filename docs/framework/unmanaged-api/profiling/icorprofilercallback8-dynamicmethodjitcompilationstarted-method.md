---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationStarted yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 1eaf29e1c93f352facde4af2ee57910783d82e5d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136459"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::D ynamicMethodJITCompilationStarted yöntemi
[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]  
  
Dinamik bir yöntemin JıT derlemesi başladığında profil oluşturucuyu bilgilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
## <a name="parameters"></a>Parametreler  
[in] `functionId`  
JıT derlemesinin başlatıldığı bellek içi işlevin tanımlayıcısı.   

[in] `fIsSafeToBlock`   
`true`, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini sağlamak için; engellemenin çalışma zamanının işlemini etkilemeyeceğini belirten `false`.  

[in] `pILHeader`    
Metodun Il üstbilgisinin ilk baytına yönelik bir işaretçi.   

[in] `cbILHeader`    
Il üstbilgisindeki bayt sayısı. 

## <a name="remarks"></a>Açıklamalar  

Bu geri çağırma, dinamik bir yöntem JıT olarak derlendiğinde tetiklenir. Buna çeşitli Il saplamaları ve LCG yöntemleri dahildir. Amacı, profil oluşturucu yazıcılarını kullanıcılara derlenen yöntemi tanımlamak için yeterli bilgi sağlamaktır.

> [!NOTE]
> Dinamik metotların meta verisi olmadığından, `functionId` değerleri meta veri belirteçlerine çözümlemek için kullanılamaz.

`pILHeader` işaretçi yalnızca geri çağırma sırasında geçerlidir.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DynamicMethodJITCompilationFinished Metodu](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8 Arabirimi](icorprofilercallback8-interface.md)
