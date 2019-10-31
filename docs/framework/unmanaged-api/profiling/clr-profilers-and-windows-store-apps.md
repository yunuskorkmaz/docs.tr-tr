---
title: CLR Profil Oluşturucular ve Microsoft Store Uygulamaları
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
ms.openlocfilehash: da5942f9a2138a536d158f75a6977d20bf31b41c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140391"
---
# <a name="clr-profilers-and-windows-store-apps"></a>CLR Profil Oluşturucular ve Microsoft Store Uygulamaları

Bu konuda, bir Windows Mağazası uygulamasında çalışan yönetilen kodu çözümleyen tanılama araçlarını yazarken göz önünde bulundurmak için gerekenler açıklanmaktadır. Ayrıca, Windows Mağazası uygulamalarına karşı çalıştırdığınızda çalışmaya devam edebilmek için mevcut geliştirme araçlarınızı değiştirme yönergeleri de sağlar. Bu bilgileri anlamak için, ortak dil çalışma zamanı profili oluşturma API 'sine alışkın olmanız en iyisidir, bu API 'yi Windows masaüstü uygulamalarında doğru şekilde çalışan bir Tanılama aracında zaten kullanmışsanız ve artık aracı değiştirme ile ilgileniyor olabilirsiniz Windows Mağazası uygulamalarına karşı doğru şekilde çalıştırmak için.

## <a name="introduction"></a>Giriş

Bunu, giriş paragrafından daha fazla yaptıysanız, CLR profil oluşturma API 'sini öğreniyorsunuz demektir. Yönetilen masaüstü uygulamalarında iyi bir şekilde çalışacak bir tanılama aracı zaten yazmış oldunuz. Artık, aracınızdaki yönetilen bir Windows Mağazası uygulamasıyla çalışması için ne yapılacağını merak ediyorsunuz. Belki de bu işi yapmayı denediniz ve bu uygulamayı basit bir görev olmadığını keşfetti. Aslında, tüm araç geliştiricileri için belirgin olmayan bazı önemli noktalar vardır. Örneğin:

- Windows Mağazası uygulamaları, önemli ölçüde azaltılan izinlerle çalışır.

- Windows meta veri dosyalarının geleneksel yönetilen modüllerle karşılaştırıldığında benzersiz özellikleri vardır.

- Windows Mağazası uygulamaları, etkileşim azaldığında kendini askıya alma alışkanlığıyla sahiptir.

- İşlemler arası iletişim mekanizmalarda artık çeşitli nedenlerle çalışmamaya çalışmayabilir.

Bu konu, bilmeniz gereken şeyleri ve bunlarla nasıl doğru şekilde ilgilenmekte olduğunu listeler.

CLR profil oluşturma API 'SI için yeni başladıysanız daha iyi tanıtım bilgileri bulmak için bu konunun sonundaki kaynaklara atlayın.

Belirli Windows API 'Leri ve bunların nasıl kullanılması gerektiği hakkında ayrıntı sağlamak, bu konunun kapsamı dışındadır. Bu konuyu bir başlangıç noktası olarak değerlendirin ve burada başvurulan herhangi bir Windows API 'si hakkında daha fazla bilgi edinmek için MSDN 'ye başvurun.

## <a name="architecture-and-terminology"></a>Mimari ve terminoloji

Genellikle, bir tanılama aracı aşağıdaki çizimde gösterildiği gibi bir mimariye sahiptir. "Profil Oluşturucu" terimini kullanır, ancak bu birçok araç, tipik performans veya bellek profili oluşturma işleminin kod kapsamı, sahte nesne çerçeveleri, zaman gezme hata ayıklama, uygulama izleme vb. gibi alanlara göre daha iyi bir şekilde geçer. Kolaylık olması için bu konu, profil oluşturucular olarak tüm bu araçlara başvuralmaya devam edecektir.

Bu konu başlığı altında aşağıdaki terminoloji kullanılır:

**Uygulama**

Bu, profil oluşturucunun analiz olduğu uygulamadır. Genellikle, bu uygulamanın geliştiricisi uygulamayla ilgili sorunları tanılamaya yardımcı olması için profil oluşturucuyu kullanıyor. Geleneksel olarak, bu uygulama bir Windows masaüstü uygulaması olacaktır, ancak bu konu başlığında Windows Mağazası uygulamaları ' na bakıyoruz.

**Profil oluşturucu DLL 'SI**

Bu, çözümlenmekte olan uygulamanın işlem alanına yüklenen bileşendir. Profiler "Agent" olarak da bilinen bu bileşen [ICorProfilerCallback](icorprofilercallback-interface.md)[ICorProfilerCallback arabirimi](icorprofilercallback-interface.md)(2, 3, vb.) arabirimlerini uygular ve ile Ilgili verileri toplamak Için [ICorProfilerInfo](icorprofilerinfo-interface.md)(2, 3, vb.) arabirimlerini kullanır. analiz edilen uygulama ve potansiyel olarak uygulamanın davranışının özellikleri.

**Profiler kullanıcı arabirimi**

Bu, profil oluşturucu kullanıcısının etkileşimde bulunduğu bir masaüstü uygulamasıdır. Uygulama durumunun kullanıcıya gösterilmesi ve kullanıcıya analiz edilen uygulamanın davranışını denetleme olanağı verilmesi sorumludur. Bu bileşen, profili oluşturulan uygulamanın işlem alanından ayrı olarak kendi işlem alanında çalışır. Profil Oluşturucu kullanıcı arabirimi, analiz edilen uygulamanın profil oluşturucu DLL 'nin başlangıçta yüklenmediği durumlarda profil oluşturucu DLL 'sini yüklemesine yol açmak için [ıclrprofile:: AttachProfiler](iclrprofiling-attachprofiler-method.md) yöntemini çağıran işlem olan "Ekle tetikleyicisi" olarak da davranabilir.

> [!IMPORTANT]
> Profil Oluşturucu kullanıcı arabiriminize bir Windows Mağazası uygulamasını denetlemek ve rapor etmek için kullanıldığında bile bir Windows masaüstü uygulaması kalmalıdır. Tanılama aracınızı Windows Mağazası 'nda paketleyebilve sunamayacak kadar beklememeniz beklenmemektedir. Araclarınızın Windows Mağazası uygulamalarının yapamadığını ve bu nesnelerin birçoğu Profiler Kullanıcı arabiriminizdeki gibi şeyler yapması gerekir.

Bu belge boyunca örnek kod şunları varsayar:

- Profil oluşturucu DLL 'niz, CLR C++PROFIL oluşturma API 'sinin gereksinimlerine göre yerel bir dll olması gerektiğinden ' de yazılır.

- Profil Oluşturucu kullanıcı arabiriminize yazılır C#. Bu gerekli değildir, ancak bu gerekli değildir, ancak profil Oluşturucu kullanıcı arabirimine yönelik dilde bir gereksinim olmadığından, neden kısa ve basit bir dil seçmemelidir?

### <a name="windows-rt-devices"></a>Windows RT cihazları

Windows RT cihazları oldukça kilitlidir. Üçüncü taraf profil oluşturucular yalnızca bu cihazlara yüklenemez. Bu belge Windows 8 bilgisayarlara odaklanır.

## <a name="consuming-windows-runtime-apis"></a>Windows Çalışma Zamanı API 'Leri kullanma

Aşağıdaki bölümlerde ele alınan çeşitli senaryolarda, Profil Oluşturucu kullanıcı arabirimi masaüstü uygulamanızın bazı yeni Windows Çalışma Zamanı API 'Leri kullanması gerekir. Masaüstü uygulamalarından hangi Windows Çalışma Zamanı API 'Lerinin kullanılabileceğini ve bunların Masaüstü uygulamalarından ve Windows Mağazası uygulamalarından çağrıldığında farklı olup olmadığını anlamak için belgelere danışmak isteyeceksiniz.

Profil Oluşturucu kullanıcı arabiriminizi yönetilen kodda yazılmışsa, bu Windows Çalışma Zamanı API 'Leri kullanmayı kolaylaştırmak için yapmanız gereken birkaç adım olacaktır. Daha fazla bilgi için bkz. [yönetilen masaüstü uygulamaları ve Windows çalışma zamanı](https://go.microsoft.com/fwlink/?LinkID=271858) makalesi.

## <a name="loading-the-profiler-dll"></a>Profil oluşturucu DLL yükleniyor

Bu bölümde, Profil Oluşturucu kullanıcı arabiriminin Windows Mağazası uygulamasının profil oluşturucu DLL 'nizi yüklemesine neden olduğu açıklanır. Bu bölümde açıklanan kod Profiler kullanıcı arabirimi masaüstü uygulamanıza aittir ve bu nedenle, masaüstü uygulamaları için güvenli olan ancak Windows Mağazası uygulamaları için güvenli olan Windows API 'Lerini kullanmayı içerir.

Profil Oluşturucu kullanıcı arabiriminizi, profil oluşturucu DLL 'nizin uygulamanın işlem alanına iki şekilde yüklenmesine neden olabilir:

- Uygulama başlangıcında, ortam değişkenleri tarafından denetlenen şekilde.

- Başlangıç tamamlandıktan sonra, [ıclrprofile:: AttachProfiler](iclrprofiling-attachprofiler-method.md) yöntemini çağırarak uygulamaya ekleme.

İlk yol bloklarınızdan biri, Windows Mağazası uygulamalarıyla düzgün şekilde çalışması için profil oluşturucu DLL 'nizin başlangıç yükleme ve iliştirme yüküne sahip olur. Her iki yükleme biçimi de ortak olarak bazı özel konuları paylaşır, bu nedenle bunlarla başlayalım.

### <a name="common-considerations-for-startup-and-attach-loads"></a>Başlangıç ve iliştirme yükleri için genel hususlar

**Profil oluşturucu DLL 'nizi imzalama**

Windows profil oluşturucu DLL 'nizi yüklemeyi denediğinde, profil oluşturucu DLL 'nizin düzgün şekilde imzalandığını doğrular. Aksi takdirde, yükleme varsayılan olarak başarısız olur. Bunu yapmak için iki yol vardır:

- Profil oluşturucu DLL 'nizin imzalandığından emin olun.

- Aracınızı kullanmadan önce, Windows 8 makinesine bir geliştirici lisansı yüklemeleri gerektiğini kullanıcıya söyleyin. Bu, otomatik olarak Visual Studio 'dan veya bir komut isteminden el ile yapılabilir. Daha fazla bilgi için bkz. [Geliştirici lisansı edinme](https://docs.microsoft.com/previous-versions/windows/apps/hh974578(v=win.10)).

**Dosya sistemi izinleri**

Windows Mağazası uygulamasının profil oluşturucu DLL 'nizi, varsayılan olarak yer aldığı dosya sistemindeki konumdan yükleme ve yürütme izni olması gerekir. Windows Mağazası uygulaması, çoğu dizinde bu izne sahip değildir ve profil oluşturucu DLL 'nizi yükleme girişimi başarısız olur Windows uygulaması olay günlüğünde şuna benzer bir giriş oluşturacak:

```output
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].
```

Genellikle, Windows Mağazası uygulamalarının diskte yalnızca sınırlı bir konum kümesine erişmesine izin verilir. Her Windows Mağazası uygulaması, kendi uygulama veri klasörlerine ve dosya sisteminde tüm Windows Mağazası uygulamalarına erişim izni verilen diğer diğer alanlara erişebilir. Tüm Windows Mağazası uygulamalarının varsayılan olarak burada okuma ve yürütme izinlerine sahip olduğu için profil oluşturucu DLL 'nizi ve bağımlılıklarını Program Files veya Program Files (x86) altında bir yere yüklemek en iyisidir.

### <a name="startup-load"></a>Başlangıç yükü

Genellikle, bir masaüstü uygulamasında, profil oluşturucu UI, gerekli CLR profil oluşturma API 'SI ortam değişkenlerini (örneğin, `COR_PROFILER`, `COR_ENABLE_PROFILING`ve `COR_PROFILER_PATH`) içeren bir ortam bloğu başlatarak profil oluşturucu DLL 'nizin başlangıç yüküne sorar ve sonra yeni bir Bu ortam bloğuyla işleme. Aynı durum Windows Mağazası uygulamaları için de geçerlidir, ancak mekanizmalar farklıdır.

**Yükseltilmiş ayrıcalıklarla çalıştırma**

Windows Mağazası uygulama Işlemi B 'yi oluşturma girişimlerini işsek, A Işleminin yüksek bütünlük düzeyinde (yükseltilmiş olmayan) değil, Orta bütünlük düzeyinde çalıştırılması gerekir. Yani, profil oluşturucu Kullanıcı arabiriminiz Orta bütünlük düzeyinde çalışıyor olmalıdır veya Windows Mağazası uygulamasını başlatmak için orta düzeyde bütünlük düzeyinde başka bir masaüstü işlemi oluşturulmalıdır.

**Profil için bir Windows Mağazası uygulaması seçme**

İlk olarak, Profil Oluşturucu kullanıcı tarafından hangi Windows Mağazası uygulamasının başlatılmasını istemeniz gerekir. Masaüstü uygulamaları için, belki de bir dosya tarama iletişim kutusu gösterebilirsiniz ve Kullanıcı bir. exe dosyası bulup seçer. Ancak Windows Mağazası uygulamaları farklıdır ve bir tarama iletişim kutusu kullanmak anlamlı değildir. Bunun yerine, kullanıcıya, bu kullanıcı tarafından seçilecek Windows Mağazası uygulamalarının bir listesini göstermek daha iyidir.

Bu listeyi oluşturmak için <xref:Windows.Management.Deployment.PackageManager> sınıfını kullanabilirsiniz. `PackageManager`, masaüstü uygulamaları tarafından kullanılabilen bir Windows Çalışma Zamanı sınıftır ve aslında *yalnızca* masaüstü uygulamalarında kullanılabilir.

İçinde C# bir masaüstü uygulaması olarak yazılmış bir kuramsal profil Oluşturucu kullanıcı arabiriminden aşağıdaki kod örneği, Windows uygulamalarının bir listesini oluşturmak için `PackageManager` kullanır:

```csharp
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();
PackageManager packageManager = new PackageManager();
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);
```

**Özel ortam bloğunu belirtme**

Yeni bir COM arabirimi olan [ıpackagedebugsettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings), bazı tanılama biçimlerinin daha kolay olması Için bir Windows Mağazası uygulamasının yürütme davranışını özelleştirmenize olanak sağlar. Yöntemlerinden biri olan [Enabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), bir ortam bloğunu başlatıldığında Windows Mağazası uygulamasına, otomatik işlem askıya alma devre dışı bırakma gibi diğer yararlı etkilerle geçişlerinizi yapmanızı sağlar. Ortam bloğu, profil oluşturucu DLL 'nizi yüklemek için CLR tarafından kullanılan ortam değişkenlerini (`COR_PROFILER`, `COR_ENABLE_PROFILING`ve `COR_PROFILER_PATH)`) belirtmeniz gerektiği için önemlidir.

Aşağıdaki kod parçacığını göz önünde bulundurun:

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, debuggerCommandLine,
                                                                 (IntPtr)fixedEnvironmentPzz);
```

Sağ almanız gereken birkaç öğe vardır:

- `packageFullName`, paketler üzerinde yineleirken ve yakalayıp `package.Id.FullName` olarak belirlenebilir.

- `debuggerCommandLine` biraz daha ilginç. Özel ortam bloğunu Windows Mağazası uygulamasına geçirmek için, kendi uyarlaması kukla hata ayıklayıcıyı yazmanız gerekir. Windows Mağazası uygulaması askıya alındı ve bu örnekte olduğu gibi bir komut satırı ile hata ayıklayıcıyı başlatarak hata ayıklayıcıyı iliştirir:

    ```console
    MyDummyDebugger.exe -p 1336 -tid 1424
    ```

     `-p 1336`, Windows Mağazası uygulamasının 1336 Işlem KIMLIĞI olduğu ve `-tid 1424` olduğu anlamına gelir. Iş parçacığı KIMLIĞI 1424, askıya alınan iş parçacığıdır. Kukla hata ayıklayıcı, komut satırından ThreadID öğesini ayrıştırır, bu iş parçacığını sürdürür ve sonra çıkın.

     Bunu yapmak için örnek C++ kod aşağıda verilmiştir (hata denetimi eklediğinizden emin olun!):

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

     Bu kukla hata ayıklayıcıyı Tanılama Aracı yüklemenizin bir parçası olarak dağıtmanız ve ardından `debuggerCommandLine` parametresinde bu hata ayıklayıcının yolunu belirtmeniz gerekir.

**Windows Mağazası uygulamasını başlatma**

Windows Mağazası uygulamasını başlatma sırasında son olarak geldi. Bunu kendiniz yapmadıysanız, [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) 'In bir Windows Mağazası uygulama işlemi oluşturma işleminin nasıl yapıldığını fark etmiş olabilirsiniz. Bunun yerine, [ıapplicationactivationmanager:: ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication) metodunu kullanmanız gerekir. Bunu yapmak için, başladığınızı Windows Mağazası uygulamasının uygulama kullanıcı modeli KIMLIĞINI almanız gerekir. Diğer bir deyişle, bildirim aracılığıyla biraz fikir yapmanız gerekir.

Paketleriniz üzerinden yineleme yaparken (önceki [başlangıç yükleme](#startup-load) bölümünde yer alan "profile Için bir Windows Mağazası uygulaması seçme" bölümüne bakın), geçerli paketin bildiriminde bulunan uygulamalar kümesini almak isteyeceksiniz:

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

Evet, bir pakette birden fazla uygulama olabilir ve her uygulamanın kendi uygulama kullanıcı modeli KIMLIĞI vardır. Bu nedenle, kullanıcıdan hangi uygulamanın profilini oluşturmasını ve bu uygulamadan uygulama kullanıcı modeli KIMLIĞINI elde etmesini istemeniz gerekir:

```csharp
while (appsEnum.GetHasCurrent() != 0)
{
    IAppxManifestApplication app = appsEnum.GetCurrent();
    string appUserModelId = app.GetAppUserModelId();
    //...
}
```

Son olarak, artık Windows Mağazası uygulamasını başlatmanız gerekenler vardır:

```csharp
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);
```

**DisableDebugging öğesini çağırmayı unutmayın**

[Ipackagedebugsettings:: EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging)öğesini çağırdığınızda, [ıpackagedebugsettings::D isabledebug](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) metodunu çağırarak, sizin tarafınızdan daha sonra temizleyebilmenizi sağlayacak bir Promise yaptınız. bu nedenle, profil oluşturma oturumu üzerindeyken bunu yaptığınızdan emin olun.

### <a name="attach-load"></a>Yük Ekle

Profil Oluşturucu kullanıcı arabirimi, profil oluşturucu DLL 'sini zaten çalışmaya başlamış olan bir uygulamaya iliştirmek istediğinde, [ıclrprofile:: AttachProfiler](iclrprofiling-attachprofiler-method.md)kullanır. Aynı durum Windows Mağazası uygulamalarıyla doğru bir şekilde geçerlidir. Ancak daha önce listelenen yaygın noktalara ek olarak, hedef Windows Mağazası uygulamasının askıya alınmadığından emin olun.

**EnableDebugging**

Başlangıç yüklerinde olduğu gibi, [ıpackagedebugsettings:: EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging) metodunu çağırın. Ortam bloğunu geçirmek için ihtiyacınız yoktur, ancak diğer özelliklerinden birine ihtiyacınız vardır: otomatik işlem askıya alma devre dışı bırakılıyor. Aksi takdirde, Profil Oluşturucu kullanıcı arabiriminizi [AttachProfiler](iclrprofiling-attachprofiler-method.md)' ı çağırdığında, hedef Windows Mağazası uygulaması askıya alınabilir. Aslında, bu durum büyük olasılıkla Kullanıcı Profil Oluşturucu kullanıcı ARABIRIMINIZE etkileşim kurmasından ve Windows Mağazası uygulamasının Kullanıcı ekranlarından hiçbirinde etkin olmaması olasıdır. Windows Mağazası uygulaması askıya alınırsa, bu, CLR 'nin profil oluşturucu DLL 'nizi eklemek için gönderdiği hiçbir sinyaline yanıt veremeyecektir.

Bu nedenle, şöyle bir şey yapmak isteyeceksiniz:

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, null /* debuggerCommandLine */,
                                                                 IntPtr.Zero /* environment */);
```

Bu, bir hata ayıklayıcı komut satırı veya ortam bloğu belirtmemenizi hariç, başlangıç yükü durumu için yaptığınız çağrıdır.

**DisableDebugging**

Her zaman olduğu gibi, profil oluşturma oturumunuz tamamlandığında [ıpackagedebugsettings::D isableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) ' i çağırmayı unutmayın.

## <a name="running-inside-the-windows-store-app"></a>Windows Mağazası uygulaması içinde çalışıyor

Bu nedenle, Windows Mağazası uygulaması son olarak profil oluşturucu DLL 'nizi yükledi. Artık profil oluşturucu DLL 'niz, hangi API 'Lerin izin verilebileceği ve daha düşük izinlerle çalıştırılması dahil olmak üzere Windows Mağazası uygulamaları için gereken farklı kurallara göre nasıl oynatılacağını taöğretmelidir.

### <a name="stick-to-the-windows-store-app-apis"></a>Windows Mağazası uygulaması API 'Lerine çubuk

Windows API 'sine göz atarken, her API 'nin masaüstü uygulamaları, Windows Mağazası uygulamaları veya her ikisi için de geçerli olduğunu fark edeceksiniz. Örneğin, [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) Işlevi belgelerinin **gereksinimler** bölümü, işlevin yalnızca masaüstü uygulamaları için geçerli olduğunu gösterir. Buna karşılık, [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex) işlevi hem masaüstü uygulamaları hem de Windows Mağazası uygulamaları için kullanılabilir.

Profil oluşturucu DLL 'nizi geliştirirken, bunu bir Windows Mağazası uygulaması gibi değerlendirin ve yalnızca Windows Mağazası uygulamaları için kullanılabilir olarak belgelenen API 'Leri kullanın. Bağımlılıklarınızı çözümleyin (örneğin, profil oluşturucu DLL 'niz denetlemek için `link /dump /imports` ' ı çalıştırabilir) ve sonra bağımlılıklarınızın hangilerinin tamam olduğunu ve ne olmadığını görmek için docs ' ı arayın. Çoğu durumda, ihlal, güvenli olarak belgelenen API 'nin daha yeni bir biçimiyle değiştirilerek (örneğin, [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) , [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)ile değiştiriliyor) düzeltilebilir.

Profil oluşturucu DLL 'nizin yalnızca masaüstü uygulamaları için uygulanan bazı API 'Leri çağırırsa ve profil oluşturucu DLL 'niz bir Windows Mağazası uygulaması içine yüklendiğinde bile çalışmaya çalışabileceğini fark edebilirsiniz. Bir Windows Mağazası uygulama işlemine yüklendiğinde profil oluşturucu DLL 'inizdeki Windows Mağazası uygulamalarıyla birlikte kullanılmak üzere belgelenmemiş API kullanmanın riskli olduğunu unutmayın:

- Bu tür API 'Ler, Windows Mağazası uygulamalarının çalıştığı benzersiz bağlamda çağrıldığında çalışır.

- Bu tür API 'Ler, farklı Windows Mağazası uygulama işlemlerinin içinden çağrıldığında tutarlı bir şekilde çalışmayabilir.

- Bu tür API 'Ler Windows Mağazası uygulamalarından geçerli Windows sürümündeki bir şekilde çalışıyor olabilir, ancak sonraki Windows sürümlerinde kesilebilir veya devre dışı bırakılabilir.

En iyi öneri, tüm ihlallerinizi düzeltemedi ve riskten kaçınmaktır.

Belirli bir API olmadan kesinlikle yapamayacağına ve Windows Mağazası uygulamaları için uygun bir değiştirme bulamamaya yönelik olduğunu fark edebilirsiniz. Böyle bir durumda, en az:

- Test, test edin, bu API kullanımınızın kullanımını test edin ve test edin.

- Windows 'un gelecek sürümlerinde Windows Mağazası uygulamaları içinden çağrılırsa, API 'nin aniden kesilebilir veya kaybolabileceğini anlayın. Bu, Microsoft tarafından uyumluluk sorunu olarak kabul edilmez ve kullanımınızı desteklemek bir öncelik vermez.

### <a name="reduced-permissions"></a>Azaltılan izinler

Windows Mağazası uygulama izinlerinin Masaüstü uygulamalarından farklı olduğu tüm yolları listelemek için bu konunun kapsamı dışındadır. Ancak, profil oluşturucu DLL 'niz (bir masaüstü uygulamasına kıyasla bir Windows Mağazası uygulamasına yüklendiğinde) her türlü kaynağa erişmeye çalıştığında, kesinlikle davranış farklı olur. Dosya sistemi en yaygın örnektir. Diskte belirli bir Windows Mağazası uygulamasının erişmesine izin verilen birkaç yer vardır (bkz. [dosya erişimi ve izinleri (Windows çalışma zamanı uygulamalar](https://docs.microsoft.com/previous-versions/windows/apps/hh967755(v=win.10))) ve PROFIL Oluşturucu dll 'niz aynı kısıtlamalar altında olacaktır. Kodunuzu iyice test edin.

### <a name="inter-process-communication"></a>İşlem arası iletişim

Bu kağıdın başındaki diyagramda gösterildiği gibi, profil oluşturucu DLL 'nizin (Windows Mağazası uygulaması işlem alanına yüklenir), kendi özel işlem sürecinize göre profil oluşturucu Kullanıcı arabiriminize (ayrı bir masaüstü uygulaması işlem alanında çalışan) iletişim kurması gerekir iletişim (IPC) kanalı. Profiler kullanıcı ARABIRIMI davranışını değiştirmek için, profil oluşturucu DLL 'sine sinyal gönderir ve profil oluşturucu DLL, çözümlenmiş Windows Mağazası uygulamasından verileri, işleme sonrası ve profil oluşturucu kullanıcısına görüntüleme için Profil Oluşturucu kullanıcı ARABIRIMINE geri gönderir.

Çoğu profil oluşturucular bu şekilde çalışması gerekir, ancak profil oluşturucu DLL 'niz bir Windows Mağazası uygulamasına yüklendiğinde IPC mekanizmalarına yönelik seçimleriniz daha sınırlı olur. Örneğin, adlandırılmış kanallar Windows Mağazası uygulama SDK 'sının bir parçası değildir, bu nedenle bunları kullanamazsınız.

Ancak, dosyalar hala yerinde, daha sınırlı bir biçimde albederdir. Olaylar da kullanılabilir.

**Dosyalar üzerinden iletişim kurma**

Verilerinizin büyük olasılıkla profil oluşturucu DLL ve Profil Oluşturucu kullanıcı arabirimi arasında dosyalar aracılığıyla geçiş yapılır. Anahtar profil oluşturucu DLL 'nizin (bir Windows Mağazası uygulaması bağlamında) ve Profil Oluşturucu kullanıcı arabiriminin okuma ve yazma erişimine sahip olduğu bir dosya konumu seçmeniz gerekir. Örneğin, geçici klasör yolu, hem profil oluşturucu DLL 'SI hem de profil oluşturucu Kullanıcı arabirimlerinizin erişebileceği, ancak başka bir Windows Mağazası uygulama paketinin erişebileceği bir konumdur (Bu nedenle, diğer Windows Mağazası uygulama paketlerinden oturum açmak için tüm bilgileri koruma).

Profil Oluşturucu UI ve Profiler DLL 'niz bu yolu bağımsız olarak belirleyebilir. Profil Oluşturucu kullanıcı arabiriminize, geçerli kullanıcı için yüklenen tüm paketler arasında yineleme yapıldığında (daha önce örnek koda bakın), geçici klasör yolunun bu kod parçacığına benzer kodla türetilebilecek `PackageId` sınıfına erişimi alır. (Her zaman olduğu gibi, kısaltma için hata denetimi atlanır.)

```csharp
// C# code for the Profiler UI.
ApplicationData appData =
    ApplicationDataManager.CreateForPackageFamily(
        packageId.FamilyName);

tempDir = appData.TemporaryFolder.Path;
```

Bu arada, profil oluşturucu DLL 'niz temelde aynı şeyi yapabilir, ancak [ApplicationData. Current](xref:Windows.Storage.ApplicationData.Current%2A) özelliğini kullanarak <xref:Windows.Storage.ApplicationData> sınıfına daha kolay bir şekilde erişebilir.

**Olaylar üzerinden iletişim kurma**

Profil Oluşturucu UI ve profil oluşturucu DLL arasında basit sinyal semantiğini istiyorsanız, Windows Mağazası uygulamalarının içindeki olayları ve masaüstü uygulamalarını kullanabilirsiniz.

Profil oluşturucu DLL 'nizden, istediğiniz adla adlandırılmış bir olay oluşturmak için [Createeventex](/windows/desktop/api/synchapi/nf-synchapi-createeventexa) işlevini çağırmanız yeterlidir. Örneğin:

```cpp
// Profiler DLL in Windows Store app (C++).
CreateEventEx(
    NULL,  // Not inherited
    "MyNamedEvent"
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */
    EVENT_ALL_ACCESS);
```

Profil Oluşturucu kullanıcı arabiriminizdeki bu adlandırılmış olayı Windows Mağazası uygulamasının ad alanı altında bulması gerekir. Örneğin, Profil Oluşturucu kullanıcı arabiriminizi [Createeventex](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)ile çağırabilir ve olay adını şöyle belirterek

`AppContainerNamedObjects\<acSid>\MyNamedEvent`

`<acSid>`, Windows Mağazası uygulamasının AppContainer SID 'sidir. Bu konunun önceki bir bölümünde, geçerli kullanıcı için yüklenmiş paketlerin nasıl yineleneceği gösterilmektedir. Bu örnek koddan PackageID ' yi elde edebilirsiniz. PackageID 'den, `<acSid>` ' ı aşağıdakine benzer kodla elde edebilirsiniz:

```csharp
IntPtr acPSID;
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);

string acSid;
ConvertSidToStringSid(acPSID, out acSid);

string acDir;
GetAppContainerFolderPath(acSid, out acDir);
```

### <a name="no-shutdown-notifications"></a>Kapanmaya yönelik bildirim yok

Bir Windows Mağazası uygulamasında çalışırken, profil oluşturucu DLL 'niz, Windows Mağazası uygulamasının çıkış yaptığını Profiler DLL 'nize bildirmek için [ICorProfilerCallback:: kapatılmasını](icorprofilercallback-shutdown-method.md) veya hatta [DllMain](/windows/desktop/Dlls/dllmain) (`DLL_PROCESS_DETACH`ile) ' i kullanmamalıdır. Aslında, bunların hiçbir şekilde çağrılmayacağını beklemelisiniz. Tarihsel olarak, birçok profil oluşturucu DLL bu bildirimleri diske boşaltma, dosyaları kapatma, Profil Oluşturucu kullanıcı arabirimine geri bildirim gönderme gibi uygun şekilde kullandı. Ancak artık profil oluşturucu DLL 'nizin biraz farklı şekilde organize olması gerekir.

Profil oluşturucu DLL 'niz, devam eden bilgileri günlüğe kaydetmeye devam etmelidir. Performans nedenleriyle, toplu iş bilgilerini bellekte toplu olarak, bir eşiğin geçmiş olduğu sürece diskte da diske boşaltmayı tercih edebilirsiniz. Ancak diske henüz boşaltılmayan bilgilerin kaybolameyeceğini varsayın. Bu, eşiği daha seyrek olarak seçmek ve Profiler 'ın Profiler 'ın, profil oluşturucu DLL tarafından yazılmış tamamlanmamış bilgilerle başa çıkmak için sağlamlaştırması gerektiğini gösterir.

## <a name="windows-runtime-metadata-files"></a>Windows Çalışma Zamanı meta veri dosyaları

Windows Çalışma Zamanı meta veri (WinMD) dosyalarının ne olduğu hakkında ayrıntılı bilgi almak için bu belgenin kapsamı dışındadır. Bu bölüm CLR profil oluşturma API 'sinin, WinMD dosyaları Windows Mağazası uygulaması tarafından, profil oluşturucu DLL 'nizin analiz edilirken yeniden nasıl davranması ile sınırlıdır.

### <a name="managed-and-non-managed-winmds"></a>Yönetilen ve yönetilmeyen Wınmds

Bir geliştirici yeni bir Windows Çalışma Zamanı bileşen projesi oluşturmak için Visual Studio kullanıyorsa, bu projenin bir derlemesi, geliştirici tarafından yazılan meta verileri (sınıfların tür açıklamaları, arabirimler vb.) açıklayan bir WinMD dosyası üretir. Bu proje, C# veya vb dilinde yazılmış bir yönetilen dil projem Ise aynı winmd dosyası bu türlerin uygulamasını da içerir (yani, geliştiricinin kaynak kodundan derlenen tüm Il 'yi içerir). Bu tür dosyalar yönetilen WinMD dosyaları olarak bilinir. Windows Çalışma Zamanı meta verileri ve temel alınan uygulamayı içerdikleri her ikisi de ilginç hale getiriyoruz.

Buna karşılık, bir geliştirici için C++Windows çalışma zamanı bileşen projesi oluşturursa, söz konusu projenin derlemesi yalnızca meta verileri Içeren bir WinMD dosyası üretir ve uygulama ayrı bır yerel dll 'de derlenir. Benzer şekilde, Windows SDK teslim eden WinMD dosyaları, Windows 'un bir parçası olarak gelen ayrı yerel dll 'Lere derlenen uygulamayla yalnızca meta veriler içerir.

Aşağıdaki bilgiler, meta veri ve uygulama içeren hem yönetilen WinMDs için hem de yalnızca meta verileri içeren yönetilmeyen Wınmds için geçerlidir.

### <a name="winmd-files-look-like-clr-modules"></a>WinMD dosyaları CLR modülleri gibi görünüyor

CLR 'nin düşünüldüğünde, tüm WinMD dosyaları modüllerdir. Bu nedenle, CLR profil oluşturma API 'si, WinMD dosyaları yüklenirken profil oluşturucu DLL 'nize ve moduleIds oldukları diğer yönetilen modüllerle aynı şekilde bildirir.

Profil oluşturucu DLL 'niz, [ICorProfilerInfo3:: GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md) yöntemini çağırarak ve [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) bayrağı için `pdwModuleFlags` output parametresini inceleyerek winmd dosyalarını diğer modüllerden ayırt edebilir. (Ve yalnızca ModuleID bir WinMD temsil ediyorsa ayarlanır.)

### <a name="reading-metadata-from-winmds"></a>Wınmds 'den meta veriler okunuyor

Normal modüller gibi WinMD dosyaları, [meta veri API 'leri](../../../../docs/framework/unmanaged-api/metadata/index.md)aracılığıyla okunabilecek meta veriler içerir. Ancak, CLR dosyalarını okurken, yönetilen kodda programlayan ve WinMD dosyasını kullanan geliştiricilerin daha doğal bir programlama deneyimine sahip olması için CLR dosyalarını okurken Windows Çalışma Zamanı türleri .NET Framework türlerine eşler. Bu eşlemelerin bazı örnekleri için bkz. [Windows Mağazası uygulamaları için .NET Framework desteği ve Windows çalışma zamanı](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).

Bu nedenle, Profil oluşturucunuz, meta veri API 'Lerini kullandığında hangi görünümde alınır: ham Windows Çalışma Zamanı görünümü veya eşlenmiş .NET Framework görünümü?  Yanıt: size ait.

Bir WinMD üzerinde [ICorProfilerInfo:: GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) yöntemini [çağırdığınızda, bu](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)eşlemeyi kapatmak için `dwOpenFlags` parametresinde [ofnotransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) ' ı ayarlamayı tercih edebilirsiniz. Aksi takdirde, varsayılan olarak eşleme etkin olur. Genellikle, profil oluşturucu DLL 'nin WinMD meta verilerinden elde ettiği dizelerin (örneğin, türlerin adları), profil oluşturucu kullanıcısına tanıdık ve doğal olarak görünmesi için bir profil oluşturucu eşlemeyi etkin tutacaktır.

### <a name="modifying-metadata-from-winmds"></a>Wınmds 'den meta verileri değiştirme

WinMDs 'de meta verileri değiştirme desteklenmiyor. Bir WinMD dosyası için [ICorProfilerInfo:: GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) metodunu çağırıp `dwOpenFlags` parametresinde [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) belirtirseniz veya [ımetadatayay](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)gibi yazılabilir bir meta veri arabirimine sorun yaparsanız [GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) başarısız olur. Bu, kendi araçlarını destekleyecek meta verileri (örneğin, AssemblyRefs veya yeni yöntemler eklemek için) değiştirmesi gereken, Il yeniden yazma profil oluşturucular önemli bir öneme sahiptir. Bu nedenle, [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) for First (önceki bölümde anlatıldığı gibi) öğesini denetlemeniz ve bu tür modüller üzerinde yazılabilir meta veri arabirimleri isteyip istemediğinizi sormaktan kaçının.

### <a name="resolving-assembly-references-with-winmds"></a>WinMDs ile derleme başvurularını çözme

İzleme veya tür denetimine yardımcı olmak için meta veri başvurularını el ile çözmek için birçok profil oluşturucular gerekir. Bu tür profil oluşturucular, CLR 'nin Wınmds 'ye işaret eden derleme başvurularını nasıl çözümlediği farkında olmalıdır, çünkü bu başvurular standart derleme başvurularından tamamen farklı bir şekilde çözümlenir.

## <a name="memory-profilers"></a>Bellek Profil oluşturucular

Çöp toplayıcı ve yönetilen yığın, bir Windows Mağazası uygulamasında ve masaüstü uygulamasında temel olarak farklı değildir. Ancak, profil oluşturucu yazarlarının farkında olması gereken bazı hafif farklılıklar vardır.

### <a name="forcegc-creates-a-managed-thread"></a>ForceGC yönetilen bir iş parçacığı oluşturur

Bellek profili oluşturma sırasında, profil oluşturucu DLL 'niz genellikle [ForceGC yöntemi](icorprofilerinfo-forcegc-method.md) yönteminin çağrılabileceği ayrı bir iş parçacığı oluşturur. Bu yeni bir şey değildir. Ancak, bir Windows Mağazası uygulamasının içinde çöp toplama işlemi yapma işleminin iş parçacığını yönetilen bir iş parçacığına dönüştürebileceği (örneğin, bu iş parçacığı için bir profil oluşturma API 'SI tehdit oluşturulacak).

Bunun sonuçlarını anlamak için, CLR profil oluşturma API 'SI tarafından tanımlanan, zaman uyumlu ve zaman uyumsuz çağrılar arasındaki farklılıkları anlamak önemlidir. Bu, Windows Mağazası uygulamalarındaki zaman uyumsuz çağrılar kavramından çok farklı olduğunu unutmayın. Daha fazla bilgi için [corprof_e_unsupported_call_sequence sahip olduğumuz](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) blog gönderisine bakın.

İlgili nokta, Profil oluşturucunuz tarafından oluşturulan iş parçacıklarında yapılan çağrıların, profil oluşturucu DLL 'inin [ICorProfilerCallback](icorprofilercallback-interface.md) metotlarından birinin bir uygulamasının dışından yapılsa bile her zaman zaman uyumlu olarak kabul edilir. En azından, bu durum olarak kullanılır. [ForceGC yöntemine](icorprofilerinfo-forcegc-method.md)yapılan ÇAĞRıLARıNıZ nedeniyle CLR 'nin Profiler iş parçacığını yönetilen bir iş parçacığına kapatmış olduğuna göre, bu iş parçacığı artık profil oluşturucunun iş parçacığını kabul edilmiyor. Bu nedenle, CLR, bu iş parçacığı için zaman uyumlu olarak niteleyen nelerin daha sıkı bir tanımını uygular — yani bir çağrı, zaman uyumlu olarak nitelendirmek için profil oluşturucu DLL 'inin [ICorProfilerCallback](icorprofilercallback-interface.md) yöntemlerinden birinin içinden kaynaklanmalıdır.

Bu uygulamada ne anlama geliyor? Çoğu [ICorProfilerInfo](icorprofilerinfo-interface.md) yöntemlerinin yalnızca zaman uyumlu olarak çağrılması güvenlidir ve aksi halde, daha sonra başarısız olur. Profil oluşturucu DLL 'niz, genellikle profil oluşturucu tarafından oluşturulan iş parçacıklarında (örneğin, [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md), [RequestReJIT](icorprofilerinfo4-requestrejit-method.md)veya [requestdönmesi](icorprofilerinfo4-requestrevert-method.md)Için) gerçekleştirilen diğer çağrılar için [ForceGC yöntemi](icorprofilerinfo-forcegc-method.md) iş parçacığını yeniden kullanıyorsa, sorun yaşayacağız . [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) gibi zaman uyumsuz güvenli bir işlev, yönetilen iş parçacıklarında çağrıldığında özel kurallara sahiptir. (Daha fazla bilgi için bkz. Profiler Stack for the blog gönderisi [: temel bilgiler ve](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) daha fazlası.)

Bu nedenle, profil oluşturucu DLL 'nizin [ForceGC yöntemini](icorprofilerinfo-forcegc-method.md) çağırmak için oluşturduğu tüm iş parçacıklarının *yalnızca* GCS 'yi TETIKLEMENIN ve sonra GC geri çağırmaları için kullanılması önerilir. Yığın örnekleme veya ayırma gibi diğer görevleri gerçekleştirmek için profil oluşturma API 'sine çağrı gerçekleştirmemelidir.

### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

.NET Framework 4,5 ' den başlayarak, profil oluşturucunun *bağımlı tanıtıcılarla*ilgili daha fazla bilgi veren yenı bir GC geri çağırması olan [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)vardır. Bu tutamaçlar, GC yaşam süresi yönetimi amacıyla bir kaynak nesnesinden bir hedef nesneye bir başvuru ekler. Bağımlı tutamaçlar hiçbir şey değildir ve yönetilen kodda çalışan geliştiriciler, Windows 8 ' den ve .NET Framework 4,5 ' den önce bile <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> sınıfını kullanarak kendi bağımlı tutamaçlarını oluşturamayacak.

Ancak, yönetilen XAML Windows Mağazası uygulamaları artık bağımlı tanıtıcıların yoğun bir şekilde kullanılmasını kolaylaştırır. Özellikle, CLR, yönetilen nesneler ve yönetilmeyen Windows Çalışma Zamanı nesneleri arasındaki başvuru döngülerini yönetmeye yardımcı olmak için bunları kullanır. Bu, artık bellek profil oluşturucular ' nin, yığın grafiğindeki diğer kenarlarla birlikte görselleştirilmesi için bu bağımlı tutamaçların bilgilendirilmesi için her zamankinden daha önemli olduğu anlamına gelir. Profiler DLL 'niz, yığın grafiğinin tamamen görünümünü oluşturmak için [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md)ve [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) öğelerini birlikte kullanmalıdır.

## <a name="conclusion"></a>Sonuç

Windows Mağazası uygulamaları içinde çalışan yönetilen kodu çözümlemek için CLR profil oluşturma API 'sini kullanmak mümkündür. Aslında, geliştirmekte olduğunuz bir profil oluşturucuyu alabilir ve Windows Mağazası uygulamalarını hedefleyecek şekilde belirli değişiklikler yapabilirsiniz. Profiler Kullanıcı arabiriminize, Windows Mağazası uygulamasını hata ayıklama modunda etkinleştirmek için yeni API 'Ler kullanılmalıdır. Profil oluşturucu DLL 'nizin yalnızca Windows Mağazası uygulamaları için geçerli olan API 'Leri tükettiğini doğrulayın. Profil oluşturucu DLL ve Profil Oluşturucu kullanıcı arabiriminizin arasındaki iletişim mekanizması, Windows Mağazası uygulaması API 'SI kısıtlamalarına göz önünde bulundurularak ve Windows Mağazası uygulamaları için yerinde kısıtlı izinlerin farkında olmadan yazılmalıdır. Profil oluşturucu DLL 'niz, CLR 'nin Wınmds 'nin nasıl davrandığını ve çöp toplayıcının yönetilen iş parçacıklarıyla karşılaştırıldığında nasıl farklı olduğunu bilmelidir.

## <a name="resources"></a>Kaynaklar

**Ortak dil çalışma zamanı**

- [Profil oluşturma (yönetilmeyen API Başvurusu)](index.md)

- [Meta veriler (yönetilmeyen API Başvurusu)](../metadata/index.md)

**CLR 'nin Windows Çalışma Zamanı etkileşimi**

- [Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

**Windows Mağazası uygulamaları**

- [Dosya erişimi ve izinleri (Windows Çalışma Zamanı uygulamalar](https://docs.microsoft.com/previous-versions/windows/apps/hh967755%28v=win.10%29)

- [Geliştirici Lisansı alın](https://docs.microsoft.com/previous-versions/windows/apps/hh974578%28v=win.10%29)

- [Ipackagedebugsettings arabirimi](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)
