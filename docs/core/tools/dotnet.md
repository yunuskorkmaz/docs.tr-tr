---
title: DotNet command - .NET Core CLI
description: "Dotnet komutu (.NET Core CLI araçlarını genel sürücüsü) ve kullanımı hakkında bilgi edinin."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2eea7d13994bfddc89d8f3513308a6620c53c88c
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2018
---
# <a name="dotnet-command"></a>DotNet komutu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet`-Komut satırı komutlarını çalıştırmak için genel sürücüsü.

## <a name="synopsis"></a>Özet

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a>Açıklama

`dotnet`Komut satırı arabirimi (CLI) zincirinin için genel bir sürücüsüdür. Kendi kendine çağrılan kısa kullanım yönergeleri sağlar.

Her belirli bir özellik, bir komut olarak uygulanır. Bu özelliği kullanmak için komut sonra belirtilen `dotnet`, gibi [ `dotnet build` ](dotnet-build.md). Tüm komut aşağıdaki bağımsız değişkenleri, kendi bağımsız değişkenler.

Yalnızca bir kez `dotnet` kendi başına bir komut çalıştırmaktır olarak kullanılan [framework bağımlı uygulamaları](../deploying/index.md). Bir uygulama DLL belirtin sonra `dotnet` uygulamasını çalıştırmak için fiili (örneğin, `dotnet myapp.dll`).

## <a name="options"></a>Seçenekler

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

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

`-v|--verbose`

Ayrıntılı çıktı sağlar.

`--version`

Kullanımdaki .NET Core SDK sürümü yazdırır.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

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

`-v|--verbose`

Ayrıntılı çıktı sağlar.

`--version`

Kullanımdaki .NET Core SDK sürümü yazdırır.

---

## <a name="dotnet-commands"></a>DotNet komutları

### <a name="general"></a>Genel

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

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

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

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
[dotnet add reference](dotnet-add-reference.md) | Proje başvurusu ekleyin.
[dotnet list reference](dotnet-list-reference.md) | Proje başvuruları listeleyin.
[dotnet remove reference](dotnet-remove-reference.md) | Proje başvurusu kaldırın.

### <a name="nuget-packages"></a>NuGet paketleri

Komut | İşlev
--- | ---
[dotnet add package](dotnet-add-package.md) | NuGet paketini ekleyin.
[dotnet remove package](dotnet-remove-package.md) | Bir NuGet paketi kaldırın.

### <a name="nuget-commands"></a>NuGet komutları

Komut | İşlev
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Sunucudan paket unlists veya siler.
[dotnet nuget locals](dotnet-nuget-locals.md) | Temizler veya http isteği önbelleği, geçici önbelleği veya makine genelinde genel paketler klasörü gibi yerel NuGet kaynakları listeler.
[dotnet nuget push](dotnet-nuget-push.md) | Sunucuya bir paket gönderir ve onu yayımlar.

## <a name="examples"></a>Örnekler

Derlenmiş ve çalıştıran bir örnek .NET Core konsol uygulaması başlatılamadı:

`dotnet new console`

Belirli bir uygulamayla ilgili bağımlılıkları geri yükleyin:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Proje ve bağımlılıklarını belirli bir dizinde oluşturun:

`dotnet build`

Adlı framework bağımlı uygulamayı çalıştırma `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Ortam değişkenleri

`DOTNET_PACKAGES`

Birincil paketi önbelleği. Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows.

`DOTNET_SERVICING`

Çalışma zamanı yüklerken paylaşılan ana bilgisayar tarafından kullanılacak hizmet dizin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir. Kümesine `true` telemetri özelliğini çevirin için (değerleri `true`, `1`, veya `yes` kabul) Aksi takdirde ayarlanmış `false` katılımı telemetri özellikleri için (değerleri `false`, `0`, veya `no` kabul). Ayarlanmadı, Varsayılanları olup olmadığını `false`, ve telemetri özellik etkindir.
