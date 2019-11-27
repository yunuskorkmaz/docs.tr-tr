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
ms.openlocfilehash: a83f8566dfe8e1b612f67d95a0e69947b72704ce
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439602"
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences Yöntemi
Sıkıştırma olmayan bir atık toplama işleminin sonucu olarak yığındaki nesnelerin yerleşimini raporlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametreler  
 `cSurvivingObjectIDRanges`  
 'ndaki Sıkıştırma olmayan çöp toplamanın sonucu olarak kalan bitişik nesnelerin blok sayısı. Diğer bir deyişle, `cSurvivingObjectIDRanges` değeri, her nesne bloğu için sırasıyla bir `ObjectID` ve uzunluğu depolayan `objectIDRangeStart` ve `cObjectIDRangeLength` dizilerinin boyutudur.  
  
 `SurvivingReferences` sonraki iki bağımsız değişkeni paralel dizilerdir. Diğer bir deyişle, `objectIDRangeStart` ve `cObjectIDRangeLength` aynı bitişik nesne bloğunu ilgilendirin.  
  
 `objectIDRangeStart`  
 'ndaki Her biri, bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan `ObjectID` değerlerden oluşan bir dizi.  
  
 `cObjectIDRangeLength`  
 'ndaki Her biri bellekteki bitişik nesnelerin devam eden bloğunun boyutu olan tamsayılar dizisi.  
  
 `objectIDRangeStart` dizisinde başvurulan her bir blok için bir boyut belirtilir.  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> Bu yöntem, 64-bit platformlarda 4 GB 'tan büyük nesneler için boyutları `MAX_ULONG` olarak raporlar. 4 GB 'den büyük nesneler için bunun yerine [ICorProfilerCallback4:: SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) metodunu kullanın.  
  
 `objectIDRangeStart` ve `cObjectIDRangeLength` dizilerinin öğeleri, bir nesnenin çöp toplamayı bir daha fazla kullanıp kullanmadığını belirlemekte aşağıdaki şekilde yorumlanmalıdır. `ObjectID` bir değerin (`ObjectID`) aşağıdaki aralıkta olduğunu varsayın:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Aşağıdaki aralıktaki `i` herhangi bir değeri için, nesne çöp toplamayı sona bıraktı:  
  
 0 < = `i` < `cSurvivingObjectIDRanges`  
  
 Sıkıştırma olmayan bir atık toplama, "ölü" nesneler tarafından kullanılan belleği geri kazanır, ancak serbest bırakılmış alanı sıkıştıramaz. Sonuç olarak, bellek yığına döndürülür, ancak hiçbir "canlı" nesne taşınmaz.  
  
 Ortak dil çalışma zamanı (CLR), sıkıştırma olmayan çöp koleksiyonları için `SurvivingReferences` çağırır. Atık koleksiyonları sıkıştırmak için, bunun yerine [ICorProfilerCallback:: MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) çağrılır. Tek bir çöp toplama işlemi, bir oluşturma için ve sıkıştırma dışı bir diğeri için sıkıştırılıyor olabilir. Belirli nesil bir atık toplama için, profil oluşturucu bir `SurvivingReferences` geri çağırma veya `MovedReferences` geri çağırması alır, ancak her ikisini birden etmez.  
  
 Belirli bir çöp toplama işlemi sırasında, sınırlı iç arabellek, sunucu çöp toplama durumunda birden çok iş parçacığı raporlama ve diğer nedenlerden dolayı birden çok `SurvivingReferences` geri çağırmaları alınabilir. Çöp toplama sırasında birden fazla geri çağırma durumunda, bilgiler birikimlidir. herhangi bir `SurvivingReferences` geri aramada bildirilen tüm başvurular çöp toplama işlemini sürdürmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [SurvivingReferences2 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
