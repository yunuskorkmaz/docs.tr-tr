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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d63dd911a5f674a3ce0b02ec78de443c7aebf84
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747165"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown Yöntemi
Profil Oluşturucu, uygulamanın kapanacağını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu kodu güvenli bir şekilde yöntemlerine çağrılamıyor [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) sonra arabirim `Shutdown` yöntemi çağrılır. Çağrıları `ICorProfilerInfo` yöntemleri sonra tanımsız davranışa neden `Shutdown` yöntemi döndürür. Sabit belirli olaylar kapatıldıktan sonra yine de oluşabilir. Profil Oluşturucu hemen bu oluştuğunda döndürülecek ilgileniriz.  
  
 `Shutdown` Yöntemin çağrılacağı, profili oluşturulan yönetilen uygulama yönetilen kod başladıysanız (diğer bir deyişle, ilk çerçeve işlem yığın üzerinde yönetilen). Uygulamanın yönetilmeyen kod olarak başlatıldı, ancak daha sonra yönetilen koda Atlanan, dolayısıyla örneği ortak dil çalışma zamanı (CLR), ardından oluşturma `Shutdown` çağrılmaz. Bu durumlarda, kitaplıkta profil oluşturucu içermelidir bir `DllMain` DLL_PROCESS_DETACH kullanan yordamı değeri tüm kaynakları serbest bırakın ve izlemeleri ve disk temizleme gibi verileri temizleme işlemini gerçekleştirin.  
  
 Genel olarak, Profil Oluşturucu ile beklenmeyen kapatma başa gerekir. Örneğin, bir işlem Win32's durdu `TerminateProcess` yöntemi (Winbase.h içinde bildirilen). Diğer durumlarda, belirli yönetilen iş parçacıkları (arka plan iş parçacıkları) sıralı yok etme iletileri için bunları sunmakla olmadan CLR durdurulur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Üst bilgi:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Initialize Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
