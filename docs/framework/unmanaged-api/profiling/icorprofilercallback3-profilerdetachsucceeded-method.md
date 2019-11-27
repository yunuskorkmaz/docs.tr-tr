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
ms.openlocfilehash: b044c493649b73566a2e70db2e19977a6a7b877d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439453"
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
 `ProfilerDetachSucceeded` geri çağırması, tüm iş parçacıkları profil oluşturucunun kodundan çıkıldıktan sonra verilir. Bu yöntem çağrıldığında, profil oluşturucu, Kullanıcı arabirimine veya günlüğe kaydetme bileşenine bildirimde bulunmak gibi yıkıcısı için uygun olmayan son dakika görevleri gerçekleştirmelidir. Ancak, bu geri arama sırasında ( [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) veya `IMetaData*` arabirimleri gibi), PROFIL Oluşturucu CLR tarafından sunulan arabirimlerde işlevleri çağırmamalıdır.  
  
 CLR, ayırma işleminin başarılı olduğunu göstermek için Windows uygulama olay günlüğü 'nde bir giriş oluşturur.  
  
 Profil Oluşturucu bu geri aramadan döndüğünde, CLR Profil Oluşturucu nesnesini serbest bırakır ve profil oluşturucu DLL 'yi kaldırır. Bu nedenle, profil oluşturucunun, yürütme bu geri çağrısından sonra profil oluşturucu DLL içinde oluşmasına neden olacak herhangi bir eylem gerçekleştirmemelidir. Örneğin, iş parçacığı oluşturmamalıdır veya zamanlayıcı geri çağırmaları kaydetmemelidir.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Meta Veri Arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [ICorProfilerInfo3 Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Profil Oluşturma Arabirimleri](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profil Oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
