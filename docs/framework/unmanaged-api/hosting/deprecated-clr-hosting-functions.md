---
title: Kullanım Dışı CLR Barındırma İşlevleri
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
ms.openlocfilehash: 8925278bdf4d48efc9e589ffc4e181d904444e6b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616430"
---
# <a name="deprecated-clr-hosting-functions"></a>Kullanım Dışı CLR Barındırma İşlevleri
Bu bölümde, barındırma API 'sinin önceki sürümlerinin kullanıldığı yönetilmeyen genel statik işlevler açıklanmaktadır.  
  
 `_Cor*`Yalnızca .NET Framework tarafından kullanılan altyapı işlevleri (işlevler) dışında, bu işlevler .NET Framework 4 ' te kullanım dışıdır.  
  
## <a name="activation-functions"></a>Etkinleştirme işlevleri  
 [ClrCreateManagedInstance İşlevi](clrcreatemanagedinstance-function.md)  
 Kullanım dışı. Belirtilen yönetilen türün bir örneğini oluşturur.  
  
 [CoInitializeCor İşlevi](coinitializecor-function.md)  
 Kullanımdan kalktı. Ortak dil çalışma zamanını (CLR) başlatmak için [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) veya [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)kullanın.  
  
 [CoInitializeEE İşlevi](coinitializeee-function.md)  
 Kullanım dışı. CLR yürütme altyapısının bir işleme yüklenmesini sağlar. Bunun yerine [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md) metodunu kullanın.  
  
 [CorBindToCurrentRuntime İşlevi](corbindtocurrentruntime-function.md)  
 Kullanım dışı. Bir XML dosyasında depolanan sürüm bilgilerini kullanarak ortak dil çalışma zamanını (CLR) bir işleme yükler.  
  
 [CorBindToRuntime İşlevi](corbindtoruntime-function.md)  
 Kullanım dışı. Yönetilmeyen ana bilgisayarların CLR 'yi bir işleme yüklemesine olanak sağlar.  
  
 [CorBindToRuntimeByCfg İşlevi](corbindtoruntimebycfg-function.md)  
 Kullanım dışı. XML dosyasından okunan sürüm bilgilerini kullanarak CLR 'yi bir işleme yükler.  
  
 [CorBindToRuntimeEx İşlevi](corbindtoruntimeex-function.md)  
 Kullanım dışı. Yönetilmeyen ana bilgisayarların CLR 'yi bir işleme yüklemesine olanak tanır ve CLR 'nin davranışını belirtmek için bayraklar ayarlamanıza olanak sağlar.  
  
 [CorBindToRuntimeHost İşlevi](corbindtoruntimehost-function.md)  
 Kullanım dışı. Ana bilgisayarların belirli bir CLR sürümünü bir işleme yüklemesine olanak sağlar.  
  
 [GetCORRequiredVersion İşlevi](getcorrequiredversion-function.md)  
 Kullanım dışı. Gereken CLR sürüm numarasını alır.  
  
 [GetCORSystemDirectory İşlevi](getcorsystemdirectory-function.md)  
 Kullanım dışı. İşleme yüklenen CLR 'nin yükleme dizinini döndürür.  
  
 [GetRealProcAddress İşlevi](getrealprocaddress-function.md)  
 Kullanım dışı. CLR 'nin en son yüklenen sürümünden aktarılmış olan belirtilen işlevin adresini alır.  
  
 [GetRequestedRuntimeInfo İşlevi](getrequestedruntimeinfo-function.md)  
 Kullanım dışı. Bir uygulama tarafından istenen CLR ile ilgili sürüm ve dizin bilgilerini alır.  
  
## <a name="clr-version-functions"></a>CLR sürüm işlevleri  
 Bu bölümdeki işlevler bir CLR sürümü döndürür; CLR 'yi etkinleştirmez.  
  
 [GetCORVersion İşlevi](getcorversion-function.md)  
 Kullanım dışı. Geçerli işlemde çalışan CLR 'nin sürüm numarasını döndürür.  
  
 [GetFileVersion İşlevi](getfileversion-function.md)  
 Kullanım dışı. Belirtilen arabelleği kullanarak belirtilen dosyanın CLR sürüm bilgilerini alır.  
  
 [GetRequestedRuntimeVersion İşlevi](getrequestedruntimeversion-function.md)  
 Kullanım dışı. Belirtilen uygulama tarafından istenen CLR 'nin sürüm numarasını alır. Bu sürüm yüklü değilse, istenen sürümden önce yüklenen en son sürümü alır.  
  
 [GetRequestedRuntimeVersionForCLSID İşlevi](getrequestedruntimeversionforclsid-function.md)  
 Kullanım dışı. Belirtilen CLSID ile sınıf için uygun CLR sürüm bilgilerini alır.  
  
 [GetVersionFromProcess İşlevi](getversionfromprocess-function.md)  
 Kullanım dışı. Belirtilen işlem tanıtıcısından ilişkilendirilen CLR 'nin sürüm numarasını alır.  
  
 [LockClrVersion İşlevi](lockclrversion-function.md)  
 Kullanım dışı. Konağın clr 'yi açıkça başlatmadan önce işlem içinde hangi CLR sürümünün kullanılacağını belirlemesine izin verir.  
  
## <a name="hosting-functions"></a>Barındırma işlevleri  
 [CallFunctionShim İşlevi](callfunctionshim-function.md)  
 Kullanım dışı. Belirtilen kitaplıkta belirtilen ad ve parametrelere sahip işleve bir çağrı yapar.  
  
 [CoEEShutDownCOM İşlevi](coeeshutdowncom-function.md)  
 Kullanım dışı. İşlemden bir COM derlemesini kaldırır.  
  
 [CorExitProcess İşlevi](corexitprocess-function.md)  
 Kullanım dışı. Geçerli yönetilmeyen işlemi kapatır.  
  
 [CorLaunchApplication İşlevi](corlaunchapplication-function.md)  
 Kullanım dışı. Belirtilen bildirimleri ve diğer uygulama verilerini kullanarak belirtilen ağ yolundaki uygulamayı başlatır.  
  
 [CorMarkThreadInThreadPool İşlevi](cormarkthreadinthreadpool-function.md)  
 Kullanım dışı. Yönetilen kodun yürütülmesi için şu anda yürütülmekte olan iş parçacığı havuzu iş parçacığını işaretler. .NET Framework sürüm 2,0 ' den başlayarak, bu işlevin etkisi yoktur. Gerekli değildir ve kodınızdan kaldırılabilir.  
  
 [CoUninitializeCor İşlevi](couninitializecor-function.md)  
 Kullanımdan kalktı. CLR bir işlemden kaldırılamıyor.  
  
 [CoUninitializeEE İşlevi](couninitializeee-function.md)  
 Kullanımdan kalktı.  
  
 [CreateDebuggingInterfaceFromVersion İşlevi](createdebugginginterfacefromversion-function.md)  
 Kullanım dışı. Belirtilen sürüm bilgilerini temel alan bir [ICorDebug](../debugging/icordebug-interface.md) nesnesi oluşturur.  
  
 [CreateICeeFileGen İşlevi](createiceefilegen-function.md)  
 Kullanım dışı. Bir [ICeeFileGen](iceefilegen-class.md) nesnesi oluşturur.  
  
 [DestroyICeeFileGen İşlevi](destroyiceefilegen-function.md)  
 Kullanım dışı. Bir [ICeeFileGen](iceefilegen-class.md) nesnesini yok eder.  
  
 [FExecuteInAppDomainCallback İşlev İşaretçisi](fexecuteinappdomaincallback-function-pointer.md)  
 Kullanım dışı. CLR 'nin yönetilen kodu yürütmek için çağırdığı bir işleve işaret eder.  
  
 [FLockClrVersionCallback İşlev İşaretçisi](flockclrversioncallback-function-pointer.md)  
 Kullanım dışı. CLR 'nin, başlatmanın başlatıldığını ya da tamamlandığını bildirmek için çağırdığı bir işleve işaret eder.  
  
 [GetCLRIdentityManager İşlevi](getclridentitymanager-function.md)  
 Kullanım dışı. CLR 'nin kimlikleri yönetmesine izin veren bir arabirime yönelik bir işaretçi alır.  
  
 [LoadLibraryShim İşlevi](loadlibraryshim-function.md)  
 Kullanım dışı. .NET Framework DLL 'nin belirtilen bir sürümünü yükler.  
  
 [LoadStringRC İşlevi](loadstringrc-function.md)  
 Kullanım dışı. Geçerli iş parçacığının varsayılan kültürünü kullanarak bir HRESULT değerini bir hata iletisine çevirir.  
  
 [LoadStringRCEx İşlevi](loadstringrcex-function.md)  
 Kullanım dışı. Belirtilen kültür için bir HRESULT değerini uygun bir hata iletisine çevirir.  
  
 [LPOVERLAPPED_COMPLETION_ROUTINE İşlev İşaretçisi](lpoverlapped-completion-routine-function-pointer.md)  
 Kullanım dışı. Bir cihaza çakışan (yani zaman uyumsuz) g/ç tamamlandığında konağa bildiren bir işleve işaret eder.  
  
 [LPTHREAD_START_ROUTINE İşlev İşaretçisi](lpthread-start-routine-function-pointer.md)  
 Kullanım dışı. Bir iş parçacığının yürütülmeye başlatıldığını konağa bildiren bir işleve işaret eder.  
  
 [RunDll32ShimW İşlevi](rundll32shimw-function.md)  
 Kullanım dışı. Belirtilen komutu yürütür.  
  
 [WAITORTIMERCALLBACK İşlev İşaretçisi](waitortimercallback-function-pointer.md)  
 Kullanım dışı. Ana bilgisayarı bir bekleme tutamacının sinyal ettiğini veya zaman aşımına uğradığını bildiren bir işleve işaret eder.  
  
## <a name="infrastructure-functions"></a>Altyapı işlevleri  
 Bu bölümdeki işlevler yalnızca .NET Framework tarafından kullanılır.  
  
 [_CorDllMain İşlevi](cordllmain-function.md)  
 CLR 'yi başlatır, DLL derlemesinin CLR üst bilgisinde yönetilen giriş noktasını bulur ve yürütmeyi başlatır.  
  
 [_CorExeMain İşlevi](corexemain-function.md)  
 CLR 'yi başlatır, çalıştırılabilir derlemenin CLR üst bilgisinde yönetilen giriş noktasını bulur ve yürütmeyi başlatır.  
  
 [_CorExeMain2 İşlevi](corexemain2-function.md)  
 Giriş noktasını belirtilen bellek eşlemeli kodda yürütür. Bu işlev, işletim sistemi yükleyicisi tarafından çağırılır.  
  
 [_CorImageUnloading İşlevi](corimageunloading-function.md)  
 Yönetilen modül görüntüleri kaldırıldığında yükleyiciyi bilgilendirir.  
  
 [_CorValidateImage İşlevi](corvalidateimage-function.md)  
 Yönetilen modül görüntülerini doğrular ve yüklendikten sonra işletim sistemi yükleyicisini bilgilendirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework 4 Barındırma Genel Statik İşlevleri](net-framework-4-hosting-global-static-functions.md)
