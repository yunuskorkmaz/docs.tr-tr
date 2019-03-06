---
title: CLR Profil oluşturucular ve Windows Store uygulamaları
ms.date: 03/30/2017
dev_langs:
- csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93344e1c5aa62e86d29a0110a9d8cffc3cea66ff
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358554"
---
# <a name="clr-profilers-and-windows-store-apps"></a>CLR Profil oluşturucular ve Windows Store uygulamaları

Bu konuda, ne zaman analiz yazma tanılama araçları bir Windows Store uygulaması içinde çalışan yönetilen kod hakkında düşünmek gerekenler açıklanmaktadır. Ayrıca, Windows Store apps karşı çalıştırdığınızda çalışmaya devam etmek için mevcut geliştirme araçlarınızı değiştirmek için yönergeler sağlar. Bu bilgileri anlamak için ortak dil çalışma zamanı profil oluşturma API ile ilgili bilgi sahibi değilseniz, zaten bu API Windows Masaüstü uygulamaları ve karşı düzgün çalışır şimdi aracı değiştirme ilginizi çeken, bir Tanılama Aracı'nda kullandığınız en iyisidir Windows Store apps karşı düzgün çalışması için.

## <a name="introduction"></a>Giriş

Bir giriş paragrafı yaptıysanız, daha sonra CLR Profil oluşturma API'si ile biliyorsunuzdur. Yönetilen Masaüstü uygulamaları karşı iyi çalışan bir tanılama aracı yazmış olduğunuz. Şimdi, aracı ile yönetilen bir Windows Store uygulaması çalışır böylece yapmanız gerekenler merak işiniz. Belki de bunun çalışmasını sağlamak ve bir basit görev olmadığını bulunan zaten çalıştınız. Aslında, birkaç tüm araçlar geliştiricilerin belirgin olmayabilecek ilgili önemli noktalar vardır. Örneğin:

- Windows Store apps bir bağlamda önemli ölçüde azaltılmış izinlerle çalıştırın.

- Windows meta veri dosyaları için geleneksel yönetilen modülleri karşılaştırıldığında benzersiz özelliklerine sahiptir.

- Windows Store apps etkileşim arızalandığında kendilerini askıya alma, bir alýþkanlýk vardır.

- İşlemler arası iletişim mekanizmaları, çeşitli nedenlerden dolayı artık çalışmayabilir.

Bu konu, farkında olmanız gereken şeyleri ve düzgün bir şekilde başa çıkma listeler.

CLR Profil oluşturma API için yeni, daha iyi giriş bilgilerini bulmak için bu konunun sonunda kaynakları aşağı atlayın.

Özel Windows API'ların nasıl kullanılacağı hakkında daha fazla ayrıntı sağlamak, bu konunun kapsamı dışında olan. Bu konuda bir başlangıç noktası göz önünde bulundurun ve burada başvurulan tüm Windows API'leri hakkında daha fazla bilgi için MSDN başvurun.

## <a name="architecture-and-terminology"></a>Mimari ve terminoloji

Genellikle, bir tanılama aracı aşağıda gösterilene benzer bir mimariye sahiptir. "Profil Oluşturucu" terimini kullanır, ancak nesne çerçeveleri de tipik performans veya kod kapsamı gibi alanlarına bellek profil, sahte, seyahat süresi hata ayıklama, uygulama izleme vb. gibi birçok araç gidin. Kolaylık olması için bu araçları profil oluşturucular olarak başvurmak bu konuda devam eder.

Bu konu başlığı altında yaptığımız aşağıdaki terimler kullanılır:

**Uygulama**

Bu, profil oluşturucu çözümleme uygulamasıdır. Genellikle, bu uygulama geliştiricisine uygulamayla sorunlarının tanılanmasına yardımcı olmak için artık profil oluşturucuyu kullanıyor. Geleneksel olarak, bu uygulama, bir Windows masaüstü uygulaması olacaktır, ancak bu konuda, Windows Store uygulamaları bekliyoruz.

**Profiler DLL**

Bu analiz uygulamanın işlem alanına yüklenen bileşendir. Bu bileşen olarak da bilinen "Aracısı" profiler uygulayan [Icorprofilercallback](icorprofilercallback-interface.md)[Icorprofilercallback arabirimi](icorprofilercallback-interface.md)(2,3, vb.) arabirimler ve tüketir [ Icorprofilerınfo](icorprofilerinfo-interface.md)(2,3, vb.) arabirimler ve potansiyel olarak çözümlenen uygulama hakkında veri toplamak için uygulamanın davranış yönlerini değiştirin.

**Profiler kullanıcı Arabirimi**

Bu profil oluşturucu kullanıcı ile etkileşime giren bir masaüstü uygulamasıdır. Bu kullanıcı için uygulama durumunu görüntülemek ve kullanıcı analiz edilen uygulama davranışını denetlemek için araçlar vererek sorumludur. Bu bileşen her zaman kendi işlem alanı, profili oluşturulan uygulama işlemi alanından ayrı çalıştırır. "Ekleme tetikleyici," çağıran işlemi olan Profiler kullanıcı arabirimini de davranabilir [Iclrprofiling::attachprofiler](iclrprofiling-attachprofiler-method.md) Profiler DLL'yi burada profil oluşturucu DLL belirtmiyor bu durumlarda analiz edilen uygulamanın yöntemi Başlangıçta yükleyin.

> [!IMPORTANT]
> Profiler kullanıcı Arabirimi, bile denetimi ve Windows Store app raporda kullanıldığında, bir Windows masaüstü uygulaması kalması gerekir. Paketini ve Windows Store, Tanılama aracında sevk beklemiyoruz. Araç, Windows Store apps yapamayacağı ve çoğu bunları Profiler kullanıcı Arabirimi içinde bulunan bir şey yapmanız gerekir.

Bu belge boyunca, örnek kod olduğunu varsayar:

- CLR Profil oluşturma API'ın gereksinimlerine uygun bir yerel DLL gerektiğinden, Profiler DLL'yi C++ dilinde yazılır.

- Profiler UI C# dilinde yazılır. Bu gerekli değildir, ancak dil Profiler UI'nin işlem için bir gereksinimi yoktur çünkü neden kısa ve basit bir dil seçin?

### <a name="windows-rt-devices"></a>Windows RT cihazları

Windows RT cihazları oldukça kilitlendiğini. Üçüncü taraf profil Oluşturucular, yalnızca bu cihazlarda yüklenemiyor. Bu belge, Windows 8 bilgisayarlarında odaklanır.

## <a name="consuming-windows-runtime-apis"></a>Windows çalışma zamanı API'ları kullanma

Aşağıdaki bölümlerde ele alınan senaryolar sayısında Profiler UI Masaüstü uygulamanızı bazı yeni Windows Runtime API'ları kullanmasını gerektiren durumlar. Hangi Windows Runtime API'ları Masaüstü uygulamalarından kullanılabileceğini anlamak için belgelere isteyebilirsiniz ve davranışlarını ne zaman farklı olup olmadığını, Masaüstü uygulamaları ve Windows Store apps çağrılır.

Profiler kullanıcı Arabirimi, yönetilen kodda yazılmış birkaç adımda bu kolay Windows çalışma zamanı API'leri kullanan hale getirmek için ihtiyacınız olacaktır. Bkz: [yönetilen Masaüstü uygulamaları ve Windows çalışma zamanı](https://go.microsoft.com/fwlink/?LinkID=271858) makale daha fazla bilgi için.

## <a name="loading-the-profiler-dll"></a>Profiler DLL yükleniyor

Bu bölümde, nasıl Profiler kullanıcı Arabirimi, Profiler DLL'yi Windows Store app neden açıklanmaktadır. Bu bölümde açıklanan kod Profiler UI Masaüstü uygulamanıza ait ve bu nedenle Masaüstü uygulamaları için güvenli ancak mutlaka Windows Store uygulamaları için güvenli bir Windows API'leri kullanarak içerir.

Profiler kullanıcı Arabirimi, Profiler DLL'yi iki yolla uygulamanın işlem alanına yüklenmesine neden olabilir:

- Uygulama başlangıcında gibi ortam değişkenlerini şu yollarla denetlenir.

- Çağırarak başlangıç tamamlandıktan sonra uygulamaya ekleyerek [Iclrprofiling::attachprofiler](iclrprofiling-attachprofiler-method.md) yöntemi.

İlk, önündeki engellerin birini alma başlatma-yükleme ve Windows Store uygulamaları ile düzgün çalışması için Profiler DLL'yi ekleme-yükleme. Her iki biçimi yükleyen bazı özel durumlar paylaşır, şimdi bunları ile başlatın.

### <a name="common-considerations-for-startup-and-attach-loads"></a>Başlangıç için ortak ilgili önemli noktalar ve yükleri ekleme

**Profiler DLL'yi imzalama**

Windows, Profiler DLL'yi yüklemeye çalıştığında, Profiler DLL'yi doğru şekilde imzalandığını doğrular. Aksi durumda, varsayılan olarak yükleme başarısız olur. Bunu yapmak için iki yol vardır:

- Profiler DLL'niz açtığınızdan emin olun.

- Kullanıcı, bir geliştirici lisansı, Windows 8 makinesinde aracınızın kullanmadan önce yüklemeniz gerektiğini söyleyin. Bu, Visual Studio'dan veya bir komut isteminden el ile otomatik olarak yapılabilir. Daha fazla bilgi için [Geliştirici lisansı alma](https://docs.microsoft.com/previous-versions/windows/apps/hh974578(v=win.10)).

**Dosya sistemi izinleri**

Windows Store uygulaması yükleme ve hangi BT dosya sistemindeki bir konumdan, Profiler DLL'yi yürütme izni olmalıdır residesBy varsayılan, Windows Store app çoğu dizin ve başarısız girişimleri, Profiler DLL'yi böyle izni yok şuna benzer bir Windows uygulama olay günlüğündeki bir girişi oluşturacak:

```Output
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].
```

Genellikle, Windows Store apps yalnızca sınırlı sayıda disk üzerindeki konumlara erişmek için izin verilir. Her Windows Store uygulaması erişim izni verilen tüm Windows Store uygulamaları için dosya sistemindeki bazı alanların yanı sıra kendi uygulamaların veri klasörlerini erişebilirsiniz. Tüm Windows Store apps okudum ve varsayılan olarak bırakılma yürütmek için Profiler DLL dosyanızı ve bağımlılıklarını yere Program dosyaları veya Program dosyaları (x86), altında yüklemek en iyisidir.

### <a name="startup-load"></a>Başlangıç yükü

Genellikle, bir masaüstü uygulamasında Profiler kullanıcı Arabirimi, Profiler DLL'yi başlangıç yükü gerekli CLR API profil oluşturma ortam değişkenlerini içeren bir ortam bloğu başlatarak ister (yani, `COR_PROFILER`, `COR_ENABLE_PROFILING`, ve `COR_PROFILER_PATH`), ve ardından bu ortam bloğu ile yeni bir işlem oluşturuluyor. Aynı Windows Store uygulamaları için geçerlidir, ancak farklı bir mekanizmasıdır.

**Yükseltilmiş çalıştırma**

İşlem, Windows Store app işlem B, A işlem üretme girişiminde Orta bütünlük düzeyinde (yani değil yükseltilmiş olduğu gibi) yüksek bütünlük düzeyinde değil düzeyini çalıştırılmalıdır. Bu da Profiler UI Orta bütünlük düzeyinde çalışıyor olması veya Windows Store app başlatılmasını halletmeniz için Orta bütünlük düzeyinde başka bir masaüstü işlem üretme gerekir anlamına gelir.

**Bir Windows Store uygulaması için profil seçme**

İlk olarak, hangi Windows Store uygulamasını başlatmak için profil oluşturucu kullanıcıdan isteyebilirsiniz. Masaüstü uygulamaları için dosya göz atma iletişim belki de gösterebilir ve kullanıcı bulma ve bir .exe dosyası seçin. Ancak Windows Store apps farklı ve göz atma iletişim kutusunu kullanarak anlam ifade etmez. Bunun yerine, kullanıcı seçmek söz konusu kullanıcı için yüklenen Windows Store uygulamaların bir listesini göstermek iyidir.

Kullanabileceğiniz <xref:Windows.Management.Deployment.PackageManager> bu liste oluşturmak için sınıf. `PackageManager` Masaüstü uygulamaları için kullanılabilir bir Windows çalışma zamanı sınıf ve hatta ise *yalnızca* Masaüstü uygulamaları için kullanılabilir.

Aşağıdaki kod örneğinde kullanıcı arabiriminden bir kuramsal Profiler içinde bir masaüstü uygulaması olarak yazılan C# kullanan `PackageManager` Windows uygulamaların bir listesini oluşturmak için:

```csharp
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();
PackageManager packageManager = new PackageManager();
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);
```

**Özel ortam bloğunu belirtme**

Yeni bir COM arabirimi [IPackageDebugSettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings), bazı tanılama formları kolaylaştırmak için Windows Store app yürütme davranışını özelleştirmenizi sağlar. Bunun yöntemlerinden biri olan [EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), başlatıldığında, Windows Store uygulaması için bir ortam bloğuna geçirmenize olanak sağlar. otomatik işlemi askıya alma devre dışı bırakma gibi başka yararlı etkileri yanı sıra. Ortam değişkenlerini belirtme gerek duyduğunuz senaryolara olduğu için ortam bloğunu önemlidir (`COR_PROFILER`, `COR_ENABLE_PROFILING`, ve `COR_PROFILER_PATH)`), Profiler DLL'yi CLR tarafından kullanılır.

Aşağıdaki kod parçacığı göz önünde bulundurun:

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, debuggerCommandLine,
                                                                 (IntPtr)fixedEnvironmentPzz);
```

Birkaç öğeleri doğru hale getirmek için ihtiyacınız vardır:

- `packageFullName` paketleri yineleme yapma ve kapmasını belirlenebilir `package.Id.FullName`.

- `debuggerCommandLine` biraz daha ilginçtir. Windows Store uygulaması için özel bir ortam bloğuna geçirmek için kendi alıyormuş işlevsiz bir hata ayıklayıcı yazma gerekir. Windows spawns Windows Store app askıya ve ardından, hata ayıklayıcı bu örnekteki gibi bir komut satırı ile başlatarak, hata ayıklayıcı ekler:

    ```Output
    MyDummyDebugger.exe -p 1336 -tid 1424
    ```

     Burada `-p 1336` Windows Store app işlem kimliği 1336, sahip olduğu anlamına gelir ve `-tid 1424` askıya alınmış iş parçacığının iş parçacığı kimliği 1424 olduğu anlamına gelir. İşlevsiz, hata ayıklayıcı komut satırından ThreadID ayrıştırma, bu iş parçacığını devam ve çıkın.

     Bunu yapmak için C++ kodu bazı örnek aşağıda verilmiştir (hata denetimi eklediğinizden emin olun!):

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

     Tanılama Aracı yüklemenizin bir parçası bir işlevsiz bu hata ayıklayıcı dağıtıp daha sonra bu hata ayıklayıcıda yolunu belirtin ihtiyacınız `debuggerCommandLine` parametresi.

**Windows Store uygulaması başlatılıyor**

Son olarak, Windows Store uygulamasını başlatmak için şu geldi. Kendi başınıza yapmak'yı zaten denediyseniz, fark etmiş [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) nasıl, Windows Store app işlem oluşturacağı değil. Bunun yerine, kullanmanız gerekecektir [IApplicationActivationManager::ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication) yöntemi. Bunu yapmak için başlatma Windows Store uygulamasının uygulama kullanıcı Model Kimliğini almak gerekir. Ve küçük bir sorunda bildirimi aracılığıyla yapmanız gerekir anlamına gelir.

Paketlerinizi yineleme sırasında ("Seçme a Windows Store uygulaması için profili" bölümüne bakın [başlangıç yükü](#startup-load) bölümüne), geçerli paketin bildiriminde bulunan uygulamalar almak isteyebilirsiniz:

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

Evet, bir paket birden fazla uygulamaya sahip olabilir ve her uygulama, kendi uygulama kullanıcı modeli kimliği vardır. Bu nedenle, kullanıcıdan hangi uygulama profiline ve belirli uygulamadan uygulama kullanıcı modeli Kimliği almak istersiniz:

```csharp
while (appsEnum.GetHasCurrent() != 0)
{
    IAppxManifestApplication app = appsEnum.GetCurrent();
    string appUserModelId = app.GetAppUserModelId();
    //...
}
```

Son olarak, artık Windows Store uygulamasını başlatmak ihtiyacınız vardır:

```csharp
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);
```

**DisableDebugging çağrılacak unutmayın**

Aradığınız ne zaman [IPackageDebugSettings::EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), sonra kendiniz çağırarak temizlemek bir promise yapılan [IPackageDebugSettings::DisableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) yöntemi, böylece gerçekleştirdiğinizden emin olun Profil oluşturma oturumu olduğunda üzerinden.

### <a name="attach-load"></a>Yük ekleme

Profiler kullanıcı Arabirimi, Profiler DLL'yi çalıştıran zaten başlamış bir uygulamaya eklemek istediğinde kullandığı [Iclrprofiling::attachprofiler](iclrprofiling-attachprofiler-method.md). Aynı ile Windows Store uygulamaları geçerlidir. Ancak daha önce listelenen ortak düşünceler yanı sıra emin değil hedef Windows Store app askıya alındı.

**EnableDebugging**

Başlangıç yük gibi çağrı [IPackageDebugSettings::EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging) yöntemi. Bir ortam bloğuna geçirmek için gerekli değildir, ancak diğer yanlarından gerekir: otomatik işlemi askıya alma devre dışı bırakılıyor. Aksi takdirde, Profiler UI çağırdığında [AttachProfiler](iclrprofiling-attachprofiler-method.md), hedef Windows Store app askıya alınabilir. Aslında, kullanıcı artık Profiler kullanıcı Arabirimi ile etkileşim kurma ve Windows Store app herhangi bir kullanıcının ekran üzerinde etkin değilse, büyük olasılıkla budur. Uygulamanın askıya alındığından Windows Store, herhangi bir yanıt vermesi mümkün olmayacaktır, CLR için Profiler DLL iliştirilecek gönderdiğini sinyal.

Bu nedenle böyle bir şey isteyeceksiniz:

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, null /* debuggerCommandLine */,
                                                                 IntPtr.Zero /* environment */);
```

Bu, bir hata ayıklayıcı komut satırı veya bir ortam bloğuna belirtmeyin dışında başlangıç yükü çalışması için yapacağınız aynı çağrısıdır.

**DisableDebugging**

Her zaman olduğu gibi çağrılacak unutmayın [IPackageDebugSettings::DisableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) , profil oluşturma oturumu tamamlanmış olduğunda.

## <a name="running-inside-the-windows-store-app"></a>İçinde Windows Store uygulamasını çalıştırma

Bu nedenle Windows Store uygulaması son olarak, Profiler DLL'yi yükledi. Profiler DLL dosyanızı nasıl Windows Store uygulamaları tarafından gerekli farklı kuralları tarafından verilen gerekir artık API izin verilen olan ve çalıştırmak nasıl dahil olmak üzere izinleri azaltıldı.

### <a name="stick-to-the-windows-store-app-apis"></a>Windows Store app API'lerine takılıyor

Windows API gezindikçe, Masaüstü uygulamaları, Windows Store apps veya her ikisi de geçerli olduğu her API belgelenen fark edeceksiniz. Örneğin, **gereksinimleri** belgelerine bölümünü [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) işlevi işlevi yalnızca Masaüstü uygulamaları için geçerli olduğunu gösterir. Buna karşılık, [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex) işlev, Masaüstü uygulamaları ve Windows Store uygulamaları için kullanılabilir.

Profiler DLL'niz geliştirirken, bir Windows Store uygulaması ise olarak kabul et ve yalnızca Windows Store uygulamaları için kullanılabilir olarak belgelenen API'lerini kullanın. Bağımlılıklarınızı analiz (örneğin, çalıştırabileceğiniz `link /dump /imports` karşı denetlenip denetlenmeyeceğini, Profiler DLL'yi) ve bağımlılıklarınızı hangisinin Tamam ve hangi olmayan görmek için belgelere bakın. Çoğu durumda, yalnızca bunları güvenli olarak belgelenen API'sının daha yeni bir form değiştirerek, ihlaller düzeltilebilir (örneğin, değiştirme [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) ile [ InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)).

Profiler DLL'niz yalnızca Masaüstü uygulamaları için geçerli olan bazı API'lerini çağırır ve henüz bunlar bile Profiler DLL dosyanız içinde bir Windows Store uygulaması ne zaman yüklendi ortağımdan fark edebilirsiniz. Profiler Windows Store app işlem içine yüklenmiş DLL içinde Windows Store uygulamaları ile kullanmak için belgelenmemiş herhangi bir API'yi kullanmak için riskli olduğunu unutmayın:

- Bu API Windows Store uygulamaları çalıştırma içinde benzersiz bir bağlamda çağrıldığında çalışacak şekilde garanti edilmez.

- Bu API, farklı Windows Store app süreçlerinde çağrıldığında tutarlı bir şekilde çalışmayabilir.

- Bu API'leri geçerli sürümü, Windows, Windows Store uygulamalarında düzgün çalışabilmesi için görünebilir, ancak kesilebilir veya gelecekteki Windows sürümlerinde devre dışı.

Tüm ihlalleri düzeltin ve riskini önlemek için en iyi öneridir bakın.

Kesinlikle belirli bir API'yi yapamayacağınız ve yerini Windows Store uygulamaları için uygun bulunamıyor bulabilirsiniz. Böyle bir durumda, en az:

- Test, test, test yaşam daylights bu API kullanım dışı.

- API aniden sonu veya adlı kaybolmasına olduğunu anlamak gelen içinde Windows Store uygulamaları gelecekteki sürümleri Windows. Bu bir uyumluluk sorunu Microsoft tarafından kabul olmaz ve uygulamanızın kullanımını destekleyen bir öncelikli olmaz.

### <a name="reduced-permissions"></a>Sınırlı izinler

Windows Store app izinleri Masaüstü uygulamalarından farklı tüm yolları listelemek için bu konunun kapsamı dışında. Ancak Profiler (bir Windows Store uygulaması bir masaüstü uygulaması karşılaştırıldığında içine yüklendiğinde) DLL, herhangi bir kaynağa erişmeye kesinlikle davranışı farklı olacaktır. Dosya sistemi en yaygın bir örnektir. Vardır, ancak birkaç yerleştirir erişmek için izin verilen bir Windows Store uygulaması disk üzerinde (bkz [dosya erişim ve izinleri (Windows çalışma zamanı uygulamaları](https://docs.microsoft.com/previous-versions/windows/apps/hh967755(v=win.10))), ve altında aynı kısıtlamalara Profiler DLL dosyanız olur. Kodunuzu baştan sona test edin.

### <a name="inter-process-communication"></a>İşlemler arası iletişim

Bu yazıda başındaki diyagramda gösterildiği gibi (Windows Store app işlem alanına yüklenir), Profiler DLL'yi Profiler (ayrı bir masaüstü uygulaması işlem alanında çalışan) kullanıcı Arabirimi aracılığıyla kendi özel arası işlemi ile iletişim kurmak büyük olasılıkla gerekir kanal iletişimi (IPC). Profiler UI davranışını değiştirmek için Profiler DLL'yi sinyali gönderir ve sonradan işlemek ve profil oluşturucu kullanıcıya görüntülemek için Profiler UI dön Profiler DLL'yi verilerini analiz edilen Windows Store app gönderir.

Çoğu profil oluşturucular bu şekilde çalışmanız gerekiyor, ancak bir Windows Store app Profiler DLL dosyanız yüklendiğinde seçimlerinizi IPC mekanizmaları için daha sınırlıdır. Bunları kullanamazsınız için örneğin, adlandırılmış Windows Store app SDK'sı, bir parçası değildir.

Ancak Elbette, yine de barındırabilir daha sınırlı bir biçimde dosyalarıdır. Olayları de mevcuttur.

**Dosyaları iletişim kurma**

Verilerinizin en büyük olasılıkla Profiler DLL'yi ve Profiler UI arasında dosyaları geçer. Dosya konumu, Profiler DLL'yi (Windows Store uygulaması bağlamında) ve Profiler UI okuma ve yazma erişimi için kullanılan anahtardır. Örneğin, Profiler DLL'yi ve Profiler UI erişebileceği bir konuma geçici klasör yoludur, ancak başka bir Windows Store uygulama paketi (Bu nedenle diğer Windows Store app paketlerden oturumunuzu herhangi bir bilgi koruma) erişebilirsiniz.

Profiler UI ve Profiler DLL'yi bu yol bağımsız olarak belirleyebilirsiniz. Geçerli kullanıcı için yüklenen tüm paketleri gezinir olduğunda Profiler UI, (bkz: önceki örnek kodu) erişimi alır `PackageId` içinden geçici klasör yolu kodla bu kod parçacığına benzer sınıfından türetilen. (Her zaman hata denetimi uzatmamak için atlandı.)

```csharp
// C# code for the Profiler UI.
ApplicationData appData =
    ApplicationDataManager.CreateForPackageFamily(
        packageId.FamilyName);

tempDir = appData.TemporaryFolder.Path;
```

Bu arada, Profiler DLL'yi temelde aynı şeyi yapmak için alabilir ancak daha kolayca almak <xref:Windows.Storage.ApplicationData> sınıfı kullanarak [ApplicationData.Current](xref:Windows.Storage.ApplicationData.Current%2A) özelliği.

**Olayları üzerinden iletişim kurma**

Profiler UI ve Profiler DLL'yi arasında basit bir sinyal semantiği istiyorsanız, Windows Store uygulamaları ve bunun yanı sıra Masaüstü uygulamaları dahilindeki olayları kullanabilirsiniz.

Profiler DLL dosyanızı yalnızca çağırabilirsiniz [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa) istediğiniz herhangi bir adla adlandırılmış bir olay oluşturmak için işlevi. Örneğin:

```cpp
// Profiler DLL in Windows Store app (C++).
CreateEventEx(
    NULL,  // Not inherited
    "MyNamedEvent"
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */
    EVENT_ALL_ACCESS);
```

Profiler UI sonra Windows Store uygulamanın ad alanı altında adlandırılmış olay bulması gerekir. Örneğin, Profiler kullanıcı Arabirimi çağırabilir [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa), olay adı olarak belirtme

`AppContainerNamedObjects\<acSid>\MyNamedEvent`

`<acSid>` Windows Store uygulamanın AppContainer SID ' dir. Bu konunun önceki bir bölümde, geçerli kullanıcı için yüklü paketleri gezinilen nasıl oluşturulacağını gösterir. Bu örnek koddan PackageId elde edebilirsiniz. Ve PackageId alabilirsiniz `<acSid>` kodu aşağıdakine benzer:

```csharp
IntPtr acPSID;
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);

string acSid;
ConvertSidToStringSid(acPSID, out acSid);

string acDir;
GetAppContainerFolderPath(acSid, out acDir);
```

### <a name="no-shutdown-notifications"></a>Kapatma bildirim yok

Windows Store uygulaması içinde çalışırken, Profiler DLL'yi üzerinde doğrulamamalısınız [Icorprofilercallback::shutdown](icorprofilercallback-shutdown-method.md) ve hatta [DllMain](/windows/desktop/Dlls/dllmain) (ile `DLL_PROCESS_DETACH`), Profiler DLL'yi bildirmek için çağırılır Windows Store uygulaması, çıkılıyor. Aslında, hiçbir zaman çağrılacağı beklemelisiniz. Tarihsel olarak, disk, dosyaları kapatma, Profiler kullanıcı Arabirimi, vb. geri bildirim göndermek için veri önbelleklerini temizleme birçok Profiler DLL'leri bildirimlerin kullanışlı basamakla kullandınız. Ancak artık, Profiler DLL'yi biraz daha farklı düzenlenmesini gerekiyor.

Bu hizmet de gider, Profiler DLL'yi günlük bilgileri olmalıdır. Performans nedeniyle, bilgiler bellek, batch ve batch bazı eşik geçmiş boyutu büyüdükçe disk için temizleme isteyebilirsiniz. Ancak, henüz diske Temizlenen tüm bilgiler kaybolabilir varsayılır. Bu, eşiğine akıllıca çekme isteyebilirsiniz ve Profiler UI Profiler DLL tarafından yazılan eksik bilgi uğraşmanız sağlamlaştırılmış olması gerektiğini anlamına gelir.

## <a name="windows-runtime-metadata-files"></a>Windows çalışma zamanı meta veri dosyaları

Buna ayrıntıya gitmek için bu belgenin kapsamı dışında hangi Windows Runtime metadata (WinMD) dosyalar var. Bu bölümde, Profiler DLL'yi çözümleme Windows Store uygulaması tarafından WinMD dosyalar yüklendiğinde nasıl CLR Profil oluşturma API tepki verir sınırlıdır.

### <a name="managed-and-non-managed-winmds"></a>Yönetilen ve yönetilmeyen Winmd'lerin

Bir geliştirici, yeni bir Windows çalışma zamanı bileşeni projesi oluşturmak için Visual Studio kullanıyorsa, bu projenin bir derleme geliştirici tarafından yazılan meta veriler (tür tanımlarının sınıfları, arabirimleri, vb.) tanımlayan bir WinMD dosyası üretir. Bu projeyi C# veya VB ile yazılmış bir yönetilen dil projesiyse, aynı WinMD dosyası da bu türlerin (geliştiricinin kaynak kodundan derlenmiş IL içerdiği anlamına gelir) uygulamasını içerir. Bu tür dosyalar yönetilen WinMD dosyası bilinir. Windows çalışma zamanı meta verileri hem de temel uygulamayı içeren ilginç.

Buna karşılık, bir geliştirici için C++ Windows çalışma zamanı bileşeni projesi oluşturur, yalnızca meta veriler içeren bir WinMD dosyası projenin bir derleme oluşturur ve uygulama ayrı bir yerel DLL derlenir. Benzer şekilde, Windows SDK'yı teslim WinMD dosyası yalnızca meta veriler, Windows bir parçası olarak gönderilen ayrı yerel DLL'leri içine derlenmiş uygulama ile içerir.

Aşağıdaki bilgileri içeren meta veri ve uygulama hem yönetilen Winmd'lerin ve yalnızca meta veriler içeren yönetilmeyen Winmd'lerin için geçerlidir.

### <a name="winmd-files-look-like-clr-modules"></a>WinMD dosyası gibi CLR modülleri arayın

CLR ilgili olduğu kadar tüm WinMD dosyası modüllerdir. CLR Profil oluşturma API'si, bu nedenle Profiler WinMD dosyası yüklediğinizde DLL ve bunların Moduleıd'lerini, diğer yönetilen modülleri olduğu gibi aynı şekilde nelerdir söyler.

Profiler DLL'niz çağırarak WinMD dosyası diğer modüllerden ayırt [Icorprofilerınfo3::getmoduleınfo2](icorprofilerinfo3-getmoduleinfo2-method.md) yöntemi ve İnceleme `pdwModuleFlags` çıkış parametresi için [COR_PRF_MODULE_WINDOWS_ Çalışma zamanı](cor-prf-module-flags-enumeration.md) bayrağı. (Bir WinMD Moduleıd temsil eder ve yalnızca, ayarlanır.)

### <a name="reading-metadata-from-winmds"></a>Winmd'lerin meta verilerini okuma

Normal modüller gibi WinMD dosyası aracılığıyla okunabilir meta verileri içeren [meta veri API'leri](../../../../docs/framework/unmanaged-api/metadata/index.md). Ancak, yönetilen kodda program ve WinMD dosyası kullanan geliştiriciler daha doğal bir programlama deneyimi yaşayabilsin WinMD dosyaları okuduğunda CLR Windows çalışma zamanı türleri .NET Framework türleri ile eşleştirir. Bu eşlemeler bazı örnekler için bkz. [Windows Store uygulamaları için .NET Framework desteği ve Windows çalışma zamanı](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).

Bu nedenle API meta veri kullandığında, profil oluşturucu hangi görünümün alırsınız: ham Windows çalışma zamanı görünümü veya eşlenmiş bir .NET Framework Görünüm?  Yanıt: size kalmıştır.

Çağırdığınızda [Icorprofilerınfo::getmodulemetadata](icorprofilerinfo-getmodulemetadata-method.md) yöntemi gibi bir meta veri arabirimi almak için bir WinMD [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), ayarlamayı da seçebilirsiniz [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)içinde `dwOpenFlags` bu eşlemesini devre dışı bırakmak için parametre. Aksi takdirde, varsayılan olarak, eşleme etkinleştirilecektir. Genellikle, Profiler DLL'yi WinMD meta verileri (örneğin, tür adları) edinir dizeleri tanıdık ve profil oluşturucu kullanıcıya doğal görüntü bir profil oluşturucu etkin, eşleme tutar.

### <a name="modifying-metadata-from-winmds"></a>Winmd'lerin meta verileri değiştirme

Meta verilerde Winmd'lerin değiştirme desteklenmez. Çağırırsanız [Icorprofilerınfo::getmodulemetadata](icorprofilerinfo-getmodulemetadata-method.md) yöntemi için bir WinMD dosyası ve belirtin [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) içinde `dwOpenFlags` parametresi veya bir yazılabilir meta verileri arabirimi gibi sorun [ Imetadataemit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) başarısız olur. İçin kendi izleme (örneğin, AssemblyRefs veya yeni yöntemler eklemek için) desteklemek için meta verileri değiştirmek için gereken IL yeniden yazma profil Oluşturucular, belirli önem budur. İçin denetlemeniz gerekir böylece [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) ilk (önceki bölümde açıklandığı gibi) ve kaçının gibi modülleri yazılabilir meta veri arabirimleri için soran öğesinden.

### <a name="resolving-assembly-references-with-winmds"></a>Winmd'lerin ile derleme başvurularını çözümleme

El ile izleme veya türü İnceleme ile yardımcı olmak için meta veri başvurularını çözümlemek birçok profil oluşturucular gerekir. Bu profil Oluşturucular, bu başvuruları tamamen farklı bir şekilde standart derleme başvurularını daha çözümlenir çünkü nasıl CLR Winmd'lerin için işaret eden derleme başvurularını çözümler dikkat etmeniz gerekir.

## <a name="memory-profilers"></a>Bellek profil oluşturucuları

Yönetilen yığın ve çöp toplayıcı, bir Windows Store uygulaması ve bir masaüstü uygulaması tamamen farklı değildir. Ancak, profil oluşturucu yazarları farkında olmanız gereken bazı farklar vardır.

### <a name="forcegc-creates-a-managed-thread"></a>ForceGC yönetilen iş parçacığı oluşturur.

Bellek profili oluşturma yaparken, Profiler DLL'yi genellikle içinden çağırmak ayrı bir iş parçacığı oluşturur [ForceGC yöntemi](icorprofilerinfo-forcegc-method.md) yöntemi. Bu yeni bir şey değildir. Ancak ne şaşırtıcı olabilir yapılması Windows Store uygulaması içinde bir çöp toplama işlemi, yönetilen bir iş parçacığı, iş parçacığı dönüştürme, (örneğin, bir profil oluşturma API ThreadID bu iş parçacığı için oluşturulur).

Bu sonuçları anlamak için CLR Profil oluşturma API'si tarafından tanımlandığı şekilde zaman uyumlu ve zaman uyumsuz çağrılar arasındaki farkları anlamak önemlidir. Bu kavramı Windows Store uygulamalarında zaman uyumsuz çağrılar, çok farklı olduğunu unutmayın. Blog gönderisine bakın [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE sahibiz neden](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) daha fazla bilgi için.

İlgili noktadır çağrılara Profiler DLL'nin birinin uygulaması dışında yapılır olsa bile, Profil Oluşturucu tarafından oluşturulan iş parçacığı üzerinde yapılan çağrılar her zaman zaman uyumlu olarak kabul edilir [Icorprofilercallback](icorprofilercallback-interface.md) yöntemleri. En az kullanılan durum olması. CLR, çağrınız nedeniyle, yönetilen bir iş parçacığı profil oluşturucunun iş parçacığı etkinleştirdiyse göre [ForceGC yöntemi](icorprofilerinfo-forcegc-method.md), iş parçacığı, profil oluşturucunun iş parçacığı artık kabul edilir. Bu nedenle, CLR iş parçacığı için zaman uyumlu olarak niteliği taşır daha katı bir tanım uygular — yani çağrı kaynaklanan gerekir Profiler DLL'nin biri içinde [Icorprofilercallback](icorprofilercallback-interface.md) zaman uyumlu olarak nitelemek için yöntemleri.

Bu uygulamada ne demektir? Çoğu [Icorprofilerınfo](icorprofilerinfo-interface.md) yöntemleri yalnızca zaman uyumlu olarak çağrılması güvenlidir ve hemen Aksi takdirde başarısız olur. Profiler DLL dosyanızı yeniden kullanır, bu nedenle, [ForceGC yöntemi](icorprofilerinfo-forcegc-method.md) tipik profiler oluşturulan iş parçacığı üzerinde yapılan diğer çağrılar için iş parçacığı (örneğin, [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md), [Requestrejıt](icorprofilerinfo4-requestrejit-method.md), veya [RequestRevert](icorprofilerinfo4-requestrevert-method.md)), sorun yaşıyorsanız oluşturacağız. Hatta bir güvenli zaman uyumsuz işlev gibi [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) yönetilen iş parçacığı tarafından çağrıldığında özel kurallara sahiptir. (Blog gönderisine bakın [Profiler yığın: Temel bilgileri ve sonraki süreci desteleyen](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) daha fazla bilgi için.)

Bu nedenle, herhangi bir iş parçacığı oluşturur, Profiler DLL'yi çağrılacak öneririz [ForceGC yöntemi](icorprofilerinfo-forcegc-method.md) kullanılmalıdır *yalnızca* GC'ler tetikler ve ardından GC geri çağırmalarına yanıt amacıyla. Örnekleme veya ayırma yığını gibi diğer görevleri gerçekleştirmek için profil oluşturma API uygulamasına çağırmalıdır değil.

### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

.NET Framework 4.5 ile başlayarak, yeni bir GC geri çağırma vardır [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md), profil oluşturucu daha tamamlamak bilgi hakkında hangi verir *bağımlı tanıtıcıları*. Bu tanıtıcıları kaynak nesneden bir başvuru GC ömür yönetimi amacıyla hedef nesne etkili bir şekilde ekleyin. Bağımlı tanıtıcıları olan yeni bir şey ve yönetilen kodda program geliştiriciler kendi bağımlı tutamaçları kullanarak oluşturmak mümkün olduğu <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> Windows 8 ve .NET Framework 4.5 önce sınıfı.

Ancak, yönetilen XAML Windows Store uygulamaları artık bağımlı işler, yoğun kullanım olun. Özellikle, CLR yönetilen nesneleri ile yönetilmeyen Windows çalışma zamanı nesneleri arasındaki başvuru döngülerini yönetmeye yardımcı olmak için bunları kullanır. Bu, önemli artık bağımlı Bu işler böylece yığın grafik kenarları geri kalanıyla birlikte görselleştirilebilir bilgilenmek hiç olmadığı kadar bellek profil oluşturucular için olduğunu gösterir. Profiler DLL'niz kullanması gereken [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), ve [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) birlikte tam bir yığın grafik görünümünü oluşturmak için .

## <a name="conclusion"></a>Sonuç

Windows Store apps içinde çalışan yönetilen kodu analiz etmek için CLR Profil oluşturma API'ı kullanmak da mümkündür. Aslında, geliştirmekte olduğunuz mevcut bir profil oluşturucu alabilir ve böylece Windows Store uygulamaları hedefleyebilirsiniz belirli bazı değişiklikler yapın. Profiler kullanıcı Arabirimi, Windows Store app hata ayıklama modunda etkinleştirmek için yeni API'leri kullanmanız gerekir. Profiler DLL'niz yalnızca bu API'leri Windows Store uygulamaları için geçerli tükettiğini emin olun. Profiler DLL'yi ve Profiler UI arasındaki iletişim mekanizmasını tanıma Windows Store uygulamaları için yerinde kısıtlanmış izinler ile Windows Store app API kısıtlamaları göz önünde ile yazılması gerekir. Profiler DLL dosyanızı nasıl Winmd'lerin, CLR değerlendirir farkında olmalıdır ve ne göre yönetilen iş parçacıkları çöp toplayıcının davranışı farklıdır.

## <a name="resources"></a>Kaynaklar

**Ortak dil çalışma zamanı**

- [Profil oluşturma (yönetilmeyen API Başvurusu)](index.md)

- [Meta veri (yönetilmeyen API Başvurusu)](../metadata/index.md)

**Windows çalışma zamanı CLR'nin etkileşim**

- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

**Windows Store uygulamaları**

- [Dosya erişimi ve izinleri (Windows çalışma zamanı uygulamaları](https://docs.microsoft.com/previous-versions/windows/apps/hh967755%28v=win.10%29)

- [Geliştirici lisansı alma](https://docs.microsoft.com/previous-versions/windows/apps/hh974578%28v=win.10%29)

- [IPackageDebugSettings arabirimi](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)
