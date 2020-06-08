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
ms.openlocfilehash: 208ce1d7ef8a1eab4f18a6d488f0cc480b5713d8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499343"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2 Yöntemi
Sıkıştırma olmayan bir atık toplama işleminin sonucu olarak yığındaki nesnelerin yerleşimini raporlar. Profil Oluşturucu [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimini uygulamışsa, bu yöntem çağrılır. Bu geri çağırma, [ICorProfilerCallback2:: Evingreferences](icorprofilercallback2-survivingreferences-method.md) yönteminin yerini alır, çünkü uzunluklarda bir ULONG 'ta belirtilebilecekleri daha büyük aralıklar bildirebilirler.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Sıkıştırma olmayan çöp toplamanın sonucu olarak kalan bitişik nesnelerin blok sayısı. Diğer bir deyişle, değeri, `cSurvivingObjectIDRanges` `objectIDRangeStart` `cObjectIDRangeLength` `ObjectID` her nesne bloğu için sırasıyla bir ve uzunluğu depolayan ve dizilerinin boyutudur.  
  
 Sonraki iki bağımsız değişkeni `SurvivingReferences2` paralel dizilerdir. Diğer bir deyişle, `objectIDRangeStart` `cObjectIDRangeLength` aynı bitişik nesne bloğuna sorun.  
  
 `objectIDRangeStart`  
 'ndaki `ObjectID`Her biri, bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan bir değer dizisi.  
  
 `cObjectIDRangeLength`  
 'ndaki Her biri bellekteki bitişik nesnelerin devam eden bloğunun boyutu olan tamsayılar dizisi.  
  
 Dizide başvurulan her bir blok için bir boyut belirtilir `objectIDRangeStart` .  
  
## <a name="remarks"></a>Açıklamalar  
 Ve dizilerinin öğeleri, `objectIDRangeStart` `cObjectIDRangeLength` bir nesnenin çöp toplamayı daha fazla kullanıp kullanmadığını anlamak için aşağıdaki şekilde yorumlanmalıdır. Bir `ObjectID` değerin ( `ObjectID` ) aşağıdaki aralıkta olduğunu varsayın:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Aşağıdaki aralıkta olan herhangi bir değeri için `i` , nesne çöp toplamayı sona bıraktı:  
  
 0 <=`i` < `cSurvivingObjectIDRanges`  
  
 Sıkıştırma olmayan bir atık toplama, "ölü" nesneler tarafından kullanılan belleği geri kazanır, ancak serbest bırakılmış alanı sıkıştıramaz. Sonuç olarak, bellek yığına döndürülür, ancak hiçbir "canlı" nesne taşınmaz.  
  
 Ortak dil çalışma zamanı (CLR), `SurvivingReferences2` sıkıştırma olmayan çöp koleksiyonları için çağırır. Atık koleksiyonları sıkıştırmak için, bunun yerine [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) çağırılır. Tek bir çöp toplama işlemi, bir oluşturma için ve sıkıştırma dışı bir diğeri için sıkıştırılıyor olabilir. Belirli nesil bir atık toplama için, profil oluşturucu bir `SurvivingReferences2` geri çağırma veya [MovedReferences2](icorprofilercallback4-movedreferences2-method.md) geri çağırması alır, ancak her ikisini birden etmez.  
  
 `SurvivingReferences2`Belirli bir çöp toplama işlemi sırasında, sınırlı iç arabellek, sunucu çöp toplama sırasında birden fazla geri çağırma ve diğer nedenlerden dolayı birden fazla geri çağırma alınabilir. Çöp toplama sırasında birden fazla geri çağırma durumunda, bilgiler birikimlidir; herhangi bir `SurvivingReferences2` geri çağırmada raporlanan tüm başvurular çöp toplamayı sürdürmemiştir.  
  
 Profil Oluşturucu hem [ICorProfilerCallback](icorprofilercallback-interface.md) hem de [ICorProfilerCallback4](icorprofilercallback4-interface.md) arabirimlerini uygularsa, `SurvivingReferences2` yöntemi [ICorProfilerCallback2:: ıvınreferences](icorprofilercallback2-survivingreferences-method.md) yönteminden önce çağrılır, ancak yalnızca `SurvivingReferences2` başarıyla döndürülür. Profil oluşturucular `SurvivingReferences2` , ikinci yöntemi çağırmayı önlemek için yöntemden hata belirten BIR hresult döndürebilir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
- [ICorProfilerCallback4 Arabirimi](icorprofilercallback4-interface.md)
