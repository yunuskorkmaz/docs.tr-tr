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
ms.openlocfilehash: d0ed1dc09e8dcee8a4c67e01279c6e13661e252d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences Yöntemi
Sıkıştırılmasını olmayan çöp toplama sonucunda yığınındaki nesneleri Düzen bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cSurvivingObjectIDRanges`  
 [in] Sıkıştırılmasını olmayan çöp toplama sonucu olarak derdi bitti bitişik nesnelerin bloğu sayısı. Diğer bir deyişle, değeri `cSurvivingObjectIDRanges` boyutu `objectIDRangeStart` ve `cObjectIDRangeLength` diziler, hangi depolama bir `ObjectID` ve uzunluk, sırasıyla, her bir bloğunda nesneleri için.  
  
 Sonraki iki bağımsız değişkenleri `SurvivingReferences` paralel dizidir. Diğer bir deyişle, `objectIDRangeStart` ve `cObjectIDRangeLength` bitişik nesneleri aynı bloğunu ilgilendiren.  
  
 `objectIDRangeStart`  
 [in] Bir dizi `ObjectID` her biri bitişik bloğunun başlangıç adresi olduğunda, değerleri, bellekte nesneleri canlı.  
  
 `cObjectIDRangeLength`  
 [in] Her biri sağlam bir blok bellekte bitişik nesnelerin boyutudur dizisi.  
  
 Başvuru her blok için belirtilen bir boyutu `objectIDRangeStart` dizi.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
>  Bu yöntem olarak boyutlarını raporlar `MAX_ULONG` 64 bit platformlarda 4 GB'den büyük nesneler için. 4 GB'den büyük nesneleri için kullanılmak [Icorprofilercallback4::survivingreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) yöntemi yerine.  
  
 Öğelerini `objectIDRangeStart` ve `cObjectIDRangeLength` diziler kabul aşağıdaki gibi bir nesne atık toplama derdi bitti olup olmadığını belirlemek için. Varsayımında bir `ObjectID` değeri (`ObjectID`) aşağıdaki aralık içinde yer:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Herhangi bir değer için `i` aşağıdaki aralıkta olduğundan, nesne çöp toplama derdi bitti:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Sıkıştırılmasını olmayan çöp toplama "ölü" nesneleri tarafından kapladığı bellek kaldırsa ancak boşaltılmış alan compact değil. Sonuç olarak, bellek için yığın döndürüldü, ancak hiçbir "canlı" nesneler taşınır.  
  
 Ortak dil çalışma zamanı (CLR) çağırır `SurvivingReferences` sıkıştırılmasını olmayan çöp koleksiyonları için. Sıkıştırma çöp koleksiyonları için [Icorprofilercallback::movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) yerine olarak adlandırılır. Tek çöp toplama, tek bir nesil sıkıştırma ve diğer olmayan sıkıştırılmasını olabilir. Belirli bir oluşturma hakkında bir atık toplama için profil oluşturucu ya da alacak bir `SurvivingReferences` geri çağırma veya bir `MovedReferences` geri çağırma, ancak ikisini.  
  
 Birden çok `SurvivingReferences` geri aramalar alınan sınırlı iç arabelleğe alma, nedeniyle ek olarak, belirli atık toplama sırasında birden çok iş parçacığı sunucu çöp toplama ve diğer nedenler söz konusu olduğunda raporlama. Çöp toplama sırasında birden çok geri aramalar söz konusu olduğunda, bilgileri toplu — birinde raporlanan tüm başvuruları `SurvivingReferences` geri çağırma varlığını sürdürmesini atık toplama.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [SurvivingReferences2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
