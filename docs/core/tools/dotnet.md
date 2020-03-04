---
title: DotNet komutu
description: DotNet komutu (.NET Core CLI için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240876"
---
# <a name="dotnet-command"></a>DotNet komutu

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet`-.NET Core CLI genel sürücü.

## <a name="synopsis"></a>Özeti

Kullanılabilir komutlar ve ortam hakkında bilgi almak için:

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

Bir komutu çalıştırmak için (SDK yüklemesi gerektirir):

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

Bir uygulamayı çalıştırmak için:

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward` .NET Core 3. x sürümünden bu yana kullanılabilir. .NET Core 2. x için `--roll-forward-on-no-candidate-fx` kullanın.

## <a name="description"></a>Açıklama

`dotnet` komutu iki işleve sahiptir:

- .NET Core projeleriyle çalışmak için komutlar sağlar.

  Örneğin, [`dotnet build`](dotnet-build.md) bir proje oluşturur. Her komut kendi seçeneklerini ve bağımsız değişkenlerini tanımlar. Tüm komutlar, komutu kullanma hakkında kısa bir belge yazdırmak için `--help` seçeneğini destekler.

- .NET Core uygulamaları çalıştırır.

  Uygulamayı çalıştırmak için bir uygulama `.dll` dosyasının yolunu belirtirsiniz. Örneğin, `dotnet myapp.dll` `myapp` uygulamayı çalıştırır. Dağıtım seçenekleri hakkında bilgi edinmek için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md) .

## <a name="options"></a>Seçenekler

Farklı seçenekler, bir komut çalıştırmak ve bir uygulamayı çalıştırmak için tek başına `dotnet` vardır.

### <a name="options-for-dotnet-by-itself"></a>Tek başına DotNet seçenekleri

Aşağıdaki seçenekler kendi `dotnet` içindir. Örneğin, `dotnet --info`. Ortamla ilgili bilgi yazdırır.

- **`--info`**

  .NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.

- **`--version`**

  Kullanımda olan .NET Core SDK sürümünü yazdırır.

- **`--list-runtimes`**

  Yüklü .NET Core çalışma zamanlarının listesini yazdırır.

- **`--list-sdks`**

  Yüklü .NET Core SDK 'larının listesini yazdırır.

- **`-h|--help`**

  Kullanılabilir komutların bir listesini yazdırır.

### <a name="sdk-options-for-running-a-command"></a>Komut çalıştırmak için SDK seçenekleri

Aşağıdaki seçenekler bir komutla `dotnet` içindir. Örneğin, `dotnet build --help`.

- **`-d|--diagnostics`**

  Tanılama çıkışını izin vermez.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`. Her komutta desteklenmez. Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.

- **`-h|--help`**

  `dotnet build --help`gibi belirli bir komutun belgelerini yazdırır.

- **`command options`**

  Her komut, bu komuta özgü seçenekleri tanımlar. Kullanılabilir seçeneklerin listesi için bkz. özel komut sayfası.

### <a name="runtime-options"></a>Çalışma zamanı seçenekleri

`dotnet` bir uygulama çalıştırdığında aşağıdaki seçenekler kullanılabilir. Örneğin, `dotnet myapp.dll --fx-version 3.1.1`.

- **`--additionalprobingpath <PATH>`**

  Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.

- **`--additional-deps <PATH>`**

  Ek *. Deps. JSON* dosyasının yolu. Bir *Deps. JSON* dosyası, derleme çakışmalarını çözmek için kullanılan bağımlılıklar, derleme bağımlılıkları ve sürüm bilgilerinin bir listesini içerir. Daha fazla bilgi için bkz. GitHub 'da [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) .

- **`--fx-version <VERSION>`**

  Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.

- **`--runtimeconfig`**

  *Runtimeconfig. JSON* dosyasının yolu. *Runtimeconfig. JSON* dosyası, çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır. Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward-on-no-candidate-fx <N>`** **.NET Core 2. x SDK ' da kullanılabilir.**

  Gerekli paylaşılan çerçeve kullanılabilir olmadığında davranışını tanımlar. `N` şu olabilir:

  - `0`-alt düzey sürüm iletmeyi devre dışı bırakın.
  - `1`-önemli sürümde değil, küçük sürümde ilet. Bu varsayılan davranıştır.
  - `2`-küçük ve büyük sürümlerde ilet.

   Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).

- **`--roll-forward <SETTING>`** **.NET Core SDK 3,0 ' den başlayarak kullanılabilir.**

  Uygulamaya nasıl iletme uygulanacağını denetler. `SETTING` aşağıdaki değerlerden biri olabilir. Belirtilmemişse, varsayılan değer `Minor`.

  - `LatestPatch`-en yüksek düzeltme eki sürümüne ilet. Bu, ikincil sürüm iletmeyi devre dışı bırakır.
  - `Minor`, gerekli alt sürüm eksikse, en düşük düzeydeki sürüme ileri doğru alın. İstenen ikincil sürüm varsa, LatestPatch ilkesi kullanılır.
  - `Major`-en düşük ana sürüme ve istenen ana sürüm eksikse en düşük alt sürüme ilet. İstenen ana sürüm varsa, Ikincil ilke kullanılır.
  - `LatestMinor`, istenen alt sürüm mevcut olsa bile en yüksek alt sürüme ilet. Bileşen barındırma senaryolarına yöneliktir.
  - `LatestMajor`, istenen ana mevcut olsa bile en yüksek büyük ve en yüksek düzeydeki sürüme ileri alın. Bileşen barındırma senaryolarına yöneliktir.
  - `Disable`-ileri geri alma. Yalnızca belirtilen sürüme bağlayın. Bu ilke, en son düzeltme eklerine iletme özelliğini devre dışı bıraktığından genel kullanım için önerilmez. Bu değer yalnızca test için önerilir.

`Disable`özel durumu ile, tüm ayarlar kullanılabilir en yüksek düzeltme eki sürümünü kullanacaktır.

İleri sarma davranışı Ayrıca bir proje dosyası özelliği, çalışma zamanı yapılandırma dosyası özelliği ve ortam değişkeni içinde de yapılandırılabilir. Daha fazla bilgi için bkz. [ana sürüm çalışma zamanı ileri iletme](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

## <a name="dotnet-commands"></a>dotnet komutları

### <a name="general"></a>Genel

| Komut                                       | İşlev                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | .NET Core uygulaması oluşturur.                                     |
| [dotnet build-server](dotnet-build-server.md) | Bir yapı tarafından başlatılan sunucularla etkileşime girer.                          |
| [dotnet clean](dotnet-clean.md)               | Derleme çıktılarını temizle.                                                |
| [dotnet help](dotnet-help.md)                 | Komutu için çevrimiçi daha ayrıntılı belgeler gösterir.           |
| [dotnet migrate](dotnet-migrate.md)           | Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.  |
| [dotnet msbuild](dotnet-msbuild.md)           | MSBuild komut satırına erişim sağlar.                        |
| [dotnet new](dotnet-new.md)                   | Belirli bir C# şablon F# için bir veya projesini başlatır.                |
| [dotnet pack](dotnet-pack.md)                 | Kodunuzun bir NuGet paketini oluşturur.                               |
| [dotnet publish](dotnet-publish.md)           | .NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md)           | Belirli bir uygulama için bağımlılıkları geri yükler.                  |
| [dotnet run](dotnet-run.md)                   | Uygulamayı kaynaktan çalıştırır.                                   |
| [dotnet sln](dotnet-sln.md)                   | Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.       |
| [dotnet store](dotnet-store.md)               | Derlemeleri çalışma zamanı paket deposunda depolar.                     |
| [dotnet test](dotnet-test.md)                 | Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.                                     |

### <a name="project-references"></a>Proje başvuruları

Komut | İşlev
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Bir proje başvurusu ekler.
[dotnet list reference](dotnet-list-reference.md) | Proje başvurularını listeler.
[dotnet remove reference](dotnet-remove-reference.md) | Proje başvurusunu kaldırır.

### <a name="nuget-packages"></a>NuGet paketleri

Komut | İşlev
--- | ---
[dotnet add package](dotnet-add-package.md) | Bir NuGet paketi ekler.
[dotnet remove package](dotnet-remove-package.md) | Bir NuGet paketini kaldırır.

### <a name="nuget-commands"></a>NuGet komutları

Komut | İşlev
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Sunucudan bir paketi siler veya listesini kaldırır.
[dotnet nuget locals](dotnet-nuget-locals.md) | Http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.
[dotnet nuget push](dotnet-nuget-push.md) | Bir paketi sunucuya gönderir ve yayımlar.

### <a name="global-tool-path-and-local-tools-commands"></a>Küresel, araç yolu ve yerel araçlar komutları

Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır. Araçları kendiniz yazabilir veya üçüncü taraflarca yazılmış Araçları yükleyebilirsiniz. Araçlar genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir. Daha fazla bilgi için bkz. [.NET Core araçlarına genel bakış](global-tools.md). Genel ve araç yolu araçları .NET Core SDK 2,1 ' den başlayarak kullanılabilir. Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.

Komut | İşlev
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Makinenize bir araç kurar.
[dotnet tool list](dotnet-tool-list.md) | Makinenizde yüklü olan tüm genel, araç-yol veya yerel araçları listeler.
[dotnet tool install](dotnet-tool-uninstall.md) | Bir aracı makinenizden kaldırır.
[dotnet tool update](dotnet-tool-update.md) | Makinenizde yüklü bir aracı güncelleştirir.

### <a name="additional-tools"></a>Ek araçlar

.NET Core SDK 2.1.300 ile başlayarak, yalnızca .NET Core SDK bir parçası olarak yalnızca `DotnetCliToolReference` kullanılarak proje temelinde kullanılabilen birçok araç vardır. Bu araçlar aşağıdaki tabloda listelenmiştir:

| Aracı                                              | İşlev                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| geliştirme-CERT                                         | Geliştirme sertifikaları oluşturur ve yönetir.                |
| [aşv](/ef/core/miscellaneous/cli/dotnet)           | Komut satırı araçlarını Entity Framework Core.                    |
| SQL-Cache                                         | Önbellek komut satırı araçlarını SQL Server.                         |
| [Kullanıcı gizli dizileri](/aspnet/core/security/app-secrets) | Geliştirme Kullanıcı gizli dizilerini yönetir.                            |
| [Servisi](/aspnet/core/tutorials/dotnet-watch)      | Dosyalar değiştiğinde bir komutu çalıştıran bir dosya İzleyicisi başlatır. |

Her araç hakkında daha fazla bilgi için `dotnet <tool-name> --help`yazın.

## <a name="examples"></a>Örnekler

Yeni bir .NET Core konsol uygulaması oluşturun:

```dotnetcli
dotnet new console
```

Belirli bir dizinde bir proje ve onun bağımlılıklarını oluşturun:

```dotnetcli
dotnet build
```

Bir uygulamayı çalıştırın:

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>Ortam değişkenleri

- `DOTNET_ROOT`, `DOTNET_ROOT(x86)`

  Varsayılan konumda yüklü değilse, .NET Core çalışma zamanlarının konumunu belirtir. Windows üzerindeki varsayılan konum `C:\Program Files\dotnet`. Linux ve macOS 'ta varsayılan konum `/usr/share/dotnet`. Bu ortam değişkeni yalnızca oluşturulan yürütülebilir dosyalar (apphosts) aracılığıyla uygulamalar çalıştırılırken kullanılır. `DOTNET_ROOT(x86)`, 64 bit IŞLETIM sisteminde 32 bitlik bir yürütülebilir dosya çalıştırılırken kullanılır.

- `DOTNET_PACKAGES`

  Genel paketler klasörü. Ayarlanmamışsa, varsayılan olarak UNIX veya Windows üzerinde `%userprofile%\.nuget\packages` `~/.nuget/packages`.

- `DOTNET_SERVICING`

  Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  .NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir. Telemetri özelliğinin (değerler `true`, `1`veya `yes` kabul edilir) devre dışı bırakmak için `true` olarak ayarlayın. Aksi takdirde, telemetri özelliklerine (değerler `false`, `0`veya `no` kabul edilir) kabul etmek için `false` olarak ayarlayın. Ayarlanmamışsa, varsayılan `false` ve telemetri özelliği etkindir.

- `DOTNET_MULTILEVEL_LOOKUP`

  .NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir. Ayarlanmazsa, varsayılan olarak 1 ' dir (mantıksal `true`). Genel konumdan çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olmak için 0 (mantıksal `false`) olarak ayarlayın. Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD` **.NET Core 3. x SDK ile başlayarak kullanılabilir.**

  İleri alma davranışını belirler. Daha fazla bilgi için bu makalenin önceki `--roll-forward` seçeneğine bakın.

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **.NET Core 2. x SDK ' da kullanılabilir.**

  `0`olarak ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır. Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).

- `DOTNET_CLI_UI_LANGUAGE`

  `en-us`gibi bir yerel ayar değeri kullanarak CLı Kullanıcı arabiriminin dilini ayarlar. Desteklenen değerler, Visual Studio ile aynıdır. Daha fazla bilgi için [Visual Studio yükleme belgelerindeki](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)yükleyici dilini değiştirme bölümüne bakın. .NET Resource Manager kuralları uygulanır, böylece tam bir eşleşme seçmeniz gerekmez&mdash;`CultureInfo` ağacındaki alt öğeleri de seçebilirsiniz. Örneğin, `fr-CA`olarak ayarlarsanız, CLı `fr` çevirileri bulur ve kullanır. Bunu desteklenmeyen bir dile ayarlarsanız, CLı Ingilizce 'ye geri döner.

- `DOTNET_DISABLE_GUI_ERRORS`

  GUI özellikli oluşturulan yürütülebilir dosyalar için, normalde belirli hata sınıfları için gösterilen iletişim kutusu açılır penceresini devre dışı bırakır. Yalnızca `stderr` yazar ve bu durumlarda çıkar.
  
- `DOTNET_ADDITIONAL_DEPS`

  CLı seçeneğine eşdeğerdir `--additional-deps`.

- `DOTNET_RUNTIME_ID`

  Algılanan RID 'yi geçersiz kılar.

- `DOTNET_SHARED_STORE`

  Bazı durumlarda derleme çözümlemenin geri döndürüleceği "paylaşılan deponun" konumu.

- `DOTNET_STARTUP_HOOKS`

  Başlangıç kancalarını yüklemek ve yürütmek için derlemelerin listesi.

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  `dotnet.exe`, `hostfxr`ve `hostpolicy`gibi barındırma bileşenlerinden tanılama izlemeyi denetler.

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md)
