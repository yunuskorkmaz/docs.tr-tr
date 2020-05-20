---
title: CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: e6913e18a4ff6e616f357a4ef43fb8b892264943
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616846"
---
# <a name="clr-hosting-interfaces"></a>CLR Barındırma Arabirimleri
Bu bölümde, yönetilmeyen ana bilgisayarların ortak dil çalışma zamanını (CLR) uygulamalarıyla tümleştirmeleri için kullanabileceği arabirimler açıklanmaktadır. Bilgiler .NET Framework sürüm 2,0 ve sonraki sürümlere aittir. Bu arabirimler konağın, çalışma zamanının daha birçok yönünü 1,0 ve 1,1 sürümlerinde mümkün olandan çok daha fazla denetlemesine olanak tanır ve CLR ile konağın yürütme modeli arasında çok daha sıkı bir tümleştirme sağlar.  
  
 .NET Framework sürüm 1,0 ve 1,1 ' de barındırma modeli, CLR 'yi bir işleme yüklemek, belirli ayarları yapılandırmak ve olay bildirimleri almak için yönetilmeyen bir konağı etkinleştirdi. Ancak, genel olarak, ana bilgisayar ve CLR bu işlemde bağımsız olarak çalışır. .NET Framework sürüm 2,0 ve sonraki sürümlerinde, yeni soyutlama katmanları konağın Win32 derlemesinde bulunan türler tarafından şu anda sağlanmış birçok kaynağı sağlamasına ve konağın yapılandırabilmesinin bir dizi özelliği genişletmesine izin verir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [IActionOnCLREvent Arabirimi](iactiononclrevent-interface.md)  
 Kayıtlı bir olay için geri çağırma gerçekleştiren bir yöntem sağlar.  
  
 [IApartmentCallback Arabirimi](iapartmentcallback-interface.md)  
 Bir grup içinde geri çağırma yapmak için yöntemler sağlar.  
  
 [IAppDomainBinding Arabirimi](iappdomainbinding-interface.md)  
 Çalışma zamanı yapılandırmasını ayarlamak için yöntemler sağlar.  
  
 [ICatalogServices Arabirimi](icatalogservices-interface.md)  
 Hizmet kataloğu için yöntemler sağlar. (Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)  
  
 [ICLRAssemblyIdentityManager Arabirimi](iclrassemblyidentitymanager-interface.md)  
 Konak ve derlemeler hakkında CLR arasındaki iletişimi destekleyen yöntemler sağlar.  
  
 [ICLRAssemblyReferenceList Arabirimi](iclrassemblyreferencelist-interface.md)  
 Konak tarafından değil, CLR tarafından yüklenen derlemelerin listesini yönetir.  
  
 [ICLRControl Arabirimi](iclrcontrol-interface.md)  
 Konağın, CLR 'nin çeşitli yönlerini uygulamasına erişmesi ve bunları yapılandırması için yöntemler sağlar.  
  
 [ICLRDebugManager Arabirimi](iclrdebugmanager-interface.md)  
 Bir ana bilgisayarın bir dizi görevi bir tanımlayıcıyla ve kolay bir adla ilişkilendirilmesini sağlayan yöntemler sağlar.  
  
 [ICLRErrorReportingManager Arabirimi](iclrerrorreportingmanager-interface.md)  
 Ana bilgisayarın hata raporlama için özel yığın dökümleri yapılandırmasını sağlayan yöntemler sağlar.  
  
 [ICLRGCManager Arabirimi](iclrgcmanager-interface.md)  
 Bir konağın, CLR 'nin çöp toplama sistemiyle etkileşimini sağlayan yöntemler sağlar.  
  
 [ICLRHostBindingPolicyManager Arabirimi](iclrhostbindingpolicymanager-interface.md)  
 Ana bilgisayarın derlemelerin ilke bilgilerinde yapılan değişiklikleri değerlendirmesi ve iletişim kurması için yöntemler sağlar.  
  
 [ICLRHostProtectionManager Arabirimi](iclrhostprotectionmanager-interface.md)  
 Ana bilgisayarın, kısmen güvenilen kodda çalışan belirli yönetilen sınıfları, yöntemleri, özellikleri ve alanları engellemesini sağlar.  
  
 [ICLRIoCompletionManager Arabirimi](iclriocompletionmanager-interface.md)  
 Konağın belirtilen g/ç isteklerinin durum CLR 'ye bildirmesini sağlayan bir geri çağırma yöntemi uygular.  
  
 [ICLRMemoryNotificationCallback Arabirimi](iclrmemorynotificationcallback-interface.md)  
 Konağın, Win32 fonksiyonuyla benzer bir yaklaşım kullanarak bellek baskısı koşullarını rapor etmesini sağlar `CreateMemoryResourceNotification` .  
  
 [ICLROnEventManager Arabirimi](iclroneventmanager-interface.md)  
 Konağın CLR olayları için geri çağırmaları kaydetmesini ve kaydını iptal etme olanağı sağlayan yöntemler sağlar.  
  
 [ICLRPolicyManager Arabirimi](iclrpolicymanager-interface.md)  
 , Ana bilgisayarın hata ve zaman aşımları durumunda gerçekleştirilecek ilke eylemlerini belirtmesini sağlayan yöntemler sağlar.  
  
 [ICLRProbingAssemblyEnum Arabirimi](iclrprobingassemblyenum-interface.md)  
 , Bu kimliği oluşturmaya veya anlamaya gerek kalmadan derlemenin CLR 'nin kimlik bilgilerini kullanarak bir derlemenin yoklama kimliklerini almasını sağlayan yöntemler sağlar.  
  
 [ICLRReferenceAssemblyEnum Arabirimi](iclrreferenceassemblyenum-interface.md)  
 Bu kimlikleri oluşturmaya veya anlamaya gerek kalmadan, konağın, CLR 'ye yönelik derleme kimliği verilerini kullanarak bir dosya veya akış tarafından başvurulan derlemelerin kümesini işlemesini sağlayan yöntemler sağlar.  
  
 [ICLRRuntimeHost Arabirimi](iclrruntimehost-interface.md)  
 Konak denetim arabirimini ayarlamaya yönelik ek bir yöntem ile [ICorRuntimeHost](icorruntimehost-interface.md)'a benzer yetenekler sağlar.  
  
 [ICLRSyncManager Arabirimi](iclrsyncmanager-interface.md)  
 , İstenen görevlerle ilgili bilgi almak ve eşitleme uygulamasında kilitlenmeleri algılamak için ana bilgisayar için yöntemler sağlar.  
  
 [ICLRTask Arabirimi](iclrtask-interface.md)  
 Konağın CLR istekleri yapmasını veya ilişkili görevle ilgili olarak CLR 'ye bildirim sağlamasını etkinleştiren yöntemler sağlar.  
  
 [ICLRTaskManager Arabirimi](iclrtaskmanager-interface.md)  
 , CLR 'nin doğrudan CLR 'nin yeni bir görev oluşturmasını, şu anda yürütülmekte olan görevi almasını ve görevin coğrafi dilini ve kültürünü ayarlamanızı sağlayan yöntemler sağlar.  
  
 [ICLRValidator Arabirimi](iclrvalidator-interface.md)  
 Taşınabilir çalıştırılabilir (PE) görüntüleri ve raporlama doğrulama hatalarını doğrulamak için yöntemler sağlar.  
  
 [ICorConfiguration Arabirimi](icorconfiguration-interface.md)  
 CLR yapılandırması için yöntemler sağlar.  
  
 [ICorThreadpool Arabirimi](icorthreadpool-interface.md)  
 İş parçacığı havuzuna erişim için yöntemler sağlar.  
  
 [IDebuggerInfo Arabirimi](idebuggerinfo-interface.md)  
 Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemler sağlar.  
  
 [IDebuggerThreadControl Arabirimi](idebuggerthreadcontrol-interface.md)  
 , Hata ayıklama Hizmetleri tarafından iş parçacıklarının engellenmesi ve engellemesini kaldırma hakkında bilgi için yöntemler sağlar.  
  
 [IGCHost Arabirimi](igchost-interface.md)  
 Çöp toplama sistemi hakkında bilgi edinmek ve çöp toplamanın bazı yönlerini denetlemek için yöntemler sağlar.  
  
 [IGCHost2 Arabirimi](igchost2-interface.md)  
 , Bir konağın çöp toplama segmentinin boyutunu ve çöp toplama sisteminin en büyük boyutunu ' dan büyük değerlere ayarlamaya olanak sağlayan [SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) yöntemini sağlar `DWORD` .  
  
 [IGCHostControl Arabirimi](igchostcontrol-interface.md)  
 Çöp toplayıcısının sanal bellek sınırlarını değiştirmesini istemek için bir yöntem sağlar.  
  
 [IGCThreadControl Arabirimi](igcthreadcontrol-interface.md)  
 Çöp toplama için engellenebilecek iş parçacıklarının zamanlamaya katılmak için yöntemler sağlar.  
  
 [IHostAssemblyManager Arabirimi](ihostassemblymanager-interface.md)  
 Bir konağın CLR veya konak tarafından yüklenmesi gereken derleme kümelerini belirtmesini sağlayan yöntemler sağlar.  
  
 [IHostAssemblyStore Arabirimi](ihostassemblystore-interface.md)  
 Bir konağın CLR 'den bağımsız olarak derlemeleri ve modülleri yüklemesine imkan tanıyan yöntemler sağlar.  
  
 [IHostAutoEvent Arabirimi](ihostautoevent-interface.md)  
 Ana bilgisayar tarafından uygulanan otomatik sıfırlama olayının gösterimini sağlar.  
  
 [IHostControl Arabirimi](ihostcontrol-interface.md)  
 Derlemelerin yüklenmesini yapılandırmak için ve konağın desteklediği barındırma arabirimlerini belirlemek için yöntemler sağlar.  
  
 [IHostCrst Arabirimi](ihostcrst-interface.md)  
 İş parçacığı için kritik bir bölümün ana bilgisayarın temsili olarak işlev görür.  
  
 [IHostGCManager Arabirimi](ihostgcmanager-interface.md)  
 CLR tarafından uygulanan çöp toplama mekanizmasında olay konağını bildiren yöntemler sağlar.  
  
 [IHostIoCompletionManager Arabirimi](ihostiocompletionmanager-interface.md)  
 CLR 'nin konak tarafından sağlanan g/ç tamamlama bağlantı noktalarıyla etkileşime geçmesini sağlayan yöntemler sağlar.  
  
 [IHostMalloc Arabirimi](ihostmalloc-interface.md)  
 CLR 'nin, ana bilgisayar aracılığıyla yığından hassas ayırmalar istemesi için yöntemler sağlar.  
  
 [IHostManualEvent Arabirimi](ihostmanualevent-interface.md)  
 Konağın el ile sıfırlama olayının temsili için bir uygulama sağlar.  
  
 [IHostMemoryManager Arabirimi](ihostmemorymanager-interface.md)  
 Standart Win32 sanal bellek işlevlerini kullanmak yerine, CLR 'nin konak üzerinden sanal bellek istekleri yapması için yöntemler sağlar.  
  
 [IHostPolicyManager Arabirimi](ihostpolicymanager-interface.md)  
 İptal, zaman aşımları veya hatalara karşı, CLR tarafından gerçekleştirilen eylemlerin ana bilgisayarına bildirimde bulunan yöntemler sağlar.  
  
 [IHostSecurityContext Arabirimi](ihostsecuritycontext-interface.md)  
 CLR 'nin konak tarafından uygulanan güvenlik bağlamı bilgilerini korumasına olanak sağlar.  
  
 [IHostSecurityManager Arabirimi](ihostsecuritymanager-interface.md)  
 , Şu anda yürütülmekte olan iş parçacığının güvenlik bağlamını ve üzerinde erişimi etkinleştiren yöntemler sağlar.  
  
 [IHostSemaphore Arabirimi](ihostsemaphore-interface.md)  
 Ana bilgisayar tarafından uygulanan semaforun bir gösterimini sağlar.  
  
 [IHostSyncManager Arabirimi](ihostsyncmanager-interface.md)  
 , Win32 eşitleme işlevlerini kullanmak yerine, Konağı çağırarak eşitleme temelleri oluşturmak için CLR için yöntemler sağlar.  
  
 [IHostTask Arabirimi](ihosttask-interface.md)  
 , CLR 'nin görevleri yönetmek üzere konakla iletişim kurmasına imkan tanıyan yöntemler sağlar.  
  
 [IHostTaskManager Arabirimi](ihosttaskmanager-interface.md)  
 CLR 'nin standart işletim sistemi iş parçacığı veya fiber işlevlerini kullanmak yerine ana bilgisayar aracılığıyla görevlerle çalışmasına imkan tanıyan yöntemler sağlar.  
  
 [IHostThreadPoolManager Arabirimi](ihostthreadpoolmanager-interface.md)  
 CLR için iş öğelerini yapılandırmak ve iş öğelerini iş parçacığı havuzuna sıraya almak için yöntemler sağlar.  
  
 [IManagedObject Arabirimi](imanagedobject-interface.md)  
 Yönetilen bir nesneyi denetlemek için yöntemler sağlar.  
  
 IObjectHandle  
 Değer temelli nesneleri yöneltme 'dan sarmalama için bir yöntem sağlar.  
  
 [ITypeName Arabirimi](itypename-interface.md)  
 Tür adı bilgilerini almak için yöntemler sağlar. (Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)  
  
 [ITypeNameBuilder Arabirimi](itypenamebuilder-interface.md)  
 Bir tür adı oluşturmak için yöntemler sağlar. (Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)  
  
 [ITypeNameFactory Arabirimi](itypenamefactory-interface.md)  
 Bir tür adının çıkarılması için yöntemler sağlar. (Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)  
  
 IValidator  
 Taşınabilir çalıştırılabilir (PE) görüntüleri ve raporlama doğrulama hatalarını doğrulamak için yöntemler sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kullanım Dışı CLR Barındırma Arabirimleri ve Yardımcı Sınıfları](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 .NET Framework sürüm 1,0 ve 1,1 ' de sunulan barındırma arabirimlerini tanımlayan konuları içerir.  
  
 [.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 .NET Framework 4 ' te belirtilen barındırma arabirimlerini tanımlayan konuları içerir.
