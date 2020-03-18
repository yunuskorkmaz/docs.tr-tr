---
title: Özel bir .NET Core çalışma zamanı ana bilgisayar yazma
description: .NET Core çalışma zamanının nasıl çalıştığını denetlemeyi gerektiren gelişmiş senaryoları desteklemek için yerel koddan .NET Core çalışma süresini barındırmayı öğrenin.
author: mjrousos
ms.date: 12/21/2018
ms.openlocfilehash: 46c7873a1865db04cf1c2b1bb2ded2b5dacbcc8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239904"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Yerel kodunuzdan .NET çalışma süresini denetlemek için özel bir .NET Core ana bilgisayar yazın

Yönetilen tüm kodlar gibi .NET Core uygulamaları da bir ana bilgisayar tarafından yürütülür. Ana bilgisayar çalışma süresini başlatmaktan (JIT ve çöp toplayıcı gibi bileşenler dahil) ve yönetilen giriş noktalarını çağırmaktan sorumludur.

.NET Core çalışma süresini barındırmak gelişmiş bir senaryodur ve .NET Core geliştiricileri barındırma konusunda endişelenmenize gerek yoktur çünkü .NET Core yapı süreçleri .NET Core uygulamalarını çalıştırmak için varsayılan bir ana bilgisayar sağlar. Ancak bazı özel durumlarda, yerel bir işlemde yönetilen kodu çağırmak veya çalışma zamanının nasıl çalıştığı üzerinde daha fazla denetim elde etmek için .NET Core çalışma zamanını açıkça barındırmak yararlı olabilir.

Bu makalede, .NET Core çalışma saatini yerel koddan başlatmak ve içinde yönetilen kodu yürütmek için gereken adımlara genel bir bakış sağlar.

## <a name="prerequisites"></a>Önkoşullar

Ana bilgisayarlar yerel uygulamalar olduğundan, bu öğretici .NET Core'u barındıracak bir C++ uygulaması oluşturmayı kapsar. Bir C++ geliştirme ortamına ihtiyacınız olacaktır [(visual studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)tarafından sağlanan gibi).

Ayrıca ana bilgisayarı test etmek için basit bir .NET Core uygulaması isteyeceksiniz, bu nedenle [.NET Core SDK'yı](https://dotnet.microsoft.com/download) yüklemeli ve [küçük bir .NET Core test uygulaması](with-visual-studio.md) ('Hello World' uygulaması gibi) oluşturmalısınız. Yeni .NET Core konsol proje şablonu tarafından oluşturulan 'Hello World' uygulaması yeterlidir.

## <a name="hosting-apis"></a>API'leri Barındırma
.NET Core'u barındırmak için kullanılabilecek üç farklı API vardır. Bu makale (ve ilişkili [örnekleri)](https://github.com/dotnet/samples/tree/master/core/hosting)tüm seçenekleri kapsar.

* .NET Core 3.0 ve üzeri 'NET Core 3.0 ve `nethost` `hostfxr` üzeri barındırma tercih edilen yöntem ve kütüphanelerin API'leri ile. Bu giriş noktaları, başlatma için çalışma zamanını bulma ve ayarlama karmaşıklığını işler ve hem yönetilen bir uygulamanın başlatılmasına hem de statik yönetilen bir yönteme çağrılmesine izin verir.
* .NET Core 3.0'dan önce .NET Core çalışma süresini barındırmanın tercih edilen yöntemi [CoreClrHost.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/hosts/inc/coreclrhost.h) API iledir. Bu API, çalışma süresini kolayca başlatmak ve durdurmak ve yönetilen kodu çağırmak için işlevleri ortaya çıkarır (yönetilen bir exe başlatarak veya statik yönetilen yöntemleri çağırarak).
* .NET Core da `ICLRRuntimeHost4` [mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h)arayüzü ile barındırılabilir. Bu API CoreClrHost.h daha uzun civarında olmuştur, bu yüzden eski ana bilgisayarları kullanarak görmüş olabilirsiniz. Hala çalışır ve CoreClrHost daha barındırma süreci üzerinde biraz daha fazla kontrol sağlar. Çoğu senaryo için olsa da, CoreClrHost.h şimdi basit API'ler nedeniyle tercih edilir.

## <a name="sample-hosts"></a>Örnek Ana Bilgisayarlar

Aşağıdaki öğreticilerde belirtilen adımları gösteren [örnek ana bilgisayarlar](https://github.com/dotnet/samples/tree/master/core/hosting) dotnet/örnekler GitHub deposunda mevcuttur. Örneklerdeki yorumlar, bu öğreticilerin numaralanmış adımlarını örnekte nerede yapıldıkları ile açıkça ilişkilendirilir. İndirme talimatları için [Örnekler ve Öğreticiler'e](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)bakın.

Örnek ana bilgisayarların öğrenme amacıyla kullanılması gerektiğini, bu nedenle hata denetimine ışık tasladıklarını ve verimlilik üzerinde okunabilirliği vurgulamak üzere tasarlandıklarını unutmayın.

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>NetHost.h ve HostFxr.h kullanarak bir ana bilgisayar oluşturun

Aşağıdaki adımlar, .NET `nethost` Core `hostfxr` çalışma saatini yerel bir uygulamada başlatmak ve yönetilen statik bir yönteme çağırmak için kitaplıkların nasıl kullanılacağını ayrıntılı olarak açıklayabilirsiniz. [Örnek,](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) .NET SDK ile `nethost` yüklü [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) üstbilgi ve [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) kitaplığı ve [dotnet/core-setup](https://github.com/dotnet/core-setup) deposundaki dosyaların kopyalarını kullanır.

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>Adım 1 - Load HostFxr ve dışa aktarılan barındırma işlevlerini alın

Kitaplık, `nethost` `get_hostfxr_path` `hostfxr` kitaplığı bulmak için işlevi sağlar. Kitaplık,.NET `hostfxr` Core çalışma zamanını barındırma işlevlerini ortaya çıkarır. Fonksiyonların tam listesi bulunabilir [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) ve [yerli barındırma tasarım belgesi](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md). Örnek ve bu öğretici aşağıdakileri kullanır:

* `hostfxr_initialize_for_runtime_config`: Ana bilgisayar bağlamını başolarak karşılar ve belirtilen çalışma zamanı yapılandırmasını kullanarak .NET Core çalışma zamanının başlatılmasıiçin hazırlanır.
* `hostfxr_get_runtime_delegate`: Çalışma zamanı işlevselliği için bir temsilci alır.
* `hostfxr_close`: Ana bilgisayar bağlamını kapatır.

Kitaplık `hostfxr` kullanılarak `get_hostfxr_path`bulunur. Daha sonra yüklenir ve dışa aktarma ları geri alınır.

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>Adım 2 - .NET Core çalışma süresini başlatın ve başlatın

Ve `hostfxr_initialize_for_runtime_config` `hostfxr_get_runtime_delegate` işlevler başlatılır ve yüklenecek yönetilen bileşen için çalışma zamanı yapılandırmasını kullanarak .NET Core çalışma zamanını başlatır. İşlev, `hostfxr_get_runtime_delegate` yönetilen bir derlemenin yüklenmesine ve bir işlev işaretçisinin bu derlemedeki statik metoduna alınmasını sağlayan bir çalışma zamanı temsilcisi almak için kullanılır.

[!code-cpp[HostFxrHost#Initialize](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>Adım 3 - Yönetilen montajı yükleyin ve işlev işaretçisini yönetilen bir yönteme alın

Yönetilen derlemeyi yüklemek ve yönetilen bir yönteme bir işlev işaretçisi almak için çalışma zamanı temsilcisi çağrılır. Temsilci, derleme yolunu, tür adını ve yöntem adını giriş olarak gerektirir ve yönetilen yöntemi çağırmak için kullanılabilecek bir işlev işaretçisini döndürür.

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

Çalışma `nullptr` zamanı temsilcisini ararken temsilci türü adı olarak geçerek, örnek yönetilen yöntem için varsayılan imza kullanır:

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

Çalışma zamanı temsilcisini ararken temsilci türü adı belirtilerek farklı bir imza kullanılabilir.

### <a name="step-4---run-managed-code"></a>Adım 4 - Yönetilen kodu çalıştırın!

Yerel ana bilgisayar artık yönetilen yöntemi arayabilir ve istenen parametreleri geçirebilir.

[!code-cpp[HostFxrHost#CallManaged](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>CoreClrHost.h kullanarak bir ana bilgisayar oluşturma

CoreClrHost.h API'nın yerel bir uygulamada .NET Core çalışma süresini başlatmak ve yönetilen statik bir yönteme çağırmak için aşağıdaki adımlar ayrıntılı olarak açıklanmıştır. Bu belgedeki kod parçacıkları bazı Windows'a özgü API'ler kullanır, ancak [tam örnek ana bilgisayar](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) hem Windows hem de Linux kod yollarını gösterir.

[Unix CoreRun ev sahibi](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/unixcorerun) coreclrhost.h kullanarak barındırma daha karmaşık, gerçek dünya örneği gösterir.

### <a name="step-1---find-and-load-coreclr"></a>Adım 1 - CoreCLR bul ve yükleyin

.NET Core çalışma zamanı API'leri *coreclr.dll* (Windows'da), *libcoreclr.so* 'de (Linux'ta) veya *libcoreclr.dylib* 'de (macOS'ta) bulunur. .NET Core barındırmanın ilk adımı CoreCLR kitaplığını yüklemektir. Bazı ana bilgisayarlar farklı yolları inceler veya kitaplığı bulmak için giriş parametrelerini kullanırken, diğerleri kitaplığı belirli bir yoldan yüklemeyi bilir (örneğin ana bilgisayarın yanında veya makine çapında bir konumdan).

Bulunduğunda, kitaplık `LoadLibraryEx` (Windows'ta) `dlopen` veya (Linux/macOS' da) yüklenir.

[!code-cpp[CoreClrHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>Adım 2 - .NET Core barındırma işlevlerini alın

CoreClrHost barındırma .NET Core için yararlı birkaç önemli yöntemleri vardır:

* `coreclr_initialize`: .NET Core çalışma zamanını başlatır ve varsayılan (ve yalnızca) AppDomain'i ayarlar.
* `coreclr_execute_assembly`: Yönetilen bir derlemeyürütür.
* `coreclr_create_delegate`: Yönetilen bir yöntem için bir işlev işaretçisi oluşturur.
* `coreclr_shutdown`: .NET Core çalışma süresini kapatır.
* `coreclr_shutdown_2`: `coreclr_shutdown`Beğen , aynı zamanda yönetilen kodun çıkış kodunu alır.

CoreCLR kitaplığını yükledikten sonra, bir sonraki adım `GetProcAddress` bu işlevlere `dlsym` (Windows'da) veya (Linux/macOS'ta) kullanarak başvuru almaktır.

[!code-cpp[CoreClrHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>Adım 3 - Çalışma zamanı özelliklerini hazırlama

Çalışma süresini başlatmadan önce, davranışı belirtmek için bazı özellikler (özellikle montaj yükleyicisi ile ilgili) hazırlamak gerekir.

Ortak özellikler şunlardır:

* `TRUSTED_PLATFORM_ASSEMBLIES`Bu, çalışma zamanının varsayılan olarak çözebileceği derleme yollarının (Windows'da ';' ve Linux'ta ':' ile sınırlandırılmış) listesidir. Bazı ana bilgisayarların yükleyebilecekleri derlemeleri listeleyen sabit kodlu bildirimleri vardır. Diğerleri bu listeye belirli konumlarda *(coreclr.dll*yanında , örneğin) herhangi bir kitaplık koyacağız.
* `APP_PATHS`Bu, güvenilen platform derlemeleri (TPA) listesinde bulunamazsa, derleme için sondalama yolları listesidir. Ana bilgisayar, TPA listesini kullanarak hangi derlemelerin yüklendiği üzerinde daha fazla denetime sahip olduğundan, hangi derlemeleri yüklemeyi beklediklerini belirlemek ve bunları açıkça listelemek için ana bilgisayarlar için en iyi yöntemdir. Ancak, çalışma zamanında sondalama gerekiyorsa, bu özellik bu senaryoyu etkinleştirebilir.
* `APP_NI_PATHS`Bu liste, yerel görüntüler için incelenecek yollar olması gerektiği dışında APP_PATHS benzer.
* `NATIVE_DLL_SEARCH_DIRECTORIES`Bu özellik, p/invoke ile çağrılan yerel kitaplıkları ararken yükleyicinin sondalaması gereken yolların bir listesidir.
* `PLATFORM_RESOURCE_ROOTS`Bu liste, kaynak uydu derlemeleri için (kültüre özgü alt dizinlerde) araştırma yolları içerir.

Bu örnek ana bilgisayarda, TPA listesi geçerli dizindeki tüm kitaplıklar listeleyerek oluşturulur:

[!code-cpp[CoreClrHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#7)]

Örnek basit olduğundan, yalnızca `TRUSTED_PLATFORM_ASSEMBLIES` özelliğe ihtiyacı vardır:

[!code-cpp[CoreClrHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>Adım 4 - Çalışma süresini başlatın

Mscoree.h barındırma API aksine (aşağıda açıklanan), CoreCLRHost.h API'lar çalışma süresini başlatmak ve tek bir çağrı ile varsayılan AppDomain tüm oluşturun. İşlev `coreclr_initialize` bir temel yol, ad ve daha önce açıklanan özellikleri alır `hostHandle` ve parametre ile ana bilgisayara bir tutamacı geri döndürür.

[!code-cpp[CoreClrHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>Adım 5 - Yönetilen kodu çalıştırın!

Çalışma zamanı başladığında, ana bilgisayar yönetilen kodu arayabilir. Bu birkaç farklı şekilde yapılabilir. Bu öğreticiye bağlı örnek `coreclr_create_delegate` kod, statik yönetilen bir yönteme temsilci oluşturmak için işlevi kullanır. Bu [API, derleme adını,](../../standard/assembly/names.md)ad alanına uygun tür adı ve yöntem adını giriş olarak alır ve yöntemi çağırmak için kullanılabilecek bir temsilci döndürür.

[!code-cpp[CoreClrHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#5)]

Bu örnekte, ana bilgisayar `managedDelegate` artık `ManagedWorker.DoWork` yöntemi çalıştırmak için arayabilirsiniz.

Alternatif olarak, `coreclr_execute_assembly` işlev yönetilen bir yürütülebilir başlatmak için kullanılabilir. Bu API, giriş parametreleri olarak bir derleme yolu ve bağımsız değişkenler dizisini alır. Montajı bu yola yükler ve ana yöntemini çağırır.

```C++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>Adım 6 - Kapatma ve temizleme

Son olarak, ana bilgisayar yönetilen kodu çalıştırmayı bitirdiğinde,.NET `coreclr_shutdown` `coreclr_shutdown_2`Core çalışma süresi ile kapatılır veya .

[!code-cpp[CoreClrHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#6)]

CoreCLR yeniden başlatmaveya boşaltma yı desteklemez. CoreCLR `coreclr_initialize` kitaplığını tekrar aramayın veya boşaltmayın.

## <a name="create-a-host-using-mscoreeh"></a>Mscoree.h kullanarak ana bilgisayar oluşturma

Daha önce de belirtildiği gibi, CoreClrHost.h şimdi .NET Core çalışma zamanı barındırma tercih edilen yöntemdir. CoreClrHost.h arabirimleri yeterli değilse (örneğin, standart olmayan başlangıç bayrakları gerekiyorsa veya varsayılan etki alanında bir AppDomainManager gerekiyorsa) `ICLRRuntimeHost4` arabirim yine de kullanılabilir. Bu talimatlar mscoree.h kullanarak .NET Core barındırma yoluyla size rehberlik edecektir.

[CoreRun ev sahibi,](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/corerun) mscoree.h kullanarak barındırma daha karmaşık, gerçek dünya bir örnek gösterir.

### <a name="a-note-about-mscoreeh"></a>mscoree.h hakkında bir not
`ICLRRuntimeHost4` .NET Core barındırma arabirimi [MSCOREE'de tanımlanır. IDL](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/inc/MSCOREE.IDL). Ana bilgisayarınızın başvurması gereken bu dosyanın üstbilgi sürümü (mscoree.h), [.NET Core çalışma süresi](https://github.com/dotnet/runtime/) oluşturulunca MIDL üzerinden oluşturulur. .NET Core çalışma zamanını oluşturmak istemiyorsanız, mscoree.h dotnet/runtime deposunda önceden oluşturulmuş bir [üstbilgi](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/) olarak da kullanılabilir.

### <a name="step-1---identify-the-managed-entry-point"></a>Adım 1 - Yönetilen giriş noktasını belirleme
Gerekli üstbilgiden[(örneğin mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h) ve stdio.h) başvurduktan sonra, bir .NET Core ana bilgisayar ının yapması gereken ilk şeylerden biri, kullanmakta olacağı yönetilen giriş noktasını bulmaktır. Örnek ana bilgisayarımızda, bu işlem yalnızca ilk komut satırı bağımsız `main` değişkenini, yöntemi yürütülecek yönetilen bir ikiliye giden yol olarak ana bilgisayarımıza götürerek yapılır.

[!code-cpp[NetCoreHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>Adım 2 - CoreCLR bul ve yükleyin
.NET Core çalışma zamanı API'leri *CoreCLR.dll* 'de (Windows'da) bulunmaktadır. Bizim barındırma arayüzü`ICLRRuntimeHost4`almak için ( ), bu bulmak ve *CoreCLR.dll*yüklemek için gereklidir. *CoreCLR.dll'yi*nasıl bulabildiğini belirlemek ana bilgisayara kalmaktadır. Bazı ana bilgisayarlar dosyanın makine çapında iyi bilinen bir konumda bulunmasını bekler *(%programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*gibi). Diğerleri *CoreCLR.dll'nin* ev sahibinin kendisi veya barındırılacak uygulamanın yanındaki bir konumdan yüklenmesini bekler. Yine de diğerleri kitaplığı bulmak için bir ortam değişkenine danışabilir.

Linux veya macOS'ta, çekirdek çalışma zamanı kitaplığı sırasıyla *libcoreclr.so* veya *libcoreclr.dylib'dir.*

Örnek ana bilgisayarımız *CoreCLR.dll*için birkaç ortak yeri inceler. Bulunduktan sonra (veya `LoadLibrary` `dlopen` Linux/macOS üzerinden) yüklenmesi gerekir.

[!code-cpp[NetCoreHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a>Adım 3 - Bir ICLRRuntimeHost4 Örnek alın
Barındırma `ICLRRuntimeHost4` arabirimi, (veya `GetProcAddress` `dlsym` Linux/macOS) üzerinde `GetCLRRuntimeHost`çağrılar ve sonra bu işlevi çağırarak alınır.

[!code-cpp[NetCoreHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a>Adım 4 - Başlangıç bayraklarını ayarlayın ve çalışma süresini başlatın
`ICLRRuntimeHost4` El ele, artık çalışma zamanı genelinde ki başlangıç bayraklarını belirleyebilir ve çalışma saatini başlatabiliriz. Başlangıç bayrakları hangi çöp toplayıcısının (GC) kullanılacağını (eşzamanlı veya sunucu), tek bir AppDomain veya birden çok AppDomain kullanıp kullanmayacağımızı ve hangi yükleyici optimizasyon ilkesini kullanacağımızı (derlemelerin etki alanından bağımsız yüklenmesi için) belirler.

[!code-cpp[NetCoreHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#4)]

Çalışma süresi, işleve `Start` yapılan bir çağrıyla başlatılır.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Adım 5 - AppDomain ayarlarını hazırlama
Çalışma süresi başladıktan sonra bir AppDomain kurmak isteriz. Ancak, bir .NET AppDomain oluştururken belirtilmesi gereken bir dizi seçenek vardır, bu nedenle bunları önce hazırlamak gerekir.

AppDomain bayrakları, güvenlik ve interop ile ilgili AppDomain davranışlarını belirtir. Eski Silverlight ana bilgisayarları bu ayarları kullanıcı kodunu zandbox olarak kullanır, ancak modern .NET Core ana bilgisayarları kullanıcı kodunu tam güven olarak çalıştırın ve interop'u etkinleştirin.

[!code-cpp[NetCoreHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#5)]

Hangi AppDomain bayraklarının kullanılacağına karar veredikten sonra AppDomain özellikleri tanımlanmalıdır. Özellikler, dizelerin anahtar/değer çiftleridir. Özelliklerin çoğu AppDomain'in derlemeleri nasıl yükleyeceğiyle ilgilidir.

Yaygın AppDomain özellikleri şunlardır:

* `TRUSTED_PLATFORM_ASSEMBLIES`Bu, AppDomain'in yüklemeye `;` öncelik vermesi `:` ve (kısmen güvenilen etki alanlarında bile) tam güven vermesi gereken derleme yollarının (Windows ve Linux/macOS'ta sınırlı dır) bir listesidir. Bu liste, .NET Framework senaryolarında GAC'ye benzer 'Framework' derlemeleri ve diğer güvenilen modülleri içerecek şekilde dir. Bazı ana bilgisayarlar bu listeye *coreclr.dll'nin* yanına herhangi bir kitaplık koyar, diğerleri kendi amaçları için güvenilir derlemeleri listeleyen sabit kodlanmış bildirimlere sahiptir.
* `APP_PATHS`Bu, güvenilen platform derlemeleri (TPA) listesinde bulunamazsa, derleme için sondalama yolları listesidir. Ana bilgisayar, TPA listesini kullanarak hangi derlemelerin yüklendiği üzerinde daha fazla denetime sahip olduğundan, hangi derlemeleri yüklemeyi beklediklerini belirlemek ve bunları açıkça listelemek için ana bilgisayarlar için en iyi yöntemdir. Ancak, çalışma zamanında sondalama gerekiyorsa, bu özellik bu senaryoyu etkinleştirebilir.
* `APP_NI_PATHS`Bu liste, yerel görüntüler için incelenecek yollar olması dışında APP_PATHS çok benzer.
* `NATIVE_DLL_SEARCH_DIRECTORIES`Bu özellik, p/invoke ile çağrılan yerel DL'leri ararken yükleyicinin sondalaması gereken yolların bir listesidir.
* `PLATFORM_RESOURCE_ROOTS`Bu liste, kaynak uydu derlemeleri için (kültüre özgü alt dizinlerde) araştırma yolları içerir.

Basit [örnek ana bilgisayarımızda](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree)bu özellikler aşağıdaki gibi ayarlanır:

[!code-cpp[NetCoreHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Adım 6 - AppDomain oluştur
Tüm AppDomain bayrakları ve özellikleri `ICLRRuntimeHost4::CreateAppDomainWithManager` hazırlandıktan sonra AppDomain'i kurmak için kullanılabilir. Bu işlev isteğe bağlı olarak etki alanının AppDomain yöneticisi olarak kullanmak üzere tam nitelikli bir montaj adı ve tür adı alır. Bir AppDomain yöneticisi, bir ana bilgisayar yöneticisinin AppDomain davranışının bazı yönlerini denetlemesine izin verebilir ve ana bilgisayar kullanıcı kodunu doğrudan çağırmak istemiyorsa yönetilen kodu başlatmak için giriş noktaları sağlayabilir.

[!code-cpp[NetCoreHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Adım 7 - Yönetilen kodu çalıştırın!
Bir AppDomain çalışır durumda ve çalışırken, ana bilgisayar artık yönetilen kodu yürütmeye başlayabilir. Bunu yapmanın en kolay yolu, `ICLRRuntimeHost4::ExecuteAssembly` yönetilen bir derlemenin giriş noktası yöntemini çağırmaktır. Bu işlevin yalnızca tek etki alanı senaryolarında çalıştığını unutmayın.

[!code-cpp[NetCoreHost#8](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#8)]

Ana bilgisayarınızın `ExecuteAssembly` gereksinimlerini karşılamazsa, başka bir seçenek `CreateDelegate` statik yönetilen yöntemiçin bir işlev işaretçisi oluşturmak için kullanmaktır. Bu, ana bilgisayara çağırdığı yöntemin imzasını bilmesini gerektirir (işlev işaretçisi türünü oluşturmak için) ancak ana bilgisayarların bir derlemenin giriş noktası dışında kod çağırma esnekliğine izin verir. İkinci parametrede sağlanan montaj adı, yüklenmesi gereken kitaplığın [tam yönetilen montaj adıdır.](../../standard/assembly/names.md)

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
    domainId,
    L"HW, Version=1.0.0.0, Culture=neutral", // Target managed assembly
    L"ConsoleApplication.Program",           // Target managed type
    L"Main",                                 // Target entry point (static method)
    (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a>Adım 8 - Temizleme
Son olarak, ana bilgisayar AppDomains'i boşaltarak, çalışma süresini durdurarak ve başvuruyu `ICLRRuntimeHost4` serbest bırakarak kendisinden sonra temizlemelidir.

[!code-cpp[NetCoreHost#9](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#9)]

CoreCLR boşaltmayı desteklemez. CoreCLR kitaplığını boşaltmayın.

## <a name="conclusion"></a>Sonuç
Ana bilgisayarınız oluşturulduktan sonra, komut satırından çalıştırılarak ve ana bilgisayar beklediği bağımsız değişkenleri geçirerek sınanabilir (yönetilen uygulamanın mscoree örnek ana bilgisayar için çalışması gibi). Ana bilgisayar için .NET Core uygulamasını belirtirken, .dll tarafından `dotnet build`üretilen .dll'yi kullandığınızdan emin olun Bağımsız uygulamalar `dotnet publish` için üretilen yürütülebilir dosyalar (.exe dosyaları) aslında varsayılan .NET Core ana bilgisayardır (böylece uygulama ana satır senaryolarında doğrudan komut satırından başlatılabilir); kullanıcı kodu aynı adı taşıyan bir dll olarak derlenir.

Başlangıçta işler işe yaramazsa, *coreclr.dll'nin* ana bilgisayar tarafından beklenen konumda mevcut olduğunu, gerekli tüm Framework kitaplıklarının TPA listesinde olduğunu ve CoreCLR'ın bitliğinin (32 bit veya 64 bit) ev sahibinin nasıl inşa edildiğiyle eşleştiğini iki kez kontrol edin.

.NET Core çalışma zamanını barındırmak, birçok geliştiricinin gerektirmeyecek, ancak yerel bir işlemden yönetilen kodu başlatması gerekenler veya .NET Core çalışma zamanının davranışı üzerinde daha fazla denetime ihtiyaç duyan kişiler için çok yararlı olabilir.
