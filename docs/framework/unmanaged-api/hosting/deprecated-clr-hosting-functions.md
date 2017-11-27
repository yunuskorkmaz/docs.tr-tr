---
title: "Kullanım Dışı CLR Barındırma İşlevleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9530fecb4f2ca6f59d165e49c282320966fd2fa8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="deprecated-clr-hosting-functions"></a>Kullanım Dışı CLR Barındırma İşlevleri
Bu bölümde barındırma API önceki sürümlerinde kullanılan yönetilmeyen genel statik işlevler açıklanmaktadır.  
  
 Altyapı işlevleri (`_Cor*` işlevler), yalnızca .NET Framework tarafından kullanılır, bu işlevler de kullanım dışı bırakıldı [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="activation-functions"></a>Etkinleştirme işlevleri  
 [Clrcreatemanagedınstance işlevi](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 Kullanım dışı. Belirtilen yönetilen türü örneğini oluşturur.  
  
 [Coınitializecor işlevi](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 Kullanımdan kalktı. Ortak dil çalışma zamanı (CLR) başlatmak için kullanın ya da [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
 [Coınitializeee işlevi](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 Kullanım dışı. CLR yürütme altyapısı bir işlemine yüklendi sağlar. Kullanım [Iclrruntimehost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi yerine.  
  
 [CorBindToCurrentRuntime işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 Kullanım dışı. Ortak dil çalışma zamanı (CLR), bir XML dosyasında depolanan sürüm bilgileri kullanarak bir sürecine yükler.  
  
 [CorBindToRuntime işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 Kullanım dışı. CLR süreç içine yüklemek için yönetilmeyen konakları etkinleştirir.  
  
 [CorBindToRuntimeByCfg işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 Kullanım dışı. CLR bir XML dosyasından okuma sürüm bilgilerini kullanarak bir sürecine yükler.  
  
 [CorBindToRuntimeEx işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 Kullanım dışı. CLR süreç içine yüklemek yönetilmeyen ana bilgisayarları etkinleştirir ve CLR davranışını belirtmek için bayrakları ayarlamanıza olanak tanır.  
  
 [CorBindToRuntimeHost işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 Kullanım dışı. Süreç içine CLR belirtilen bir sürümünü yüklemek ana bilgisayarları sağlar.  
  
 [GetCORRequiredVersion işlevi](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 Kullanım dışı. Gerekli CLR sürüm numarasını alır.  
  
 [GetCORSystemDirectory işlevi](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 Kullanım dışı. İşlem içine yüklenmiş CLR yükleme dizinini döndürür.  
  
 [GetRealProcAddress işlevi](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 Kullanım dışı. Son yüklenen sürümünden CLR dışarı belirtilen işlev adresi alır.  
  
 [Getrequestedruntimeınfo işlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 Kullanım dışı. Bir uygulama tarafından istenen CLR sürümü ve dizin bilgilerini alır.  
  
## <a name="clr-version-functions"></a>CLR sürüm işlevleri  
 Bu bölümdeki işlevler CLR sürümü döndürür; CLR etkinleştirmeyin.  
  
 [GetCORVersion işlevi](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 Kullanım dışı. Geçerli işlemde çalışan CLR sürüm numarasını döndürür.  
  
 [GetFileVersion işlevi](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 Kullanım dışı. Belirtilen arabellek kullanarak dosyanın belirtilen CLR sürüm bilgilerini alır.  
  
 [GetRequestedRuntimeVersion işlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 Kullanım dışı. Belirtilen uygulama tarafından istenen CLR sürüm numarasını alır. Bu sürümü yüklü değilse, önce istenen sürümü yüklü en son sürümünü alır.  
  
 [Getrequestedruntimeversionforclsıd işlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 Kullanım dışı. Belirtilen CLSID sınıfı için uygun CLR sürüm bilgilerini alır.  
  
 [GetVersionFromProcess işlevi](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 Kullanım dışı. Belirtilen işlem tanıtıcı ile ilişkili CLR sürüm numarasını alır.  
  
 [LockClrVersion işlevi](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 Kullanım dışı. CLR açıkça başlatmadan önce işlemi içinde CLR hangi sürümünün kullanılacağını belirlemek için ana sağlar.  
  
## <a name="hosting-functions"></a>Barındırma işlevleri  
 [CallFunctionShim işlevi](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 Kullanım dışı. Belirtilen ada ve parametreleri belirtilen Kitaplığı'nda sahip işlevine bir çağrı yapar.  
  
 [CoEEShutDownCOM işlevi](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 Kullanım dışı. Bir COM derlemesine işleminden kaldırır.  
  
 [CorExitProcess işlevi](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 Kullanım dışı. Geçerli yönetilmeyen işlemi kapatır.  
  
 [CorLaunchApplication işlevi](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 Kullanım dışı. Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolundaki uygulamayı başlatır.  
  
 [Cormarkthreadınthreadpool işlevi](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 Kullanım dışı. Yönetilen kod yürütülmesi için şu anda yürütülen iş parçacığı havuzu iş parçacığı işaretler. .NET Framework sürüm 2.0 ile başlayarak, bu işlev hiçbir etkisi olmaz. Gerekli değildir ve kodunuzdan kaldırılabilir.  
  
 [CoUninitializeCor işlevi](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 Kullanımdan kalktı. CLR bir işlemden kaldırılamıyor.  
  
 [CoUninitializeEE işlevi](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 Kullanımdan kalktı.  
  
 [Createdebuggingınterfacefromversion işlevi](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 Kullanım dışı. Oluşturur bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) nesne tabanlı belirtilen sürüm bilgileri.  
  
 [Createıceefilegen işlevi](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 Kullanım dışı. Oluşturur bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesnesi.  
  
 [Destroyıceefilegen işlevi](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 Kullanım dışı. Bozar bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesnesi.  
  
 [Fexecuteınappdomaincallback işlev işaretçisi](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 Kullanım dışı. Yönetilen kod yürütmek için CLR çağıran bir işlev noktalarına.  
  
 [FLockClrVersionCallback işlev işaretçisi](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 Kullanım dışı. Konak bildirmek için CLR çağıran bir işlev noktalarına başlatmanın başlatılan tamamlandı ya da.  
  
 [Getclrıdentitymanager işlevi](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 Kullanım dışı. Bir işaretçi kimlikleri yönetmek CLR sağlayan bir arabirim alır.  
  
 [LoadLibraryShim işlevi](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 Kullanım dışı. .NET Framework DLL belirtilen sürümünü yükler.  
  
 [LoadStringRC işlevi](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 Kullanım dışı. Bir HRESULT değeri, geçerli iş parçacığının varsayılan kültürü kullanarak hata iletisine çevirir.  
  
 [LoadStringRCEx işlevi](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 Kullanım dışı. Uygun bir hata iletisi belirtilen kültür için HRESULT değerine dönüşür.  
  
 [Lpoverlapped_completıon_routıne işlev işaretçisi](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 Kullanım dışı. İşaret eden bir çakışan olduğunda ana bilgisayar bildiren bir işlev (diğer bir deyişle, zaman uyumsuz) bir aygıt g/ç işlemi tamamlandı.  
  
 [Lpthread_start_routıne işlev işaretçisi](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 Kullanım dışı. Bir iş parçacığını yürütmek için başlatıldı konak bildiren bir işlev noktalarına.  
  
 [RunDll32ShimW işlevi](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 Kullanım dışı. Belirtilen komut yürütür.  
  
 [WAITORTIMERCALLBACK işlev işaretçisi](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 Kullanım dışı. Ana bilgisayar bekleme tanıtıcısı da işaret veya bırakıldığı zaman aşımına uğradı olduğunu bildiren bir işlev noktalarına.  
  
## <a name="infrastructure-functions"></a>Altyapı işlevleri  
 Bu bölümde yalnızca .NET Framework tarafından kullanılmak üzere işlevlerdir.  
  
 [_CorDllMain işlevi](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 CLR başlatır, DLL derlemenin CLR üstbilgisinde yönetilen giriş noktasını bulur ve yürütmeye başlar.  
  
 [_CorExeMain işlevi](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 CLR başlatır, yürütülebilir derlemenin CLR üstbilgisinde yönetilen giriş noktasını bulur ve yürütmeye başlar.  
  
 [_CorExeMain2 işlevi](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 Giriş noktası belirtilen bellekle eşlenen kodu yürütür. Bu işlev, işletim sistemi yükleyicisi tarafından çağrılır.  
  
 [_Corımageunloading işlevi](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 Yönetilen modül görüntüleri kaldırılır, yükleyici size bildirir.  
  
 [_Corvalidateımage işlevi](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 Yönetilen modül görüntüleri doğrular ve bunlar yüklendikten sonra işletim sistemi yükleyicisi bildirir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET framework 4 barındırma genel statik işlevleri](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md) 
