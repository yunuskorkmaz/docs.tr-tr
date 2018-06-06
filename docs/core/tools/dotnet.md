---
title: DotNet command - .NET Core CLI
description: Dotnet komutu (.NET Core CLI araçlarını genel sürücüsü) ve kullanımı hakkında bilgi edinin.
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 788dc746705f9328683019ab3ad9836204a1ea63
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805665"
---
# <a name="dotnet-command"></a>DotNet komutu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet` -Komut satırı komutlarını çalıştırmak için genel sürücüsü.

## <a name="synopsis"></a>Özet

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a>Açıklama

`dotnet` Komut satırı arabirimi (CLI) zincirinin için genel bir sürücüsüdür. Kendi kendine çağrılan kısa kullanım yönergeleri sağlar.

Her belirli bir özellik, bir komut olarak uygulanır. Bu özelliği kullanmak için komutu sonra belirtilen `dotnet`, gibi [ `dotnet build` ](dotnet-build.md). Tüm komut aşağıdaki bağımsız değişkenleri, kendi bağımsız değişkenler.

Yalnızca bir kez `dotnet` kendi başına bir komut çalıştırmaktır olarak kullanılan [framework bağımlı uygulamaları](../deploying/index.md). Bir uygulama DLL belirtin sonra `dotnet` uygulamasını çalıştırmak için fiili (örneğin, `dotnet myapp.dll`).

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

Ek yoluna *deps.json* dosya.

`--additionalprobingpath <PATH>`

Algılama İlkesi ve araştırma için derlemeleri içeren yolu.

`-d|--diagnostics`

Tanılama çıktıları sağlar.

`--fx-version <VERSION>`

Uygulamayı çalıştırmak için kullanılacak yüklü .NET çekirdeği çalışma zamanı sürümü.

`-h|--help`

Komutu için kısa bir Yardım yazdırır. İle kullanıyorsanız, `dotnet`, ayrıca kullanılabilir komutların listesini yazdırır.

`--info`

CLI araçları ve geçerli işletim sistemi gibi ortam hakkında ayrıntılı bilgi yazdırır, sürüm ve diğer bilgiler için SHA uygulayın.

`--list-runtimes`

Yüklü .NET çekirdeği çalışma zamanları görüntüler.

`--list-sdks`

Yüklü .NET Core SDK'ları görüntüler.

`--roll-forward-on-no-candidate-fx`

 Dökümünü hiçbir aday paylaşılan Framework'te iletin.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`. Her komut desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.

`--version`

Kullanımdaki .NET Core SDK sürümü yazdırır.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

Ek yoluna *deps.json* dosya.

`--additionalprobingpath <PATH>`

Algılama İlkesi ve araştırma için derlemeleri içeren yolu.

`-d|--diagnostics`

Tanılama çıktıları sağlar.

`--fx-version <VERSION>`

Uygulamayı çalıştırmak için kullanılacak yüklü .NET çekirdeği çalışma zamanı sürümü.

`-h|--help`

Komutu için kısa bir Yardım yazdırır. İle kullanıyorsanız, `dotnet`, ayrıca kullanılabilir komutların listesini yazdırır.

`--info`

CLI araçları ve geçerli işletim sistemi gibi ortam hakkında ayrıntılı bilgi yazdırır, sürüm ve diğer bilgiler için SHA uygulayın.

`--roll-forward-on-no-candidate-fx`

 Dökümünü hiçbir aday paylaşılan Framework'te iletin.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`. Her komut desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.

`--version`

Kullanımdaki .NET Core SDK sürümü yazdırır.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Algılama İlkesi ve araştırma için derlemeleri içeren yolu.

`-d|--diagnostics`

Tanılama çıktıları sağlar.

`--fx-version <VERSION>`

Uygulamayı çalıştırmak için kullanılacak yüklü .NET çekirdeği çalışma zamanı sürümü.

`-h|--help`

Komutu için kısa bir Yardım yazdırır. İle kullanıyorsanız, `dotnet`, ayrıca kullanılabilir komutların listesini yazdırır.

`--info`

CLI araçları ve geçerli işletim sistemi gibi ortam hakkında ayrıntılı bilgi yazdırır, sürüm ve diğer bilgiler için SHA uygulayın.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyi ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`. Her komut desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.

`--version`

Kullanımdaki .NET Core SDK sürümü yazdırır.

---

## <a name="dotnet-commands"></a>DotNet komutları

### <a name="general"></a>Genel

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

| Komut                                       | İşlev                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Bir .NET Core uygulaması oluşturur.                                     |
| [DotNet yapı-sunucu](dotnet-build-server.md) | Bir yapı tarafından başlatılan sunucularıyla etkileşim kurar.                          |
| [dotnet clean](dotnet-clean.md)               | Temiz yapı çıkarır.                                                |
| [dotnet help](dotnet-help.md)                 | Komutu için çevrimiçi belgeleri ayrıntılı gösterir.           |
| [dotnet migrate](dotnet-migrate.md)           | Geçerli bir önizleme 2 projeyi .NET Core SDK 1.0 projeye geçirir.  |
| [dotnet msbuild](dotnet-msbuild.md)           | MSBuild komut satırında erişim sağlar.                        |
| [dotnet new](dotnet-new.md)                   | Bir C# veya belirli bir şablon için F # projesine başlatır.                |
| [dotnet pack](dotnet-pack.md)                 | Kodunuzun bir NuGet paketi oluşturur.                               |
| [dotnet publish](dotnet-publish.md)           | .NET framework bağımlı veya kendi içinde bulunan uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md)           | Belirli bir uygulamayla ilgili bağımlılıkları yükler.                  |
| [dotnet run](dotnet-run.md)                   | Uygulama kaynağından çalışır.                                   |
| [dotnet sln](dotnet-sln.md)                   | Eklemek için seçenekler kaldırın ve bir çözüm dosyasında projelerini listeleyin.       |
| [dotnet store](dotnet-store.md)               | Derlemeleri çalışma zamanı paketi deposunda saklar.                     |
| [dotnet test](dotnet-test.md)                 | Test Çalıştırıcısı kullanarak testleri çalıştırır.                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

| Komut                             | İşlev                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Bir .NET Core uygulaması oluşturur.                                     |
| [dotnet clean](dotnet-clean.md)     | Temiz yapı çıkarır.                                              |
| [dotnet help](dotnet-help.md)       | Komutu için çevrimiçi belgeleri ayrıntılı gösterir.           |
| [dotnet migrate](dotnet-migrate.md) | Geçerli bir önizleme 2 projeyi .NET Core SDK 1.0 projeye geçirir.  |
| [dotnet msbuild](dotnet-msbuild.md) | MSBuild komut satırında erişim sağlar.                        |
| [dotnet new](dotnet-new.md)         | Bir C# veya belirli bir şablon için F # projesine başlatır.                |
| [dotnet pack](dotnet-pack.md)       | Kodunuzun bir NuGet paketi oluşturur.                               |
| [dotnet publish](dotnet-publish.md) | .NET framework bağımlı veya kendi içinde bulunan uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md) | Belirli bir uygulamayla ilgili bağımlılıkları yükler.                  |
| [dotnet run](dotnet-run.md)         | Uygulama kaynağından çalışır.                                   |
| [dotnet sln](dotnet-sln.md)         | Eklemek için seçenekler kaldırın ve bir çözüm dosyasında projelerini listeleyin.       |
| [dotnet store](dotnet-store.md)     | Derlemeleri çalışma zamanı paketi deposunda saklar.                     |
| [dotnet test](dotnet-test.md)       | Test Çalıştırıcısı kullanarak testleri çalıştırır.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

| Komut                             | İşlev                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Bir .NET Core uygulaması oluşturur.                                     |
| [dotnet clean](dotnet-clean.md)     | Temiz yapı çıkarır.                                              |
| [dotnet migrate](dotnet-migrate.md) | Geçerli bir önizleme 2 projeyi .NET Core SDK 1.0 projeye geçirir.  |
| [dotnet msbuild](dotnet-msbuild.md) | MSBuild komut satırında erişim sağlar.                        |
| [dotnet new](dotnet-new.md)         | Bir C# veya belirli bir şablon için F # projesine başlatır.                |
| [dotnet pack](dotnet-pack.md)       | Kodunuzun bir NuGet paketi oluşturur.                               |
| [dotnet publish](dotnet-publish.md) | .NET framework bağımlı veya kendi içinde bulunan uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md) | Belirli bir uygulamayla ilgili bağımlılıkları yükler.                  |
| [dotnet run](dotnet-run.md)         | Uygulama kaynağından çalışır.                                   |
| [dotnet sln](dotnet-sln.md)         | Eklemek için seçenekler kaldırın ve bir çözüm dosyasında projelerini listeleyin.       |
| [dotnet test](dotnet-test.md)       | Test Çalıştırıcısı kullanarak testleri çalıştırır.                                     |

---

### <a name="project-references"></a>Proje başvuruları

Komut | İşlev
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Proje başvurusu ekler.
[dotnet list reference](dotnet-list-reference.md) | Proje başvuruları listeler.
[dotnet remove reference](dotnet-remove-reference.md) | Proje başvurusu kaldırır.

### <a name="nuget-packages"></a>NuGet paketleri

Komut | İşlev
--- | ---
[dotnet add package](dotnet-add-package.md) | Bir NuGet paketi ekler.
[dotnet remove package](dotnet-remove-package.md) | Bir NuGet Paketi kaldırır.

### <a name="nuget-commands"></a>NuGet komutları

Komut | İşlev
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Sunucudan paket unlists veya siler.
[dotnet nuget locals](dotnet-nuget-locals.md) | Temizler veya http isteği önbelleği, geçici önbelleği veya makine genelinde genel paketler klasörü gibi yerel NuGet kaynakları listeler.
[dotnet nuget push](dotnet-nuget-push.md) | Sunucuya bir paket gönderir ve onu yayımlar.

### <a name="global-tools-commands"></a>Genel Araçlar komutları

[.NET core genel Araçları](global-tools.md) .NET Core SDK 2.1.300 başlayarak kullanılabilir:

Komut | İşlev
--- | ---
[DotNet aracı yükleme](dotnet-tool-install.md) | Makinenize genel bir aracı yükler.
[DotNet araç listesi](dotnet-tool-list.md) | Tüm genel makinenizde varsayılan dizin veya belirtilen yol şu anda yüklü araçları listeler.
[DotNet Aracı kaldırma](dotnet-tool-uninstall.md) | Genel bir aracı makinenizden kaldırır.
[DotNet aracı güncelleştirmesi](dotnet-tool-update.md) | Genel bir aracı makinenizde güncelleştirir.

### <a name="additional-tools"></a>Ek araçlar

.NET Core SDK 2.1.300, yalnızca bir başına proje temel kullanarak kullanılabilir araçları sayısı ile başlayan `DotnetCliToolReference` artık kullanılabilir .NET Core SDK'ın bir parçası olarak. Bu araçlar içerir:

| Aracı                                              | İşlev                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| Geliştirme sertifikaları                                         | Oluşturur ve geliştirme sertifikaları yönetir.                |
| [EF](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Çekirdek komut satırı araçları.                    |
| SQL önbellek                                         | SQL Server önbellek komut satırı araçları.                         |
| [kullanıcı parolaları](/aspnet/core/security/app-secrets) | Geliştirme kullanıcı parolaları yönetir.                            |
| [İzleme](/aspnet/core/tutorials/dotnet-watch)      | Dosyalar değiştiğinde, bir komut çalıştıran bir dosya İzleyicisi başlatır. |

Her aracı hakkında daha fazla bilgi için yürütme `dotnet <tool-name> --help`.

## <a name="examples"></a>Örnekler

Yeni bir .NET Core konsol uygulaması oluşturur:

`dotnet new console`

Belirli bir uygulamayla ilgili bağımlılıkları geri yükleyin:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Proje ve bağımlılıklarını belirli bir dizinde oluşturun:

`dotnet build`

Adlı framework bağımlı uygulamayı çalıştırma `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Ortam değişkenleri

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`DOTNET_PACKAGES`

Birincil paketi önbelleği. Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows.

`DOTNET_SERVICING`

Çalışma zamanı yüklerken paylaşılan ana bilgisayar tarafından kullanılacak hizmet dizin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir. Kümesine `true` telemetri özelliğini çevirin için (değerleri `true`, `1`, veya `yes` kabul). Aksi takdirde kümesine `false` telemetri özelliklerini geri çevirme (değerleri `false`, `0`, veya `no` kabul). Ayarlanmazsa varsayılan olup olmadığını `false` ve telemetri özellik etkindir.

`DOTNET_MULTILEVEL_LOOKUP`

.NET çekirdeği çalışma zamanı, paylaşılan framework veya SDK olmadığını çözümlenmiş genel konumu belirtir. Ayarlanmazsa, varsayılan olarak, `true`. Kümesine `false` değil genel konumdan çözmek ve .NET çekirdeği yüklemeleri buluncaya (değerleri `0` veya `false` kabul edilir). Birden çok düzeyli arama hakkında daha fazla bilgi için bkz: [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

İleriye doğru sürümü geri alma devre dışı bırakır küçük. Daha fazla bilgi için bkz: [ileriye](../whats-new/dotnet-core-2-1.md#roll-forward).

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

Birincil paketi önbelleği. Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows.

`DOTNET_SERVICING`

Çalışma zamanı yüklerken paylaşılan ana bilgisayar tarafından kullanılacak hizmet dizin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir. Kümesine `true` telemetri özelliğini çevirin için (değerleri `true`, `1`, veya `yes` kabul). Aksi takdirde kümesine `false` telemetri özelliklerini geri çevirme (değerleri `false`, `0`, veya `no` kabul). Ayarlanmazsa varsayılan olup olmadığını `false` ve telemetri özellik etkindir.

`DOTNET_MULTILEVEL_LOOKUP`

.NET çekirdeği çalışma zamanı, paylaşılan framework veya SDK olmadığını çözümlenmiş genel konumu belirtir. Ayarlanmazsa, varsayılan olarak, `true`. Kümesine `false` değil genel konumdan çözmek ve .NET çekirdeği yüklemeleri buluncaya (değerleri `0` veya `false` kabul edilir). Birden çok düzeyli arama hakkında daha fazla bilgi için bkz: [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

Birincil paketi önbelleği. Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows.

`DOTNET_SERVICING`

Çalışma zamanı yüklerken paylaşılan ana bilgisayar tarafından kullanılacak hizmet dizin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir. Kümesine `true` telemetri özelliğini çevirin için (değerleri `true`, `1`, veya `yes` kabul). Aksi takdirde kümesine `false` telemetri özelliklerini geri çevirme (değerleri `false`, `0`, veya `no` kabul). Ayarlanmazsa varsayılan olup olmadığını `false` ve telemetri özellik etkindir.

---
