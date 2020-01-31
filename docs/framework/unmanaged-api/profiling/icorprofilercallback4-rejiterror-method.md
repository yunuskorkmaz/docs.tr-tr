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
ms.openlocfilehash: 66195ea9df4c8e9ce847b38f7d020a3bebffcd37
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865187"
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError Yöntemi
Profil oluşturucuyu, Just-In-Time (JıT) derleyicisinin yeniden derleme sürecinde bir hatayla karşılaşdığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametreler  
 `moduleID`  
 'ndaki Başarısız yeniden derleme denemesinin yapıldığı `ModuleID`.  
  
 `methodId`  
 'ndaki Başarısız yeniden derleme denemesinin yapıldığı yöntemin `MethodDef`.  
  
 `functionId`  
 'ndaki Yeniden derleme için yeniden Derlenmekte olan veya işaretlenmiş işlev örneği. Bu değer, hata oluşturma temelinde hata temelinde oluştuysa (örneğin, profil oluşturucu yeniden derlenecek Yöntem için geçersiz bir meta veri belirteci belirtilmişse) `NULL` olabilir.  
  
 `hrStatus`  
 'ndaki Hatanın doğasını gösteren bir HRESULT. Değerlerin listesi için durum HRESULTS bölümüne bakın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu geri aramadan döndürülen değerler yok sayılır.  
  
## <a name="status-hresults"></a>Durum HRESULTS  
  
|Durum dizisi HRESULT|Açıklama|  
|--------------------------|-----------------|  
|E_INVALIDARG|`moduleID` veya `methodDef` belirteci `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|Modül henüz tam olarak yüklenmedi veya kaldırılıyor sürecinde.|  
|CORPROF_E_MODULE_IS_DYNAMIC|Belirtilen modül dinamik olarak üretildi (örneğin, `Reflection.Emit`ile) ve bu nedenle bu yöntem tarafından desteklenmez.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|Yöntemi toplanabilir bir derlemeye örneklenmiştir ve bu nedenle yeniden derlenmesi mümkün değildir. Yansıma dışı bir bağlamda (örneğin, `List<MyCollectibleStruct>`) tanımlanan türlerin ve işlevlerin toplanabilir bir derlemede örneklenebilir olduğunu unutmayın.|  
|E_OUTOFMEMORY|JıT yeniden derleme için belirtilen yöntem işaretlenmeye çalışılırken CLR 'nin belleği tükendi.|  
|Diğer|İşletim sistemi, CLR denetimi dışında bir hata döndürdü. Örneğin, bir bellek sayfasının erişim korumasını değiştirmek için bir sistem çağrısı başarısız olursa, işletim sistemi hatası görüntülenir.|  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
