---
title: DotNet komutu
description: Dotnet komut (.NET Core CLI araçları için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 06/04/2018
ms.openlocfilehash: 107a529952cce62dac840874fa5d6d8986376adf
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185642"
---
# <a name="dotnet-command"></a>DotNet komutu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet` -.NET kaynak kodu ve ikili dosyaları yönetme bir araç.

## <a name="synopsis"></a>Synopsis

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

`dotnet` .NET kaynak kodu ve ikili dosyaları yönetmek için bir araçtır. Gibi belirli görevleri gerçekleştiren komutları gösteren [ `dotnet build` ](dotnet-build.md) ve [ `dotnet run` ](dotnet-run.md). Her komut bağımsız kendi değişkenlerini tanımlar. Tür `--help` kısa erişmek için her komuttan sonra Yardım belgeleri.

`dotnet` DLL, uygulama belirterek uygulamaları çalıştırmak için kullanılan `dotnet myapp.dll`. Bkz: [.NET Core uygulama dağıtımı](../deploying/index.md) için dağıtım seçenekleri hakkında bilgi edinmek için.

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

Ek yolu *deps.json* dosya.

`--additionalprobingpath <PATH>`

Algılama İlkesi ve araştırma için derlemeleri içeren yolu.

`-d|--diagnostics`

Tanılama çıkışı sağlar.

`--fx-version <VERSION>`

Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanı sürümü.

`-h|--help`

Belirli bir komut için belgeler gibi yazdırır `dotnet build --help`. `dotnet --help` Kullanılabilir komutların bir listesini yazdırır.

`--info`

Bir .NET Core yüklemesi ve geçerli işletim sistemi ve .NET Core sürümünün SHA tamamlama gibi makine ortamı hakkında ayrıntılı bilgi yazdırır.

`--list-runtimes`

Yüklü .NET Core çalışma zamanlarını görüntüler.

`--list-sdks`

Yüklü .NET Core SDK'ları görüntüler.

`--roll-forward-on-no-candidate-fx <N>`

Gerekli paylaşılan çerçeve olmadığında davranışını tanımlar. `N` aşağıdakilerden biri olabilir:
* `0` -Daha alt sürümü ileri sarma devre dışı bırakın.
* `1` -İkincil sürüm, ancak ana sürüm İleri sarmanın. Bu varsayılan davranıştır.
* `2` -Küçük ve büyük sürüme göre İleri sarmanın.

 Daha fazla bilgi için [İleri sarmanın](../whats-new/dotnet-core-2-1.md#roll-forward).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`. Her komutu desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.

`--version`

Kullanımda .NET Core SDK'sı sürümünü yazdırır.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

Ek yolu *deps.json* dosya.

`--additionalprobingpath <PATH>`

Algılama İlkesi ve araştırma için derlemeleri içeren yolu.

`-d|--diagnostics`

Tanılama çıkışı sağlar.

`--fx-version <VERSION>`

Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanı sürümü.

`-h|--help`

Belirli bir komut için belgeler gibi yazdırır `dotnet build --help`. `dotnet --help` Kullanılabilir komutların bir listesini yazdırır.

`--info`

Bir .NET Core yüklemesi ve geçerli işletim sistemi ve .NET Core sürümünün SHA tamamlama gibi makine ortamı hakkında ayrıntılı bilgi yazdırır.

`--roll-forward-on-no-candidate-fx`

 Devre dışı bırakır podverze Top iletme, eğer ayarlanmış `0`. Daha fazla bilgi için [İleri sarmanın](../whats-new/dotnet-core-2-1.md#roll-forward).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`. Her komutu desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.

`--version`

Kullanımda .NET Core SDK'sı sürümünü yazdırır.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Algılama İlkesi ve araştırma için derlemeleri içeren yolu.

`-d|--diagnostics`

Tanılama çıkışı sağlar.

`--fx-version <VERSION>`

Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanı sürümü.

`-h|--help`

Belirli bir komut için belgeler gibi yazdırır `dotnet build --help`. `dotnet --help` Kullanılabilir komutların bir listesini yazdırır.

`--info`

Bir .NET Core yüklemesi ve geçerli işletim sistemi ve .NET Core sürümünün SHA tamamlama gibi makine ortamı hakkında ayrıntılı bilgi yazdırır.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`. Her komutu desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.

`--version`

Kullanımda .NET Core SDK'sı sürümünü yazdırır.

---

## <a name="dotnet-commands"></a>DotNet komutları

### <a name="general"></a>Genel

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

| Komut                                       | İşlev                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Bir .NET Core uygulaması oluşturur.                                     |
| [dotnet build-server](dotnet-build-server.md) | Bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.                          |
| [dotnet clean](dotnet-clean.md)               | Temiz yapı çıkarır.                                                |
| [dotnet help](dotnet-help.md)                 | Komut için çevrimiçi belgeleri ayrıntılı gösterir.           |
| [dotnet migrate](dotnet-migrate.md)           | Geçerli bir önizleme 2 projesi bir .NET Core SDK'sı 1.0 projesine geçirir.  |
| [dotnet msbuild](dotnet-msbuild.md)           | MSBuild komut satırını erişim sağlar.                        |
| [dotnet new](dotnet-new.md)                   | Başlatan bir C# veya F# verilen şablonu için proje.                |
| [dotnet pack](dotnet-pack.md)                 | Kodunuzun bir NuGet paketi oluşturur.                               |
| [dotnet publish](dotnet-publish.md)           | .NET framework bağımlı veya kendi içinde uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md)           | Belirli bir uygulama için bağımlılıkları yükler.                  |
| [dotnet run](dotnet-run.md)                   | Uygulama kaynağından çalışır.                                   |
| [dotnet sln](dotnet-sln.md)                   | Eklemek için seçenekler kaldırın ve çözüm dosyasındaki projeleri listeleyin.       |
| [dotnet store](dotnet-store.md)               | Derlemeler çalışma zamanı Paket Deposu.                     |
| [dotnet test](dotnet-test.md)                 | Test Çalıştırıcısı kullanarak testleri çalıştırır.                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

| Komut                             | İşlev                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Bir .NET Core uygulaması oluşturur.                                     |
| [dotnet clean](dotnet-clean.md)     | Temiz yapı çıkarır.                                              |
| [dotnet help](dotnet-help.md)       | Komut için çevrimiçi belgeleri ayrıntılı gösterir.           |
| [dotnet migrate](dotnet-migrate.md) | Geçerli bir önizleme 2 projesi bir .NET Core SDK'sı 1.0 projesine geçirir.  |
| [dotnet msbuild](dotnet-msbuild.md) | MSBuild komut satırını erişim sağlar.                        |
| [dotnet new](dotnet-new.md)         | Başlatan bir C# veya F# verilen şablonu için proje.                |
| [dotnet pack](dotnet-pack.md)       | Kodunuzun bir NuGet paketi oluşturur.                               |
| [dotnet publish](dotnet-publish.md) | .NET framework bağımlı veya kendi içinde uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md) | Belirli bir uygulama için bağımlılıkları yükler.                  |
| [dotnet run](dotnet-run.md)         | Uygulama kaynağından çalışır.                                   |
| [dotnet sln](dotnet-sln.md)         | Eklemek için seçenekler kaldırın ve çözüm dosyasındaki projeleri listeleyin.       |
| [dotnet store](dotnet-store.md)     | Derlemeler çalışma zamanı Paket Deposu.                     |
| [dotnet test](dotnet-test.md)       | Test Çalıştırıcısı kullanarak testleri çalıştırır.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

| Komut                             | İşlev                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Bir .NET Core uygulaması oluşturur.                                     |
| [dotnet clean](dotnet-clean.md)     | Temiz yapı çıkarır.                                              |
| [dotnet migrate](dotnet-migrate.md) | Geçerli bir önizleme 2 projesi bir .NET Core SDK'sı 1.0 projesine geçirir.  |
| [dotnet msbuild](dotnet-msbuild.md) | MSBuild komut satırını erişim sağlar.                        |
| [dotnet new](dotnet-new.md)         | Başlatan bir C# veya F# verilen şablonu için proje.                |
| [dotnet pack](dotnet-pack.md)       | Kodunuzun bir NuGet paketi oluşturur.                               |
| [dotnet publish](dotnet-publish.md) | .NET framework bağımlı veya kendi içinde uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md) | Belirli bir uygulama için bağımlılıkları yükler.                  |
| [dotnet run](dotnet-run.md)         | Uygulama kaynağından çalışır.                                   |
| [dotnet sln](dotnet-sln.md)         | Eklemek için seçenekler kaldırın ve çözüm dosyasındaki projeleri listeleyin.       |
| [dotnet test](dotnet-test.md)       | Test Çalıştırıcısı kullanarak testleri çalıştırır.                                     |

---

### <a name="project-references"></a>Proje başvuruları

Komut | İşlev
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Bir proje başvurusu ekler.
[dotnet list reference](dotnet-list-reference.md) | Proje başvuruları listeler.
[dotnet remove reference](dotnet-remove-reference.md) | Bir proje başvurusu kaldırır.

### <a name="nuget-packages"></a>NuGet paketleri

Komut | İşlev
--- | ---
[dotnet add package](dotnet-add-package.md) | Bir NuGet paketi ekler.
[dotnet remove package](dotnet-remove-package.md) | Bir NuGet Paketi kaldırır.

### <a name="nuget-commands"></a>NuGet komutları

Komut | İşlev
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Sunucudan bir paket unlists veya siler.
[dotnet nuget locals](dotnet-nuget-locals.md) | Temizler veya http istek önbelleği, geçici bir önbellekte veya makine genelindeki genel paketleri klasörü gibi yerel NuGet kaynakları listeler.
[dotnet nuget push](dotnet-nuget-push.md) | Sunucuya bir paket gönderir ve belgeyi yayımlar.

### <a name="global-tools-commands"></a>Genel Araçlar komutları

[.NET core Araçları Genel](global-tools.md) 2.1.300 .NET Core SDK ile başlayarak kullanılabilir:

Komut | İşlev
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Makinenize genel bir aracı yükler.
[dotnet tool list](dotnet-tool-list.md) | Tüm genel varsayılan dizinde makinenizde veya belirtilen yolda yüklü araçları listeler.
[dotnet tool install](dotnet-tool-uninstall.md) | Genel bir aracı makinenizde kaldırır.
[dotnet tool update](dotnet-tool-update.md) | Genel bir aracı makinenizde güncelleştirir.

### <a name="additional-tools"></a>Ek araçlar

.NET Core SDK 2.1.300, yalnızca bir proje kullanarak mevcut araçlar ile başlayan `DotnetCliToolReference` artık .NET Core SDK'sını bir parçası olarak. Bu araçlar aşağıdaki tabloda listelenmiştir:

| Aracı                                              | İşlev                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Oluşturur ve geliştirme sertifikaları yönetir.                |
| [EF](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core komut satırı araçları.                    |
| SQL önbellek                                         | SQL Server önbellek komut satırı araçları.                         |
| [kullanıcı parolaları](/aspnet/core/security/app-secrets) | Geliştirme kullanıcı parolalarını yönetir.                            |
| [İzleme](/aspnet/core/tutorials/dotnet-watch)      | Bir komut dosyaları değiştirdiğinizde çalıştıran bir dosya İzleyicisi başlatır. |

Her araç hakkında daha fazla bilgi için türü `dotnet <tool-name> --help`.

## <a name="examples"></a>Örnekler

Yeni bir .NET Core konsol uygulaması oluşturur:

`dotnet new console`

Belirli bir uygulamanın bağımlılıklarını geri yükleme:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Bir proje ve bağımlılıkları belirli bir dizinde oluşturun:

`dotnet build`

DLL, uygulama çalıştırmak `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Ortam değişkenleri

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`DOTNET_PACKAGES`

Birincil paket önbelleğini. Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows üzerinde.

`DOTNET_SERVICING`

Çalışma zamanı yüklerken paylaşılan bir ana bilgisayar tarafından kullanılacak bakım dizin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir. Kümesine `true` ayrılma telemetri özelliği (değerleri `true`, `1`, veya `yes` kabul). Aksi takdirde, kümesine `false` telemetri özelliklerini kabul etme (değerleri `false`, `0`, veya `no` kabul). Varsayılan ayarlanmazsa `false` ve telemetri özellik etkin durumda.

`DOTNET_MULTILEVEL_LOOKUP`

.NET Core çalışma zamanı, paylaşılan çerçeve veya SDK olup olmadığını çözümlenen genel konumu belirtir. Ayarlanmazsa, varsayılan olarak, `true`. Kümesine `false` değil genel konumundan çözmek ve .NET Core yüklemeleri yalıtıncaya (değerleri `0` veya `false` kabul edilir). Çok düzeyli arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

Devre dışı bırakır podverze Top iletme, eğer ayarlanmış `0`. Daha fazla bilgi için [İleri sarmanın](../whats-new/dotnet-core-2-1.md#roll-forward).

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

Birincil paket önbelleğini. Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows üzerinde.

`DOTNET_SERVICING`

Çalışma zamanı yüklerken paylaşılan bir ana bilgisayar tarafından kullanılacak bakım dizin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir. Kümesine `true` ayrılma telemetri özelliği (değerleri `true`, `1`, veya `yes` kabul). Aksi takdirde, kümesine `false` telemetri özelliklerini kabul etme (değerleri `false`, `0`, veya `no` kabul). Varsayılan ayarlanmazsa `false` ve telemetri özellik etkin durumda.

`DOTNET_MULTILEVEL_LOOKUP`

.NET Core çalışma zamanı, paylaşılan çerçeve veya SDK olup olmadığını çözümlenen genel konumu belirtir. Ayarlanmazsa, varsayılan olarak, `true`. Kümesine `false` değil genel konumundan çözmek ve .NET Core yüklemeleri yalıtıncaya (değerleri `0` veya `false` kabul edilir). Çok düzeyli arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

Birincil paket önbelleğini. Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows üzerinde.

`DOTNET_SERVICING`

Çalışma zamanı yüklerken paylaşılan bir ana bilgisayar tarafından kullanılacak bakım dizin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir. Kümesine `true` ayrılma telemetri özelliği (değerleri `true`, `1`, veya `yes` kabul). Aksi takdirde, kümesine `false` telemetri özelliklerini kabul etme (değerleri `false`, `0`, veya `no` kabul). Varsayılan ayarlanmazsa `false` ve telemetri özellik etkin durumda.

---
