---
title: dotnet komutu
description: Dotnet komutu (.NET Core CLI için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 02/13/2020
ms.openlocfilehash: 6a08297499d955db44e342dc82fed25b7b9b8171
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739073"
---
# <a name="dotnet-command"></a>dotnet komutu

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

## <a name="name"></a>Adı

`dotnet`- .NET Core CLI için genel sürücü.

## <a name="synopsis"></a>Özet

Kullanılabilir komutlar ve ortam hakkında bilgi almak için:

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

Bir komutçalıştırmak için (SDK yüklemegerektirir):

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

Bir uygulamayı çalıştırmak için:

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward`.NET Core 3.x'ten beri kullanılabilir. .NET Core 2.x için kullanın. `--roll-forward-on-no-candidate-fx`

## <a name="description"></a>Açıklama

Komutun `dotnet` iki işlevi vardır:

- .NET Core projeleri ile çalışmak için komutlar sağlar.

  Örneğin, [`dotnet build`](dotnet-build.md) bir proje oluşturur. Her komut kendi seçeneklerini ve bağımsız değişkenlerini tanımlar. Tüm komutlar, `--help` komutun nasıl kullanılacağı hakkında kısa belgeler yazdırma seçeneğini destekler.

- .NET Core uygulamalarını çalıştırıyor.

  Uygulamayı çalıştırmak için bir `.dll` uygulama dosyasına giden yolu belirtirsiniz.  Uygulamayı çalıştırmak için bulmak ve konsol uygulamaları durumunda `Main` yöntemdir giriş noktası yürütmek anlamına gelir. Örneğin, `dotnet myapp.dll` `myapp` uygulamayı çalıştırın. Dağıtım seçenekleri hakkında bilgi edinmek için [.NET Core uygulama dağıtımına](../deploying/index.md) bakın.

## <a name="options"></a>Seçenekler

Tek `dotnet` başına, bir komutu çalıştırmak ve bir uygulamayı çalıştırmak için farklı seçenekler mevcuttur.

### <a name="options-for-dotnet-by-itself"></a>Dotnet seçenekleri tek başına

Aşağıdaki seçenekler tek `dotnet` başına vardır. Örneğin, `dotnet --info`. Çevre yle ilgili bilgileri yazdırır.

- **`--info`**

  Geçerli işletim sistemi gibi bir .NET Core yüklemesi ve makine ortamı hakkında ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA'sını işler.

- **`--version`**

  .NET Core SDK'nın kullanımdaki sürümünü yazdırır.

- **`--list-runtimes`**

  Yüklenen .NET Core çalışma saatlerinin listesini yazdırır. SDK'nın x86 sürümü yalnızca x86 çalışma saatlerini listeler ve SDK'nın x64 sürümü yalnızca x64 çalışma saatlerini listeler.

- **`--list-sdks`**

  Yüklenen .NET Core SDK'ların listesini yazdırır.

- **`-h|--help`**

  Kullanılabilir komutların listesini yazdırır.

### <a name="sdk-options-for-running-a-command"></a>Komut çalıştırmak için SDK seçenekleri

Aşağıdaki seçenekler bir `dotnet` komut ile vardır. Örneğin, `dotnet build --help`.

- **`-d|--diagnostics`**

  Tanılama çıktısını sağlar.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntılı düzeyini ayarlar. İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve . Her komutta desteklenmez. Bu seçeneğin kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.

- **`-h|--help`**

  Belirli bir komut için belgeleri yazdırır, örneğin. `dotnet build --help`

- **`command options`**

  Her komut, bu komuta özgü seçenekleri tanımlar. Kullanılabilir seçeneklerlistesi için belirli komut sayfasına bakın.

### <a name="runtime-options"></a>Çalışma zamanı seçenekleri

Bir uygulama çalıştırıldığında `dotnet` aşağıdaki seçenekler kullanılabilir. Örneğin, `dotnet myapp.dll --fx-version 3.1.1`.

- **`--additionalprobingpath <PATH>`**

  Sondalama ilkesi ve sondalama için derlemeler içeren yol.

- **`--additional-deps <PATH>`**

  Ek bir *.deps.json* dosyasına giden yol. *Deps.json* dosyası, derleme çakışmalarını gidermek için kullanılan bağımlılıkların, derleme bağımlılıklarının ve sürüm bilgilerinin listesini içerir. Daha fazla bilgi için GitHub'daki [Runtime Configuration Files'a](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) bakın.

- **`--fx-version <VERSION>`**

  .NET Core çalışma zamanı sürümü uygulamayı çalıştırmak için kullanmak.

- **`--runtimeconfig`**

  *Runtimeconfig.json* dosyasına giden yol. *Runtimeconfig.json* dosyası, çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır. Daha fazla bilgi için [.NET Core çalışma zamanı yapılandırma ayarlarına](../run-time-config/index.md#runtimeconfigjson)bakın.

- **`--roll-forward-on-no-candidate-fx <N>`****.NET Core 2.x SDK'da mevcuttur.**

  Gerekli paylaşılan çerçeve kullanılamadığında davranışı tanımlar. `N`olabilir:

  - `0`- Hatta küçük sürümü ileri rulo devre dışı.
  - `1`- Roll ileri küçük sürümü, ancak ana sürümünde değil. Bu varsayılan davranıştır.
  - `2`- Küçük ve ana versiyonlarda ileri ye doğru yuvarlan.

   Daha fazla bilgi için [bkz.](../whats-new/dotnet-core-2-1.md#roll-forward)

- **`--roll-forward <SETTING>`****.NET Core SDK 3.0 ile başlayan kullanılabilir.**

  Kullanıma almanın uygulamaya nasıl uygulandığını denetler. Aşağıdaki `SETTING` değerlerden biri olabilir. Belirtilmemişse, `Minor` varsayılandır.

  - `LatestPatch`- En yüksek yama sürümüne doğru yuvarlan. Bu, küçük sürümün devrilmelerini devre dışı kılabilir.
  - `Minor`- İstenen küçük sürüm eksikse, en düşük yüksek minör sürüme doğru ileri doğru yuvarlan. İstenen küçük sürüm varsa, En Son Yama ilkesi kullanılır.
  - `Major`- İstenen ana sürüm eksikse, en düşük yüksek ana sürüme ve en düşük küçük sürüme yuvarlan. İstenen ana sürüm varsa, Küçük ilke kullanılır.
  - `LatestMinor`- İstenen küçük sürüm mevcut olsa bile, en yüksek minör sürüme doğru yuvarlan. Bileşen barındırma senaryoları için tasarlanmıştır.
  - `LatestMajor`- İstenilen ana sürüm mevcut olsa bile, en yüksek majör ve en yüksek minör sürüme doğru yuvarlan. Bileşen barındırma senaryoları için tasarlanmıştır.
  - `Disable`- Öne yuvarlanmayın. Yalnızca belirtilen sürüme bağla. Bu ilke, en son düzeltme ekilerine ilerleme yitirme özelliğini devre dışı kattığı için genel kullanım için önerilmez. Bu değer yalnızca sınama için önerilir.

`Disable`Hariç, tüm ayarlar mevcut en yüksek yama sürümünü kullanır.

Roll forward davranışı, proje dosyası özelliğinde, çalışma zamanı yapılandırma dosyası özelliğinde ve ortam değişkeninde de yapılandırılabilir. Daha fazla bilgi için [Bkz. Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

## <a name="dotnet-commands"></a>dotnet komutları

### <a name="general"></a>Genel

| Komut                                       | İşlev                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Bir .NET Core uygulaması oluşturur.                                     |
| [dotnet build-server](dotnet-build-server.md) | Bir yapı tarafından başlatılan sunucularla etkileşim de eder.                          |
| [dotnet clean](dotnet-clean.md)               | Yapı çıktılarını temizleyin.                                                |
| [dotnet help](dotnet-help.md)                 | Komut için çevrimiçi olarak daha ayrıntılı belgeler gösterir.           |
| [dotnet migrate](dotnet-migrate.md)           | Geçerli bir Önizleme 2 projesini bir .NET Core SDK 1.0 projesine geçirin.  |
| [dotnet msbuild](dotnet-msbuild.md)           | MSBuild komut satırına erişim sağlar.                        |
| [dotnet new](dotnet-new.md)                   | Belirli bir şablon için C# veya F# projesini başlatır.                |
| [dotnet pack](dotnet-pack.md)                 | Kodunuzu bir NuGet paketi oluşturur.                               |
| [dotnet publish](dotnet-publish.md)           | .NET framework'e bağımlı veya bağımsız bir uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md)           | Belirli bir uygulama için bağımlılıkları geri yükler.                  |
| [dotnet run](dotnet-run.md)                   | Uygulamayı kaynaktan çalıştırın.                                   |
| [dotnet sln](dotnet-sln.md)                   | Çözüm dosyasına proje ekleme, kaldırma ve listele etme seçenekleri.       |
| [dotnet store](dotnet-store.md)               | Montajları çalışma zamanı paket deposunda saklar.                     |
| [dotnet test](dotnet-test.md)                 | Bir test koşucusu kullanarak testler çalışır.                                     |

### <a name="project-references"></a>Proje başvuruları

Komut | İşlev
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Proje başvurusu ekler.
[dotnet list reference](dotnet-list-reference.md) | Proje başvurularını listeler.
[dotnet remove reference](dotnet-remove-reference.md) | Proje başvurularını kaldırır.

### <a name="nuget-packages"></a>NuGet paketleri

Komut | İşlev
--- | ---
[dotnet add package](dotnet-add-package.md) | Bir NuGet paketi ekler.
[dotnet remove package](dotnet-remove-package.md) | NuGet paketini kaldırır.

### <a name="nuget-commands"></a>NuGet komutları

Komut | İşlev
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Bir paketi sunucudan siler veya listeler.
[dotnet nuget push](dotnet-nuget-push.md) | Bir paketi sunucuya iter ve yayımlar.
[dotnet nuget locals](dotnet-nuget-locals.md) | Http isteği önbelleği, geçici önbellek veya makine çapında ki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.
[dotnet nuget add source](dotnet-nuget-add-source.md) | Bir NuGet kaynağı ekler.
[dotnet nuget disable source](dotnet-nuget-disable-source.md) | NuGet kaynağını devre dışı kılmış olur.
[dotnet nuget enable source](dotnet-nuget-enable-source.md) | Bir NuGet kaynağı sağlar.
[dotnet nuget list source](dotnet-nuget-list-source.md) | Tüm yapılandırılan NuGet kaynaklarını listeler.
[dotnet nuget remove source](dotnet-nuget-remove-source.md) | NuGet kaynağını kaldırır.
[dotnet nuget update source](dotnet-nuget-update-source.md) | Bir NuGet kaynağını güncelleştirir.

### <a name="global-tool-path-and-local-tools-commands"></a>Genel, araç yolu ve yerel araçlar komutları

Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır. Araçları kendiniz yazabilir veya üçüncü şahıslar tarafından yazılmış araçları yükleyebilirsiniz. Araçlar, genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir. Daha fazla bilgi için [.NET Core araçlarına genel bakış](global-tools.md)ala. .NET Core SDK 2.1 ile başlayan global ve araç yolu araçları mevcuttur. Yerel araçlar .NET Core SDK 3.0 ile başlayarak kullanılabilir.

Komut | İşlev
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Makinenize bir alet yükler.
[dotnet tool list](dotnet-tool-list.md) | Şu anda makinenizde yüklü olan tüm genel, araç yolu veya yerel araçları listeler.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Makinenizdeki bir aracı kaldırın.
[dotnet tool update](dotnet-tool-update.md) | Makinenize yüklenen bir aracı güncelleştirir.

### <a name="additional-tools"></a>Ek araçlar

.NET Core SDK 2.1.300 ile başlayarak, sadece proje bazında `DotnetCliToolReference` kullanılabilen bir dizi araç artık .NET Core SDK'nın bir parçası olarak kullanılabilir. Bu araçlar aşağıdaki tabloda listelenmiştir:

| Araç                                              | İşlev                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Geliştirme sertifikaları oluşturur ve yönetir.                |
| [Ef](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core komut satırı araçları.                    |
| sql önbellek                                         | SQL Server önbellek komut satırı araçları.                         |
| [kullanıcı sırları](/aspnet/core/security/app-secrets) | Geliştirme kullanıcı sırlarını yönetir.                            |
| [Izle](/aspnet/core/tutorials/dotnet-watch)      | Dosyalar değiştiğinde komutu çalıştıran bir dosya izleyicisi başlatır. |

Her araç hakkında daha `dotnet <tool-name> --help`fazla bilgi için yazın.

## <a name="examples"></a>Örnekler

Yeni bir .NET Core konsol uygulaması oluşturun:

```dotnetcli
dotnet new console
```

Belirli bir dizinde bir proje ve bağımlılıkları oluşturun:

```dotnetcli
dotnet build
```

Bir uygulama çalıştırın:

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>Ortam değişkenleri

- `DOTNET_ROOT`, `DOTNET_ROOT(x86)`

  Varsayılan konumda yüklü değillerse .NET Core çalışma saatlerinin konumunu belirtir. Windows'daki varsayılan `C:\Program Files\dotnet`konum. Linux ve macOS üzerinde `/usr/share/dotnet`varsayılan konum . Bu ortam değişkeni yalnızca oluşturulan yürütülebilir uygulamalar (ek hosts) aracılığıyla uygulamaları çalıştırırken kullanılır. `DOTNET_ROOT(x86)`bunun yerine, 64 bit işletim sistemi üzerinde 32 bit çalıştırılabilir çalıştırılırken kullanılır.

- `DOTNET_PACKAGES`

  Genel paketler klasörü. Ayarlanmamışsa, varsayılan `~/.nuget/packages` olarak Unix'te veya `%userprofile%\.nuget\packages` Windows'da olur.

- `DOTNET_SERVICING`

  Çalışma süresini yüklerken paylaşılan ana bilgisayar tarafından kullanılacak servis dizininin konumunu belirtir.

- `DOTNET_NOLOGO`

  .NET Core karşılama ve telemetri iletilerinin ilk çalıştırmada görüntülenip görüntülenmediğini belirtir. `true` Bu iletileri `true`(değerler, veya `1` `yes` kabul edilen) veya izin `false` verecek şekilde `false` `0`(değerler, , veya `no` kabul edilen) sessize almak üzere ayarlayın. Ayarlanmazsa, varsayılan `false` değerdir ve iletiler ilk çalıştırmada görüntülenir. Bu bayrağın telemetri üzerinde `DOTNET_CLI_TELEMETRY_OPTOUT` hiçbir etkisi yoktur (telemetri göndermeyi devre dışı bırakmak için bkz.

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  .NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft'a gönderilmeyeceğini belirtir. Telemetri özelliğini devre dışı bırakacak şekilde `1`ayarlayın `yes` (değerler `true`, veya kabul edilir). `true` Aksi takdirde, `false` telemetri özellikleri `false`(değerler , `0`veya `no` kabul) içine tercih etmek için ayarlayın. Ayaredilmezse, varsayılan `false` ve telemetri özelliği etkindir.

- `DOTNET_MULTILEVEL_LOOKUP`

  .NET Core çalışma zamanı, paylaşılan çerçeve veya SDK'nın genel konumdan çözülüp çözülmeyeceğini belirtir. Ayarlanmazise, varsayılan olarak 1 `true`(mantıksal). Genel konumdan `false`çözüme kavuşturulması ve .NET Core yüklemelerini yalıtmak için 0 (mantıksal) olarak ayarlayın. Çok düzeyli arama hakkında daha fazla bilgi [için, Çok düzeyli SharedFX Arama'ya](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)bakın.

- `DOTNET_ROLL_FORWARD`**.NET Core 3.x SDK ile başlayan kullanılabilir.**

  Yuvarlanan ileri davranışını belirler. Daha fazla bilgi `--roll-forward` için bu makalenin önceki seçeneğine bakın.

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**.NET Core 2.x SDK'da mevcuttur.**

  Devre dışı bırakır küçük sürüm, `0`eğer ayarlanırsa. Daha fazla bilgi için [bkz.](../whats-new/dotnet-core-2-1.md#roll-forward)

- `DOTNET_CLI_UI_LANGUAGE`

  CLI UI'nin dilini ayarlar. `en-us` Desteklenen değerler Visual Studio ile aynıdır. Daha fazla bilgi için [Visual Studio yükleme belgelerinde](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)yükleyici dilini değiştirme bölümüne bakın. .NET kaynak yöneticisi kuralları geçerlidir, böylece&mdash; `CultureInfo` ağaçtaki torunları da seçebileceğiniz tam bir eşleşme seçmeniz gerekmez. Örneğin, bunu `fr-CA`ayarlarsanız, CLI `fr` çevirileri bulur ve kullanır. Desteklenmeyen bir dile ayarlarsanız, CLI İngilizce'ye geri döner.

- `DOTNET_DISABLE_GUI_ERRORS`

  GUI özellikli oluşturulan yürütülebilirler için - normalde belirli hata sınıfları için gösteren iletişim açılır pencereaçılır penceresini devre dışı kılabilir. Sadece bu `stderr` gibi durumlarda yazar ve çıkar.
  
- `DOTNET_ADDITIONAL_DEPS`

  CLI seçeneğine `--additional-deps`eşdeğerdir.

- `DOTNET_RUNTIME_ID`

  Algılanan RID geçersiz kılar.

- `DOTNET_SHARED_STORE`

  Montaj çözünürlüğünün bazı durumlarda geri aldığı "paylaşılan deponun" konumu.

- `DOTNET_STARTUP_HOOKS`

  Başlangıç kancalarını yüklemek ve çalıştırmak için montajların listesi.

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  Barındırma bileşenlerinden gelen tanılama izlemelerini `dotnet.exe` `hostfxr`denetler, örneğin , , ve `hostpolicy`.

## <a name="see-also"></a>Ayrıca bkz.

- [Runtime Yapılandırma Dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md)
