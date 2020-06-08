---
title: ICorProfilerCallback3::ProfilerDetachSucceeded Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
ms.openlocfilehash: 93406dddf7babd8cf61032666737b993c2f721f4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499603"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>ICorProfilerCallback3::ProfilerDetachSucceeded Yöntemi
Profil oluşturucuyu ortak dil çalışma zamanının (CLR) profil oluşturucu DLL 'sini kaldırmak üzere olduğunu bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bu geri çağırmada döndürülen değer yoksayıldı.  
  
## <a name="remarks"></a>Açıklamalar  
 `ProfilerDetachSucceeded`Tüm iş parçacıkları profil oluşturucunun kodundan çıktıktan sonra geri çağırma yapılır. Bu yöntem çağrıldığında, profil oluşturucu, Kullanıcı arabirimine veya günlüğe kaydetme bileşenine bildirimde bulunmak gibi yıkıcısı için uygun olmayan son dakika görevleri gerçekleştirmelidir. Ancak profil oluşturucu, bu geri çağırma sırasında CLR tarafından sunulan arabirimlerde işlevleri çağırmamalıdır ( [ICorProfilerInfo](icorprofilerinfo-interface.md) veya `IMetaData*` arabirimleri gibi).  
  
 CLR, ayırma işleminin başarılı olduğunu göstermek için Windows uygulama olay günlüğü 'nde bir giriş oluşturur.  
  
 Profil Oluşturucu bu geri aramadan döndüğünde, CLR Profil Oluşturucu nesnesini serbest bırakır ve profil oluşturucu DLL 'yi kaldırır. Bu nedenle, profil oluşturucunun, yürütme bu geri çağrısından sonra profil oluşturucu DLL içinde oluşmasına neden olacak herhangi bir eylem gerçekleştirmemelidir. Örneğin, iş parçacığı oluşturmamalıdır veya zamanlayıcı geri çağırmaları kaydetmemelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../metadata/metadata-interfaces.md)
- [ICorProfilerInfo3 Arabirimi](icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](profiling-interfaces.md)
- [Profil Oluşturma](index.md)
