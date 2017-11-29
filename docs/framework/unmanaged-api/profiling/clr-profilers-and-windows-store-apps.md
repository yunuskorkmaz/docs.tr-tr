---
title: "CLR Profil oluşturucular ve Windows mağazası uygulamaları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db1152e82edde34dc8dbaba09f20b9f769dffbca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="clr-profilers-and-windows-store-apps"></a>CLR Profil oluşturucular ve Windows mağazası uygulamaları
Bu konuda, ne zaman analiz yazma tanılama araçları içinde Windows mağazası uygulaması çalıştıran yönetilen kodu hakkında düşünmek için gerekenler açıklanmaktadır.  Ayrıca, Windows mağazası uygulamaları karşı çalıştırdığınızda çalışmaya devam etmek için mevcut geliştirme araçları değiştirmek için yönergeler sağlar.  Bu bilgileri anlamak için ortak dil çalışma zamanı profil oluşturma API'si ile sahibiyseniz, zaten bu API Windows Masaüstü uygulamaları için ve karşı düzgün çalışır şimdi aracı değiştirme ilgileniyor, bir tanı aracı olarak kullandığınız en iyisidir Windows mağazası uygulamaları karşı doğru çalışması için.  
  
 Bu konu aşağıdaki bölümlerden oluşur:  
  
 [Giriş](#Intro)  
 [Mimari ve terminolojisi](#Arch)  
 [Windows RT cihazları](#RT)  
[Windows çalışma zamanı API'ları kullanma](#Consuming)  
[Profil Oluşturucu DLL yükleniyor](#Loading)  
 [Başlangıç için ortak ilgili önemli noktalar ve yükleri ekleme](#Common)  
 [Başlangıç yükleme](#Startup)  
 [Yük ekleme](#Attach)  
[Windows mağazası uygulaması içinde çalışan](#Running)  
 [Windows mağazası uygulama API'lerine takılıyor](#APIs)  
 [Sınırlı izinlere](#Permissions)  
 [İşlemler arası iletişim](#Interprocess)  
 [Kapatma bildirim yok](#Shutdown)  
[Windows çalışma zamanı meta veri dosyaları](#Metadata)  
 [Yönetilen ve yönetilmeyen WinMDs](#WMDs)  
 [CLR modülleri gibi WinMD dosyaları arayın](#CLRModules)  
 [WinMDs meta verilerini okuma](#Reading)  
 [WinMDs meta verilerini değiştirme](#Modifying)  
 [Derleme başvurularını WinMDs ile çözme](#Resolving)  
[Bellek profil oluşturucuları](#Profilers)  
 [Yönetilen iş parçacığı ForceGC oluşturur](#ForceGC)  
 [ConditionalWeakTableReferences](#WeakTable)  
[Sonuç](#Conclusion)  
[Kaynakları](#Resources)  
  
<a name="Intro"></a>   
## <a name="introduction"></a>Giriş  
 Giriş paragrafı yaptıysanız sonra CLR Profil oluşturma API'si ile biliyorsunuzdur.  İyi yönetilen Masaüstü uygulamaları karşı çalışır bir Tanı Aracı yazmış olduğunuz.  Şimdi, böylece yönetilen bir Windows mağazası uygulaması ile aracının çalıştığı yapmanız gerekenler merak.  Belki de bu çalışma ve basit bir görev olmadığını bulunmuş zaten çalıştınız.  Aslında, bir dizi tüm araçlar geliştiricilerine göze görünmeyebilir dikkat edilecek noktalar vardır.  Örneğin:  
  
-   Windows mağazası uygulamaları ciddi bir şekilde sınırlı izinlere sahip bir bağlamda çalıştırın.  
  
-   Windows meta veri dosyaları için geleneksel yönetilen modüller karşılaştırıldığında benzersiz özelliklerine sahiptir.  
  
-   Windows mağazası uygulamaları etkileşim azaldığında kendilerini askıya alma, bir alýþkanlýk vardır.  
  
-   İşlemler arası iletişim mekanizmaları artık çeşitli nedenlerle çalışmayabilir.  
  
 Bu konu, farkında olması gereken şeyleri ve bunlarla düzgün bir şekilde nasıl listeler.  
  
 CLR Profil oluşturma API için yeni varsa, daha iyi giriş bilgilerini bulmak için bu konunun sonundaki kaynakları aşağıya doğru atlayın.  
  
 Belirli Windows API'larını ve nasıl kullanıldıkları hakkında ayrıntılı bilgi sağlayan, bu konunun kapsamı dışında olan.  Bu konuda bir başlangıç noktası göz önünde bulundurun ve burada başvurulan tüm Windows API'leri hakkında daha fazla bilgi için MSDN bakın.  
  
<a name="Arch"></a>   
## <a name="architecture-and-terminology"></a>Mimari ve terminolojisi  
 Genellikle, bir tanı aracı aşağıdaki çizimde gösterildiği gibi bir mimari sahiptir. "Profil Oluşturucu" terimini kullanır, ancak iyi tipik performans veya kod kapsamı gibi alanlarına bellek profil, nesne çerçeveleri mock, zaman seyahat hata ayıklama, uygulama izleme vb. gibi birçok Araçlar gidin.  Kolaylık olması için bu araçları profil oluşturucular olarak başvurmak bu konuda devam eder.  
  
 Bu konu boyunca aşağıdaki terimler kullanılır:  
  
 Uygulama  
 Profil Oluşturucu çözümleme uygulamasıdır.  Genellikle, bu uygulama geliştiricisi uygulama ile ilgili sorunları tanılamak için şimdi profil oluşturucu kullanıyor.  Geleneksel olarak, bu uygulama bir Windows masaüstü uygulaması olacaktır, ancak bu konuda, Windows mağazası uygulamaları bekliyoruz.  
  
 Profil Oluşturucu DLL  
 Bu çözümlenmekte uygulamanızın işlem alanına yükleyen bileşendir.  Bu bileşen olarak da bilinen profil oluşturucu "Aracısı," uygulayan [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)[Icorprofilercallback arabirimi](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)(2,3, vb.) arabirimleri ve tüketir [ Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)(2,3, vb.) çözümlenen uygulama hakkında ve büyük olasılıkla veri toplamak üzere arabirimleri uygulamanın davranışını yönlerini değiştirin.  
  
 Profil Oluşturucu kullanıcı Arabirimi  
 Bu, Profil Oluşturucu kullanıcı ile etkileşime giren bir masaüstü uygulamasıdır.  Bu kullanıcı için uygulama durumunu görüntülemek ve kullanıcı çözümlenen uygulama davranışını denetlemek için araçlar vererek sorumludur.  Bu bileşen profili oluşturuluyor uygulama işlemi alanından ayrı kendi işlem alanında her zaman çalışır.  Profil Oluşturucu kullanıcı Arabirimi, aynı zamanda "ekleme tetikleyici," çağırır işlemi olan davranamaz [Iclrprofiling::attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) burada profil oluşturucu DLL belirtmiyor bu durumlarda profil oluşturucu DLL'yi çözümlenen Uygulanmanın için yöntemi Başlangıçta yükleyin.  
  
> [!IMPORTANT]
>  Profil Oluşturucu UI bile denetim ve Windows mağazası uygulaması raporda kullanıldığında, bir Windows masaüstü uygulaması kalmalıdır.  Paketini ve Windows Mağazası'nda, Tanılama Aracı sevk etmek erişebilmeyi beklerler yok.  Windows mağazası uygulamaları yapamayacağı ve pek çok şeyi profil oluşturucu UI içinde bulunan işlemler yapmak, Aracı gerekir.  
  
 Bu belge boyunca örnek kod varsayılmaktadır:  
  
-   CLR Profil oluşturma API gereksinimlerine uygun bir yerel DLL'i gerektiğinden, profil oluşturucu DLL C++'da yazılır.  
  
-   Profil Oluşturucu UI C# dilinde yazılmıştır.  Bu gerekli değildir, ancak profil oluşturucu Arabiriminin işlemi için dil gereksinimi olduğundan, kısa ve basit bir dil neden çekme?  
  
<a name="RT"></a>   
### <a name="windows-rt-devices"></a>Windows RT cihazları  
 Windows RT cihazları oldukça kilitlendiğini.  Üçüncü taraf profil oluşturucular yalnızca bu tür cihazlarda yüklenemiyor.  Bu belge, Windows 8 bilgisayarlarında odaklanır.  
  
<a name="Consuming"></a>   
## <a name="consuming-windows-runtime-apis"></a>Windows çalışma zamanı API'ları kullanma  
 Aşağıdaki bölümlerde ele alınan senaryolar sayısı cinsinden, bazı yeni Windows çalışma zamanı API'ları kullanmak profil oluşturucu UI Masaüstü uygulamanız gerekir.  Hangi Windows çalışma zamanı API'leri, Masaüstü uygulamalardan kullanılabileceğini anlamak için belgelere istersiniz ve davranışlarını ne zaman farklı olup olmadığını, Masaüstü uygulamalarına ve Windows mağazası uygulamaları çağrılır.  
  
 Profil Oluşturucu UI yönetilen kodda yazılır, bu kolay Windows çalışma zamanı API'lerini kullanan sağlamak için yapmanız gereken birkaç adım olacaktır.  Bkz: [yönetilen Masaüstü uygulamaları ve Windows çalışma zamanı](http://go.microsoft.com/fwlink/?LinkID=271858) daha fazla bilgi için makalenin.  
  
<a name="Loading"></a>   
## <a name="loading-the-profiler-dll"></a>Profil Oluşturucu DLL yükleniyor  
 Bu bölümde, nasıl profil oluşturucu UI profil oluşturucu DLL yüklemek Windows mağazası uygulaması neden açıklanmaktadır.  Bu bölümde açıklanan kod profil oluşturucu UI Masaüstü uygulamanızda ait ve bu nedenle Masaüstü uygulamaları için güvenli, ancak Windows mağazası uygulamaları için mutlaka güvenli Windows API'leri kullanarak içerir.  
  
 Profil Oluşturucu kullanıcı Arabirimi uygulamanın işlem alanına iki yolla yüklenmesi profil oluşturucu DLL neden olabilir:  
  
-   Uygulama başlangıcında ortam değişkenleri tarafından denetlenen.  
  
-   Çağırarak başlatma tamamlandıktan sonra uygulamaya ekleyerek [Iclrprofiling::attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) yöntemi.  
  
 İlk roadblocks biri, başlangıç yük ve Windows mağazası uygulamaları ile düzgün çalışması için profil oluşturucu DLL attach-yük alma.  Her iki form yükleyen bazı özel durumlar paylaşır, bu nedenle bunlarla başlayalım.  
  
<a name="Common"></a>   
### <a name="common-considerations-for-startup-and-attach-loads"></a>Başlangıç için ortak ilgili önemli noktalar ve yükleri ekleme  
 **DLL oluşturucunuz imzalama**  
 Windows, profil oluşturucu DLL'yi yüklemeye çalıştığında, profil oluşturucu DLL doğru şekilde imzalanmış doğrular.  Aksi durumda, varsayılan olarak yükleme başarısız olur. Bunu yapmak için iki yol vardır:  
  
-   Profil Oluşturucu DLL imzalanır emin olun.  
  
-   Kullanıcı, bunlar bir geliştirici lisansı kendi Windows 8 makinede, aracı kullanmadan önce yüklemeniz gerektiğini bildirin.  Bu, Visual Studio'dan veya bir komut isteminden el ile otomatik olarak yapılabilir.  Daha fazla bilgi için bkz: [bir geliştirici lisansı alması](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx).  
  
 **Dosya sistemi izinleri**  
 Windows mağazası uygulamasını yükleme ve dosya sistemindeki içinde bulunduğu konumdan profil oluşturucu DLL yürütme izni olması gerekir.  Varsayılan olarak, Windows mağazası uygulaması çoğu dizinleri gibi izinlere sahip değil ve profil oluşturucu DLL yüklenemiyor başarısız tüm girişimler şunun gibi Windows uygulama olay günlüğünde bir giriş oluşturur:  
  
```Output  
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].  
```  
  
 Genellikle, Windows mağazası uygulamaları yalnızca sınırlı sayıda disk üzerindeki konumlara erişmek için izin verilir.  Her Windows mağazası uygulaması kendi uygulamaların veri klasörlerini gibi diğer birkaç alanlarına erişim izni verilen tüm Windows mağazası uygulamaları için dosya sistemini de erişebilirsiniz.  Profil Oluşturucu DLL ve bağımlılıklarını seçeneğinin altındaki bir yerde programı veya Program dosyaları (x86), çünkü tüm Windows mağazası uygulamaları okuma ve Yürütme izinleri var. varsayılan olarak yüklemek en iyisidir.  
  
<a name="Startup"></a>   
### <a name="startup-load"></a>Başlangıç yükleme  
 Genellikle, bir masaüstü uygulamasının profil oluşturucu UI profil oluşturucu DLL başlatma yükü gerekli CLR Profil oluşturma API ortam değişkenleri içeren bir ortam bloğu başlatarak ister (yani, `COR_PROFILER`, `COR_ENABLE_PROFILING`, ve `COR_PROFILER_PATH`), ve ardından yeni bir işlem bu ortam bloğu ile oluşturuluyor.  Aynı Windows mağazası uygulamaları için geçerlidir, ancak mekanizmaları farklıdır.  
  
 **Yükseltilmiş çalıştırma**  
 İşlem, Windows mağazası uygulaması işlem B, A işlem oluşturma girişimleri sırasında Orta bütünlüğü (yani değil yükseltilmiş olan) yüksek bütünlüğü düzeyinde değil düzeyi, çalıştırılması gerekir.  Bu profil oluşturucu UI Orta bütünlüğü düzeyinde çalıştırıyor olması gerekir ya da Windows mağazası uygulamasını başlatarak ilgilenebilmek için Orta bütünlüğü düzeyinde Masaüstü başka bir işlem oluşturma gerekir, anlamına gelir.  
  
 **Profil için Windows mağazası uygulaması seçme**  
 İlk olarak, hangi Windows mağazası uygulamasını başlatmak için profil oluşturucu kullanıcıya sor istersiniz.  Masaüstü uygulamaları için belki de dosya göz atma iletişim Göster ve kullanıcı bulma ve bir .exe dosyası seçin.  Windows mağazası uygulamaları farklı ve göz atma iletişim kullanarak doesn't make Sense ancak.  Bunun yerine, kullanıcı seçmek bu kullanıcı için yüklenen Windows mağazası uygulamalarının listesini göstermek iyidir.  
  
 Kullanabileceğiniz [PackageManager sınıfı](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx) bu listesini oluşturmak için.  `PackageManager`Masaüstü uygulamaları için kullanılabilir bir Windows çalışma zamanı sınıf ve hatta şeklindedir *yalnızca* Masaüstü uygulamaları için kullanılabilir.  
  
 C# yses masaüstü uygulamasında olarak yazılmış kuramsal bir profil oluşturucu UI aşağıdaki kodu örnekten `PackageManager` Windows uygulamaların bir listesini oluşturmak için:  
  
```csharp  
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();  
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();  
PackageManager packageManager = new PackageManager();  
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);  
```  
  
 **Özel ortam blok belirtme**  
 Yeni bir COM arabirimi [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx), bazı tanılama formları kolaylaştırmak için Windows mağazası uygulaması yürütme davranışını özelleştirmenizi sağlar.  Kendi yöntemlerden birini [EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx), başlatıldığında, Windows mağazası uygulaması için bir ortam bloğu geçirmenize olanak verir otomatik işlemi askıya devre dışı bırakma gibi başka yararlı etkileri yanı sıra.  Ortam değişkenlerini belirtmenize gerek yeri olan ortam bloğu önemlidir, çünkü (`COR_PROFILER`, `COR_ENABLE_PROFILING`, ve `COR_PROFILER_PATH)`) profil oluşturucu DLL'yi için CLR tarafından kullanılır.  
  
 Aşağıdaki kod parçacığını göz önünde bulundurun:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, debuggerCommandLine,   
                                                                 (IntPtr)fixedEnvironmentPzz);  
```  
  
 Birkaç sağ almak için gerekli öğeleri şunlardır:  
  
-   `packageFullName`paketler yineleme yapma ve ele geçirme sırasında belirlenen `package.Id.FullName`.  
  
-   `debuggerCommandLine`biraz daha ilginç olacaktır.  Windows mağazası uygulaması için özel ortam blok geçirmek için kendi simplistic Kukla hata ayıklayıcı yazmanız gerekir.  Windows spawns Windows mağazası uygulaması askıya ve ardından, hata ayıklayıcı bu örnekteki gibi bir komut satırı ile başlatarak, hata ayıklayıcı ekler:  
  
    ```Output  
    MyDummyDebugger.exe -p 1336 -tid 1424  
    ```  
  
     Burada `-p 1336` Windows mağazası uygulaması işlem kimliği 1336 olduğu anlamına gelir ve `-tid 1424` iş parçacığı kimliği 1424 askıya alınmış iş parçacığı olduğu anlamına gelir.  Kukla, hata ayıklayıcı komut satırından ThreadID ayrıştırma, bu iş parçacığını devam ve çıkın.  
  
     İşte bazı örnek Bunu yapmak için C++ kodu (hata denetimi eklediğinizden emin olun!):  
  
    ```cpp  
    int wmain(int argc, wchar_t* argv[])  
    {      
        // …  
        // Parse command line here  
        // …  
  
        HANDLE hThread = OpenThread(THREAD_SUSPEND_RESUME,   
                                                                  FALSE /* bInheritHandle */, nThreadID);  
        ResumeThread(hThread);  
        CloseHandle(hThread);  
        return 0;  
    }  
    ```  
  
     Bu Kukla hata ayıklayıcı Tanılama Aracı yüklemesinin bir parçası dağıtmak ve bu hata ayıklayıcıda yolunu belirtmeniz gerekir `debuggerCommandLine` parametresi.  
  
 **Windows mağazası uygulamasını başlatma**  
 Windows mağazası uygulamasını başlatmak için şu anda son edinildi. Bunu kendiniz yapmak'yı zaten zaten denediyseniz, fark etmiş [CreateProcess](https://msdn.microsoft.com/library/windows/desktop/ms682425\(v=vs.85\).aspx) olan bir Windows mağazası uygulama işlemini oluşturma değil.  Bunun yerine, kullanmak için ihtiyaç duyarsınız [IApplicationActivationManager::ActivateApplication](https://msdn.microsoft.com/library/windows/desktop/Hh706903\(v=vs.85\).aspx) yöntemi.  Bunu yapmak için başlatma Windows mağazası uygulaması App kullanıcı Model Kimliğini almak gerekir.  Ve bildirim aracılığıyla biraz sorunda yapmanız gerekir anlamına gelir.  
  
 Paketlerinizi yineleme sırasında ("Seçme bir Windows mağazası uygulaması için profil" bölümüne bakın [başlangıç yük](#Startup) bölümüne), geçerli paketin bildiriminde bulunan uygulama kümesini yakalayın isteyeceksiniz:  
  
```csharp  
string manifestPath = package.InstalledLocation.Path + "\\AppxManifest.xml";  
  
AppxPackaging.IStream manifestStream;  
SHCreateStreamOnFileEx(  
                    manifestPath,  
                    0x00000040,     // STGM_READ | STGM_SHARE_DENY_NONE  
                    0,              // file creation attributes  
                    false,          // fCreate  
                    null,           // reserved  
                    out manifestStream);  
  
IAppxManifestReader manifestReader = appxFactory.CreateManifestReader(manifestStream);  
  
IAppxManifestApplicationsEnumerator appsEnum = manifestReader.GetApplications();  
```  
  
 Evet, bir paket birden çok uygulama sahip olabilir ve her uygulamanın kendi uygulama kullanıcı modeli kimliği vardır.  Bu nedenle, kullanıcı profili için hangi uygulama isteyin ve belirli uygulamadan uygulama kullanıcısı Model kimliği alın isteyeceksiniz:  
  
```csharp  
while (appsEnum.GetHasCurrent() != 0)  
{  
    IAppxManifestApplication app = appsEnum.GetCurrent();  
    string appUserModelId = app.GetAppUserModelId();  
…  
```  
  
 Son olarak, artık Windows mağazası uygulamasını başlatmak ihtiyacınız vardır:  
  
```csharp  
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();  
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);  
```  
  
 **DisableDebugging çağırmak unutmayın**  
 Aradığınız zaman [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx), kendiniz sonra çağırarak temizlenmesi promise yapılan [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) yöntemi, bu nedenle gerçekleştirdiğinizden emin olun Bu profil oluşturma oturumu üzerinden olduğunda.  
  
<a name="Attach"></a>   
### <a name="attach-load"></a>Yük ekleme  
 Zaten çalışan başlamış bir uygulamaya profil oluşturucu DLL eklemek profil oluşturucu UI istediği zaman kullandığı [Iclrprofiling::attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md).  Windows mağazası uygulamaları ile aynı geçerlidir.  Ancak daha önce listelenen ortak konulara ek olarak olduğundan emin olun hedef Windows mağazası uygulaması değil askıya alındı.  
  
 **EnableDebugging**  
 Başlangıç yük gibi çağıran [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx) yöntemi.  Bir ortam bloğu geçirmesi gerekmez, ancak diğer özelliklerinden biri gerekir: otomatik işlemi askıya devre dışı bırakma.  Aksi takdirde, profil oluşturucu UI çağırdığında [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md), hedef Windows mağazası uygulaması askıya alınabilir.  Aslında, bu kullanıcının artık, Profil Oluşturucu kullanıcı Arabirimi ile etkileşim ve Windows mağazası uygulaması herhangi bir kullanıcının ekranlar üzerinde etkin değilse olasıdır.  Ve app askıya Windows mağazası, hiçbirine yanıt yükleyemezsiniz, CLR için profil oluşturucu DLL eklenecek gönderdiğini işaret eder.  
  
 Bu nedenle böyle bir şeyler isteyeceksiniz:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, null /* debuggerCommandLine */,   
                                                                 IntPtr.Zero /* environment */);  
```  
  
 Bu, bir hata ayıklayıcı komut satırından veya bir ortam bloğu belirtmeyin dışında başlangıç yük çalışması için yapacağınız aynı çağrıdır.  
  
 **DisableDebugging**  
 Her zaman olduğu gibi arama yapmayı unutmayın [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) profil oluşturma oturumu tamamlanmış olduğunda.  
  
<a name="Running"></a>   
## <a name="running-inside-the-windows-store-app"></a>Windows mağazası uygulaması içinde çalışan  
 Bu nedenle Windows mağazası uygulaması son olarak, profil oluşturucu DLL yükledi.  Profil Oluşturucu DLL Windows mağazası uygulamaları tarafından gereken farklı kuralları tarafından yürütmek nasıl öğrettin gerekir artık API'ler izin verilen olan ve çalıştırmak nasıl dahil olmak üzere izinleri azalır.  
  
<a name="APIs"></a>   
### <a name="stick-to-the-windows-store-app-apis"></a>Windows mağazası uygulama API'lerine takılıyor  
 Windows API gezinirken her API Masaüstü uygulamaları, Windows mağazası uygulamaları veya her ikisi de geçerli olduğu belgelenmiştir olduğunu fark edeceksiniz.  Örneğin, **gereksinimleri** belgelerine bölümünü [InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx) işlevi gösterir işlevi yalnızca Masaüstü uygulamaları için geçerlidir. Buna karşılık, [InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx) işlevidir hem Masaüstü uygulamaları hem de Windows mağazası uygulamaları için kullanılabilir.  
  
 Profil Oluşturucu DLL geliştirirken, bir Windows mağazası uygulaması ise gibi ele alın ve yalnızca Windows mağazası uygulamaları için kullanılabilir olarak belgelenen API'lerini kullanır.  Bağımlılıkları çözümlemek (örneğin, çalıştırabilirsiniz `link /dump /imports` denetlemek için profil oluşturucu DLL karşı) ve ardından, bağımlılıkları hangisinin Tamam ve hangi olmayan görmek için belgeleri arayın.  Çoğu durumda, ihlalleri yalnızca bunları güvenli olarak belgelenen API'ın daha yeni bir form ile değiştirerek sabit (örneğin, değiştirme [InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx) ile [ InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx)).  
  
 Profil Oluşturucu DLL yalnızca Masaüstü uygulamaları için geçerli bazı API'lerini çağırır ve henüz bile, profil oluşturucu DLL Windows mağazası uygulaması içinde ne zaman yüklendi çalışmaya göründüğü fark edebilirsiniz.  Profil Oluşturucu bir Windows mağazası uygulama işlemine yüklendiğinde dll Windows mağazası uygulamaları ile kullanmak için belgelenmemiş herhangi bir API'yi kullanmak için riskli olduğunu unutmayın:  
  
-   Windows mağazası uygulamaları çalıştırmak benzersiz bağlamında çağrıldığında çalışması için bu API'leri garanti edilmez.  
  
-   Bu tür API'leri, farklı Windows mağazası uygulama süreçlerinde çağrıldığında tutarlı bir şekilde çalışmayabilir.  
  
-   Bu tür API'leri geçerli sürümü, Windows, Windows mağazası uygulamalarında düzgün çalışabilmesi için görünebilir, ancak kesilebilir veya gelecekteki Windows sürümlerinde devre dışı.  
  
 Tüm ihlallerini düzeltmek ve riskini önlemek için en iyi öneridir bakın.  
  
 Kesinlikle olmadan belirli bir API yapamayacağı ve yerine yeni bir Windows mağazası uygulamaları için uygun bulunamıyor bulabilirsiniz.  Böyle bir durumda, en az:  
  
-   Test, test yaşam daylights bu API, kullanım dışı.  
  
-   API aniden bölün veya adlı kaybolur olduğunu anlamak gelen içinde Windows mağazası uygulamaları gelecekteki Sunumlarda Windows.  Bu bir uyumluluk sorunu Microsoft tarafından kabul olmaz ve sizin kullanımını destekleyen bir öncelik olmaz.  
  
<a name="Permissions"></a>   
### <a name="reduced-permissions"></a>Sınırlı izinlere  
 Windows mağazası uygulama izinleri Masaüstü uygulamalardan farklı tüm yolları listelemek için bu konunun kapsamı dışında.  Ancak profil oluşturucu (Windows mağazası uygulaması bir masaüstü uygulamasının karşılaştırıldığında içine yüklendiğinde) DLL herhangi bir kaynağa erişmeyi dener edildiğinde kesinlikle davranışı farklı olacaktır.  En yaygın örnek dosya sistemidir.  Vardır ancak birkaç yerleştirir belirli bir Windows mağazası uygulaması erişmesine izin verilip disk üzerinde (bkz [dosya erişim ve izinleri (Windows çalışma zamanı uygulamaları](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)), ve profil oluşturucu DLL aynı kısıtlamalara altında olacaktır.  Kodunuzu baştan sona test edin.  
  
<a name="Interprocess"></a>   
### <a name="inter-process-communication"></a>İşlemler arası iletişim  
 Bu yazı başındaki diyagramda gösterildiği gibi profil oluşturucu DLL'si (Windows mağazası uygulama işlem alanına yüklü), Profil Oluşturucu kullanıcı Arabirimi (ayrı masaüstü uygulaması işlem alanında çalışır), kendi özel arası süreci ile iletişim kurmak büyük olasılıkla gerekir iletişim (IPC) kanalı.  Profil Oluşturucu UI sinyalleri davranışını değiştirmek için profil oluşturucu DLL gönderir ve sonrası işleme ve profil oluşturucu kullanıcıya görüntülemek için profil oluşturucu UI dön çözümlenen Windows mağazası uygulamasından profil oluşturucu DLL verileri gönderir.  
  
 Bu şekilde çalışması çoğu profil oluşturucular gerekir, ancak bir Windows mağazası uygulamasına profil oluşturucu DLL yüklendiğinde IPC mekanizmaları ilgili seçimlerinizi daha sınırlıdır.  Bunları kullanamazlar Örneğin, adlandırılmış kanallar Windows mağazası uygulama SDK'sı, bir parçası değildir.  
  
 Ancak doğal olarak, dosyalar yine de daha kısıtlı bir şekilde barındırabilir.  Olayları de kullanılabilir.  
  
 **Dosyaları iletişim**  
 Verilerinizden en iyi büyük olasılıkla profil oluşturucu DLL ve Profil Oluşturucu kullanıcı Arabirimi arasında dosyaları geçer.  Profil Oluşturucu DLL (Windows mağazası uygulaması bağlamında) ve profil oluşturucu UI okuduğunuzu dosya konumunu ve yazma erişimi seçmek için kullanılan anahtardır.  Örneğin, geçici klasör yolu hem profil oluşturucu DLL hem de profil oluşturucu UI erişebileceği bir konuma ancak başka bir Windows mağazası uygulama paketi (Bu nedenle diğer Windows mağazası uygulama paketlerden oturum herhangi bir bilgi koruma) erişebilir.  
  
 Profil Oluşturucu kullanıcı Arabirimi ve profil oluşturucu DLL bu yolu bağımsız olarak belirleyebilirsiniz.  Profil Oluşturucu geçerli kullanıcı için yüklenen tüm paketler dolaşır zaman UI, (bkz: örnek kod önceki) alır erişimi `PackageId` içinden geçici klasör yolu türetilen bu parçacığı benzer bir kod ile sınıfı,.  (Her zaman olduğu gibi hata denetimi okumanızdır atlandı.)  
  
```csharp  
// C# code for the Profiler UI.  
ApplicationData appData =  
    ApplicationDataManager.CreateForPackageFamily(  
        packageId.FamilyName);  
  
tempDir = appData.TemporaryFolder.Path;  
```  
  
 Bu sırada, profil oluşturucu DLL temelde aynı şeyi yapabilirsiniz, mümkün olsa daha kolayca almak [ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx) kullanarak sınıfı [ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx) özelliği.  
  
 **Olayları üzerinden iletişim**  
 Profil Oluşturucu kullanıcı Arabirimi ve profil oluşturucu DLL arasında basit sinyal semantiği istiyorsanız, masaüstü uygulamalarının yanı sıra Windows mağazası uygulamaları olayları kullanabilirsiniz.  
  
 Yalnızca çağırabilirsiniz, profil oluşturucu DLL'den [CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx) istediğiniz herhangi bir ad ile adlandırılmış bir olay oluşturmak için işlevi.  Örneğin:  
  
```cpp  
// Profiler DLL in Windows Store app (C++).  
CreateEventEx(   
    NULL,  // Not inherited  
    "MyNamedEvent"  
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */  
    EVENT_ALL_ACCESS);  
```  
  
 Profil Oluşturucu kullanıcı Arabirimi, sonra Windows mağazası uygulamanızın ad alanı altındaki adlandırılmış olay bulması gerekir.  Örneğin, profil oluşturucu UI çağırabilirsiniz [CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx), olay adı olarak belirtme  
  
 `AppContainerNamedObjects\<acSid>\MyNamedEvent`  
  
 `<acSid>`Windows mağazası uygulamanızın Appcontaıner SID ' dir.  Bu konuda daha önceki bir bölümünü geçerli kullanıcı için yüklenen paketler üzerinden yinelemek nasıl oluşturulacağını gösterir.  Bu örnek koddan PackageId elde edebilirsiniz.  Ve PackageId elde edebilirsiniz `<acSid>` kodu aşağıdakine benzer:  
  
```csharp  
IntPtr acPSID;  
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);  
  
string acSid;  
ConvertSidToStringSid(acPSID, out acSid);  
  
string acDir;  
GetAppContainerFolderPath(acSid, out acDir);  
```  
  
<a name="Shutdown"></a>   
### <a name="no-shutdown-notifications"></a>Kapatma bildirim yok  
 Windows mağazası uygulaması içinde çalışırken, profil oluşturucu DLL üzerinde doğrulamamalısınız [Icorprofilercallback::shutdown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md) ve hatta [DllMain](https://msdn.microsoft.com/library/windows/desktop/ms682583\(v=vs.85\).aspx) (ile `DLL_PROCESS_DETACH`) profil oluşturucu DLL bildirmek için çağrılan Windows mağazası uygulaması, çıkılıyor.  Aslında, hiçbir zaman çağrılacağı beklemelisiniz.  Tarihsel olarak, disk, dosyaları kapatma, Profil Oluşturucu kullanıcı Arabirimi, vb. için bildirimleri göndermek için önbellekleri temizlemek için çok sayıda profil oluşturucu DLL'leri bildirimlerin uygun yerlerde kullandınız.  Ancak şimdi profil oluşturucu DLL biraz farklı bir şekilde düzenlenmesi gerekir.  
  
 Profil Oluşturucu DLL gidiyor günlük bilgileri olmalıdır.  Performansı artırmak için bellek bilgileri toplu ve onu toplu bazı Eşiği aşan boyutu büyüdükçe diske temizleme isteyebilirsiniz.  Ancak henüz diske herhangi bir bilgi kaybolabilir varsayalım.  Bu, eşik akıllıca seçmek istersiniz ve profil oluşturucu UI profil oluşturucu DLL tarafından yazılan bilgileri eksik uğraşmanız sağlamlaştırılmış olması gerektiğini anlamına gelir.  
  
<a name="Metadata"></a>   
## <a name="windows-runtime-metadata-files"></a>Windows çalışma zamanı meta veri dosyaları  
 Bu ayrıntıya gitmek için bu belgenin kapsamı dışında hangi Windows çalışma zamanı meta (WinMD) dosyalarının adıdır.    Bu bölüm, profil oluşturucu DLL çözümleme Windows mağazası uygulaması tarafından WinMD dosyalar yüklendiğinde nasıl CLR Profil oluşturma API tepki verdiğini için sınırlı değildir.  
  
<a name="WMDs"></a>   
### <a name="managed-and-non-managed-winmds"></a>Yönetilen ve yönetilmeyen WinMDs  
 Bir geliştirici, yeni bir Windows çalışma zamanı bileşeni projesi oluşturmak için Visual Studio kullanıyorsa, projenin bir yapı geliştirici tarafından yazılan meta veriler (türü açıklamalarını sınıflar, arabirimler, vb.) açıklayan bir WinMD dosyası oluşturur.  Bu proje C# veya VB ile yazılmış bir yönetilen dil projesiyse o aynı WinMD dosyası bu türlerde (geliştiricinin kaynak kodundan derlenmiş IL içerdiği anlamına gelir) uygulamasını da içerir.  Bu tür dosyalar yönetilen WinMD dosyası olarak bilinir.  Windows çalışma zamanı meta verileri ve temel uygulaması içeren ilginç.  
  
 Buna karşılık, bir geliştirici C++ için bir Windows çalışma zamanı bileşeni proje oluşturursa, yalnızca meta veriler içeren bir WinMD dosyası projenin bir yapı oluşturur ve uygulama ayrı bir yerel DLL derlenirken.  Benzer şekilde, Windows SDK'ın sevk WinMD dosyalar Windows'un bir parçası sevk ayrı yerel DLL'leri içine derlenmiş uygulamasıyla yalnızca meta veri içerir.  
  
 Aşağıdaki bilgiler, meta verileri ve uygulama içerir, hem yönetilen WinMDs ve yalnızca meta veriler içeren yönetilmeyen WinMDs için geçerlidir.  
  
<a name="CLRModules"></a>   
### <a name="winmd-files-look-like-clr-modules"></a>CLR modülleri gibi WinMD dosyaları arayın  
 CLR ilgili olduğu kadar tüm WinMD modülleri dosyalarıdır.  CLR Profil oluşturma API, bu nedenle profil oluşturucu WinMD dosyaları yüklediğinizde DLL ve bunların ModuleIDs, diğer yönetilen modülleri için olduğu gibi aynı şekilde nelerdir söyler.  
  
 Profil Oluşturucu DLL WinMD dosyaları diğer modüllerden çağırarak ayırabilmesi [Icorprofilerınfo3::getmoduleınfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) yöntemi ve İnceleme `pdwModuleFlags` çıkış parametresi için [COR_PRF_MODULE_WINDOWS_ Çalışma zamanı](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) bayrağı.  (Bir WinMD Moduleıd temsil eder ve yalnızca, bu ayarlanır.)  
  
<a name="Reading"></a>   
### <a name="reading-metadata-from-winmds"></a>WinMDs meta verilerini okuma  
 Normal modülleri gibi WinMD dosyaları aracılığıyla okuma meta verileri içeren [meta veri API'leri](../../../../docs/framework/unmanaged-api/metadata/index.md).  Ancak, yönetilen kodda program ve WinMD dosyası tüketen geliştiriciler daha doğal bir programlama deneyimi böylece WinMD dosyaları okuduğunda CLR Windows çalışma zamanı türlerini .NET Framework türleri ile eşleştirir.  Bu eşlemeler bazı örnekleri için bkz: [Windows mağazası uygulamaları için .NET Framework desteği ve Windows çalışma zamanı](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).  
  
 Bu nedenle API meta veri kullandığında oluşturucunuz hangi görünümünü görürsünüz: ham Windows çalışma zamanı görünümü veya eşlenmiş bir .NET Framework Görünüm?  Yanıt: bunu size bağlıdır.  
  
 Çağırdığınızda [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) bir meta veri arabirimi gibi elde etmek için bir WinMD yöntemi [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), ayarlamayı da seçebilirsiniz [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)içinde `dwOpenFlags` bu eşlemesini devre dışı bırakmak için parametre.  Aksi takdirde, varsayılan olarak, eşleme etkinleştirilecek.  Genellikle, böylece profil oluşturucu DLL WinMD meta verileri (örneğin, adları türlerinin) edinir dizeleri tanıdık ve profil oluşturucu kullanıcıya doğal görüneceğini bir profil oluşturucu etkin eşleme tutar.  
  
<a name="Modifying"></a>   
### <a name="modifying-metadata-from-winmds"></a>WinMDs meta verilerini değiştirme  
 Meta verilerde WinMDs değiştirme desteklenmez.  Çağırırsanız [Icorprofilerınfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) yöntemi bir WinMD için dosya ve belirtin [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) içinde `dwOpenFlags` parametresi veya yazılabilir meta verileri arabirimdeki gibi isteyin [ Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) başarısız olur.  Bu, kendi izleme (örneğin, AssemblyRefs veya yeni yöntemleri eklemek için) desteklemek için meta verileri değiştirmeye ihtiyaç duyan IL yeniden yazma işlemi profil oluşturucular için belirli bir öneme sahip olur.  İçin denetlemeniz gerekir böylece [COR_PRF_MODULE_WINDOWS_RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) ilk (önceki bölümde açıklandığı gibi) ve ayarladıysa böyle modülleri için yazılabilir meta veri arabirimleri isteyen.  
  
<a name="Resolving"></a>   
### <a name="resolving-assembly-references-with-winmds"></a>Derleme başvurularını WinMDs ile çözme  
 El ile araçları veya türü denetleme yardımcı olmak için meta veri başvuruları çözümlemek birçok profil oluşturucular gerekir.  Bu tür profil oluşturucular bu başvuruları standart derleme başvurularını tamamen farklı bir biçimde çözümlenir çünkü nasıl CLR WinMDs için noktası derleme başvurularını çözümler dikkat etmeniz gerekir.  
  
<a name="Profilers"></a>   
## <a name="memory-profilers"></a>Bellek profil oluşturucuları  
 Yönetilen yığın ve atık toplayıcı bir Windows mağazası uygulaması ve bir masaüstü uygulamasının temelde farklı değildir.  Ancak, farkında olması için profil oluşturucu yazarlar gereken bazı farklar vardır.  
  
<a name="ForceGC"></a>   
### <a name="forcegc-creates-a-managed-thread"></a>Yönetilen iş parçacığı ForceGC oluşturur  
 Bellek profili oluşturma yaparken, profil oluşturucu DLL genellikle içinden çağırmak ayrı bir iş parçacığı oluşturduğu [ForceGC yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) yöntemi.  Yeni bir şey budur.  Ancak ne şaşırtıcı olabilir bir Windows mağazası uygulaması içinde çöp toplama yapmanın act yönetilen bir iş parçacığı, iş parçacığı dönüştürme (örneğin, bir profil oluşturma API ThreadID o iş parçacığı için oluşturulur).  
  
 Bu sonuçlarını anlamak için CLR Profil oluşturma API'si tarafından tanımlandığı şekilde zaman uyumlu ve zaman uyumsuz çağrıları arasındaki farkları anlamak önemlidir. Windows mağazası uygulamalarında zaman uyumsuz çağrılar kavramı çok farklı olduğunu unutmayın.  Blog gönderisine bakın [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE sahibiz neden](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) daha fazla bilgi için.  
  
 İlgili çağrılara profil oluşturucu DLL'nin birinin uygulaması dışında yapılır olsa bile, Profil Oluşturucu tarafından oluşturulan iş parçacığı üzerinde yapılan çağrıları her zaman zaman uyumlu olarak kabul edilir noktasıdır [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) yöntemleri.  En az kullanılan harf olmalıdır.  CLR, aramanız için nedeniyle, yönetilen bir iş parçacığı oluşturucunuz'ın iş parçacığı etkinleştirdiyse göre [ForceGC yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md), iş parçacığı artık oluşturucunuz'ın iş parçacığı olarak kabul edilir.  Bu nedenle, CLR ne zaman uyumlu olarak o iş parçacığı için niteleyen daha sıkı bir tanım zorlar — öğesine bir çağrı kaynaklanan gerekir, profil oluşturucu DLL'nin birini içinde [Icorprofilercallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) zaman uyumlu olarak nitelemek için yöntemleri.  
  
 Ne bu uygulamada anlama geliyor?  Çoğu [Icorprofilerınfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) yöntemleri yalnızca zaman uyumlu olarak çağrılması güvenlidir ve hemen Aksi takdirde başarısız olur.  Profil Oluşturucu DLL yeniden kullanır, bu nedenle, [ForceGC yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) genellikle Profil Oluşturucu tarafından oluşturulan iş parçacıklarında yapılan diğer çağrıları için iş parçacığı (örneğin, [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md), [Requestrejıt](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md), veya [RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)), sorun yaşıyorsanız oluşturacağız.  Bile bir güvenli zaman uyumsuz işlev gibi [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) yönetilen iş parçacığı tarafından çağrıldığında özel kurallar vardır. (Blog gönderisine bakın [taramasını profil oluşturucu yığınının: temel kavramları ve ötesine](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) daha fazla bilgi için.)  
  
 Bu nedenle, profil oluşturucu DLL oluşturur çağırmak için herhangi bir iş parçacığı öneririz [ForceGC yöntemi](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) kullanılması gereken *yalnızca* GC'ler tetikleme ve GC geri aramalar için yanıt amacıyla.  Bunu örnekleme veya ayırma yığını gibi diğer görevleri gerçekleştirmek için profil oluşturma API uygulamasına çağırmalıdır değil.  
  
<a name="WeakTable"></a>   
### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences  
 .NET Framework 4. 5'ile başlayarak, var. yeni bir GC geri çağırma [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md), profil oluşturucu daha tamamlamak bilgi hakkında hangi verir *bağımlı tanıtıcıları*. Bu tanıtıcıları kaynak nesneden bir başvuru GC ömrü yönetim amacıyla hedef nesnesi için etkili bir şekilde ekleyin.  Bağımlı tanıtıcılarıdır yeni bir şey ve yönetilen kodda program geliştiriciler kullanarak kendi bağımlı tanıtıcıları oluşturmak mümkün olmuştur <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> bile Windows 8 ve .NET Framework 4.5 önce sınıfı.  
  
 Ancak, yönetilen XAML Windows mağazası uygulamaları artık bağımlı tanıtıcıları kullanımına ağırlık olun.  Özellikle, CLR başvuru döngüleri yönetilen ve yönetilmeyen Windows çalışma zamanı nesneleri arasında yönetmeye yardımcı olmak için bunları kullanır.  Bu, daha fazla önemlidir şimdi bu bağımlı işler böylece yığın grafik kenarları geri kalanı ile birlikte canlandırılabilir haberdar olmak herhangi bir zamanda bellek profil oluşturucuları için olduğunu gösterir.  Profil Oluşturucu DLL kullanması gereken [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), ve [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) birlikte yığın grafik eksiksiz bir görünüm oluşturmak için .  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Sonuç  
 Windows mağazası uygulamaları içinde çalışan yönetilen kodu analiz etmek için CLR Profil oluşturma API kullanmak da mümkündür.  Aslında, geliştirmekte var olan bir profil oluşturucu kılın ve böylece Windows mağazası uygulamaları hedefleyebilirsiniz belirli bazı değişiklikler yapın.   Profil Oluşturucu kullanıcı Arabirimi, Windows mağazası uygulaması hata ayıklama modunda etkinleştirmek için yeni API'ları kullanmanız gerekir.  Profil Oluşturucu DLL yalnızca Windows mağazası uygulamaları için geçerli bu API'leri tüketir emin olun.  Profil Oluşturucu DLL ve profil oluşturucu UI arasındaki iletişim mekanizması Windows mağazası uygulama API kısıtlamaları göz önüne ve Windows mağazası uygulamaları için yerinde kısıtlı izinleri tanıma ile yazılması gerekir.  Profil Oluşturucu DLL CLR WinMDs, nasıl işler farkında olmalıdır ve atık toplayıcının davranışı nasıl yönetilen iş parçacığı göre farklılık gösterir.  
  
<a name="Resources"></a>   
## <a name="resources"></a>Kaynaklar  
 **Ortak dil çalışma zamanı**  
 -   [CLR Profil oluşturma API Başvurusu](../../../../docs/framework/unmanaged-api/profiling/index.md)  
  
-   [CLR meta veri API Başvurusu](../../../../docs/framework/unmanaged-api/metadata/index.md)  
  
 **Windows çalışma zamanı ile CLR'nin etkileşimi**  
 [Windows mağazası uygulamaları ve Windows çalışma zamanı için .NET framework desteği](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
  
 **Windows mağazası uygulamaları**  
 -   [Dosya erişim ve izinleri (Windows çalışma zamanı uygulamaları](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)  
  
-   [Bir geliştirici lisansı alma](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)  
  
-   [IPackageDebugSettings arabirimi](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma](../../../../docs/framework/unmanaged-api/profiling/index.md)
