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
ms.openlocfilehash: 83e32b2b69d53772f8a4ebaabe1c025b95d1da47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown Yöntemi
Profil Oluşturucu uygulamanın kapanacağını bildirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Profil Oluşturucu kodu güvenle yöntemleri çağrılamaz [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) sonra arabirim `Shutdown` yöntemi çağrılır. Yapılan her çağrı `ICorProfilerInfo` yöntemleri neden sonra tanımsız davranış `Shutdown` yöntemi döndürür. Değişmez belirli olaylar kapatıldıktan sonra hala oluşabilir; Profil Oluşturucu hemen bu oluştuğunda döndürülecek ilgilenebilmek.  
  
 `Shutdown` Yöntemi çağrılır, yalnızca profili oluşturuluyor yönetilen uygulama yönetilen kod başladıysanız (diğer bir deyişle, ilk çerçeve işlem yığında yönetilen). Uygulama yönetilmeyen kodu olarak başladı, ancak daha sonra yönetilen koda Atlanan, böylece örneği ortak dil çalışma zamanı (CLR), ardından oluşturmayı `Shutdown` çağrılmaz. Bu durumlarda, kendi Kitaplığı'nda profil oluşturucu içermelidir bir `DllMain` DLL_PROCESS_DETACH kullanan yordamı değer tüm kaynakları serbest ve vb. diske izlemeleri temizleme gibi verilerini temizleme işlenmesini gerçekleştirme.  
  
 Genel olarak, Profil Oluşturucu ile beklenmeyen kapatmalar başa gerekir. Örneğin, bir işlem Win32 tarafından 's durdurulamaz `TerminateProcess` yöntemi (Winbase.h içinde bildirilen). Diğer durumlarda, CLR düzenli yok etme iletileri kendileri için sunmakla olmadan belirli yönetilen iş parçacığı (arka plan iş parçacıkları) durdurulur.  
  
## <a name="requirements"></a>Gereksinimler  
 **Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Başlık:** CorProf.idl, CorProf.h  
  
 **Kitaplığı:** CorGuids.lib  
  
 **.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ICorProfilerCallback Arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Initialize Yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
