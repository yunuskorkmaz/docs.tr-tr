---
title: Özel bir .NET Core çalışma zamanı ana bilgisayarı yazma
description: .NET Core çalışma zamanı nasıl çalıştığını denetleme gerektiren gelişmiş senaryoları desteklemek için yerel koddan .NET Core çalışma zamanı ana öğrenin.
author: mjrousos
ms.date: 02/03/2017
ms.custom: seodec18
ms.openlocfilehash: 861a02d2e409637d11c874f16ecd56a1a0fcd92a
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169644"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Yerel koddan .NET çalışma zamanı denetlemek için özel bir .NET Core konak yazma

Tüm yönetilen kod gibi .NET Core uygulamaları bir ana bilgisayar tarafından yürütülür. Ana bilgisayar sorumlu çalışma zamanı (atık toplayıcı ve JIT gibi bileşenler dahil olmak üzere) başlatmak için giriş noktaları yönetilen uygulama etki alanları oluşturma ve çağırma.

.NET Core çalışma zamanı barındırma Gelişmiş bir senaryodur ve çoğu durumda, .NET Core geliştiricilerinin .NET Core derleme nedeni işlemleri barındırma hakkında endişelenmeniz gerekmez, .NET Core uygulamaları çalıştırmak için bir varsayılan konak sağlar. Bazı özel durumlarda, yine de bu açıkça barındırmak için .NET Core çalışma zamanı yerel işlem veya çalışma zamanı nasıl çalıştığını daha fazla denetim kazanmak için yönetilen kod yürütmesini bir yolu olarak ya da yararlı olabilir.

Bu makalede, yerel koddan .NET Core çalışma zamanı başlangıç, ilk uygulama etki alanı oluşturmak için gerekli adımları genel bir fikir veren (<xref:System.AppDomain>) ve yönetilen kod yürütün.

## <a name="prerequisites"></a>Önkoşullar

Yerel uygulamalar konak olmadığından, bu öğreticide .NET Core barındırmak için bir C++ uygulaması oluşturmak ele alınacaktır. Bir C++ geliştirme ortamı gerekir (tarafından sağlanan gibi [Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).

Bu nedenle yükleme yapılmalıdır Ayrıca, ana bilgisayarı sınamak için basit bir .NET Core uygulaması isteyeceksiniz [.NET Core SDK'sı](https://www.microsoft.com/net/core) ve [küçük .NET Core uygulaması derleme](../../core/tutorials/with-visual-studio.md) (örneğin, bir 'Merhaba Dünya' uygulama). Yeni .NET Core konsol proje şablonu tarafından oluşturulan 'Hello World' uygulama yeterlidir.

Bu öğretici ve onun ilişkili örnek bir Windows konak oluşturmak; UNIX barındırma hakkında bu makalenin sonunda notlara bakın.

## <a name="creating-the-host"></a>Konağı oluşturma

A [örnek konak](https://github.com/dotnet/samples/tree/master/core/hosting) şu makalede açıklanan adımları gösteren kullanılabilir dotnet/samples GitHub deposunda. Örnek ait açıklamaları *host.cpp* numaralı adımlar burada örnekte çalıştırıldığını ile bu öğreticiden açıkça ilişkilendirme dosya. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Örnek konak ışığı hata denetleme ve verimlilik üzerinde okunabilirliği vurgulamak için tasarlanmış, öğrenme amacıyla kullanılmak üzere tasarlanmıştır aklınızda bulundurun. Daha fazla gerçek ana bilgisayar örneği kullanılabilir [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) depo. [CoreRun konak](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun), özellikle daha basit bir örnek okuduktan sonra incelemek için iyi bir genel amaçlı ana bilgisayardır.

### <a name="a-note-about-mscoreeh"></a>Mscoree.h hakkında bir Not
Arabirimi barındırma birincil .NET Core (`ICLRRuntimeHost2`) tanımlanan [MSCOREE. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Bir üst bilgi sürümü ana başvuruda bulunmanız gerekir, bu dosyanın (mscoree.h) MIDL üretilen olduğunda [.NET Core çalışma zamanı](https://github.com/dotnet/coreclr/) oluşturulmuştur. .NET Core çalışma zamanı oluşturmak istemiyorsanız mscoree.h olarak da kullanılabilir bir [önceden derlenmiş üst bilgi](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) dotnet/coreclr deposunda. [.NET Core çalışma zamanı oluşturma hakkında yönergeler](https://github.com/dotnet/coreclr#building-the-repository) kendi GitHub deposunda bulunabilir. 

### <a name="step-1---identify-the-managed-entry-point"></a>1. adım - yönetilen giriş noktasını tanımlayın
Gerekli üst bilgileri başvuran sonra ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) ve örneğin, stdıo.h), bir .NET Core konak gerçekleştirmelisiniz gereken ilk unsur biridir, kullanacağınız yönetilen giriş noktasını bulun. Bizim örnek konak bu yalnızca ilk komut satırı bağımsız değişkeni bizim konağa yönetilen ikili bir yolu olarak yararlanarak gerçekleştirilir, `main` yöntemi yürütülür.

[!code-cpp[NetCoreHost#1](../../../samples/core/hosting/host.cpp#1)]

### <a name="step-2---find-and-load-coreclrdll"></a>Adım 2 - bulma ve yükleme CoreCLR.dll
.NET Core çalışma zamanı API'leri bulunan *CoreCLR.dll* (Windows üzerinde). Barındırma arabirimimizi almak için (`ICLRRuntimeHost2`), bulmak ve yüklemek için gerekli olan *CoreCLR.dll*. Nasıl bulur bir kural tanımlamak için ana kadar olan *CoreCLR.dll*. Bazı konakların iyi bilinen bir makineye konuma (örneğin, % programfiles%\dotnet\shared\Microsoft.NETCore.App\1.1.0) bulunması dosyası bekler. Başkalarının beklediğiniz *CoreCLR.dll* ya da yanında bir konumdan kendisini veya barındırılması için uygulama yüklenmeyecek. Yine de diğer kitaplığı bulmak için bir ortam değişkeni başvurun.

Linux veya Mac üzerinde temel çalışma zamanı kitaplığı olan *libcoreclr.so* veya *libcoreclr.dylib*sırasıyla.

Bizim örnek konak için bazı ortak konumları araştırmaları *CoreCLR.dll*. Bir kez bulundu, onu aracılığıyla yüklenmesi gereken `LoadLibrary` (veya `dlopen` Linux/Mac üzerinde).

[!code-cpp[NetCoreHost#2](../../../samples/core/hosting/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost2-instance"></a>3. adım: ICLRRuntimeHost2 örneğini alma
`ICLRRuntimeHost2` Arabirimi barındırma alınır çağırarak `GetProcAddress` (veya `dlsym` Linux/Mac üzerinde) üzerinde `GetCLRRuntimeHost`ve ardından bu işlev çağırma. 

[!code-cpp[NetCoreHost#3](../../../samples/core/hosting/host.cpp#3)]

### <a name="step-4---setting-startup-flags-and-starting-the-runtime"></a>Adım 4 - başlangıç bayrakları ayarlama ve çalışma zamanı başlatma
İle bir `ICLRRuntimeHost2` yakından, biz artık çalışma zamanı genelinde başlangıç bayrakları belirtin ve çalışma zamanı'nı başlatın. Başlangıç bayrakları hangi atık tek bir AppDomain veya birden çok AppDomains kullanacağız olup olmadığını (eşzamanlı veya sunucu) kullanmak için toplayıcı (GC) ve (etki alanından bağımsız derlemeler için yüklenmesini) kullanmak için hangi yükleyici iyileştirme ilkesini belirler.

[!code-cpp[NetCoreHost#4](../../../samples/core/hosting/host.cpp#4)]

Çalışma zamanı, çağrı kullanmaya `Start` işlevi.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Adım 5 - AppDomain hazırlama ayarları
Çalışma zamanı başlatıldıktan sonra biz AppDomain ayarlamak istersiniz. Bu ilk hazırlamak gereklidir, ancak bir .NET AppDomain oluştururken belirtilmelidir birkaç seçenek vardır.

AppDomain bayrakları, güvenlik ve birlikte çalışabilirlik ile ilgili AppDomain davranışları belirtin. Bu ayarlar için korumalı alan kullanıcı kodu eski Silverlight ana kullanılan, ancak çoğu modern .NET Core konakları kullanıcı kod tam güven çalıştırın ve birlikte çalışabilirliği etkinleştirmek.

[!code-cpp[NetCoreHost#5](../../../samples/core/hosting/host.cpp#5)]

Hangi kullanılacak AppDomain bayrakları karar verdikten sonra AppDomain özellikleri tanımlanması gerekir. Anahtar/değer çiftlerinin dize özelliklerdir. Özelliklerin birçoğu, AppDomain derlemeleri nasıl yükleneceğini için ilgilidir.

Ortak AppDomain özellikler şunlardır:

* `TRUSTED_PLATFORM_ASSEMBLIES` Bu bir bütünleştirilmiş kodu yolları listesidir (Windows üzerinde ';' ile ayrılmış ve ':' UNIX üzerinde), AppDomain (kısmen güvenilen etki alanlarında çift için), yükleme ve verin tam güven öncelik vermelisiniz. Bu liste 'Framework' derlemeleri ve diğer güvenilen modüller, .NET Framework senaryoları GAC'de benzer içerecek şekilde tasarlanmıştır. Bazı konakların kitaplık yanındaki sokar *coreclr.dll* bu listede, diğer sabit kodlanmış bildirimleri kendi amaçları için güvenilir bütünleştirilmiş kodların listesi vardır.
* `APP_PATHS` Bu araştırma için bir derleme'da güvenilir platform derlemeleri (TPA) listesinde bulunamazsa yollarının bir listesidir. Bu yollar, kullanıcıların derlemelerini bulunabileceği konumları olarak yöneliktir. Bir korumalı alan AppDomain içinde bu yolları yüklenen derlemeler yalnızca kısmi güven verilir. Ortak APP_PATH yolları, hedef uygulama öğesinden yüklenmiş yolu veya burada kullanıcı varlıkları Canlı bilinen diğer konumlar içerir.
*  `APP_NI_PATHS` Yerel görüntüler için araştırıldığı yolları olacak şekilde hazırlanmıştır dışında bu liste için APP_PATHS çok benzer.
*  `NATIVE_DLL_SEARCH_DIRECTORIES` Bu özellik, p/Invoke Yerel DLL'leri çağrıldığı zaman yükleyici araştırma yolları bir listesidir.
*  `PLATFORM_RESOURCE_ROOTS` Bu liste, kaynak uydu derlemelerine (kültüre özgü alt dizinlerde) için araştırmaya yolları içerir.

İçinde bizim [basit örnek konak](https://github.com/dotnet/samples/tree/master/core/hosting), bu özellikler aşağıdaki ayarlamaları yapın:

[!code-cpp[NetCoreHost#6](../../../samples/core/hosting/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>6. adım: uygulama etki alanı oluşturma
Tüm AppDomain bayraklar ve Özellikler hazır sonra `ICLRRuntimeHost2::CreateAppDomainWithManager` AppDomain ayarlamak için kullanılabilir. Bu işlev, isteğe bağlı olarak bir tam derleme adını ve etki alanının AppDomain Yöneticisi kullanmak üzere tür adı alır. AppDomain Yöneticisi bazı yönlerini AppDomain davranışını denetlemek bir konak izin verebilir ve giriş noktaları, konak kullanıcı kodu doğrudan çağırmak istiyorsanız değil, yönetilen kod başlatmak için sağlayabilir.   

[!code-cpp[NetCoreHost#7](../../../samples/core/hosting/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>7. adım - yönetilen kodu çalıştırma!
AppDomain ile çalışmaya, ana bilgisayar artık yönetilen kod başlatabilirsiniz. Bunu yapmanın en kolay yolu kullanmaktır `ICLRRuntimeHost2::ExecuteAssembly` yönetilen derlemenin giriş noktası yöntemini çağırmak için. Bu işlev yalnızca tek etki alanlı senaryolarda çalıştığını unutmayın.

[!code-cpp[NetCoreHost#8](../../../samples/core/hosting/host.cpp#8)]

Başka bir seçenek, varsa `ExecuteAssembly` ana bilgisayarınızın gereksinimlerini karşılamıyor, kullanmaktır `CreateDelegate` Yönetilen yöntemi statik bir işlev işaretçisine oluşturmak için. Bu konak noktası (işlev işaretçisi türü oluşturmak için) çağırma olan ancak ana bilgisayar bütünleştirilmiş kodun giriş dışındaki kod çağırmak esneklik sağlar metodun imzası bilmek gerektirir.

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
  domainId,
  L"HW, Version=1.0.0.0, Culture=neutral",  // Target managed assembly
  L"ConsoleApplication.Program",            // Target managed type
  L"Main",                                  // Target entry point (static method)
  (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a>8 - temizleme adım
Son olarak, ana bilgisayar kendisini sonra uygulama etki alanları kaldırma, çalışma zamanı durdurma ve serbest bırakma temizlemek `ICLRRuntimeHost2` başvuru.

[!code-cpp[NetCoreHost#9](../../../samples/core/hosting/host.cpp#9)]

## <a name="about-hosting-net-core-on-unix"></a>UNIX üzerinde .NET Core barındırma hakkında
.NET core, Windows, Linux ve Mac işletim sistemleri üzerinde çalışan platformlar arası ürünüdür. Yerel uygulama, bunlar arasında bazı farklar ana bilgisayarları farklı platformlar için yine de sahip olur. Kullanarak yukarıda açıklanan işlem `ICLRRuntimeHost2` çalışma zamanını başlatma, AppDomain oluşturmak ve yönetilen kodu yürütmek için desteklenen tüm işletim sistemlerinde çalışması gerekir. Ancak, mscoree.h içinde tanımlanan arabirimleri mscoree birçok Win32 varsayım yapmaz beri Unix platformlarında çalışmak için çok uğraşmayı gerektirebilir.

Barındırma platformlarına UNIX daha kolay hale getirmek için daha fazla platform nötr barındırma API sarmalayıcılar kümesidir bulunan [coreclrhost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h).

Coreclrhost.h (yerine doğrudan mscoree.h) kullanarak bir örnek şurada görülebilir [UnixCoreRun konak](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts). Coreclrhost.h API'lerinden çalışma zamanını barındırmak için kullanılacak adımların mscoree.h kullanırken adımlara benzer:

1. Yönetilen kodu yürütmek için tanımlayın (komutu parametreleri, örneğin satır). 
2. CoreCLR Kitaplığı yükleyin.
    1. `dlopen("./libcoreclr.so", RTLD_NOW | RTLD_LOCAL);` 
3. İşlev işaretçileri CoreCLR için 's alma `coreclr_initialize`, `coreclr_create_delegate`, `coreclr_execute_assembly`, ve `coreclr_shutdown` kullanan işlevler `dlsym`
    1. `coreclr_initialize_ptr coreclr_initialize = (coreclr_initialize_ptr)dlsym(coreclrLib, "coreclr_initialize");`
4. AppDomain özellikleri (örneğin, TPA liste) ayarlayın. 5. adımı mscoree iş akışı ile aynı yukarıda budur.
5. Kullanım `coreclr_initialize` çalışma zamanını başlatma ve AppDomain oluşturmak için. Bu ayrıca oluşturur bir `hostHandle` gelecekte çağrıları barındırma kullanılacak işaretçi.
    1. Bu işlev her iki adım 4 ile 6 rollerini önceki akışından unutmayın. 
6. Hangisini `coreclr_execute_assembly` veya `coreclr_create_delegate` yönetilen kodu yürütmek için. Bu işlevler mscoree için ait benzer `ExecuteAssembly` ve `CreateDelegate` 7. adım önceki iş akışının işlevleri.
7. Kullanım `coreclr_shutdown` AppDomain kaldırma ve çalışma zamanı kapatmak için. 

## <a name="conclusion"></a>Sonuç
Konağınız oluşturulduktan sonra test edilebilir komut satırından çalıştırarak ve (yönetilen uygulama çalıştırmak için gibi) herhangi bir bağımsız değişken geçirme konak bekliyor. .NET Core uygulaması çalıştırmak ana bilgisayar için belirtirken tarafından üretilen .dll dosyasını kullanmaya dikkat edin `dotnet build`. Yürütülebilir dosyalar tarafından üretilen `dotnet publish` gerçekten varsayılan kendi içindeki uygulamaları için .NET Core barındıran (uygulamayı doğrudan ana hat senaryolarda komut satırından başlatılabilir böylece); kullanıcı kodu aynı ada sahip bir dll içine derlenmiş. 

Şeyler başlangıçta işe yaramazsa, sağlayamazsanız *coreclr.dll* TPA listesinde gerekli tüm Framework kitaplıkları ve o CoreCLR'ın bit genişliği (32 veya 64-bit) ile eşleşen konak tarafından beklenen konumda kullanılabilir nasıl konak oluşturulmuştur.

.NET Core çalışma zamanı barındırma birçok geliştiricinin yapılması gerekmez, ancak bunlar için yönetilen koddan yerel işlem veya .NET Core çalışma zamanı davranışı hakkında daha fazla denetime gereksinim duyan başlatmak gereksinim duyan İleri düzey bir senaryodur, çok kullanışlı olabilir. .NET Core yan yana çalıştırmak mümkün olduğundan kendisi ile başlatmak ve birden çok .NET Core çalışma zamanı sürümünü başlatmak ve bunları aynı işlemde tüm uygulamaları yürütmek konaklar oluşturmaya bile mümkündür. 
