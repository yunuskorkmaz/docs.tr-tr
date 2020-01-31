---
title: ICorProfilerCallback::Shutdown Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: 490f9dd5446a51bd07881cdb9825d737e380a63e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865863"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown Yöntemi
Profil oluşturucuyu uygulamanın kapandığını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu kodu, `Shutdown` yöntemi çağrıldıktan sonra [ICorProfilerInfo](icorprofilerinfo-interface.md) arabiriminin yöntemlerini güvenli bir şekilde çağıramaz. `ICorProfilerInfo` yöntemlere yapılan çağrılar, `Shutdown` yöntemi döndüğünde tanımsız davranışa neden olur. Bazı sabit olaylar, kapatmadan sonra yine de gerçekleşebilir; Profil Oluşturucu, bu gerçekleştiğinde hemen döndürülmelidir.  
  
 `Shutdown` yöntemi yalnızca, profili oluşturulan yönetilen uygulama yönetilen kod olarak (yani, işlem yığınında ilk çerçeve yönetiliyorsa) başlatıldığında çağrılır. Uygulama, yönetilmeyen kod olarak başlatıldıysa ancak daha sonra yönetilen koda atlamışsa, bu nedenle ortak dil çalışma zamanının (CLR) bir örneğini oluşturup `Shutdown` çağırılacaktır. Bu gibi durumlarda, profil oluşturucu, tüm kaynakları serbest bırakmak ve verilerin temizleme işlemini gerçekleştirmek (örneğin, verileri diske bırakmak vb.) için DLL_PROCESS_DETACH değerini kullanan bir `DllMain` yordamını içermelidir.  
  
 Genel olarak, profil oluşturucunun beklenmedik kapanmalar ile Cope olması gerekir. Örneğin, bir işlem Win32's `TerminateProcess` yöntemi tarafından durdurulur (Winbase. h içinde bildirilmiştir). Diğer durumlarda CLR, belirli yönetilen iş parçacıklarını (arka plan iş parçacıkları) bunlar için düzenli olarak yok etme iletileri teslim etmeden durdurur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf. IDL, CorProf. h  
  
 **Kitaplık:** Corguid. lib  
  
 **.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](icorprofilercallback-interface.md)
- [Initialize Yöntemi](icorprofilercallback-initialize-method.md)
