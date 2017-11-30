---
title: "ICorProfilerCallback4::ReJITError Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITError
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c8b1f3c5b206b2e6a108e784a206d597b69fd662
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError Yöntemi
Profil Oluşturucu tam zamanında (JIT) derleyici derleme işlemindeki bir hata ile karşılaştı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `moduleID`  
 [in] `ModuleID` İçinde hangi başarısız yeniden derlenmek girişiminde bulunuldu.  
  
 `methodId`  
 [in] `MethodDef` Yönteminin başarısız yeniden derlenmek girişiminde bulunuldu.  
  
 `functionId`  
 [in] Derlenmiş veya için işaretlendi yeniden derlenmek yapılıyor işlevi örneği. Bu değer olabilir `NULL` (örneğin, profil oluşturucu yöntemi derlenmesi için bir geçersiz meta veriler belirteci belirtilmişse) başına oluşturmada temel yerine yöntemi başına temelinde hatası durumunda.  
  
 `hrStatus`  
 [in] Hatanın yapısını gösteren bir HRESULT. Değerlerin listesi için durumu HRESULTS bölümüne bakın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu geri dönüş değerleri yoksayılır.  
  
## <a name="status-hresults"></a>Durum HRESULTS  
  
|Durum dizi HRESULT|Açıklama|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID` Veya `methodDef` belirteci `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Modül henüz tam olarak yüklü değil veya kaldırıldığında sürecinde olduğundan.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Belirtilen modül dinamik olarak oluşturulan (örneğin, `Reflection.Emit`) ve bu nedenle bu yöntem tarafından desteklenmiyor.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|Yöntemi, collectible derlemeye örneği ve bu nedenle derlenmesi mümkün değildir. Türleri Not ve yansıma olmayan bağlamında tanımlanan işlevleri (örneğin, `List<MyCollectibleStruct>`) collectible derlemeye oluşturulabilir.|  
|E_OUTOFMEMORY|CLR JIT yeniden derlenmek belirtilen yöntemini işaretlemek çalışırken yetersiz bellek tükendi.|  
|Diğer|İşletim sistemi CLR denetimi dışında kalan bir hata döndürdü. Örneğin, belleğin bir sayfası erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hatası görüntülenir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilercallback arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Icorprofilercallback4 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
