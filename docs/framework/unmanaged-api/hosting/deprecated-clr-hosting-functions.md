---
title: Kullanım Dışı CLR Barındırma İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa84ca0defd173563817673aad183a8b64226d41
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135817"
---
# <a name="deprecated-clr-hosting-functions"></a>Kullanım Dışı CLR Barındırma İşlevleri
Bu bölümde barındırma API'sinin önceki sürümlerinde kullanılan yönetilmeyen genel statik işlevler açıklanmaktadır.  
  
 Altyapı işlevleri (`_Cor*` işlevler), yalnızca .NET Framework tarafından kullanılır, bu işlevler de kullanımdan kaldırılan [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="activation-functions"></a>Etkinleştirme işlevleri  
 [ClrCreateManagedInstance İşlevi](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 Kullanım dışı. Belirli bir yönetilen türün bir örneğini oluşturur.  
  
 [CoInitializeCor İşlevi](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 Kullanımdan kalktı. Ortak dil çalışma zamanı (CLR) başlatmak için ya da kullanmak [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).  
  
 [CoInitializeEE İşlevi](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 Kullanım dışı. CLR yürütme motorunun bir işleme yüklenmesini sağlar. Kullanım [Iclrruntimehost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi yerine.  
  
 [CorBindToCurrentRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 Kullanım dışı. Ortak dil çalışma zamanı (CLR), bir XML dosyasında depolanan sürüm bilgilerini kullanarak bir işlem içine yükler.  
  
 [CorBindToRuntime İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 Kullanım dışı. CLR'yi bir işleme yüklemek için yöneilmeyen ana bilgisayarları etkinleştirir.  
  
 [CorBindToRuntimeByCfg İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 Kullanım dışı. CLR, bir XML dosyasından okunan sürüm bilgilerini kullanarak bir işlem içine yükler.  
  
 [CorBindToRuntimeEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 Kullanım dışı. CLR'yi bir işleme yüklemek için yönetilmeyen ana bilgisayarları etkinleştirir ve CLR'nin davranışını belirtmek için bayrakları ayarlamanızı sağlar.  
  
 [CorBindToRuntimeHost İşlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 Kullanım dışı. Bir işleme belirtilen bir CLR sürümü yüklemek için ana bilgisayarları etkinleştirir.  
  
 [GetCORRequiredVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 Kullanım dışı. Gerekli CLR sürüm numarasını alır.  
  
 [GetCORSystemDirectory İşlevi](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 Kullanım dışı. İşlem içine yüklenmiş CLR yükleme dizinini döndürür.  
  
 [GetRealProcAddress İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 Kullanım dışı. En son yüklenen sürümünden CLR dışa aktarılan belirtilen işlevin adresini alır.  
  
 [GetRequestedRuntimeInfo İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 Kullanım dışı. Bir uygulama tarafından istenen CLR hakkındaki sürüm ve dizin bilgilerini alır.  
  
## <a name="clr-version-functions"></a>CLR sürüm işlevleri  
 Bu bölümdeki işlevler bir CLR sürümü döndürür; Bunlar, CLR'yi etkinleştirmez.  
  
 [GetCORVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 Kullanım dışı. Geçerli işlemde çalışan CLR'nin sürüm numarasını döndürür.  
  
 [GetFileVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 Kullanım dışı. Belirtilen arabelleği kullanarak belirtilen dosyanın CLR sürümü bilgisini alır.  
  
 [GetRequestedRuntimeVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 Kullanım dışı. Belirtilen uygulamanın istediği CLR sürüm numarasını alır. Bu sürüm yüklü değilse istenen sürümden önce yüklenen en son sürümü alır.  
  
 [GetRequestedRuntimeVersionForCLSID İşlevi](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 Kullanım dışı. Belirtilen CLSID'yi içeren sınıf için uygun CLR sürümü bilgisini alır.  
  
 [GetVersionFromProcess İşlevi](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 Kullanım dışı. Belirtilen işlem tanımlayıcısıyla ilişkili CLR sürüm numarasını alır.  
  
 [LockClrVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 Kullanım dışı. Hangi CLR sürümünün işlem dahilinde CLR açıkça başlatılmadan önce kullanılacak belirlemek konak sağlar.  
  
## <a name="hosting-functions"></a>Barındırma işlevleri  
 [CallFunctionShim İşlevi](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 Kullanım dışı. Belirtilen kitaplık içinde belirtilen ad ve parametreler içeren işleve bir çağrı yapar.  
  
 [CoEEShutDownCOM İşlevi](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 Kullanım dışı. İşlemden COM derlemesini kaldırır.  
  
 [CorExitProcess İşlevi](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 Kullanım dışı. Yönetilmeyen geçerli işlemi kapatır.  
  
 [CorLaunchApplication İşlevi](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 Kullanım dışı. Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolunda uygulamayı başlatır.  
  
 [CorMarkThreadInThreadPool İşlevi](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 Kullanım dışı. Yürütülmekte olan iş parçacığı havuzu iş parçacığını yönetilen kodun yürütülmesi için işaretler. Bu işlev, .NET Framework sürüm 2.0 ile başlayarak, hiçbir etkisi olmaz. Gerekli değildir ve kodunuzdan kaldırılabilir.  
  
 [CoUninitializeCor İşlevi](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 Kullanımdan kalktı. CLR bir işlemden olamaz.  
  
 [CoUninitializeEE İşlevi](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 Kullanımdan kalktı.  
  
 [CreateDebuggingInterfaceFromVersion İşlevi](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 Kullanım dışı. Oluşturur bir [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) nesne belirtilen sürüm bilgisi esas alarak.  
  
 [CreateICeeFileGen İşlevi](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 Kullanım dışı. Oluşturur bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesne.  
  
 [DestroyICeeFileGen İşlevi](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 Kullanım dışı. Yok eder bir [Iceefilegen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) nesne.  
  
 [FExecuteInAppDomainCallback İşlev İşaretçisi](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 Kullanım dışı. CLR'nin yönetilen kodu yürütmek için çağırdığı bir işleve işaret eder.  
  
 [FLockClrVersionCallback İşlev İşaretçisi](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 Kullanım dışı. CLR ana bilgisayara bildirmek için çağırdığı bir işleve işaret başlatmanın çalışmaya tamamlandı ya da.  
  
 [GetCLRIdentityManager İşlevi](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 Kullanım dışı. CLR'nin kimlikleri yönetmenize izin veren bir arabirim işaretçisi alır.  
  
 [LoadLibraryShim İşlevi](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 Kullanım dışı. Belirtilen bir .NET Framework DLL sürümünü yükler.  
  
 [LoadStringRC İşlevi](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 Kullanım dışı. Geçerli iş parçacığının varsayılan kültürünü kullanarak, bir HRESULT değerini hata iletisine çevirir.  
  
 [LoadStringRCEx İşlevi](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 Kullanım dışı. HRESULT değerini belirtilen kültür için uygun hata iletisine çevirir.  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 Kullanım dışı. Tamamlandığı zaman ana bilgisayara bildiren bir işleve işaret eder (diğer bir deyişle, zaman uyumsuz) bir aygıt g/ç işlemi tamamlandı.  
  
 [LPTHREAD_START_ROUTINE İşlev İşaretçisi](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 Kullanım dışı. Bir iş parçacığının yürütülmeye başlandığını ana bilgisayara bildiren bir işleve işaret eder.  
  
 [RunDll32ShimW İşlevi](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 Kullanım dışı. Belirtilen komutu yürütür.  
  
 [WAITORTIMERCALLBACK İşlev İşaretçisi](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 Kullanım dışı. Ana bilgisayar bekleme tanıtıcısı sinyal veya zaman aşımına uğradı olduğunu bildiren bir işleve işaret eder.  
  
## <a name="infrastructure-functions"></a>Altyapı işlevleri  
 Bu bölümdeki işlevler yalnızca .NET Framework tarafından içindir.  
  
 [_CorDllMain İşlevi](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 CLR'yi başlatır, DLL derlemesinin CLR başlığındaki yönetilen giriş noktasını bulur ve yürütmeyi başlatır.  
  
 [_CorExeMain İşlevi](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 CLR'yi başlatır, derlemesinin CLR başlığındaki yönetilen giriş noktasını bulur ve yürütmeyi başlatır.  
  
 [_CorExeMain2 İşlevi](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 Belirtilen bellek eşlemeli kod içinde giriş noktasını yürütür. Bu işlev, işletim sistemi yükleyicisi tarafından çağrılır.  
  
 [_CorImageUnloading İşlevi](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 Yönetilen modül görüntüleri yüklenmediği zaman yükleyiciye bildirir.  
  
 [_CorValidateImage İşlevi](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 Yönetilen modül görüntüleri doğrular ve bunlar yüklendikten sonra işletim sistemi yükleyicisi bildirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 4 Barındırma Genel Statik İşlevleri](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md)
