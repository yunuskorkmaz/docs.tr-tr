---
title: ".NET Core barındırma"
description: "Yerel koddan .NET çekirdeği çalışma zamanı barındırma"
keywords: ".NET, .NET core, barındırma, .NET Core barındırma"
author: mjrousos
ms.author: mikerou
ms.date: 2/3/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13edec8b-614d-47ed-9e95-ed6d3b94ec0c
ms.openlocfilehash: 1f0983b909244dda7270d3eff01dc302383639a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-net-core"></a>.NET Core barındırma

Yönetilen kod gibi .NET Core uygulamaları bir ana bilgisayar tarafından yürütülür. Konak (JIT ve atık toplayıcı gibi bir bileşenler dahil) çalışma zamanı başlatmak için sorumlu, giriş noktaları yönetilen uygulama etki alanları oluşturma ve çağırma.

.NET çekirdeği çalışma zamanı barındırma Gelişmiş bir senaryodur ve çoğu durumda, .NET geliştiricilerinin .NET Core yapı olduğundan işlemler barındırma hakkında endişelenmeniz gerekmez çekirdek .NET Core uygulamaları çalıştırmak için varsayılan bir ana bilgisayar sağlayın. Bazı özel durumlarda yine de bu konağa açıkça .NET çekirdeği çalışma zamanı olarak yerel bir işlemde veya çalışma şeklini üzerinde daha fazla denetim kazanmak için yönetilen kod çağırma ya da yararlı olabilir.

Bu makalede .NET çekirdeği çalışma zamanı yerel koddan başlatmak için ilk uygulama etki alanı oluşturmak için gerekli adımları genel bir bakış sunar (<xref:System.AppDomain>) ve yönetilen kod içinde yürütün.

## <a name="prerequisites"></a>Önkoşullar

Yerel uygulamalar konak olmadığından, Bu öğretici bir ana bilgisayara .NET Core C++ uygulaması oluşturma ele alınacaktır. C++ geliştirme ortamı gerekir (tarafından sağlanan gibi [Visual Studio](https://www.visualstudio.com/downloads/)).

Yüklemeniz gerekir böylece konak ile test etmek için basit bir .NET Core uygulaması da isteyeceksiniz [.NET Core SDK](https://www.microsoft.com/net/core) ve [küçük bir .NET Core test uygulaması oluşturma](../../core/tutorials/with-visual-studio.md) (örneğin, bir 'Hello World' uygulaması). Yeni .NET Core konsol proje şablonu tarafından oluşturulan 'Hello World' uygulaması yeterli olur.

Bu öğretici ve onun ilişkili örnek bir Windows konağının oluşturun; üzerinde UNIX barındırma hakkında bu makalenin sonunda notlarına bakın.

## <a name="creating-the-host"></a>Konak oluşturma

A [örnek konak](https://github.com/dotnet/docs/tree/master/samples/core/hosting) bu makalede açıklanan adımları gösteren kullanılabilir dotnet/belgeler GitHub deposunda. Örnek ait açıklamaları *host.cpp* numaralı adımlar burada bunlar örnekte gerçekleştirilen ile bu öğreticiden açıkça ilişkilendirme dosya. Yükleme yönergeleri için bkz: [örnekler ve öğreticiler](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Örnek konak amacıyla, böylece hata denetimi üzerinde açık olduğundan ve verimliliği okunabilirlik vurgulamak için tasarlanmış öğrenme için kullanılması amaçlanmıştır aklınızda bulundurun. Daha fazla gerçek ana bilgisayar örnekleri kullanılabilir [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) deposu. [CoreRun konak](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun), özellikle, daha basit örnek okuduktan sonra incelemek için iyi bir genel amaçlı ana bilgisayardır.

### <a name="a-note-about-mscoreeh"></a>Not mscoree.h hakkında
Arabirim barındırma birincil .NET Core (`ICLRRuntimeHost2`) tanımlanan [MSCOREE. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Ana bilgisayarınız başvurmak için ihtiyaç duyacağı, bu dosyanın (mscoree.h) üstbilgisi sürümü MIDL üretilen zaman [.NET çekirdeği çalışma zamanı](https://github.com/dotnet/coreclr/) yerleşik olarak bulunur. .NET çekirdeği çalışma zamanı oluşturmak istemiyorsanız mscoree.h olarak da kullanılabilir bir [önceden derlenmiş üstbilgi](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) dotnet/coreclr deposunda. [.NET çekirdeği çalışma zamanı oluşturma hakkında yönergeler](https://github.com/dotnet/coreclr#building-the-repository) , GitHub deposunda bulunabilir. 

### <a name="step-1---identify-the-managed-entry-point"></a>1. adım - yönetilen giriş noktası tanımlama
Gerekli üstbilgileri başvuran sonra ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) ve örneğin stdio.h), bir .NET Core konak gerçekleştirmelisiniz ilk şey biri, kullanacağınız yönetilen giriş noktasını bulun. Bizim örnek konak bu yalnızca ilk komut satırı bağımsız değişkeni bizim konağa yönetilen ikili bir yolu olarak gerçekleştirerek gerçekleştirilir, `main` yöntemi yürütülür.

[!code-cpp[NetCoreHost#1](../../../samples/core/hosting/host.cpp#1)]

### <a name="step-2---find-and-load-coreclrdll"></a>2. adım - bulma ve yükleme CoreCLR.dll
API bulunan .NET çekirdeği çalışma zamanı *CoreCLR.dll* (Windows'da ile). Barındırma arabirimimizi almak için (`ICLRRuntimeHost2`), bulmak ve yüklemek için gerekli olan *CoreCLR.dll*. Nasıl bulur için bir kural tanımlamak için ana kadar olan *CoreCLR.dll*. Bazı ana bilgisayarlar (örneğin, % programfiles%\dotnet\shared\Microsoft.NETCore.App\1.1.0) bilinen bir makineye konumda bulunması dosyaya bekler. Başkalarının bekler *CoreCLR.dll* ya da konak yanında bir konumdan kendisini veya barındırılması için uygulama yüklenir. Hala başkalarının kitaplığı bulmak için bir ortam değişkeni başvurun.

Linux veya Mac, çekirdek çalışma zamanı kitaplığı olan *libcoreclr.so* veya *libcoreclr.dylib*sırasıyla.

Bizim örnek ana bilgisayar için birkaç ortak konumlarını yoklamaları *CoreCLR.dll*. Bir kez bulundu, onu aracılığıyla yüklenmesi gereken `LoadLibrary` (veya `dlopen` Linux/Mac üzerinde).

[!code-cpp[NetCoreHost#2](../../../samples/core/hosting/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost2-instance"></a>3. adım - ICLRRuntimeHost2 örneği Al
`ICLRRuntimeHost2` Arabirimi barındırma alınır çağırarak `GetProcAddress` (veya `dlsym` Linux/Mac üzerinde) üzerinde `GetCLRRuntimeHost`ve ardından bu işlev çağırma. 

[!code-cpp[NetCoreHost#3](../../../samples/core/hosting/host.cpp#3)]

### <a name="step-4---setting-startup-flags-and-starting-the-runtime"></a>Adım 4 - başlangıç bayrakları ayarlama ve çalışma zamanı başlatma
İle bir `ICLRRuntimeHost2` eldeki, biz artık çalışma zamanı genelinde başlangıç bayrakları belirtin ve çalışma zamanı başlatın. Başlangıç bayrakları hangi tek bir AppDomain veya birden çok appdomains oluşturuyor kullanacağız olup olmadığını (eşzamanlı veya sunucu) kullanmak için atıktoplayıcı (GC) ve (etki alanı Tarafsız derlemeler için yüklenmesini) kullanmak için hangi yükleyicisi iyileştirme İlkesi belirler.

[!code-cpp[NetCoreHost#4](../../../samples/core/hosting/host.cpp#4)]

Çalışma zamanı için bir çağrı kullanmaya `Start` işlevi.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Adım 5 - hazırlama AppDomain ayarları
Çalışma zamanı başladıktan sonra biz AppDomain ayarlamak isteyeceksiniz. Bu ilk hazırlamak gereklidir, ancak bir .NET AppDomain oluştururken belirtilmelidir seçenekleri mevcuttur.

AppDomain bayrakları güvenlik ve birlikte çalışma ile ilgili AppDomain davranışları belirtin. Korumalı alan kullanıcı kodu için bu ayarları daha eski Silverlight ana kullanılan, ancak çoğu modern .NET Core konakları tam güven kullanıcı kodu çalıştırın ve birlikte çalışabilirlik etkinleştirin.

[!code-cpp[NetCoreHost#5](../../../samples/core/hosting/host.cpp#5)]

Hangi kullanılacak AppDomain bayrakları karar sonra AppDomain özellikleri tanımlanması gerekir. Dizeleri anahtar/değer çiftlerini özelliklerdir. Özelliklerin çoğu AppDomain derlemeler nasıl yükleneceğini için ilgilidir.

Ortak AppDomain özellikleri şunlardır:

* `TRUSTED_PLATFORM_ASSEMBLIES`Derleme yolların listesini budur (ayrılmış Windows tarafından ';' ve ':' UNIX üzerinde) hangi AppDomain (kısmen güvenilen etki alanlarında çift için) yükleme ve verin tam güven öncelik vermeniz. Bu liste 'Framework' derlemeler ve diğer güvenilen modüller, .NET Framework senaryoları GAC'de benzer içerecek şekilde tasarlanmıştır. Bazı ana bilgisayarlar herhangi bir kitaplığı yanına sokar *coreclr.dll* bu listede, diğerleri sabit kodlanmış bildirimlerinin kendi amaçları için güvenilir derlemeler listesi vardır.
* `APP_PATHS`Bu araştırma için derlemeyi'da güvenilir platform derlemeler (TPA) listesinde bulunamazsa yollarının listesidir. Bu yolları kullanıcıların derlemeleri bulunabileceği konumlarının olması amaçlanmıştır. Bir korumalı alan AppDomain içinde bu yolları yüklenen derlemeler yalnızca kısmi güven verilecektir. Ortak APP_PATH yolları, hedef uygulama yüklü değildi yolu veya burada kullanıcı varlıklar Canlı bilinen başka konumlara içerir.
*  `APP_NI_PATHS`Yerel görüntüler için araştırılan yolları olma amacını bu listeyi APP_PATHS için çok benzerdir.
*  `NATIVE_DLL_SEARCH_DIRECTORIES`Bu özellik, yerel DLL'leri p/Invoke çağrıldığında yükleyicisi araştırma yolları listesidir.
*  `PLATFORM_RESOURCE_ROOTS`Bu liste kaynak uydu derlemeleri (kültüre özgü alt dizinlerde) için araştırma yolları içerir.
*  `AppDomainCompatSwitch`Bu dize, açık bir hedef Framework ad (derleme karşı çalıştırmak için tasarlanmıştır hangi Framework gösteren bir derleme düzeyi öznitelik) olmadan derlemeler için hangi uyumluluk quirks kullanılması gerektiğini belirtir. Genellikle, bu ayarlanmalı `"UseLatestBehaviorWhenTFMNotSpecified"` ancak bazı ana bilgisayarlar eski Silverlight veya Windows Phone uyumluluk quirks, bunun yerine almak isteyebilirsiniz.

İçinde bizim [basit örnek konak](https://github.com/dotnet/docs/tree/master/samples/core/hosting), bu özellikleri şu şekilde ayarlanır:

[!code-cpp[NetCoreHost#6](../../../samples/core/hosting/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>6. adım - AppDomain oluşturma
Tüm AppDomain bayraklar ve Özellikler hazır sonra `ICLRRuntimeHost2::CreateAppDomainWithManager` AppDomain ayarlamak için kullanılabilir. Bu işlev, isteğe bağlı olarak bir tam nitelikli derleme adı ve etki alanının AppDomain Yöneticisi olarak kullanılacak türü adı alır. AppDomain Yöneticisi AppDomain davranışının bazı yönlerini denetlemek bir konak izin verebilir ve giriş noktaları konak kullanıcı kodu doğrudan çağırma istiyorsanız değil, yönetilen kod başlatmaktan sağlayabilir.   

[!code-cpp[NetCoreHost#7](../../../samples/core/hosting/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Adım 7 - Çalıştır yönetilen kod!
AppDomain ile çalışır, ana bilgisayar şimdi yönetilen kod yürütme başlatabilirsiniz. Bunu yapmanın en kolay yolu kullanmaktır `ICLRRuntimeHost2::ExecuteAssembly` yönetilen bir derlemenin giriş noktası yöntemini çağırmak için. Bu işlev yalnızca tek etki alanlı senaryolarda çalıştığını unutmayın.

[!code-cpp[NetCoreHost#8](../../../samples/core/hosting/host.cpp#8)]

Başka bir seçenek değilse `ExecuteAssembly` ana bilgisayarın gereksinimlerini karşılamıyor, kullanmaktır `CreateDelegate` Yönetilen yöntemi statik bir işlev işaretçisi oluşturmak için. Bu yöntemi (işlev işaretçisi türü oluşturmak için) çağırma olduğu ancak ana kod derlemenin girişi dışında çağrılacak esnekliğini sağlar imzasını noktası bilmeniz konak gerektirir.

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
Son olarak, ana bilgisayar kendisini sonra appdomains oluşturuyor kaldırılması, çalışma zamanı durdurma ve serbest bırakma temizlenmesi `ICLRRuntimeHost2` başvuru.

[!code-cpp[NetCoreHost#9](../../../samples/core/hosting/host.cpp#9)]

## <a name="about-hosting-net-core-on-unix"></a>.NET Core üzerinde UNIX barındırma hakkında
.NET core, Windows, Linux ve Mac işletim sistemlerinde çalışan platformlar arası üründür. Yerel uygulamalar olarak bunları arasındaki bazı farklar farklı platformlar için ana bilgisayarlar yine de sahip olur. Kullanarak yukarıda açıklanan işlemi `ICLRRuntimeHost2` çalışma zamanı başlatmak, AppDomain oluşturmak ve yönetilen kod yürütmek için desteklenen tüm işletim sistemlerinde çalışması gerekir. Ancak, mscoree.h içinde tanımlanan arabirimleri mscoree çoğu Win32 varsayımlar yapar ile UNIX platformlarında çalışmaya sıkıcı olabilir.

Barındırma UNIX platformlarında daha kolay yapmak için daha fazla platformdan bağımsız barındırma API sarmalayıcıları kümesi kullanılabilir [coreclrhost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h).

Coreclrhost.h (yerine doğrudan mscoree.h) kullanarak bir örnek görülebilir [UnixCoreRun konak](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts). Çalışma zamanı barındırmak için coreclrhost.h API'lerden kullanma adımları mscoree.h kullanırken adımlara benzer:

1. Yönetilen kod yürütmek için tanımlamak (komuttan parametreleri, örneğin satır). 
2. CoreCLR kitaplığı yüklenemedi.
    1. `dlopen("./libcoreclr.so", RTLD_NOW | RTLD_LOCAL);` 
3. İşlev işaretçileri CoreCLR için 's alma `coreclr_initialize`, `coreclr_create_delegate`, `coreclr_execute_assembly`, ve `coreclr_shutdown` kullanarak işlevleri`dlsym`
    1. `coreclr_initialize_ptr coreclr_initialize = (coreclr_initialize_ptr)dlsym(coreclrLib, "coreclr_initialize");`
4. AppDomain özellikleri (örneğin, TPA listesi) ayarlayın. Bu adım 5 mscoree akışından yukarıda aynıdır.
5. Kullanım `coreclr_initialize` çalışma zamanı başlamak ve AppDomain oluşturmak için. Bu ayrıca oluşturacak bir `hostHandle` gelecekte çağrıları barındırma kullanılacak işaretçi.
    1. Bu işlev önceki iş akışından her iki adım 4 ile 6 rolleri gerçekleştirmediğini unutmayın. 
6. Kullanın ya da `coreclr_execute_assembly` veya `coreclr_create_delegate` yönetilen kod yürütmek için. Bu işlevler mscoree için 's benzer `ExecuteAssembly` ve `CreateDelegate` adım 7 önceki iş akışının işlevlerden.
7. Kullanım `coreclr_shutdown` AppDomain kaldırma ve çalışma zamanı kapatmak için. 

## <a name="conclusion"></a>Sonuç
Ana bilgisayarınız oluşturulduktan sonra sınanabilir komut satırından çalıştırarak ve (gibi çalıştırmak için yönetilen uygulama) herhangi bir bağımsız değişken geçirme konak bekliyor. .NET Core uygulamayı çalıştırmak ana bilgisayar için belirtirken tarafından üretilen .dll kullandığınızdan emin olun `dotnet build`. Yürütülebilir dosyalar üretilen tarafından `dotnet publish` kullanıcı kodu aynı ada sahip bir DLL'e derlenmiş; gerçekte varsayılan kendi içinde bulunan uygulamalar için .NET Core Konağı (uygulama doğrudan komut satırından mainline senaryolarda başlatılabilir böylece). 

Şeyler başlangıçta işe yaramazsa, iki kez kontrol *coreclr.dll* TPA listesinde tüm gerekli Framework kitaplıkları ve bu CoreCLR'ın verileri (32 veya 64-bit) eşleşen ana bilgisayar tarafından beklenen konumda kullanılabilir nasıl ana bilgisayar oluşturuldu.

.NET çekirdeği çalışma zamanı barındırma pek çok geliştirici gerektiren çalışmaz, ancak olanlar için yönetilen koddan yerel bir işlem veya .NET çekirdeği çalışma zamanı davranışı hakkında daha fazla denetime gereksinim duyan başlatmak gereksinim duyan Gelişmiş bir senaryo, çok kullanışlı olabilir. .NET Core yan yana çalıştırmanız mümkün olduğundan kendisiyle, başlatmak ve .NET çekirdeği çalışma zamanı birden fazla sürümünü başlatın ve uygulamaları tümünün aynı işlemde yürütmek konak oluşturmak bile mümkündür. 
