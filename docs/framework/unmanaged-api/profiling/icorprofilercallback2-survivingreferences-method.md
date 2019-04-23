---
title: ICorProfilerCallback2::SurvivingReferences Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da06ce49415317393b3489c2b8f97afc58f7c83b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191308"
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences Yöntemi
Sıkıştırma dışı bir atık toplama sonucunda yığın nesnelerin yerleşimini bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cSurvivingObjectIDRanges`  
 [in] Sıkıştırma olmayan çöp toplama işleminin sonucu olarak kurtulan bitişik nesnelerin blokların sayısı. Diğer bir deyişle, değerini `cSurvivingObjectIDRanges` boyutu `objectIDRangeStart` ve `cObjectIDRangeLength` diziler, hangi depolama bir `ObjectID` ve uzunluğu, nesnelerin her blok için sırasıyla.  
  
 Sonraki iki bağımsız değişkenleri `SurvivingReferences` paralel dizidir. Diğer bir deyişle, `objectIDRangeStart` ve `cObjectIDRangeLength` bitişik nesnelerin aynı blok ilgilendiriyor.  
  
 `objectIDRangeStart`  
 [in] Bir dizi `ObjectID` her birinin başlangıç adresi bloğunun bitişik olduğunda, değerleri, Canlı nesneleri bellekte.  
  
 `cObjectIDRangeLength`  
 [in] Her biri bellekte bitişik nesnelerin sürdüren bir blok boyutu olan bir tamsayı dizisi.  
  
 Başvurulduğundan her blok için belirtilen bir boyutu `objectIDRangeStart` dizisi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
>  Bu yöntem boyutları olarak raporlar `MAX_ULONG` 64-bit platformlarda 4 GB'den büyük olan nesneler için. 4 GB'den daha büyük nesneleri için kullanılmak [Icorprofilercallback4::survivingreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) yöntemi yerine.  
  
 Öğeleri `objectIDRangeStart` ve `cObjectIDRangeLength` diziler yorumlanabilir gibi bir nesne çöp toplamadan kurtulan olup olmadığını belirlemek için. Varsayımında bir `ObjectID` değeri (`ObjectID`) aşağıdaki aralığında yer:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 İçin herhangi bir değerini `i` aşağıdaki aralığında olan, nesnenin çöp toplamadan kurtulan:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Sıkıştırma dışı bir atık toplama "etkin olmayan" nesnelerin kapladığı belleği geri kazanır, ancak serbest bırakılan bu alanı compact değil. Sonuç olarak, bellek için yığın döndürülür, ancak "canlı" nesne taşındı.  
  
 Ortak dil çalışma zamanı (CLR) çağıran `SurvivingReferences` sıkıştırma olmayan çöp toplama için. Sıkıştırma çöp koleksiyonları için [Icorprofilercallback::movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) yerine çağrılır. Tek bir çöp toplama, tek bir nesil için sıkıştırma ve diğer olmayan sıkıştırma olabilir. Herhangi belirli nesil çöp toplama için profil oluşturucu ya da alacak bir `SurvivingReferences` geri çağırma veya bir `MovedReferences` geri çağırma, ancak ikisine birden değil.  
  
 Birden çok `SurvivingReferences` geri çağırmaları alınan sınırlı iç arabelleğe, nedeniyle ek olarak, belirli bir çöp toplama sırasında raporlama sunucu çöp toplama ve diğer nedenlerle olması durumunda birden çok iş parçacığı. Bir çöp toplama sırasında birden çok geri çağırmaları söz konusu olduğunda, bilgileri toplu — içinde bildirilen tüm başvuruları `SurvivingReferences` çöp toplama geri çağırma önceliklidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [SurvivingReferences2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
