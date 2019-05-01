---
title: CLR Barındırma Arabirimleri
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03839a2c6e52f9d2dcdd2e0941ff4fdbeb8a3a17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789668"
---
# <a name="clr-hosting-interfaces"></a>CLR Barındırma Arabirimleri
Bu bölümde, yönetilmeyen arabirimler açıklanmaktadır. konaklar, ortak dil çalışma zamanı (CLR) uygulamalarıyla tümleştirmeleri için kullanabilirsiniz. Bilgiler .NET Framework sürüm 2.0 ve sonraki sürümler ile ilgilidir. Bu arabirimler, çalışma zamanı 1.0 ve 1.1 sürümlerinde mümkün olandan çok daha fazla yönlerini denetlemek konak etkinleştirmek ve kadar CLR ve ana bilgisayarın yürütme modeli arasında sıkı bir tümleştirme sağlar.  
  
 .NET Framework 1.0 ve 1.1 sürümlerinde, barındırma modeli CLR'yi bir işleme, belirli ayarları yapılandırmak ve olay bildirimlerini almak üzere yüklemek yönetilmeyen bir konak etkin. Ancak, genel olarak, konak ve CLR bağımsız olarak bu işlemde çalışan. .NET Framework sürüm 2.0 ve sonraki sürümlerinde soyutlama yeni katmanları Win32 bütünleştirilmiş kodundaki türler tarafından şu anda sağlanan kaynak sağlayın ve konak yapılandırabileceğiniz özellikler kümesini genişletin konak sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [IActionOnCLREvent Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Kayıtlı bir olay için bir geri çağırma işlemini gerçekleştiren bir yöntem sağlar.  
  
 [IApartmentCallback Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Bir grup içinde geri çağırmaları sağlama yöntemleri sağlar.  
  
 [IAppDomainBinding Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Çalışma zamanı yapılandırma ayarlaması için yöntemler sağlar.  
  
 [ICatalogServices Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Hizmetleri kataloglama için yöntemler sağlar. (Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)  
  
 [ICLRAssemblyIdentityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 CLR derlemeleri hakkında ile konak arasındaki iletişimi desteklemek için yöntemler sağlar.  
  
 [ICLRAssemblyReferenceList Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 CLR tarafından ve konak tarafından yüklenen derlemelerin bir listesini yönetir.  
  
 [ICLRControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Erişim ve çeşitli yönlerini, CLR yapılandırmak konak için yöntemler sağlar.  
  
 [ICLRDebugManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Bir görev kümesi bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek bir konak olanak tanıyan yöntemler sağlar.  
  
 [ICLRErrorReportingManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Hata bildirimi için özel bir yığın dökümlerini yapılandırmak konak olanak tanıyan yöntemler sağlar.  
  
 [ICLRGCManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 CLR'nin çöp toplama sistemi ile etkileşim kurmak bir konak olanak tanıyan yöntemler sağlar.  
  
 [ICLRHostBindingPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Değerlendirmek ve ilke bilgilerini derlemeler için değişiklikleri iletişim kurmak ana bilgisayar için yöntemler sağlar.  
  
 [ICLRHostProtectionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Yönetilen sınıflar, yöntemler, özellikler ve alanları kısmen güvenilen kod çalıştırılmasını engellemek konak sağlar.  
  
 [ICLRIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 CLR belirtilen g/ç istekleri durumunu bildirmek için ana sağlayan bir geri çağırma yöntemi uygular.  
  
 [ICLRMemoryNotificationCallback Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Win32 için benzer bir yaklaşım kullanarak rapor bellek baskısı koşullarını sağlayan `CreateMemoryResourceNotification` işlevi.  
  
 [ICLROnEventManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Kaydolun ve CLR olayları için geri çağırmaları kaydını silmek konak olanak tanıyan yöntemler sağlar.  
  
 [ICLRPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 Hataları ve zaman aşımları durumunda uygulanacak ilke eylemleri belirtmek konak olanak tanıyan yöntemler sağlar.  
  
 [ICLRProbingAssemblyEnum Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 CLR, iç oluşturmak veya kimliğe anlamanıza gerek kalmadan derlemenin kimlik bilgilerini kullanarak bir derleme araştırma kimliklerini almak konağı etkinleştirme yöntemleri sağlar.  
  
 [ICLRReferenceAssemblyEnum Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Bir dosya veya akışı oluşturmak veya kimliklerle anlamanıza gerek kalmadan iç CLR için olan derleme kimlik verilerini kullanarak tarafından başvurulan derlemeler kümesini işlemek için ana olanak tanıyan yöntemler sağlar.  
  
 [ICLRRuntimeHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Benzer özellikleri sağlayan [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), ana bilgisayar denetimi arabirimi ayarlamak için ek bir yöntem ile.  
  
 [ICLRSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 İstenilen görevler hakkında bilgi almak ve kilitlenmeleri eşitleme uygulanması algılamak için konak için yöntemler sağlar.  
  
 [ICLRTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 CLR isteklerde veya CLR ilişkili görevle ilgili bildirim sağlamak için konak olanak tanıyan yöntemler sağlar.  
  
 [ICLRTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 CLR yeni bir görev oluşturma, şu anda yürütülmekte olan görevi Al ve coğrafi dil ve kültür görev için açıkça istemek üzere konağın olanak tanıyan yöntemler sağlar.  
  
 [ICLRValidator Arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Taşınabilir yürütülebilir (PE) görüntüleri doğrulanıyor ve doğrulama hatalarını raporlama için yöntemler sağlar.  
  
 [ICorConfiguration Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 CLR yapılandırmak için yöntemler sağlar.  
  
 [ICorThreadpool Arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 İş parçacığı havuzu erişmek için yöntemler sağlar.  
  
 [IDebuggerInfo Arabirimi](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Hata Ayıklama Hizmetleri durumuyla ilgili bilgileri almak için yöntemler sağlar.  
  
 [IDebuggerThreadControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Engelleme hakkında konak bildiren ve hata ayıklama Hizmetleri tarafından iş parçacıklarının engellemesinin kaldırılması için yöntemler sağlar.  
  
 [IGCHost Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Çöp toplama işleminin bazı yönlerini denetleme ve çöp toplama sistemi hakkında bilgi almak için yöntemler sağlar.  
  
 [IGCHost2 Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Sağlar [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) yönteminin çöp toplama kesim boyutunu ve en büyük boyutu çöp toplama sistemin oluşturma sıfır değerleri büyük ayarlamak bir konak tanıyan `DWORD`.  
  
 [IGCHostControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Çöp toplayıcı sanal bellek sınırlarını değiştirmek için ana istemek sağlayan bir yöntem sağlar.  
  
 [IGCThreadControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Çöp toplama işlemi için normalde engellenecek iş parçacıklarını zamanlama katılım için yöntemler sağlar.  
  
 [IHostAssemblyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 Konak veya CLR tarafından yüklenmesi gereken derlemeler kümesini belirtmek bir konak olanak tanıyan yöntemler sağlar.  
  
 [IHostAssemblyStore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Derlemeler ve CLR bağımsız olarak modülleri yüklemek bir konak olanak tanıyan yöntemler sağlar.  
  
 [IHostAutoEvent Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Otomatik sıfırlama olaya ana bilgisayar tarafından uygulanan bir gösterimini sağlar.  
  
 [IHostControl Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Derlemeleri yüklenmesini yapılandırma ve ana bilgisayar destekler hangi barındırma arabirimleri belirlemek için yöntemler sağlar.  
  
 [IHostCrst Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 İş parçacığı için kritik bir bölüm konağın gösterimi işlevi görür.  
  
 [IHostGCManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 CLR tarafından uygulanan çöp toplama mekanizması olayların ana bilgisayara bildirmek için yöntemler sağlar.  
  
 [IHostIoCompletionManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Ana bilgisayar tarafından sağlanan g/ç tamamlama bağlantı noktaları ile etkileşim kurmak CLR olanak tanıyan yöntemler sağlar.  
  
 [IHostMalloc Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 CLR'nin yığın konağı üzerinden hassas ayırmaları istek için yöntemler sağlar.  
  
 [IHostManualEvent Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Ana bilgisayarın uygulamasını elle sıfırlama olayı bir gösterimini sağlar.  
  
 [IHostMemoryManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Standart Win32 sanal bellek işlevleri kullanmak yerine ana bilgisayar üzerinden sanal bellek isteğinde bulunmak CLR için yöntemler sağlar.  
  
 [IHostPolicyManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Ana bilgisayarının durumunda, CLR gerçekleştirdiği işlemleri durdurur, zaman aşımı veya hataları bildirmek için yöntemler sağlar.  
  
 [IHostSecurityContext Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Ana bilgisayar tarafından uygulanan güvenlik bağlamını korumak CLR sağlar.  
  
 [IHostSecurityManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Erişimi etkinleştir ve şu anda çalışan bir iş parçacığı üzerinde güvenlik bağlamını denetlemek için yöntemler sağlar.  
  
 [IHostSemaphore Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Ana bilgisayar tarafından uygulanan semafor bir gösterimini sağlar.  
  
 [IHostSyncManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Eşitleme temellerine Win32 eşitleme işlevleri kullanmak yerine konak çağırarak oluşturmak CLR için yöntemler sağlar.  
  
 [IHostTask Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Görevleri yönetmek üzere konaklarla iletişim kurmak CLR olanak tanıyan yöntemler sağlar.  
  
 [IHostTaskManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Görevleri için standart işletim sistemi iş parçacığı veya fiber işlevlerini yerine ana bilgisayar üzerinden çalışmak CLR olanak tanıyan yöntemler sağlar.  
  
 [IHostThreadPoolManager Arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 CLR iş parçacığı havuzu yapılandırmak ve iş parçacığı havuzu iş öğelerine sıraya almak için yöntemler sağlar.  
  
 [IManagedObject Arabirimi](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Yönetilen bir nesnenin denetlemek için yöntemler sağlar.  
  
 "IObjectHandle"  
 Yöneltme açma değere göre sıralama nesneler için bir yöntem sağlar.  
  
 [ITypeName Arabirimi](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Tür adı bilgileri almak için yöntemler sağlar. (Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)  
  
 [ITypeNameBuilder Arabirimi](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Bir tür adı oluşturmak için yöntemleri sağlar. (Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)  
  
 [ITypeNameFactory Arabirimi](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Bir tür adı ayrıştırma için yöntemler sağlar. (Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)  
  
 "IValidator"  
 Taşınabilir yürütülebilir (PE) görüntüleri doğrulanıyor ve doğrulama hatalarını raporlama için yöntemler sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kullanım Dışı CLR Barındırma Arabirimleri ve Coclass’ları](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 .NET Framework sürüm 1.0 ve 1.1 barındırma arabirimlerini açıklayan konulara içerir.  
  
 [.NET Framework 4 ve 4.5'e Eklenen CLR Barındırma Arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Sağlanan barındırma arabirimleri açıklayan konulara içeren [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].
