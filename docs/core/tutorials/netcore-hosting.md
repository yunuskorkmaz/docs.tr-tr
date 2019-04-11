---
title: Özel bir .NET Core çalışma zamanı ana bilgisayarı yazma
description: .NET Core çalışma zamanı nasıl çalıştığını denetleme gerektiren gelişmiş senaryoları desteklemek için yerel koddan .NET Core çalışma zamanı ana öğrenin.
author: mjrousos
ms.date: 12/21/2018
ms.custom: seodec18
ms.openlocfilehash: 53cdc13d5a356a2975182c58374a0e9c6639ec17
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481151"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Yerel koddan .NET çalışma zamanı denetlemek için özel bir .NET Core konak yazma

Tüm yönetilen kod gibi .NET Core uygulamaları bir ana bilgisayar tarafından yürütülür. Konak, çalışma zamanı (bileşenler JIT ve çöp toplayıcı gibi) başlangıç ve yönetilen giriş noktaları çağırma sorumludur.

.NET Core çalışma zamanı barındırma Gelişmiş bir senaryodur ve çoğu durumda, .NET Core geliştiricilerinin .NET Core derleme nedeni işlemleri barındırma hakkında endişelenmeniz gerekmez, .NET Core uygulamaları çalıştırmak için bir varsayılan konak sağlar. Bazı özel durumlarda, yine de bu açıkça barındırmak için .NET Core çalışma zamanı yerel işlem veya çalışma zamanı nasıl çalıştığını daha fazla denetim kazanmak için yönetilen kod yürütmesini bir yolu olarak ya da yararlı olabilir.

Bu makalede, yerel koddan .NET Core çalışma zamanı başlatma ve yönetilen kodu çalıştırmak için gerekli adımları genel bir bakış sağlar.

## <a name="prerequisites"></a>Önkoşullar

Yerel uygulamalar konak olmadığından, bu öğreticide .NET Core barındırmak için bir C++ uygulaması oluşturmak ele alınacaktır. Bir C++ geliştirme ortamı gerekir (tarafından sağlanan gibi [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).

Bu nedenle yükleme yapılmalıdır Ayrıca, ana bilgisayarı sınamak için basit bir .NET Core uygulaması isteyeceksiniz [.NET Core SDK'sı](https://www.microsoft.com/net/core) ve [küçük .NET Core uygulaması derleme](../../core/tutorials/with-visual-studio.md) (örneğin, bir 'Merhaba Dünya' uygulama). Yeni .NET Core konsol proje şablonu tarafından oluşturulan 'Hello World' uygulama yeterlidir.

## <a name="hosting-apis"></a>API'leri barındırma
.NET Core konağı için kullanılabilecek iki farklı API vardır. Bu belge (ve ilişkili [örnekleri](https://github.com/dotnet/samples/tree/master/core/hosting)) iki seçenek de kapsar.

* .NET Core çalışma zamanı barındırma tercih edilen yöntemi olan [CoreClrHost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h) API. Bu API işlevleri kolayca başlatmak için kullanıma sunar ve çalışma zamanı durduruluyor ve bunları çağırırken yönetilen kod (veya yönetilen bir exe açarak yönetilen statik yöntemleri çağırarak).
* .NET core de barındırılabilir ile `ICLRRuntimeHost4` arabiriminde [mscoree.h](https://github.com/dotnet/coreclr/blob/master/src/pal/prebuilt/inc/mscoree.h). Eski konakları kullanmadan görülen şekilde bu API CoreClrHost.h, daha uzun etrafında olmuştur. Hala çalışır ve CoreClrHost daha barındırma işlemi üzerinde biraz daha fazla denetim sağlar. Çoğu senaryo için yine de CoreClrHost.h artık, daha basit API'ler nedeniyle tercih edilir.

## <a name="sample-hosts"></a>Örnek konakları
[Örnek konakları](https://github.com/dotnet/samples/tree/master/core/hosting) öğreticilerde özetlenen adımları gösteren kullanılabilir dotnet/samples GitHub deposunda. Örneklerin açıklamaları açıkça bu öğreticilerden numaralandırılmış adımları örnek burada çalıştırıldığını ile ilişkilendirin. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Bu nedenle bunlar üzerinde hata denetimi açık ve verimlilik üzerinde okunabilirliği vurgulamak için tasarlanmış, öğrenme amacıyla kullanılacak örnek konakları yöneliktir aklınızda bulundurun. Daha fazla gerçek ana bilgisayar örneği kullanılabilir [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) depo. [CoreRun konak](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun) ve [UNIX CoreRun konak](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/unixcorerun), özellikle de daha basit örneklerin okuduktan sonra incelemek için iyi bir genel amaçlı konakları olan.

## <a name="create-a-host-using-coreclrhosth"></a>CoreClrHost.h kullanarak bir konağı oluşturma

Aşağıdaki adımları CoreClrHost.h API .NET Core çalışma zamanı yerel bir uygulama ve yönetilen bir statik yöntem çağrısına başlatmak için nasıl kullanılacağını açıklamaktadır. Bu belgede yer alan kod parçacıkları bazı Windows özel API'leri kullanın ancak [tam örnek konak](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) hem Windows hem de Linux kod yollarını gösterir.

### <a name="step-1---find-and-load-coreclr"></a>Adım 1 - bulma ve yükleme CoreCLR

.NET Core çalışma zamanı API'leri bulunan *coreclr.dll* (Windows) şirket içinde *libcoreclr.so* (Linux) üzerinde veya *libcoreclr.dylib* (macos'ta). .NET Core barındırma ilk adımı, CoreCLR kitaplığını sağlamaktır. Bazı konakların farklı yollarını araştırma veya başkalarının belirli bir yolda (konak, örneğin yanındaki veya bir makine genelindeki konumdan) yükleyin bilmeleri sırada kitaplığı bulmak için giriş parametrelerini kullanın.

Bir kez bulundu, kitaplığı ile yüklenen `LoadLibraryEx` (Windows üzerinde) veya `dlopen` (üzerinde Linux/Mac).

[!code-cpp[CoreClrHost#1](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>Adım 2 - Get .NET Core barındırma işlevleri

.NET Core barındırma için çeşitli önemli yöntemler yararlı CoreClrHost sahiptir:

* `coreclr_initialize`: .NET Core çalışma zamanı başlar ve varsayılan ayarlar (ve yalnızca) AppDomain.
* `coreclr_execute_assembly`: Eğer yönetilmiş bir derlemeyi yürütür.
* `coreclr_create_delegate`: Bir işlev işaretçisi ile yönetilen bir yöntem oluşturur.
* `coreclr_shutdown`: .NET Core çalışma zamanı kapatır.
* `coreclr_shutdown_2`: Gibi `coreclr_shutdown`, ancak ayrıca yönetilen kodun çıkış kodu alır.

CoreCLR kitaplığı yüklendikten sonra sonraki adıma kullanarak bu işlevlere yönelik başvurulara almaktır `GetProcAddress` (Windows üzerinde) veya `dlsym` (üzerinde Linux/Mac).

[!code-cpp[CoreClrHost#2](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>Adım 3 - çalışma zamanı özellikleri hazırlama

Çalışma zamanı'nı başlatmadan önce bazı özellikler (bütünleştirilmiş kod yükleyicisini özellikle ilgili) davranışını belirtmek için hazırlamak üzere gereklidir.

Ortak özellikler şunlardır:

* `TRUSTED_PLATFORM_ASSEMBLIES`
  Bu bir bütünleştirilmiş kodu yolları listesidir (Windows üzerinde ';' ile ayrılmış ve ':' Linux üzerinde), çalışma zamanı varsayılan olarak çözümleyebilmesi. Bazı ana bilgisayarlar, sabit kodlanmış bildirimlerinin derlemeleri yüklemek listesi vardır. Diğer tüm kitaplık belirli konumlara koyduğunuzdan (yanındaki *coreclr.dll*, örneğin) bu listede.
* `APP_PATHS`
  Bu araştırma için bir derleme'da güvenilir platform derlemeleri (TPA) listesinde bulunamazsa yollarının bir listesidir. Daha fazla denetim TPA listesini kullanarak derlemeleri üzerinde yüklü olan konak olduğundan, yüklemek ve bunları doğrudan belirterek listelemek için beklediği hangi derlemelerin belirlemek ana bilgisayarlar için en iyi yöntem var. Ancak, çalışma zamanında yoklama gerekirse bu özellik bu senaryonun etkinleştirebilirsiniz.
*  `APP_NI_PATHS` Bu liste, yerel görüntüler için araştırıldığı yolları olacak şekilde hazırlanmıştır dışında APP_PATHS için benzerdir.
*  `NATIVE_DLL_SEARCH_DIRECTORIES` Bu özellik, p/Invoke yerel kitaplıklar aranıyor çağrıldığı zaman yükleyici araştırma yolları bir listesidir.
*  `PLATFORM_RESOURCE_ROOTS` Bu liste, kaynak uydu derlemelerine (kültüre özgü alt dizinlerde) için araştırmaya yolları içerir.

Bu örnek konak TPA listenin geçerli dizindeki tüm kitaplıkları listeleyerek oluşturulur:

[!code-cpp[CoreClrHost#7](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#7)]

Örneği basit olduğundan, yalnızca gereken `TRUSTED_PLATFORM_ASSEMBLIES` özelliği:

[!code-cpp[CoreClrHost#3](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>4. adım: çalışma zamanını başlatma

Mscoree.h aksine (aşağıda açıklanmıştır) barındırma API'si, CoreCLRHost.h API'leri çalışma zamanını başlatma ve tümü tek bir çağrı ile ' % s'varsayılan uygulama etki alanı oluşturun. `coreclr_initialize` İşlevini, daha önce açıklanan özellikler taban yolu ve adı alır ve döndürür, barındırmak için bir tanıtıcı geri `hostHandle` parametresi.

[!code-cpp[CoreClrHost#4](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>5. adım - yönetilen kodu çalıştırma!

Başlatıldı çalışma zamanı ile yönetilen kod ana bilgisayar çağırabilirsiniz. Bu, birkaç farklı yöntemle içinde yapılabilir. Örnek kod, Bu öğretici kullanım bağlı `coreclr_create_delegate` statik bir yönetilen yöntemi temsilci oluşturmak için işlev. Bu API alan [derleme adı](../../framework/app-domains/assembly-names.md), ad alanıyla nitelenen tür adı ve girdi ve yöntemini çağırmak için kullanılan bir temsilci döndürür yöntemi adı.

[!code-cpp[CoreClrHost#5](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#5)]

Bu örnekte, konak çağırabilirsiniz `managedDelegate` çalıştırılacak `ManagedWorker.DoWork` yöntemi.

Alternatif olarak, `coreclr_execute_assembly` işlevi, yönetilen bir yürütülebilir dosyayı başlatmak için kullanılabilir. Bu API, bir derleme yolu ve bağımsız değişken dizisi, giriş parametre olarak alır. Bu yol, derleme yüklenir ve onun ana yöntemini çağırır.

```C++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>Adım 6 - Kapat ve Temizle

Ana çalışan yönetilen kod yapıldığında, son olarak, .NET Core çalışma zamanı ile kapatılmış `coreclr_shutdown` veya `coreclr_shutdown_2`.

[!code-cpp[CoreClrHost#6](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#6)]

CoreCLR, yeniden başlatma veya kaldırılmasını desteklemez. Çağırmayın `coreclr_initialize` yeniden veya CoreCLR kitaplığı kaldırma.

## <a name="create-a-host-using-mscoreeh"></a>Mscoree.h kullanarak bir konağı oluşturma

Daha önce belirtildiği gibi CoreClrHost.h artık .NET Core çalışma zamanı barındırma için tercih edilen yöntemdir. `ICLRRuntimeHost4` Arabirimi hala kullanılabilir, ancak CoreClrHost.h arabirimleri yeterli değilse (standart başlangıç bayrakları gibi gerekli olup olmadığını veya varsayılan etki alanına bir AppDomainManager gerekiyorsa). Bu yönergeler mscoree.h kullanarak .NET Core barındırma aracılığıyla size yol gösterir.

### <a name="a-note-about-mscoreeh"></a>Mscoree.h hakkında bir Not
`ICLRRuntimeHost4` .NET Core barındırma arabiriminin tanımlanmış [MSCOREE. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Bir üst bilgi sürümü ana başvuruda bulunmanız gerekir, bu dosyanın (mscoree.h) MIDL üretilen olduğunda [.NET Core çalışma zamanı](https://github.com/dotnet/coreclr/) oluşturulmuştur. .NET Core çalışma zamanı oluşturmak istemiyorsanız mscoree.h olarak da kullanılabilir bir [önceden derlenmiş üst bilgi](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) dotnet/coreclr deposunda. [.NET Core çalışma zamanı oluşturma hakkında yönergeler](https://github.com/dotnet/coreclr#building-the-repository) kendi GitHub deposunda bulunabilir.

### <a name="step-1---identify-the-managed-entry-point"></a>1. adım - yönetilen giriş noktasını tanımlayın
Gerekli üst bilgileri başvuran sonra ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) ve örneğin, stdıo.h), bir .NET Core konak gerçekleştirmelisiniz gereken ilk unsur biridir, kullanacağınız yönetilen giriş noktasını bulun. Bizim örnek konak bu yalnızca ilk komut satırı bağımsız değişkeni bizim konağa yönetilen ikili bir yolu olarak yararlanarak gerçekleştirilir, `main` yöntemi yürütülür.

[!code-cpp[NetCoreHost#1](~/samples/core/hosting/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>Adım 2 - bulma ve yükleme CoreCLR
.NET Core çalışma zamanı API'leri bulunan *CoreCLR.dll* (Windows üzerinde). Barındırma arabirimimizi almak için (`ICLRRuntimeHost4`), bulmak ve yüklemek için gerekli olan *CoreCLR.dll*. Nasıl bulur bir kural tanımlamak için ana kadar olan *CoreCLR.dll*. Bazı konakların dosyanın iyi bilinen bir makineye konumda mevcut olmasını beklediğiniz (gibi *%programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*). Başkalarının beklediğiniz *CoreCLR.dll* ya da yanında bir konumdan kendisini veya barındırılması için uygulama yüklenmeyecek. Yine de diğer kitaplığı bulmak için bir ortam değişkeni başvurun.

Linux veya Mac üzerinde temel çalışma zamanı kitaplığı olan *libcoreclr.so* veya *libcoreclr.dylib*sırasıyla.

Bizim örnek konak için bazı ortak konumları araştırmaları *CoreCLR.dll*. Bir kez bulundu, onu aracılığıyla yüklenmesi gereken `LoadLibrary` (veya `dlopen` Linux/Mac üzerinde).

[!code-cpp[NetCoreHost#2](~/samples/core/hosting/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a>3. adım: ICLRRuntimeHost4 örneğini alma
`ICLRRuntimeHost4` Arabirimi barındırma alınır çağırarak `GetProcAddress` (veya `dlsym` Linux/Mac üzerinde) üzerinde `GetCLRRuntimeHost`ve ardından bu işlev çağırma.

[!code-cpp[NetCoreHost#3](~/samples/core/hosting/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a>4. adım - başlangıç bayraklarını ayarlayın ve çalışma zamanını başlatma
İle bir `ICLRRuntimeHost4` yakından, biz artık çalışma zamanı genelinde başlangıç bayrakları belirtin ve çalışma zamanı'nı başlatın. Başlangıç bayrakları, hangi atık tek bir AppDomain veya birden çok AppDomains kullanacağız olup olmadığını (eşzamanlı veya sunucu) kullanmak için toplayıcı (GC) ve (etki alanından bağımsız derlemeler için yüklenmesini) kullanmak için hangi yükleyici iyileştirme ilkesini belirler.

[!code-cpp[NetCoreHost#4](~/samples/core/hosting/HostWithMscoree/host.cpp#4)]

Çalışma zamanı, çağrı kullanmaya `Start` işlevi.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Adım 5 - AppDomain hazırlama ayarları
Çalışma zamanı başlatıldıktan sonra biz AppDomain ayarlamak istersiniz. Bu ilk hazırlamak gereklidir, ancak bir .NET AppDomain oluştururken belirtilmelidir birkaç seçenek vardır.

AppDomain bayrakları, güvenlik ve birlikte çalışabilirlik ile ilgili AppDomain davranışları belirtin. Bu ayarlar için korumalı alan kullanıcı kodu eski Silverlight ana kullanılan, ancak çoğu modern .NET Core konakları kullanıcı kod tam güven çalıştırın ve birlikte çalışabilirliği etkinleştirmek.

[!code-cpp[NetCoreHost#5](~/samples/core/hosting/HostWithMscoree/host.cpp#5)]

Hangi kullanılacak AppDomain bayrakları karar verdikten sonra AppDomain özellikleri tanımlanması gerekir. Anahtar/değer çiftlerinin dize özelliklerdir. Özelliklerin birçoğu, AppDomain derlemeleri nasıl yükleneceğini için ilgilidir.

Ortak AppDomain özellikler şunlardır:

* `TRUSTED_PLATFORM_ASSEMBLIES`
  Bu bir bütünleştirilmiş kodu yolları listesidir (tarafından ayrılmış `;` Windows üzerinde ve `:` Linux/Mac üzerinde), AppDomain (kısmen güvenilen etki alanlarında çift için), yükleme ve verin tam güven öncelik vermelisiniz. Bu liste 'Framework' derlemeleri ve diğer güvenilen modüller, .NET Framework senaryoları GAC'de benzer içerecek şekilde tasarlanmıştır. Bazı konakların kitaplık yanındaki sokar *coreclr.dll* bu listede, diğer sabit kodlanmış bildirimleri kendi amaçları için güvenilir bütünleştirilmiş kodların listesi vardır.
* `APP_PATHS`
  Bu araştırma için bir derleme'da güvenilir platform derlemeleri (TPA) listesinde bulunamazsa yollarının bir listesidir. Daha fazla denetim TPA listesini kullanarak derlemeleri üzerinde yüklü olan konak olduğundan, yüklemek ve bunları doğrudan belirterek listelemek için beklediği hangi derlemelerin belirlemek ana bilgisayarlar için en iyi yöntem var. Ancak, çalışma zamanında yoklama gerekirse bu özellik bu senaryonun etkinleştirebilirsiniz.
*  `APP_NI_PATHS` Yerel görüntüler için araştırıldığı yolları olacak şekilde hazırlanmıştır dışında bu liste için APP_PATHS çok benzer.
*  `NATIVE_DLL_SEARCH_DIRECTORIES` Bu özellik, p/Invoke Yerel DLL'leri çağrıldığı zaman yükleyici araştırma yolları bir listesidir.
*  `PLATFORM_RESOURCE_ROOTS` Bu liste, kaynak uydu derlemelerine (kültüre özgü alt dizinlerde) için araştırmaya yolları içerir.

İçinde bizim [basit örnek konak](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree), bu özellikler aşağıdaki ayarlamaları yapın:

[!code-cpp[NetCoreHost#6](~/samples/core/hosting/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>6. adım: uygulama etki alanı oluşturma
Tüm AppDomain bayraklar ve Özellikler hazır sonra `ICLRRuntimeHost4::CreateAppDomainWithManager` AppDomain ayarlamak için kullanılabilir. Bu işlev, isteğe bağlı olarak bir tam derleme adını ve etki alanının AppDomain Yöneticisi kullanmak üzere tür adı alır. AppDomain Yöneticisi bazı yönlerini AppDomain davranışını denetlemek bir konak izin verebilir ve giriş noktaları, konak kullanıcı kodu doğrudan çağırmak istiyorsanız değil, yönetilen kod başlatmak için sağlayabilir.

[!code-cpp[NetCoreHost#7](~/samples/core/hosting/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>7. adım - yönetilen kodu çalıştırma!
AppDomain ile çalışmaya, ana bilgisayar artık yönetilen kod başlatabilirsiniz. Bunu yapmanın en kolay yolu kullanmaktır `ICLRRuntimeHost4::ExecuteAssembly` yönetilen derlemenin giriş noktası yöntemini çağırmak için. Bu işlev yalnızca tek etki alanlı senaryolarda çalıştığını unutmayın.

[!code-cpp[NetCoreHost#8](~/samples/core/hosting/HostWithMscoree/host.cpp#8)]

Başka bir seçenek, varsa `ExecuteAssembly` ana bilgisayarınızın gereksinimlerini karşılamıyor, kullanmaktır `CreateDelegate` Yönetilen yöntemi statik bir işlev işaretçisine oluşturmak için. Bu konak noktası (işlev işaretçisi türü oluşturmak için) çağırma olan ancak ana bilgisayar bütünleştirilmiş kodun giriş dışındaki kod çağırmak esneklik sağlar metodun imzası bilmek gerektirir. İkinci parametre sağlanan derleme adı [tam yönetilen bütünleştirilmiş kod adı](../../framework/app-domains/assembly-names.md) kitaplığı yüklenemedi.

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

### <a name="step-8---clean-up"></a>8 - temizleme adım
Son olarak, ana bilgisayar kendisini sonra uygulama etki alanları kaldırma, çalışma zamanı durdurma ve serbest bırakma temizlemek `ICLRRuntimeHost4` başvuru.

[!code-cpp[NetCoreHost#9](~/samples/core/hosting/HostWithMscoree/host.cpp#9)]

CoreCLR kaldırılmasını desteklemez. CoreCLR kitaplığı bellekten değil.

## <a name="conclusion"></a>Sonuç
Konağınız oluşturulduktan sonra komut satırından çalıştırarak test edilebilir ve konak herhangi bir bağımsız değişken geçirme (gibi mscoree örnek ana bilgisayar için çalıştırmak istediğiniz yönetilen uygulamayı) bekliyor. .NET Core uygulaması çalıştırmak ana bilgisayar için belirtirken tarafından üretilen .dll dosyasını kullanmaya dikkat edin `dotnet build`. Yürütülebilir dosyalar (.exe dosyaları) tarafından üretilen `dotnet publish` gerçekten varsayılan kendi içindeki uygulamaları için .NET Core barındıran (uygulamayı doğrudan ana hat senaryolarda komut satırından başlatılabilir böylece); kullanıcı kodu aynı ada sahip bir dll içine derlenmiş.

Şeyler başlangıçta işe yaramazsa, sağlayamazsanız *coreclr.dll* TPA listesinde gerekli tüm Framework kitaplıkları ve o CoreCLR'ın bit genişliği (32 veya 64-bit) ile eşleşen konak tarafından beklenen konumda kullanılabilir nasıl konak oluşturulmuştur.

.NET Core çalışma zamanı barındırma birçok geliştiricinin yapılması gerekmez, ancak bunlar için yönetilen koddan yerel işlem veya .NET Core çalışma zamanı davranışı hakkında daha fazla denetime gereksinim duyan başlatmak gereksinim duyan İleri düzey bir senaryodur, çok kullanışlı olabilir.
