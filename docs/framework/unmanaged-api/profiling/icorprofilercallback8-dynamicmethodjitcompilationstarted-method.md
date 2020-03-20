---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: e8b1a243b691d8d5eb364fd16821fd9156505c60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177052"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method
[.NET Framework 4.7 ve sonraki sürümlerde desteklendi]  
  
Dinamik bir yöntemin JIT derlemesi başladığında profilleyiciyi not alar.  
  
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
[içinde]`functionId`  
JIT derlemesinin başlatıldıği bellek içi işlevin tanımlayıcısı.

[içinde] `fIsSafeToBlock` engellemenin çalışma zamanının arama iş parçacığının bu geri aramadan dönmesini beklemesine neden olabileceğini belirtmek 
 `true` için; `false` engellemenin çalışma zamanının çalışmasını etkilemeyeceğini belirtmek için.  

[içinde] `pILHeader` Yöntemin IL üstbilgisinin ilk baytına işaretçi.

[içinde] `cbILHeader` IL üstbilgisindeki bayt sayısı.

## <a name="remarks"></a>Açıklamalar  

Dinamik bir yöntem JIT tarafından derlendiğinde bu geri arama tetiklenir. Bu çeşitli IL saplamaları ve LCG yöntemleri içerir. Amacı, profil oluşturucu yazarlara derlenen yöntemi kullanıcılara tanımlamak için yeterli bilgi sağlamaktır.

> [!NOTE]
> `functionId`dinamik yöntemlerin meta verisi olmadığından, değerler meta veri belirteçlerini gidermek için kullanılamaz.

İşaretçi `pILHeader` yalnızca geri arama sırasında geçerlidir.

## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üstbilgi:** CorProf.idl, CorProf.h  
  
 **Kütüphane:** CorGuids.lib  
  
 **.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DynamicMethodJITCompilationFinished Yöntemi](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8 Arabirimi](icorprofilercallback8-interface.md)
