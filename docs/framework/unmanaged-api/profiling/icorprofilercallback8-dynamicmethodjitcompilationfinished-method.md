---
title: ICorProfilerCallback8::D ynamicMethodJITCompilationFinished yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 0e04459614ca697908fb9b71ecc3931ac305a838
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136579"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::D ynamicMethodJITCompilationFinished yöntemi
[.NET Framework 4,7 ve sonraki sürümlerde desteklenir]  
  
Dinamik bir yöntemin JıT derlemesi tamamlandığında profil oluşturucuyu bilgilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a>Parametreler  
[in] `functionId`  
JıT derlemesinin başlatıldığı bellek içi işlevin tanımlayıcısı.   

[in] `hrStatus`   
JıT derlemesinin başarılı olup olmadığını gösteren bir değer.

[in] `fIsSafeToBlock`   
`true`, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesini sağlamak için; engellemenin çalışma zamanının işlemini etkilemeyeceğini belirten `false`.  

## <a name="remarks"></a>Açıklamalar  

Bu geri çağırma, dinamik bir yöntemin JıT derlemesi tamamlandığında tetiklenir. Buna çeşitli Il saplamaları ve LCG yöntemleri dahildir. Amacı, profil oluşturucu yazıcılarını kullanıcılara derlenen yöntemi tanımlamak için yeterli bilgi sağlamaktır.

> [!NOTE]
> Dinamik metotların meta verisi olmadığından, `functionId` değerleri meta veri belirteçlerine çözümlemek için kullanılamaz.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DynamicMethodJITCompilationStarted Metodu](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8 Arabirimi](icorprofilercallback8-interface.md)
