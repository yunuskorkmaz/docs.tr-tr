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
ms.openlocfilehash: bec50183e6a8690cb02f3dc06d32b7449e055cea
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865174"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2 Yöntemi
Sıkıştırma olmayan bir atık toplama işleminin sonucu olarak yığındaki nesnelerin yerleşimini raporlar. Profil Oluşturucu [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimini uygulamışsa, bu yöntem çağrılır. Bu geri çağırma, [ICorProfilerCallback2:: Evingreferences](icorprofilercallback2-survivingreferences-method.md) yönteminin yerini alır, çünkü uzunluklarda bir ULONG 'ta belirtilebilecekleri daha büyük aralıklar bildirebilirler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cSurvivingObjectIDRanges`  
 'ndaki Sıkıştırma olmayan çöp toplamanın sonucu olarak kalan bitişik nesnelerin blok sayısı. Diğer bir deyişle, `cSurvivingObjectIDRanges` değeri, her nesne bloğu için sırasıyla bir `ObjectID` ve uzunluğu depolayan `objectIDRangeStart` ve `cObjectIDRangeLength` dizilerinin boyutudur.  
  
 `SurvivingReferences2` sonraki iki bağımsız değişkeni paralel dizilerdir. Diğer bir deyişle, `objectIDRangeStart` ve `cObjectIDRangeLength` aynı bitişik nesne bloğunu ilgilendirin.  
  
 `objectIDRangeStart`  
 'ndaki Her biri, bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan `ObjectID` değerlerden oluşan bir dizi.  
  
 `cObjectIDRangeLength`  
 'ndaki Her biri bellekteki bitişik nesnelerin devam eden bloğunun boyutu olan tamsayılar dizisi.  
  
 `objectIDRangeStart` dizisinde başvurulan her bir blok için bir boyut belirtilir.  
  
## <a name="remarks"></a>Açıklamalar  
 `objectIDRangeStart` ve `cObjectIDRangeLength` dizilerinin öğeleri, bir nesnenin çöp toplamayı bir daha fazla kullanıp kullanmadığını belirlemekte aşağıdaki şekilde yorumlanmalıdır. `ObjectID` bir değerin (`ObjectID`) aşağıdaki aralıkta olduğunu varsayın:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Aşağıdaki aralıktaki `i` herhangi bir değeri için, nesne çöp toplamayı sona bıraktı:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Sıkıştırma olmayan bir atık toplama, "ölü" nesneler tarafından kullanılan belleği geri kazanır, ancak serbest bırakılmış alanı sıkıştıramaz. Sonuç olarak, bellek yığına döndürülür, ancak hiçbir "canlı" nesne taşınmaz.  
  
 Ortak dil çalışma zamanı (CLR), sıkıştırma olmayan çöp koleksiyonları için `SurvivingReferences2` çağırır. Atık koleksiyonları sıkıştırmak için, bunun yerine [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) çağırılır. Tek bir çöp toplama işlemi, bir oluşturma için ve sıkıştırma dışı bir diğeri için sıkıştırılıyor olabilir. Belirli nesil bir atık toplama için, profil oluşturucu bir `SurvivingReferences2` geri çağırma veya [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) geri çağırması alır, ancak her ikisini birden etmez.  
  
 Belirli bir çöp toplama işlemi sırasında birden çok `SurvivingReferences2` geri çağırma işlemleri, sınırlı iç arabellek, sunucu çöp toplama sırasında birden fazla geri çağırma ve diğer nedenlerden dolayı alınabilir. Çöp toplama sırasında birden fazla geri çağırma durumunda, bilgiler birikimlidir; Tüm `SurvivingReferences2` geri çağırmada raporlanan tüm başvurular çöp toplamayı sürdürmemiştir.  
  
 Profiler hem [ICorProfilerCallback](icorprofilercallback-interface.md) hem de [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimlerini uygularsa, `SurvivingReferences2` yöntemi [ICorProfilerCallback2:: ıvınreferences](icorprofilercallback2-survivingreferences-method.md) yönteminden önce çağrılır, ancak yalnızca `SurvivingReferences2` başarıyla döndürülür. Profil oluşturucular, ikinci yöntemi çağırmayı önlemek için `SurvivingReferences2` yönteminden hata belirten bir HRESULT döndürebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
