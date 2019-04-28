---
title: ICorProfilerCallback4::SurvivingReferences2 Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ad96224daf79b17d3902217af061173580f1478a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597205"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2 Yöntemi
Sıkıştırma dışı bir atık toplama sonucunda yığın nesnelerin yerleşimini bildirir. Profil Oluşturucu uygulanırsa, bu yöntem çağrılır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimi. Bu geri çağırma değiştirir [Icorprofilercallback2::survivingreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) yöntemi, daha büyük olan uzunluğu aşan bir ULONG ifade edilebilir nesne aralıklarını rapor edebilirsiniz çünkü.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cSurvivingObjectIDRanges`  
 [in] Sıkıştırma olmayan çöp toplama işleminin sonucu olarak kurtulan bitişik nesnelerin blokların sayısı. Diğer bir deyişle, değerini `cSurvivingObjectIDRanges` boyutu `objectIDRangeStart` ve `cObjectIDRangeLength` diziler, hangi depolama bir `ObjectID` ve uzunluğu, nesnelerin her blok için sırasıyla.  
  
 Sonraki iki bağımsız değişkenleri `SurvivingReferences2` paralel dizidir. Diğer bir deyişle, `objectIDRangeStart` ve `cObjectIDRangeLength` bitişik nesnelerin aynı blok ilgilendiriyor.  
  
 `objectIDRangeStart`  
 [in] Bir dizi `ObjectID` her birinin başlangıç adresi bloğunun bitişik olduğunda, değerleri, Canlı nesneleri bellekte.  
  
 `cObjectIDRangeLength`  
 [in] Her biri bellekte bitişik nesnelerin sürdüren bir blok boyutu olan bir tamsayı dizisi.  
  
 Başvurulduğundan her blok için belirtilen bir boyutu `objectIDRangeStart` dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
 Öğeleri `objectIDRangeStart` ve `cObjectIDRangeLength` diziler yorumlanabilir gibi bir nesne çöp toplamadan kurtulan olup olmadığını belirlemek için. Varsayımında bir `ObjectID` değeri (`ObjectID`) aşağıdaki aralığında yer:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 İçin herhangi bir değerini `i` aşağıdaki aralığında olan, nesnenin çöp toplamadan kurtulan:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Sıkıştırma dışı bir atık toplama "etkin olmayan" nesnelerin kapladığı belleği geri kazanır, ancak serbest bırakılan bu alanı compact değil. Sonuç olarak, bellek için yığın döndürülür, ancak "canlı" nesne taşındı.  
  
 Ortak dil çalışma zamanı (CLR) çağıran `SurvivingReferences2` sıkıştırma olmayan çöp toplama için. Sıkıştırma çöp koleksiyonları için [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) yerine çağrılır. Tek bir çöp toplama, tek bir nesil için sıkıştırma ve diğer olmayan sıkıştırma olabilir. Herhangi belirli nesil çöp toplama için profil oluşturucu ya da alacak bir `SurvivingReferences2` geri çağırma veya bir [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) geri çağırma, ancak ikisine birden değil.  
  
 Birden çok `SurvivingReferences2` geri çağırmaları alınan sınırlı iç arabelleğe alma nedeniyle ek olarak, belirli bir çöp toplama, sunucu çöp toplama sırasında birden çok geri çağırmaları ve diğer nedenlerle sırasında. Bir çöp toplama sırasında birden çok geri çağırmaları söz konusu olduğunda, bilgileri toplu olarak; içinde bildirilen tüm başvuruları `SurvivingReferences2` çöp toplama geri çağırma önceliklidir.  
  
 Profil Oluşturucu hem de uyguluyorsa [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) ve [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimleri `SurvivingReferences2` önce yöntemi çağrıldığında [Icorprofilercallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) yöntemi, ancak yalnızca `SurvivingReferences2` başarıyla döndürür. Profil oluşturucular hatasından gösteren HRESULT döndürebilir `SurvivingReferences2` yöntemi ikinci yöntem çağırmaktan kaçının.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback4 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
