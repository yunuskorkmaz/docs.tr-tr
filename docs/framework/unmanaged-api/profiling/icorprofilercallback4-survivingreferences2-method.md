---
title: "ICorProfilerCallback4::SurvivingReferences2 Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.SurvivingReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ced8542d2e84b6c317e20d7ff440e6c159383bfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2 Yöntemi
Sıkıştırılmasını olmayan çöp toplama sonucunda yığınındaki nesneleri Düzen bildirir. Profil Oluşturucu uygulanırsa bu yöntem çağrılır [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimi. Bu geri çağırma değiştirir [Icorprofilercallback2::survivingreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) yöntemi, daha büyük olan uzunluğu aşan bir ULONG ifade edilebilir nesneleri aralıklarına raporlayabilirsiniz olduğundan.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cSurvivingObjectIDRanges`  
 [in] Sıkıştırılmasını olmayan çöp toplama sonucu olarak derdi bitti bitişik nesnelerin bloğu sayısı. Diğer bir deyişle, değeri `cSurvivingObjectIDRanges` boyutu `objectIDRangeStart` ve `cObjectIDRangeLength` diziler, hangi depolama bir `ObjectID` ve uzunluk, sırasıyla, her bir bloğunda nesneleri için.  
  
 Sonraki iki bağımsız değişkenleri `SurvivingReferences2` paralel dizidir. Diğer bir deyişle, `objectIDRangeStart` ve `cObjectIDRangeLength` bitişik nesneleri aynı bloğunu ilgilendiren.  
  
 `objectIDRangeStart`  
 [in] Bir dizi `ObjectID` her biri bitişik bloğunun başlangıç adresi olduğunda, değerleri, bellekte nesneleri canlı.  
  
 `cObjectIDRangeLength`  
 [in] Her biri sağlam bir blok bellekte bitişik nesnelerin boyutudur dizisi.  
  
 Başvuru her blok için belirtilen bir boyutu `objectIDRangeStart` dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 Öğelerini `objectIDRangeStart` ve `cObjectIDRangeLength` diziler kabul aşağıdaki gibi bir nesne atık toplama derdi bitti olup olmadığını belirlemek için. Varsayımında bir `ObjectID` değeri (`ObjectID`) aşağıdaki aralık içinde yer:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Herhangi bir değer için `i` aşağıdaki aralıkta olduğundan, nesne çöp toplama derdi bitti:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Sıkıştırılmasını olmayan çöp toplama "ölü" nesneleri tarafından kapladığı bellek kaldırsa ancak boşaltılmış alan compact değil. Sonuç olarak, bellek için yığın döndürüldü, ancak hiçbir "canlı" nesneler taşınır.  
  
 Ortak dil çalışma zamanı (CLR) çağırır `SurvivingReferences2` sıkıştırılmasını olmayan çöp koleksiyonları için. Sıkıştırma çöp koleksiyonları için [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) yerine olarak adlandırılır. Tek çöp toplama, tek bir nesil sıkıştırma ve diğer olmayan sıkıştırılmasını olabilir. Belirli bir oluşturma hakkında bir atık toplama için profil oluşturucu ya da alacak bir `SurvivingReferences2` geri çağırma veya bir [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) geri çağırma, ancak ikisini.  
  
 Birden çok `SurvivingReferences2` geri aramalar alınan sınırlı iç arabelleğe alma nedeniyle ek olarak, belirli atık toplama, sunucu çöp toplama sırasında birden çok geri aramalar ve diğer nedenler sırasında. Çöp toplama sırasında birden çok geri aramalar söz konusu olduğunda toplu bilgileridir; içinde bildirilen tüm başvuruları `SurvivingReferences2` geri çağırma varlığını sürdürmesini atık toplama.  
  
 Profil Oluşturucu her ikisi de uyguluyorsa [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) ve [Icorprofilercallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) arabirimleri, `SurvivingReferences2` yöntemi çağrılmadan önce [Icorprofilercallback2:: SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) yöntemi, ancak yalnızca `SurvivingReferences2` başarıyla döndürür. Profil oluşturucular hatasından gösteren bir HRESULT dönebilirsiniz `SurvivingReferences2` ikinci yöntem çağırma önlemek için yöntem.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Icorprofilercallback arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Icorprofilercallback2 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [Icorprofilercallback4 arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
