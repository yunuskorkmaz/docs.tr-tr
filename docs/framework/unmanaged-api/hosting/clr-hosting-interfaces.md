---
title: "CLR Barındırma Arabirimleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3efdf649d0039f2eb6b39d5cb17c839b90e97508
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="clr-hosting-interfaces"></a>CLR Barındırma Arabirimleri
Bu bölümde yönetilmeyen arabirimler açıklanmaktadır konakları ortak dil çalışma zamanı (CLR) uygulamalarına tümleştirmeleri için kullanabilirsiniz. Bilgi, .NET Framework sürüm 2.0 ve sonraki sürümler için geçerlidir. Bu arabirimleri çalışma zamanı 1.0 ve 1.1 sürümleri içinde mümkün olandan çok daha fazla yönlerini denetlemek konak etkinleştirin ve CLR ve ana bilgisayarın yürütme modeli arasında çok sıkı tümleştirme sağlar.  
  
 .NET Framework sürüm 1.0 ve 1.1'da, barındırma model CLR belirli ayarları yapılandırmak ve olay bildirimlerini almak için bir işlem yüklemek yönetilmeyen bir ana bilgisayar etkin. Ancak, genel olarak, konak ve CLR bağımsız olarak bu işleminde çalıştırılır. .NET Framework sürüm 2.0 ve sonraki sürümler soyutlama yeni katmanları Win32 derlemesindeki türler tarafından şu anda sağlanan kaynakların çoğunu sağlar ve ana bilgisayar yapılandırabilirsiniz işlevler kümesini genişletmek konak olanak tanır.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Iactiononclrevent arabirimi](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Kayıtlı bir olay için bir geri çağırma gerçekleştiren bir yöntem sağlar.  
  
 [Iapartmentcallback arabirimi](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Geri aramalar bir grup içinde sağlama yöntemleri sağlar.  
  
 [Iappdomainbinding arabirimi](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Çalışma zamanı yapılandırma ayarlaması için yöntemleri sağlar.  
  
 [Icatalogservices arabirimi](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Hizmetleri Katalog için yöntemleri sağlar. (Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)  
  
 [Iclrassemblyıdentitymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 CLR derlemeleri hakkında ile konak arasındaki iletişimi destekleyen yöntemler sağlar.  
  
 [Iclrassemblyreferencelist arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 CLR tarafından ve ana bilgisayar tarafından yüklenen bir derleme listesi yönetir.  
  
 [Iclrcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Erişim ve çeşitli yönlerini, CLR yapılandırmak ana bilgisayar için yöntemleri sağlar.  
  
 [Iclrdebugmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Bir dizi görevi bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek bir konak sağlayan yöntemler sağlar.  
  
 [Iclrerrorreportingmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Hata bildirimi için özel yığın dökümleri yapılandırmak konak sağlayan yöntemler sağlar.  
  
 [Iclrgcmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 CLR'ın çöp toplama sistemi ile etkileşim kurmak bir konak sağlayan yöntemler sağlar.  
  
 [Iclrhostbindingpolicymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Değerlendirmek ve derlemeler için ilke bilgilerini değişiklikleri iletişim kurmak ana bilgisayar için yöntemleri sağlar.  
  
 [Iclrhostprotectionmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Yönetilen sınıflar, yöntemler, özellikler ve kısmen güvenilen kodu çalıştırma alanların engellemek ana bilgisayarı sağlar.  
  
 [Iclrıocompletionmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 Belirtilen g/ç isteklerin durumunu CLR bilgilendirmek için ana sağlayan bir geri çağırma yöntemi uygular.  
  
 [Iclrmemorynotificationcallback arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Win32 için benzer bir yaklaşım kullanarak rapor bellek baskısı koşullarını konağa etkinleştirir `CreateMemoryResourceNotification` işlevi.  
  
 [Iclroneventmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Kaydolun ve CLR olayları için geri çağırmaları kaydı için ana sağlayan yöntemler sağlar.  
  
 [Iclrpolicymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 İlke hataları ve zaman aşımları durumunda gerçekleştirilecek eylemleri belirtmek için ana sağlayan yöntemler sağlar.  
  
 [Iclrprobingassemblyenum arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 Oluşturma veya kimliğe anlamak zorunda kalmadan CLR için iç derlemenin kimlik bilgilerini kullanarak bir derleme yoklama kimliklerini almak konak sağlayan yöntemler sağlar.  
  
 [Iclrreferenceassemblyenum arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Bir dosya veya CLR için iç oluşturun veya bu kimlikleri anlamak zorunda kalmadan derleme kimlik verilerini kullanarak akış tarafından başvurulan derlemeler kümesini işlemek için ana sağlayan yöntemler sağlar.  
  
 [Iclrruntimehost arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Benzer özellikleri sağlayan [Icorruntimehost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), ana bilgisayar denetim arabirimi ayarlamak için ek bir yöntem ile.  
  
 [Iclrsyncmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 Kilitlenmeler, eşitleme uygulamasında algılamak için ve istenen görevler hakkında bilgi almak için ana bilgisayar için yöntemleri sağlar.  
  
 [Iclrtask arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 Ana bilgisayar CLR isteklerde veya CLR ilişkili görevle ilgili bildirim sağlamak için sağlayan yöntemler sağlar.  
  
 [Iclrtaskmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 CLR yeni bir görev oluşturma, şu anda yürütülen görev almak ve coğrafi dil ve kültür görev için ayarlanmış istemenin konak sağlayan yöntemler sağlar.  
  
 [Iclrvalidator arabirimi](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Taşınabilir yürütülebilir (PE) görüntüler doğrulama ve doğrulama hatalarını raporlama için yöntemleri sağlar.  
  
 [Icorconfiguration arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 CLR yapılandırmak için yöntemleri sağlar.  
  
 [Icorthreadpool arabirimi](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 İş parçacığı havuzu erişmek için yöntemler sağlar.  
  
 [Idebuggerınfo arabirimi](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Hata ayıklama hizmetlerinin durumu hakkında bilgi almak için yöntemleri sağlar.  
  
 [Idebuggerthreadcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Engelleme hakkında konak bildirme ve hata ayıklama Hizmetleri tarafından iş parçacıklarının kaldırma için yöntemleri sağlar.  
  
 [Igchost arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Çöp toplama sistemi hakkında bilgi edinme ve atık toplama bazı yönlerini denetleme yöntemleri sağlar.  
  
 [Igchost2 arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Sağlar [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) atık toplama kesim boyutunu ve en büyük boyutu sıfır atık toplama sistemin nesil değerlere büyük ayarlamak bir konak etkinleştirir yöntemi `DWORD`.  
  
 [Igchostcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Sanal bellek sınırları değiştirmek için ana istemek atık toplayıcı sağlayan bir yöntem sağlar.  
  
 [Igcthreadcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Çöp toplama için engellenmesi iş parçacıklarını zamanlama içinde katılan için yöntemleri sağlar.  
  
 [Ihostassemblymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 CLR veya ana bilgisayar tarafından yüklenmesi gereken derlemeler kümesini belirtmek bir konak sağlayan yöntemler sağlar.  
  
 [Ihostassemblystore arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Derlemeler ve modüller CLR bağımsız olarak yüklemek bir konak sağlayan yöntemler sağlar.  
  
 [Ihostautoevent arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Ana bilgisayar tarafından uygulanan bir otomatik sıfırlama olay gösterimini sağlar.  
  
 [Ihostcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Derlemeleri yükleme yapılandırma ve ana bilgisayar destekler hangi barındırma arabirimleri belirlemek için yöntemleri sağlar.  
  
 [Ihostcrst arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 İş parçacığı oluşturma için önemli bir bölümü ana bilgisayarın gösterimi olarak görev yapar.  
  
 [Ihostgcmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 CLR tarafından uygulanan atık toplama mekanizması olayları ana bildir yöntemleri sağlar.  
  
 [Ihostıocompletionmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Ana bilgisayar tarafından sağlanan g/ç tamamlama bağlantı noktaları ile etkileşim kurmak CLR sağlayan yöntemler sağlar.  
  
 [Ihostmalloc arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 Ana bilgisayar üzerinden öbek hassas ayırmaları istemesini CLR için yöntemleri sağlar.  
  
 [Ihostmanualevent arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Ana bilgisayarın uygulamasını elle sıfırlama olayı bir gösterimini sağlar.  
  
 [Ihostmemorymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Standart Win32 sanal bellek işlevleri kullanmak yerine ana bilgisayar üzerinden sanal bellek istekler yapmasını CLR için yöntemleri sağlar.  
  
 [Ihostpolicymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Durumunda, CLR gerçekleştirdiği işlemleri ana durdurur, zaman aşımı veya hatalar bildiren yöntemleri sağlar.  
  
 [Ihostsecuritycontext arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Ana bilgisayar tarafından uygulanan güvenlik bağlamı bilgilerini korumak CLR sağlar.  
  
 [Ihostsecuritymanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Erişimi etkinleştir ve şu anda yürütülen iş parçacığı güvenlik bağlamı, üzerinde denetleyen yöntemleri sağlar.  
  
 [Ihostsemaphore arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Ana bilgisayar tarafından uygulanan semafor gösterimini sağlar.  
  
 [Ihostsyncmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Eşitleme temelleri Win32 eşitleme işlevlerini kullanmak yerine ana çağırarak oluşturmak CLR için yöntemleri sağlar.  
  
 [Ihosttask arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Görevleri yönetmek için konak ile iletişim kurmak CLR sağlayan yöntemler sağlar.  
  
 [Ihosttaskmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Görevler için standart işletim sistemi iş parçacığı oluşturma veya fiber işlevlerini yerine ana bilgisayar üzerinden çalışmak CLR sağlayan yöntemler sağlar.  
  
 [Ihostthreadpoolmanager arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 İş parçacığı havuzu yapılandırmak için ve iş parçacığı havuzu iş öğelerine kuyruğuna CLR için yöntemleri sağlar.  
  
 [IManagedObject arabirimi](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Yönetilen bir nesnenin denetleme yöntemleri sağlar.  
  
 "IObjectHandle"  
 Yöneltme açma sıralama değerli nesneleri için bir yöntem sağlar.  
  
 [Itypename arabirimi](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Tür adı bilgilerini alma yöntemleri sağlar. (Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)  
  
 [Itypenamebuilder arabirimi](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Tür adı oluşturmak için yöntemleri sağlar. (Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)  
  
 [Itypenamefactory arabirimi](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Tür adı deconstructing için yöntemleri sağlar. (Bu arabirim .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.)  
  
 "IValidator"  
 Taşınabilir yürütülebilir (PE) görüntüler doğrulama ve doğrulama hatalarını raporlama için yöntemleri sağlar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Kullanım dışı CLR barındırma arabirimleri ve coclass'ları](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 .NET Framework sürüm 1.0 ve 1.1 sağlanan barındırma arabirimleri açıklayan konuları içerir.  
  
 [.NET Framework 4 ve 4.5 eklenen CLR barındırma arabirimleri](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Sağlanan barındırma arabirimleri açıklayan konulara içeren [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].
