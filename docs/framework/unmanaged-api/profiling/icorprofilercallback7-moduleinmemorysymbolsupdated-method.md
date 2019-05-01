---
title: ICorProfilerCallback7::ModuleInMemorySymbolsUpdated yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12414064bf0651eab443951bde2a50dcff7b2291
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992101"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7::ModuleInMemorySymbolsUpdated yöntemi
[.NET Framework 4.6.1 ve sonraki sürümlerinde desteklenen]  
  
 Her bir bellek içi modül ile ilişkili simge akışı güncelleştirildiğinde, profil oluşturucu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>Parametreler  
 [in] `moduleId`  
 Bellek içi modülü, sembol stream güncelleştirilir tanımlayıcısı.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu geri çağırma ayarlanmasıyla denetlenir [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) çağırırken olay maskesini bayrağı [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) yöntemi.  
  
> [!NOTE]
>  Bu olay şu anda örtük olarak oluşturulmuş veya aracılığıyla değiştirilmiş sembolleri oluşmaz <xref:System.Reflection.Emit> API'leri.  
  
 Bile ne zaman sembolleri Önden yönetilen aşırı çağrısında sağlanan <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> içeren yöntemleri bir `rawSymbolStore` çalışma zamanı derleme için sembolleri belirtmek için bağımsız değişken değil gerçekten ilişkilendirmek sembolik veri modülü ile kadar sonra [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) geri çağırma oluştu. Bu olay, bu modüller için semboller toplamak için daha yeni bir fırsat sağlar.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ModuleLoadFinished Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
