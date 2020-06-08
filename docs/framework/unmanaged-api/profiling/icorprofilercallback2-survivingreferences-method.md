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
ms.openlocfilehash: 3681106bca94f1fefb2f24a1aa4254eb2b1b0531
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499746"
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences Yöntemi
Sıkıştırma olmayan bir atık toplama işleminin sonucu olarak yığındaki nesnelerin yerleşimini raporlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
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
 'ndaki Sıkıştırma olmayan çöp toplamanın sonucu olarak kalan bitişik nesnelerin blok sayısı. Diğer bir deyişle, değeri, `cSurvivingObjectIDRanges` `objectIDRangeStart` `cObjectIDRangeLength` `ObjectID` her nesne bloğu için sırasıyla bir ve uzunluğu depolayan ve dizilerinin boyutudur.  
  
 Sonraki iki bağımsız değişkeni `SurvivingReferences` paralel dizilerdir. Diğer bir deyişle, `objectIDRangeStart` `cObjectIDRangeLength` aynı bitişik nesne bloğuna sorun.  
  
 `objectIDRangeStart`  
 'ndaki `ObjectID`Her biri, bellekte bulunan bitişik ve canlı nesneler bloğunun başlangıç adresi olan bir değer dizisi.  
  
 `cObjectIDRangeLength`  
 'ndaki Her biri bellekteki bitişik nesnelerin devam eden bloğunun boyutu olan tamsayılar dizisi.  
  
 Dizide başvurulan her bir blok için bir boyut belirtilir `objectIDRangeStart` .  
  
## <a name="remarks"></a>Açıklamalar  
  
> [!IMPORTANT]
> Bu yöntem `MAX_ULONG` , 64-bit platformlarda 4 GB 'den büyük nesneler için boyutları raporlar. 4 GB 'den büyük nesneler için bunun yerine [ICorProfilerCallback4:: SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md) metodunu kullanın.  
  
 Ve dizilerinin öğeleri, `objectIDRangeStart` `cObjectIDRangeLength` bir nesnenin çöp toplamayı daha fazla kullanıp kullanmadığını anlamak için aşağıdaki şekilde yorumlanmalıdır. Bir `ObjectID` değerin ( `ObjectID` ) aşağıdaki aralıkta olduğunu varsayın:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Aşağıdaki aralıkta olan herhangi bir değeri için `i` , nesne çöp toplamayı sona bıraktı:  
  
 0 <=`i` < `cSurvivingObjectIDRanges`  
  
 Sıkıştırma olmayan bir atık toplama, "ölü" nesneler tarafından kullanılan belleği geri kazanır, ancak serbest bırakılmış alanı sıkıştıramaz. Sonuç olarak, bellek yığına döndürülür, ancak hiçbir "canlı" nesne taşınmaz.  
  
 Ortak dil çalışma zamanı (CLR), `SurvivingReferences` sıkıştırma olmayan çöp koleksiyonları için çağırır. Atık koleksiyonları sıkıştırmak için, bunun yerine [ICorProfilerCallback:: MovedReferences](icorprofilercallback-movedreferences-method.md) çağrılır. Tek bir çöp toplama işlemi, bir oluşturma için ve sıkıştırma dışı bir diğeri için sıkıştırılıyor olabilir. Belirli nesil bir atık toplama için, profil oluşturucu bir `SurvivingReferences` geri çağırma ya da `MovedReferences` geri çağırma alır, ancak her ikisini birden etmez.  
  
 `SurvivingReferences`Sınırlı iç arabelleğe alma, sunucu çöp toplama durumunda birden çok iş parçacığı raporlama ve diğer nedenlerden dolayı belirli bir atık toplama sırasında birden fazla geri çağırma alınabilir. Çöp toplama sırasında birden fazla geri çağırma durumunda, bilgiler birikimlidir. herhangi bir geri aramada bildirilen tüm başvurular `SurvivingReferences` çöp toplamayı sürdürmelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 Arabirimi](icorprofilercallback2-interface.md)
- [SurvivingReferences2 Yöntemi](icorprofilercallback4-survivingreferences2-method.md)
