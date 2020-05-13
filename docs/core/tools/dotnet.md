---
title: DotNet komutu
description: DotNet komutu (.NET Core CLI için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 02/13/2020
ms.openlocfilehash: 88e92b3ff5e8f68b980015a817434dd2d67df93a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378835"
---
# <a name="dotnet-command"></a>DotNet komutu

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

## <a name="name"></a>Name

`dotnet`-.NET Core CLI için genel sürücü.

## <a name="synopsis"></a>Özeti

Kullanılabilir komutlar ve ortam hakkında bilgi almak için:

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

Bir komutu çalıştırmak için (SDK yüklemesi gerektirir):

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

`--roll-forward`, .NET Core 3. x sürümünden bu yana kullanılabilir. `--roll-forward-on-no-candidate-fx`.NET Core 2. x için kullanın.

## <a name="description"></a>Açıklama

`dotnet`Komutun iki işlevi vardır:

- .NET Core projeleriyle çalışmak için komutlar sağlar.

  Örneğin, [`dotnet build`](dotnet-build.md) bir proje oluşturur. Her komut kendi seçeneklerini ve bağımsız değişkenlerini tanımlar. Tüm komutlar, `--help` komutu kullanma hakkında kısa bir belge yazdırma seçeneğini destekler.

- .NET Core uygulamaları çalıştırır.

  Uygulamayı çalıştırmak için bir uygulama dosyasının yolunu belirtin `.dll` .  Uygulamayı çalıştırmak için, konsol uygulamaları söz konusu olduğunda giriş noktasını bulmak ve yürütmek anlamına gelir `Main` . Örneğin, `dotnet myapp.dll` `myapp` uygulamayı çalıştırır. Dağıtım seçenekleri hakkında bilgi edinmek için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md) .

## <a name="options"></a>Seçenekler

Farklı seçenekler, `dotnet` bir komut çalıştırmak ve bir uygulamayı çalıştırmak için tek başına kullanılabilir.

### <a name="options-for-dotnet-by-itself"></a>Tek başına DotNet seçenekleri

Aşağıdaki seçenekler `dotnet` kendi kendine yöneliktir. Örneğin, `dotnet --info`. Ortamla ilgili bilgi yazdırır.

- **`--info`**

  .NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.

- **`--version`**

  Kullanımda olan .NET Core SDK sürümünü yazdırır.

- **`--list-runtimes`**

  Yüklü .NET Core çalışma zamanlarının listesini yazdırır. SDK 'nın x86 sürümü yalnızca x86 çalışma zamanlarını listeler ve SDK 'nın x64 sürümü yalnızca x64 çalışma zamanları listeler.

- **`--list-sdks`**

  Yüklü .NET Core SDK 'larının listesini yazdırır.

- **`-h|--help`**

  Kullanılabilir komutların bir listesini yazdırır.

### <a name="sdk-options-for-running-a-command"></a>Komut çalıştırmak için SDK seçenekleri

Aşağıdaki seçenekler `dotnet` bir komutla yöneliktir. Örneğin, `dotnet build --help`.

- **`-d|--diagnostics`**

  Tanılama çıkışını izin vermez.

- **`-v|--verbosity <LEVEL>`**

  Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` . Her komutta desteklenmez. Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.

- **`-h|--help`**

  Gibi belirli bir komutun belgelerini yazdırır `dotnet build --help` .

- **`command options`**

  Her komut, bu komuta özgü seçenekleri tanımlar. Kullanılabilir seçeneklerin listesi için bkz. özel komut sayfası.

### <a name="runtime-options"></a>Çalışma zamanı seçenekleri

Bir uygulama çalıştırıldığında aşağıdaki seçenekler mevcuttur `dotnet` . Örneğin, `dotnet myapp.dll --roll-forward Major`.

- **`--additionalprobingpath <PATH>`**

  Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.

- **`--additional-deps <PATH>`**

  Ek *. Deps. JSON* dosyasının yolu. Bir *Deps. JSON* dosyası, derleme çakışmalarını çözmek için kullanılan bağımlılıklar, derleme bağımlılıkları ve sürüm bilgilerinin bir listesini içerir. Daha fazla bilgi için bkz. GitHub 'da [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) .

- **`--depsfile <PATH_TO_DEPSFILE>`**

  *Deps. JSON* dosyasının yolu. *Deps. JSON* dosyası, uygulamayı çalıştırmak için gerekli bağımlılıklar hakkında bilgi içeren bir yapılandırma dosyasıdır. Bu dosya .NET Core SDK tarafından oluşturulur.

- **`--runtimeconfig`**

  *Runtimeconfig. JSON* dosyasının yolu. *Runtimeconfig. JSON* dosyası, çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır. Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward <SETTING>`****.NET Core SDK 3,0 ' den başlayarak kullanılabilir.**

  Uygulamaya nasıl iletme uygulanacağını denetler. `SETTING`Aşağıdaki değerlerden biri olabilir. Belirtilmemişse, `Minor` varsayılandır.

  - `LatestPatch`-En yüksek düzeltme eki sürümüne ilet. Bu, ikincil sürüm iletmeyi devre dışı bırakır.
  - `Minor`-İstenen alt sürüm eksikse, en düşük düzeydeki sürüme ilet. İstenen ikincil sürüm varsa, LatestPatch ilkesi kullanılır.
  - `Major`-İstenen ana sürüm eksikse, en düşük ana sürüme ve en düşük alt sürüme ilet. İstenen ana sürüm varsa, Ikincil ilke kullanılır.
  - `LatestMinor`-İstenen alt sürüm mevcut olsa bile en yüksek düzeyde alt sürüme ilet. Bileşen barındırma senaryolarına yöneliktir.
  - `LatestMajor`-İstenen ana mevcut olsa bile en yüksek ve en yüksek düzeyde alt sürüme ilet. Bileşen barındırma senaryolarına yöneliktir.
  - `Disable`-İleri geri alma. Yalnızca belirtilen sürüme bağlayın. Bu ilke, en son düzeltme eklerine iletme özelliğini devre dışı bıraktığından genel kullanım için önerilmez. Bu değer yalnızca test için önerilir.

  Hariç `Disable` olmak üzere, tüm ayarlar kullanılabilir en yüksek düzeltme eki sürümünü kullanacaktır.

  İleri sarma davranışı Ayrıca bir proje dosyası özelliği, çalışma zamanı yapılandırma dosyası özelliği ve ortam değişkeni içinde de yapılandırılabilir. Daha fazla bilgi için bkz. [ana sürüm çalışma zamanı ileri iletme](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

- **`--roll-forward-on-no-candidate-fx <N>`****.NET Core 2. x SDK ' da kullanılabilir.**

  Gerekli paylaşılan çerçeve kullanılabilir olmadığında davranışını tanımlar. `N`şunları yapabilirsiniz:

  - `0`-Hatta ikincil sürüm iletmeyi devre dışı bırakın.
  - `1`-Önemli sürümde değil, küçük sürümde ilet. Bu, varsayılan davranıştır.
  - `2`-Küçük ve büyük sürümlerde ilet.

  Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).

  .NET Core 3,0 ile başlayarak bu seçeneğin yerini almıştır `--roll-forward` ve bunun yerine bu seçenek kullanılmalıdır.

- **`--fx-version <VERSION>`**

  Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.

  Bu seçenek, uygulamanın dosyasındaki ilk Framework başvurusunun sürümünü geçersiz kılar `.runtimeconfig.json` . Bu, yalnızca tek bir çerçeve başvurusu varsa beklendiği gibi çalıştığı anlamına gelir. Uygulamanın birden fazla Framework başvurusu varsa, bu seçeneğin kullanılması hatalara neden olabilir.

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
| [dotnet new](dotnet-new.md)                   | Belirli bir şablon için C# veya F # projesi başlatır.                |
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
[dotnet nuget push](dotnet-nuget-push.md) | Bir paketi sunucuya gönderir ve yayımlar.
[dotnet nuget locals](dotnet-nuget-locals.md) | Http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.
[dotnet nuget add source](dotnet-nuget-add-source.md) | Bir NuGet kaynağı ekler.
[dotnet nuget disable source](dotnet-nuget-disable-source.md) | Bir NuGet kaynağını devre dışı bırakır.
[dotnet nuget enable source](dotnet-nuget-enable-source.md) | Bir NuGet kaynağını sunar.
[dotnet nuget list source](dotnet-nuget-list-source.md) | Tüm yapılandırılmış NuGet kaynaklarını listeler.
[dotnet nuget remove source](dotnet-nuget-remove-source.md) | Bir NuGet kaynağını kaldırır.
[dotnet nuget update source](dotnet-nuget-update-source.md) | Bir NuGet kaynağını güncelleştirir.

### <a name="global-tool-path-and-local-tools-commands"></a>Küresel, araç yolu ve yerel araçlar komutları

Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır. Araçları kendiniz yazabilir veya üçüncü taraflarca yazılmış Araçları yükleyebilirsiniz. Araçlar genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir. Daha fazla bilgi için bkz. [.NET Core araçlarına genel bakış](global-tools.md). Genel ve araç yolu araçları .NET Core SDK 2,1 ' den başlayarak kullanılabilir. Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.

Komut | İşlev
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Makinenize bir araç kurar.
[dotnet tool list](dotnet-tool-list.md) | Makinenizde yüklü olan tüm genel, araç-yol veya yerel araçları listeler.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Bir aracı makinenizden kaldırır.
[dotnet tool update](dotnet-tool-update.md) | Makinenizde yüklü bir aracı güncelleştirir.

### <a name="additional-tools"></a>Ek araçlar

.NET Core SDK 2.1.300 ' den itibaren, yalnızca kullanılarak proje bazında kullanılabilen birçok araç, `DotnetCliToolReference` .NET Core SDK bir parçası olarak kullanılabilir. Bu araçlar aşağıdaki tabloda listelenmiştir:

| Araç                                              | İşlev                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| geliştirme-CERT                                         | Geliştirme sertifikaları oluşturur ve yönetir.                |
| [aşv](/ef/core/miscellaneous/cli/dotnet)           | Komut satırı araçlarını Entity Framework Core.                    |
| SQL-Cache                                         | Önbellek komut satırı araçlarını SQL Server.                         |
| [Kullanıcı gizli dizileri](/aspnet/core/security/app-secrets) | Geliştirme Kullanıcı gizli dizilerini yönetir.                            |
| [Servisi](/aspnet/core/tutorials/dotnet-watch)      | Dosyalar değiştiğinde bir komutu çalıştıran bir dosya İzleyicisi başlatır. |

Her araç hakkında daha fazla bilgi için, yazın `dotnet <tool-name> --help` .

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

  Varsayılan konumda yüklü değilse, .NET Core çalışma zamanlarının konumunu belirtir. Windows üzerinde varsayılan konum `C:\Program Files\dotnet` . Linux ve macOS 'ta varsayılan konum `/usr/share/dotnet` . Bu ortam değişkeni yalnızca oluşturulan yürütülebilir dosyalar (apphosts) aracılığıyla uygulamalar çalıştırılırken kullanılır. `DOTNET_ROOT(x86)`, 64 bit IŞLETIM sisteminde 32 bitlik bir yürütülebilir dosya çalıştırılırken kullanılır.

- `DOTNET_PACKAGES`

  Genel paketler klasörü. Ayarlanmamışsa, varsayılan olarak `~/.nuget/packages` UNIX veya `%userprofile%\.nuget\packages` Windows üzerinde olur.

- `DOTNET_SERVICING`

  Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.

- `DOTNET_NOLOGO`

  .NET Core karşılama ve telemetri iletilerinin ilk çalıştırmada görüntülenip görüntülenmeyeceğini belirtir. `true`Bu iletilerin sessize (değerler `true` , `1` veya `yes` kabul edildi) veya `false` izin ver (değerler `false` , `0` veya `no` kabul edildi) olarak ayarlanmış olarak ayarlayın. Ayarlanmamışsa, varsayılan olur `false` ve iletiler ilk çalıştırmada görüntülenir. Bu bayrağın telemetri üzerinde hiçbir etkisi yoktur ( `DOTNET_CLI_TELEMETRY_OPTOUT` telemetri göndermek için bkz.).

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  .NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir. `true`Telemetri özelliğini devre dışı bırakmak için olarak ayarlayın (değerler `true` , `1` veya `yes` kabul edildi). Aksi takdirde, `false` telemetri özelliklerini (değerler `false` , `0` veya `no` kabul edildi) kabul etmek için olarak ayarlayın. Ayarlanmamışsa, varsayılan olarak `false` ve telemetri özelliği etkindir.

- `DOTNET_MULTILEVEL_LOOKUP`

  .NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir. Ayarlanmazsa, varsayılan olarak 1 (mantıksal) olur `true` . `false`Genel konumdan çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olmak için 0 (mantıksal) olarak ayarlayın. Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD`**.NET Core 3. x ile başlayarak kullanılabilir.**

  İleri alma davranışını belirler. Daha fazla bilgi için `--roll-forward` Bu makaledeki önceki seçeneğe bakın.

- `DOTNET_ROLL_FORWARD_TO_PRERELEASE`**.NET Core 3. x ile başlayarak kullanılabilir.**

  `1`(Etkin) olarak ayarlandıysa, yayın sürümünden yayın öncesi sürümüne ileri doğru bir şekilde geri dönme imkanı sağlar. Varsayılan olarak ( `0` -Disabled), .NET Core çalışma zamanının yayın sürümü istendiğinde, geri alma yalnızca sürüm sürümlerini göz önünde bulunduracaktır.

  Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**.NET Core 2. x ' te kullanılabilir.**

  , Olarak ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır `0` . Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).

  Bu ayarın yerini .NET Core 3,0 ' de almıştır `DOTNET_ROLL_FORWARD` . Bunun yerine yeni ayarlar kullanılmalıdır.

- `DOTNET_CLI_UI_LANGUAGE`

  CLı Kullanıcı arabiriminin dilini, gibi bir yerel ayar değeri kullanarak ayarlar `en-us` . Desteklenen değerler, Visual Studio ile aynıdır. Daha fazla bilgi için [Visual Studio yükleme belgelerindeki](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)yükleyici dilini değiştirme bölümüne bakın. .NET Resource Manager kuralları uygulanır, bu sayede tam bir eşleşme seçmeniz gerekmez, ağaçta alt &mdash; öğeleri de seçebilirsiniz `CultureInfo` . Örneğin, olarak ayarlarsanız `fr-CA` , CLI çevirileri bulur ve kullanır `fr` . Bunu desteklenmeyen bir dile ayarlarsanız, CLı Ingilizce 'ye geri döner.

- `DOTNET_DISABLE_GUI_ERRORS`

  GUI özellikli oluşturulan yürütülebilir dosyalar için-normalde belirli hata sınıfları için gösterilen iletişim kutusu açılır penceresini devre dışı bırakır. Bu durumda yalnızca öğesine yazar `stderr` ve çıkar.
  
- `DOTNET_ADDITIONAL_DEPS`

  CLı seçeneğine eşdeğerdir `--additional-deps` .

- `DOTNET_RUNTIME_ID`

  Algılanan RID 'yi geçersiz kılar.

- `DOTNET_SHARED_STORE`

  Bazı durumlarda derleme çözümlemenin geri döndürüleceği "paylaşılan deponun" konumu.

- `DOTNET_STARTUP_HOOKS`

  Başlangıç kancalarını yüklemek ve yürütmek için derlemelerin listesi.

- `DOTNET_BUNDLE_EXTRACT_BASE_DIR`**.NET Core 3. x ile başlayarak kullanılabilir.**

  Yürütülmeden önce tek dosya uygulamasının ayıklandığı bir dizini belirtir.

  Daha fazla bilgi için bkz. [tek dosya yürütülebilir dosyaları](../whats-new/dotnet-core-3-0.md#single-file-executables).

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  , Ve gibi barındırma bileşenlerinden tanılama izlemeyi denetler `dotnet.exe` `hostfxr` `hostpolicy` .

  * `COREHOST_TRACE=[0/1]`-Varsayılan, `0` -izleme devre dışı. Olarak ayarlanırsa `1` , tanılama izlemesi etkinleştirilir.
  * `COREHOST_TRACEFILE=<file path>`-yalnızca izleme etkinse etkilidir `COREHOST_TRACE=1` . Ayarlandığında, izleme bilgileri belirtilen dosyaya yazılır, aksi takdirde izleme bilgileri üzerine yazılır `stderr` . **.NET Core 3. x ile başlayarak kullanılabilir.**
  * `COREHOST_TRACE_VERBOSITY=[1/2/3/4]`-Varsayılan değer `4` . Ayar yalnızca, ile izleme etkinleştirildiğinde kullanılır `COREHOST_TRACE=1` . **.NET Core 3. x ile başlayarak kullanılabilir.**
    * `4`-Tüm izleme bilgileri yazılır
    * `3`-yalnızca bilgilendirme, uyarı ve hata iletileri yazılır
    * `2`-yalnızca uyarı ve hata iletileri yazılır
    * `1`-yalnızca hata iletileri yazılır

  Uygulama başlatma hakkında ayrıntılı izleme bilgileri almanın tipik yolu, `COREHOST_TRACE=1` uygulamayı ayarlamak ve çalıştırmak için kullanılır `COREHOST_TRACEFILE=host_trace.txt` . `host_trace.txt`Geçerli dizinde ayrıntılı bilgiler içeren yeni bir dosya oluşturulur.

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md)
