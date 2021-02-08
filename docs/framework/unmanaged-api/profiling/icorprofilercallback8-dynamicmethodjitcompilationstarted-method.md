---
description: 'Hakkında daha fazla bilgi edinin: ICorProfilerCallback8::D ynamicMethodJITCompilationStarted yöntemi'
title: ICorProfilerCallback8::D ynamicMethodJITCompilationStarted yöntemi
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 186b41564e0aabb069b06356b8eccbe90296ec4b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781707"
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

'ndaki `functionId`  
JıT derlemesinin başlatıldığı bellek içi işlevin tanımlayıcısı.

[in] `fIsSafeToBlock` 
 `true` Bu engellemenin, çalışma zamanının çağıran iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini göstermek için; `false`engellemenin çalışma zamanının işlemini etkilemeyeceğini göstermek için.  

[in] `pILHeader` Metodun Il üstbilgisinin ilk baytına yönelik bir işaretçi.

[in] `cbILHeader` Il üstbilgisindeki bayt sayısı.

## <a name="remarks"></a>Açıklamalar  

Bu geri çağırma, dinamik bir yöntem JıT olarak derlendiğinde tetiklenir. Buna çeşitli Il saplamaları ve LCG yöntemleri dahildir. Amacı, profil oluşturucu yazıcılarını kullanıcılara derlenen yöntemi tanımlamak için yeterli bilgi sağlamaktır.

> [!NOTE]
> `functionId` Dinamik metotların meta verisi olmadığından, meta veri belirteçlerine çözümlemek için değerler kullanılamaz.

`pILHeader`İşaretçi yalnızca geri çağırma sırasında geçerlidir.

## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DynamicMethodJITCompilationFinished Yöntemi](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8 Arabirimi](icorprofilercallback8-interface.md)
