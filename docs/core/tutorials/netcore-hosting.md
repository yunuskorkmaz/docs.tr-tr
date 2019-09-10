---
title: Özel bir .NET Core çalışma zamanı Konağı yazma
description: .NET Core çalışma zamanının nasıl çalıştığını denetlemek için gerekli olan gelişmiş senaryoları desteklemek üzere yerel koddan .NET Core çalışma zamanının barındıralınacağını öğrenin.
author: mjrousos
ms.date: 12/21/2018
ms.custom: seodec18
ms.openlocfilehash: 1f04ccfa56c399a4dba003ec0de8a87f888ef848
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849320"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>.NET çalışma zamanını yerel kodunuzda denetlemek için özel bir .NET Core ana bilgisayarı yazma

Tüm yönetilen kodlar gibi .NET Core uygulamaları da bir ana bilgisayar tarafından yürütülür. Konak, çalışma zamanının (JıT ve çöp toplayıcı gibi bileşenler dahil) başlatılması ve yönetilen giriş noktalarını çağırmaktan sorumludur.

.NET Core çalışma zamanının barındırılması, gelişmiş bir senaryodur ve .NET Core derleme işlemlerinde .NET Core uygulamalarını çalıştırmak için bir varsayılan konak sağladığından .NET Core geliştiricilerinin barındırılmasına gerek kalmaz. Bazı özel koşullarda, .NET Core çalışma zamanını açıkça barındırmak için, yerel bir işlemde yönetilen kodu çağırma ya da çalışma zamanının nasıl çalıştığı hakkında daha fazla denetim elde etmek için yararlı olabilir.

Bu makale, .NET Core çalışma zamanını yerel koddan başlatmak ve içindeki yönetilen kodu yürütmek için gerekli olan adımlara genel bir bakış sunar.

## <a name="prerequisites"></a>Önkoşullar

Konaklar yerel uygulamalar olduğundan, bu öğreticide .NET Core barındırmak için C++ bir uygulama oluşturma konusu ele alınacaktır. Bir C++ geliştirme ortamı (örneğin, [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)tarafından sağlanacaktır) gerekir.

Ayrıca, bir basit .NET Core uygulamasının konak ile test edebilmesi için, [.NET Core SDK](https://dotnet.microsoft.com/download) yüklemeli ve [küçük bir .NET Core test uygulaması](with-visual-studio.md) (' Merhaba Dünya ' uygulaması gibi) oluşturmalısınız. Yeni .NET Core konsol projesi şablonu tarafından oluşturulan ' Merhaba Dünya ' uygulaması yeterlidir.

## <a name="hosting-apis"></a>Barındırma API 'Leri
.NET Core barındırmak için kullanılabilecek üç farklı API vardır. Bu belge (ve ilişkili [örnekleri](https://github.com/dotnet/samples/tree/master/core/hosting)) tüm seçenekleri kapsar.

* .NET Core 3,0 ve üzeri sürümlerde .NET Core çalışma zamanının barındırılması için tercih edilen yöntem, `nethost` ve `hostfxr` kitaplıklarının API 'larıdır. Bu giriş noktaları, başlatma için çalışma zamanını bulma ve ayarlama karmaşıklığını ve hem yönetilen bir uygulamanın başlatılmasına hem de statik yönetilen bir yönteme çağrılmasını sağlar.
* .NET Core 3,0 ' den önceki .NET Core çalışma zamanını barındırmak için tercih edilen yöntem [Coreclrhost. h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h) API 'sidir. Bu API, çalışma zamanının kolayca başlatılmasına ve durdurulmasına ve yönetilen kodun çağrılmasını (yönetilen bir exe başlatarak veya statik yönetilen yöntemleri çağırarak) işlevleri kullanıma sunar.
* .NET Core, `ICLRRuntimeHost4` [Mscoree. h](https://github.com/dotnet/coreclr/blob/master/src/pal/prebuilt/inc/mscoree.h)içinde arabirimiyle de barındırılabilir. Bu API CoreClrHost. h öğesinden daha uzun bir süredir, bu nedenle daha eski konakları kullanarak görebilirsiniz. Hala işe yarar ve barındırma işlemi üzerinde CoreClrHost 'dan biraz daha fazla denetime izin verir. Çoğu senaryoda, daha basit API 'Ler nedeniyle CoreClrHost. h artık tercih edilir.

## <a name="sample-hosts"></a>Örnek konaklar
Aşağıdaki öğreticilerde özetlenen adımları gösteren [örnek ana bilgisayarlar](https://github.com/dotnet/samples/tree/master/core/hosting) DotNet/Samples GitHub deposunda mevcuttur. Örnekteki açıklamalar, bu öğreticilerden numaralandırılmış adımları açık bir şekilde, örnekte gerçekleştirdikleri yerle ilişkilendirir. İndirme yönergeleri için bkz. [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Örnek konakların öğrenme amaçlarıyla kullanılması gerektiğini aklınızda bulundurun. bu sayede hata denetimi açık olur ve verimlilik genelinde okunabilirliği vurgulamak için tasarlanmıştır.

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>NetHost. h ve HostFxr. h kullanarak bir konak oluşturun

Aşağıdaki adımlarda, `nethost` ve `hostfxr` kitaplıklarının .NET Core çalışma zamanını yerel bir uygulamada başlatmak ve yönetilen bir statik yönteme çağırmak için nasıl kullanılacağı açıklanır. [Örnek](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) , .NET SDK `nethost` ile yüklenen üstbilgiyi ve kitaplığı, [DotNet/Core-Setup](https://github.com/dotnet/core-setup) deposundan [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) ve [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) dosyalarının kopyalarını kullanır.

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>1\. adım-HostFxr 'yi yükleyin ve dışarıya aktarılmış barındırma işlevlerini alın

Kitaplık, Kitaplığı`hostfxr` bulmaya `get_hostfxr_path` yönelik işlevi sağlar. `nethost` `hostfxr` Kitaplık, .NET Core çalışma zamanını barındırmak için işlevler sunar. İşlevlerin tam listesi [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) ve [yerel barındırma tasarımı belgesinde](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md)bulunabilir. Örnek ve bu öğretici şunları kullanır:
* `hostfxr_initialize_for_runtime_config`: Bir konak bağlamını başlatır ve belirtilen çalışma zamanı yapılandırmasını kullanarak .NET Core çalışma zamanının başlatılmasına hazırlar.
* `hostfxr_get_runtime_delegate`: Çalışma zamanı işlevselliği için bir temsilci alır.
* `hostfxr_close`: Bir konak bağlamını kapatır.

`hostfxr` Kitaplık kullanılarak`get_hostfxr_path`bulunur. Daha sonra yüklenir ve dışarı aktarmaları alınır.

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>2\. adım-.NET Core çalışma zamanını başlatma ve başlatma

`hostfxr_initialize_for_runtime_config` Ve`hostfxr_get_runtime_delegate` işlevleri, yüklenecek yönetilen bileşen için çalışma zamanı yapılandırmasını kullanarak .NET Core çalışma zamanını başlatabilir ve başlatır. `hostfxr_get_runtime_delegate` İşlevi, yönetilen bir derlemeyi yüklemeye ve bu derlemede bir statik metoda işlev işaretçisi almaya izin veren bir çalışma zamanı temsilcisi almak için kullanılır.

[!code-cpp[HostFxrHost#Initialize](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>3\. adım-yönetilen derlemeyi yükle ve bir yönetilen yönteme işlev işaretçisi al

Çalışma zamanı temsilcisi, yönetilen derlemeyi yüklemek ve yönetilen bir yönteme bir işlev işaretçisi almak için çağrılır. Temsilci, derleme yolu, tür adı ve yöntem adını girdi olarak gerektirir ve yönetilen yöntemi çağırmak için kullanılabilecek bir işlev işaretçisi döndürür.

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

Çalışma zamanı `nullptr` temsilcisini çağırırken temsilci türü adı olarak geçirerek, örnek yönetilen yöntem için varsayılan bir imza kullanır:

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

Çalışma zamanı temsilcisi çağrılırken temsilci türü adı belirtilerek farklı bir imza kullanılabilir.

### <a name="step-4---run-managed-code"></a>4\. adım-yönetilen kodu çalıştırın!

Yerel ana bilgisayar artık yönetilen yöntemi çağırabilir ve istenen parametrelere geçirebilir.

[!code-cpp[HostFxrHost#CallManaged](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>CoreClrHost. h kullanarak bir konak oluşturun

Aşağıdaki adımlar, yerel bir uygulamada .NET Core çalışma zamanını başlatmak ve yönetilen bir statik yönteme çağırmak için CoreClrHost. h API 'sinin nasıl kullanılacağını açıklamaktadır. Bu belgedeki kod parçacıkları Windows 'a özgü bazı API 'Ler kullanır, ancak [tam örnek ana bilgisayar](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) hem Windows hem de Linux kod yollarını gösterir.

[UNIX CoreRun ana makinesi](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/unixcorerun) coreclrhost. h kullanarak daha karmaşık ve gerçek bir barındırma örneğini göstermektedir.

### <a name="step-1---find-and-load-coreclr"></a>1\. adım-CoreCLR bulma ve yükleme

.NET Core çalışma zamanı API 'Leri *CoreCLR. dll* (Windows 'da), *libcoreclr.so* (Linux üzerinde) veya *libcoreclr. dylib* (MacOS 'ta) içinde bulunur. .NET Core barındırmak için ilk adım CoreCLR kitaplığını yüklemek. Bazı konaklar farklı yolları araştırırken veya başkalarının belirli bir yoldan (örneğin, ana bilgisayarın yanında veya makine genelindeki bir konumdan) yüklenmesini öğrenirken, kitaplığı bulmak için giriş parametrelerini kullanır.

Oluşturulduktan sonra, kitaplık (Windows 'da) `LoadLibraryEx` veya `dlopen` (Linux/Mac üzerinde) ile yüklenir.

[!code-cpp[CoreClrHost#1](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>2\. adım-.NET Core barındırma işlevlerini edinme

CoreClrHost, .NET Core 'u barındırmak için yararlı çeşitli önemli yöntemlere sahiptir:

* `coreclr_initialize`: .NET Core çalışma zamanını başlatır ve varsayılan (ve yalnızca) AppDomain 'i ayarlar.
* `coreclr_execute_assembly`: Yönetilen bir derlemeyi yürütür.
* `coreclr_create_delegate`: Yönetilen metoda bir işlev işaretçisi oluşturur.
* `coreclr_shutdown`: .NET Core çalışma zamanını kapatır.
* `coreclr_shutdown_2`: Benzer `coreclr_shutdown`şekilde, ancak yönetilen kodun çıkış kodunu da alır.

CoreCLR kitaplığı 'nı yükledikten sonra, bir sonraki adım bu işlevlere (Windows 'da) veya `GetProcAddress` `dlsym` (Linux/Mac 'te) kullanarak başvuru almaya yönelik olur.

[!code-cpp[CoreClrHost#2](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>3\. adım-çalışma zamanı özelliklerini hazırlama

Çalışma zamanına başlamadan önce, bazı özelliklerin davranışı belirtmek için (özellikle de derleme yükleyicisindeki) hazırlanması gerekir.

Ortak özellikler şunlardır:

* `TRUSTED_PLATFORM_ASSEMBLIES`Bu, çalışma zamanının varsayılan olarak çözebileceği derleme yollarının (Windows üzerinde '; ' ve Linux üzerinde ': ' ile ayrılmış) bir listesidir. Bazı konaklarda, yükleyebilecekleri derlemeleri listelemek için sabit kodlanmış bildirimler vardır. Diğerleri, belirli konumlara (örneğin, *CoreCLR. dll*' den sonra) bu listedeki tüm kitaplıkları yerleştirir.
* `APP_PATHS`Bu, bir derleme için içinde araştırma yapılacak yolların bir listesidir ve Güvenilir Platform derlemeleri (TPA) listesinde bulunamamıştır. Konakta TPA listesi kullanılarak hangi derlemelerin yüklendiği üzerinde daha fazla denetime sahip olduğu için, ana bilgisayarların yüklenmesini bekledikleri derlemeleri belirlemesi ve bunları açıkça listelemeleri için en iyi uygulamadır. Ancak çalışma zamanında yoklama gerekiyorsa, bu özellik bu senaryoyu etkinleştirebilir.
* `APP_NI_PATHS`Bu liste, yerel görüntüler için araştırılan yollar olması dışında APP_PATHS öğesine benzerdir.
* `NATIVE_DLL_SEARCH_DIRECTORIES`Bu özellik, p/Invoke aracılığıyla çağrılan yerel kitaplıkları ararken yükleyicinin araştırması gereken yolların bir listesidir.
* `PLATFORM_RESOURCE_ROOTS`Bu liste, kaynak uydu derlemeleri (kültüre özgü alt dizinlerde) için araştırmanın yollarını içerir.

Bu örnek konakta, TPA listesi yalnızca geçerli dizindeki tüm kitaplıklar listelenerek oluşturulur:

[!code-cpp[CoreClrHost#7](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#7)]

Örnek basittir, yalnızca `TRUSTED_PLATFORM_ASSEMBLIES` özelliği gereklidir:

[!code-cpp[CoreClrHost#3](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>4\. adım-çalışma zamanını başlatma

Mscoree. h barındırma API 'sinden (aşağıda açıklanmıştır) farklı olarak CoreCLRHost. h API 'Leri, çalışma zamanını başlatır ve tek bir çağrı ile varsayılan AppDomain 'i oluşturur. İşlevi bir temel yolu, adı ve daha önce açıklanan özellikleri alır ve `hostHandle` parametresi aracılığıyla konağa bir tanıtıcı geri döndürür. `coreclr_initialize`

[!code-cpp[CoreClrHost#4](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>5\. adım-yönetilen kodu çalıştırın!

Çalışma zamanı başlatıldıktan sonra, konak yönetilen kodu çağırabilir. Bu, birkaç farklı yolla yapılabilir. Bu öğreticiye bağlı örnek kod, statik bir `coreclr_create_delegate` yönetilen metoda bir temsilci oluşturmak için işlevini kullanır. Bu API, [derleme adı](../../framework/app-domains/assembly-names.md), ad alanı nitelenmiş tür adı ve yöntem adını girdi olarak alır ve yöntemi çağırmak için kullanılabilecek bir temsilci döndürür.

[!code-cpp[CoreClrHost#5](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#5)]

Bu örnekte, ana bilgisayar artık `managedDelegate` `ManagedWorker.DoWork` yöntemi çalıştırmak için çağırabilir.

Alternatif olarak, `coreclr_execute_assembly` işlev yönetilen bir yürütülebilir dosyayı başlatmak için kullanılabilir. Bu API, giriş parametreleri olarak bir derleme yolu ve bağımsız değişken dizisi alır. Derlemeyi o yolda yükler ve Main metodunu çağırır.

```C++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>6\. adım-kapatıp Temizleme

Son olarak, konak yönetilen kod çalıştırmayı tamamladıktan sonra .NET Core çalışma zamanı veya `coreclr_shutdown` `coreclr_shutdown_2`ile kapanır.

[!code-cpp[CoreClrHost#6](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#6)]

CoreCLR yeniden başlatma veya kaldırmayı desteklemiyor. Yeniden çağırmayın `coreclr_initialize` veya CoreCLR kitaplığını kaldırın.

## <a name="create-a-host-using-mscoreeh"></a>Mscoree. h kullanarak bir konak oluşturma

Daha önce bahsedildiği gibi, CoreClrHost. h artık .NET Core çalışma zamanını barındırmak için tercih edilen yöntemdir. `ICLRRuntimeHost4` Arabirim hala kullanılabilir değilse, coreclrhost. h arabirimleri yeterli değilse (örneğin, varsayılan etki alanında bir AppDomainManager gerekliyse), ancak standart olmayan başlangıç bayrakları gerekliyse. Bu yönergeler, mscoree. h kullanarak .NET Core barındırmada size kılavuzluk eder.

[Corerun Host](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun) , mscoree. h kullanarak daha karmaşık, gerçek bir barındırma örneğini göstermektedir.

### <a name="a-note-about-mscoreeh"></a>Mscoree. h hakkında bir Note
.Net `ICLRRuntimeHost4` Core barındırma arabirimi, mscoree içinde tanımlanmıştır [. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Bu dosyanın (mscoree. h), ana bilgisayarın başvurması gereken üst bilgi sürümü, [.NET Core çalışma zamanı](https://github.com/dotnet/coreclr/) oluşturulduğunda MIDL aracılığıyla üretilir. .NET Core çalışma zamanını derlemek istemiyorsanız, mscoree. h Ayrıca DotNet/CoreCLR deposunda [önceden oluşturulmuş bir üstbilgi](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) olarak da kullanılabilir. [.NET Core çalışma zamanı oluşturma yönergeleri](https://github.com/dotnet/coreclr#building-the-repository) GitHub deposunda bulunabilir.

### <a name="step-1---identify-the-managed-entry-point"></a>1\. adım-yönetilen giriş noktasını tanımla
Gerekli üstbilgilere (örneğin,[Mscoree. h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) ve stdio. h) başvurulduktan sonra, .NET Core ana bilgisayarının yapması gereken ilk şeylerden biri, kullanacağı yönetilen giriş noktasını bulmalıdır. Örnek ana sistemimizde bu, `main` yöntemi yürütülecek bir yönetilen ikilinin yolu olarak ana bilgisayar için yalnızca ilk komut satırı bağımsız değişkeni alınarak yapılır.

[!code-cpp[NetCoreHost#1](~/samples/core/hosting/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>2\. adım-CoreCLR bulma ve yükleme
.NET Core çalışma zamanı API 'Leri *CoreCLR. dll* ' de (Windows üzerinde) bulunur. Barındırma arabirimimizi (`ICLRRuntimeHost4`) almak için *CoreCLR. dll dosyasını*bulup yüklemeniz gerekir. *CoreCLR. dll*' nin nasıl bulunacağını gösteren bir kural tanımlamak, ana bilgisayara yöneliktir. Bazı konaklar, dosyanın iyi bilinen bir makine genelinde konuma (örneğin, *%ProgramFiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*) sahip olmasını bekler. Diğer kişiler, *CoreCLR. dll ' nin* , ana bilgisayarın kendisinin veya barındırılacak uygulamanın yanındaki bir konumdan yükleneceğini bekler. Hala diğerleri kitaplığı bulmak için bir ortam değişkenine danışmayı de gerektirebilir.

Linux veya Mac üzerinde, çekirdek çalışma zamanı kitaplığı sırasıyla *libcoreclr.so* veya *libcoreclr. dylib*olur.

Örnek ana bilgisayar *CoreCLR. dll*için bazı yaygın konumları yoklamız. Bu, (veya `LoadLibrary` `dlopen` Linux/Mac) aracılığıyla yüklenmelidir.

[!code-cpp[NetCoreHost#2](~/samples/core/hosting/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a>3\. adım-bir ICLRRuntimeHost4 örneği edinme
Barındırma arabirimi, `dlsym` üzerinde `GetProcAddress` (veyaLinux/Mac)çağrılarakvesonrabuişleviçağırarakalınır.`GetCLRRuntimeHost` `ICLRRuntimeHost4`

[!code-cpp[NetCoreHost#3](~/samples/core/hosting/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a>4\. adım-başlangıç bayraklarını ayarlama ve çalışma zamanını başlatma
Bir `ICLRRuntimeHost4` arada, artık çalışma zamanı genelinde başlangıç bayraklarını belirtebilir ve çalışma zamanını başlatabiliriz. Başlangıç bayrakları, tek bir AppDomain veya birden çok AppDomain kullandığımızda ve hangi yükleyici iyileştirme ilkesinin kullanılacağını (örneğin, derlemelerin etki alanı içi yüklemesi için) hangi çöp toplayıcısının (GC) kullanılacağını (eş zamanlı veya sunucu) belirtir.

[!code-cpp[NetCoreHost#4](~/samples/core/hosting/HostWithMscoree/host.cpp#4)]

Çalışma zamanı, `Start` işleve bir çağrı ile başlatılır.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>5\. adım-AppDomain ayarlarını hazırlama
Çalışma zamanı başlatıldıktan sonra bir AppDomain kurmak istiyoruz. Ancak, bir .NET AppDomain oluştururken belirtilmesi gereken birkaç seçenek vardır; bu nedenle öncelikle bunları hazırlamak gerekir.

AppDomain bayrakları, güvenlik ve birlikte çalışabilirlik ile ilgili AppDomain davranışlarını belirtir. Daha eski Silverlight konakları bu ayarları Sandbox Kullanıcı koduna kullanır, ancak modern .NET Core ana bilgisayarları Kullanıcı kodunu tam güven olarak çalıştırır ve birlikte çalışabilirliği etkinleştirir.

[!code-cpp[NetCoreHost#5](~/samples/core/hosting/HostWithMscoree/host.cpp#5)]

Hangi AppDomain kullanım bayraklarını kullanacağınızı saptarken, AppDomain özellikleri tanımlanmalıdır. Özellikler, dizelerin anahtar/değer çiftleridir. Özelliklerin çoğu, AppDomain 'in derlemeleri nasıl yükleceğiyle ilgilidir.

Ortak AppDomain özellikleri şunları içerir:

* `TRUSTED_PLATFORM_ASSEMBLIES`Bu, AppDomain 'in yükleme ve tam güven (kısmen `;` güvenilen etki alanlarında `:` bile) için öncelik vermesi gereken derleme yollarının (Windows ve Linux üzerinde ile ayrılmış) bir listesidir. Bu liste, .NET Framework senaryolarındaki GAC 'ye benzer şekilde ' Framework ' derlemelerini ve diğer güvenilen modülleri içermesi için tasarlanmıştır. Bazı konaklar, bu listede *CoreCLR. dll ' nin* yanına bir kitaplık koyar, diğerlerinin güvenilen derlemeleri bu şekilde listelemesine yönelik sabit kodlanmış bildirimler vardır.
* `APP_PATHS`Bu, bir derleme için içinde araştırma yapılacak yolların bir listesidir ve Güvenilir Platform derlemeleri (TPA) listesinde bulunamamıştır. Konakta TPA listesi kullanılarak hangi derlemelerin yüklendiği üzerinde daha fazla denetime sahip olduğu için, ana bilgisayarların yüklenmesini bekledikleri derlemeleri belirlemesi ve bunları açıkça listelemeleri için en iyi uygulamadır. Ancak çalışma zamanında yoklama gerekiyorsa, bu özellik bu senaryoyu etkinleştirebilir.
* `APP_NI_PATHS`Bu liste, yerel görüntüler için araştırılan yollar olması dışında APP_PATHS 'e çok benzer.
* `NATIVE_DLL_SEARCH_DIRECTORIES`Bu özellik, p/Invoke aracılığıyla çağrılan yerel dll 'Leri ararken yükleyicinin araştırması gereken yolların bir listesidir.
* `PLATFORM_RESOURCE_ROOTS`Bu liste, kaynak uydu derlemeleri (kültüre özgü alt dizinlerde) için araştırmanın yollarını içerir.

[Basit örnek ana](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree)sistemimizde bu özellikler aşağıdaki şekilde ayarlanır:

[!code-cpp[NetCoreHost#6](~/samples/core/hosting/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>6\. adım-AppDomain oluşturma
Tüm AppDomain bayrakları ve özellikleri hazırlandıktan sonra, `ICLRRuntimeHost4::CreateAppDomainWithManager` AppDomain 'i kurmak için kullanılabilir. Bu işlev, isteğe bağlı olarak tam bir derleme adı ve etki alanının AppDomain Yöneticisi olarak kullanılacak tür adını alır. AppDomain Yöneticisi, bir konağın AppDomain davranışının bazı yönlerini denetlemesine izin verebilir ve konak Kullanıcı kodunu doğrudan çağırmayı düşünmüyorsanız yönetilen kodu başlatmak için giriş noktaları sağlayabilir.

[!code-cpp[NetCoreHost#7](~/samples/core/hosting/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>7\. adım-yönetilen kodu çalıştırın!
AppDomain çalışıyor ve çalışır durumda olduğunda, ana bilgisayar artık yönetilen kodu yürütmeye başlayabilir. Bunu yapmanın en kolay yolu, yönetilen bir derlemenin `ICLRRuntimeHost4::ExecuteAssembly` giriş noktası yöntemini çağırmak için kullanmaktır. Bu işlevin yalnızca tek etki alanı senaryolarında çalışıp çalışmadığını unutmayın.

[!code-cpp[NetCoreHost#8](~/samples/core/hosting/HostWithMscoree/host.cpp#8)]

Diğer bir seçenek, `ExecuteAssembly` ana bilgisayarınızın ihtiyaçlarını karşılamıyorsa, statik yönetilen bir yönteme bir `CreateDelegate` işlev işaretçisi oluşturmak için kullanılır. Bu, konağın çağrı yaptığı yöntemin imzasını bilmesini gerektirir (işlev işaretçisi türünü oluşturmak için), ancak bir derlemenin giriş noktası dışında kodu çağırma esnekliğine izin verir. İkinci parametrede belirtilen derleme adı, yüklenecek kitaplığın [tam yönetilen derleme adıdır](../../framework/app-domains/assembly-names.md) .

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

### <a name="step-8---clean-up"></a>8\. adım-temizle
Son olarak, ana bilgisayar etki alanları kaldırılıyor, çalışma zamanını durdurup ve `ICLRRuntimeHost4` başvuruyu serbest bırakarak, ana bilgisayar kendiliğinden temizlemelidir.

[!code-cpp[NetCoreHost#9](~/samples/core/hosting/HostWithMscoree/host.cpp#9)]

CoreCLR, kaldırmayı desteklemiyor. CoreCLR kitaplığını kaldırmayın.

## <a name="conclusion"></a>Sonuç
Ana bilgisayarınız derlendikten sonra, komut satırından çalıştırılarak ve konağın beklediği bağımsız değişkenler (örneğin, yönetilen uygulama, mscoree örnek ana bilgisayarı için çalışır) geçirerek test edilebilir. Konağın çalıştırılacağı .NET Core uygulamasını belirtirken, tarafından `dotnet build`oluşturulan. dll dosyasını kullandığınızdan emin olun. Kendi içindeki uygulamalar için tarafından `dotnet publish` oluşturulan yürütülebilir dosyalar (. exe dosyaları) aslında varsayılan .NET Core ana bilgisayarı (uygulamanın ana hat senaryolarında doğrudan komut satırından başlatılabilmesi için), Kullanıcı kodu aynı ada sahip bir dll 'de derlenir.

İlk başta çalışmazsa, *CoreCLR. dll* ' nin ana bilgisayar tarafından beklenen konumda kullanılabilir olduğunu, tüm gerekli çerçeve kitaplıklarının TPA listesinde olduğunu ve CoreCLR 'nin bitme (32-veya 64-bit) konağın nasıl derlendiğine uygun olduğunu kontrol edin.

.NET Core çalışma zamanının barındırılması, birçok geliştiricinin gerek duymayacağı, ancak yerel bir işlemden yönetilen kodu başlatması gereken veya .NET Core çalışma zamanının davranışı üzerinde daha fazla denetime ihtiyaç duyan bir Gelişmiş senaryodur. Bu, çok faydalı olabilir.
