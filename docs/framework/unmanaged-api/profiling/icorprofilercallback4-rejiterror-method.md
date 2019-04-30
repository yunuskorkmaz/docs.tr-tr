---
title: ICorProfilerCallback4::ReJITError Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66f152279a21f28b54acebbf0be7c65bb73efa70
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767481"
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError Yöntemi
Profil Oluşturucu, just-ın-time (JIT) derleyici yeniden derleme işleminde bir hata ile karşılaştı bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleID`  
 [in] `ModuleID` İçinde başarısız bir yeniden derleme girişiminde bulunuldu.  
  
 `methodId`  
 [in] `MethodDef` Yönteminin başarısız güncellemelerden denemesi yapıldı.  
  
 `functionId`  
 [in] Znovu veya için işaretlendi yeniden derleme yapılıyor işlevi örneği. Bu değer olabilir `NULL` (örneğin, profil oluşturucu yöntemi derlenmesi için bir geçersiz meta veri belirteci belirtilmişse) örnekleme başına temel yerine yöntemi başına temelinde hatası durumunda.  
  
 `hrStatus`  
 [in] Hatanın yapısını gösteren HRESULT. Değerlerin bir listesi için durumu HRESULTS bölümüne bakın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu geri arama dönüş değerleri yok sayılır.  
  
## <a name="status-hresults"></a>Durum HRESULTS  
  
|Durum dizi HRESULT|Açıklama|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID` Veya `methodDef` belirteç `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Modül henüz tam yüklü değil veya yüklenmemiş sürecinde olduğundan.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Belirtilen modül dinamik olarak oluşturulan (örneğin, `Reflection.Emit`) ve bu nedenle bu yöntem tarafından desteklenmiyor.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|Yöntem bir toplanabilir bütünleştirilmiş koda örneği ve derlenmesi mümkün değildir. Türleri unutmayın ve yansıma olmayan bağlamda tanımlı işlevler (örneğin, `List<MyCollectibleStruct>`) toplanabilir derlemeye oluşturulabilir.|  
|E_OUTOFMEMORY|CLR JIT yeniden derlemesi için belirtilen yöntemi işaretlemek çalışırken belleği yetersiz kaldı.|  
|Diğer|İşletim sistemi CLR denetimin dışında kalan bir hata döndürdü. Örneğin, belleğin bir sayfası erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hata görüntülenir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
