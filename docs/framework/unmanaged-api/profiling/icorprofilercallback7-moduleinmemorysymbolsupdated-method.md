---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerCallback7:: Moduleınmemorysymbolsupdated yöntemi'
title: 'ICorProfilerCallback7:: Moduleınmemorysymbolsupdated yöntemi'
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
ms.openlocfilehash: 74adf7edc5269824a924933eb3284a5964e1bac1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781733"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7:: Moduleınmemorysymbolsupdated yöntemi

[.NET Framework 4.6.1 ve sonraki sürümlerde desteklenir]  
  
 Bellek içi modülle ilişkili sembol akışı güncelleştirildiğinde profil oluşturucuyu bilgilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>Parametreler  

 'ndaki `moduleId`  
 Sembol akışı güncelleştirilmiş olan bellek içi modülün tanıtıcısı.  
  
## <a name="remarks"></a>Açıklamalar  

 Bu geri çağırma, [ICorProfilerCallback5:: SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) yöntemi çağrılırken [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](cor-prf-high-monitor-enumeration.md) Event Mask bayrağı ayarlanarak denetlenir.  
  
> [!NOTE]
> Bu olay şu anda, API 'ler aracılığıyla örtük olarak oluşturulan veya değiştirilen semboller için çıkarılmamaktadır <xref:System.Reflection.Emit> .  
  
 Semboller, derleme için sembolleri belirtmek üzere bir bağımsız değişken içeren yönetilen yöntemlerin aşırı yüklerinden birine yapılan bir çağrıda önde gelen olsa bile <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> `rawSymbolStore` , [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) geri çağırması gerçekleşene kadar çalışma zamanı aslında sembolik verileri modülle ilişkilendirmeyebilir. Bu olay, bu tür modüller için sembolleri toplamaya yönelik daha sonraki bir fırsat sağlar.  
  
## <a name="requirements"></a>Gereksinimler  

 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ModuleLoadFinished Yöntemi](icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2 Yöntemi](icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7 Arabirimi](icorprofilercallback7-interface.md)
