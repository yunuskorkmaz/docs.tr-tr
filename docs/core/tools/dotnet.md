---
title: DotNet komutu
description: DotNet komutu (.NET Core CLI araçları için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 06/04/2018
ms.openlocfilehash: e1571bea1594b492427bdf5b3a7959733459c54e
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331014"
---
# <a name="dotnet-command"></a>DotNet komutu

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Ad

`dotnet`-.NET kaynak kodu ve ikili dosyaları yönetmeye yönelik bir araç.

## <a name="synopsis"></a>Özeti

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```

---

## <a name="description"></a>Açıklama

`dotnet`, .NET kaynak kodu ve ikili dosyalarını yönetmeye yönelik bir araçtır. [`dotnet build`](dotnet-build.md) [Ve`dotnet run`](dotnet-run.md)gibi belirli görevleri gerçekleştiren komutları açığa çıkarır. Her komut kendi bağımsız değişkenlerini tanımlar. Kısa `--help` yardım belgelerine erişmek için her komuttan sonra yazın.

`dotnet`, gibi bir uygulama DLL `dotnet myapp.dll`belirterek uygulamaları çalıştırmak için kullanılabilir. Dağıtım seçenekleri hakkında bilgi edinmek için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md) .

## <a name="options"></a>Seçenekler

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`--additional-deps <PATH>`

Ek *. Deps. JSON* dosyasının yolu.

`--additionalprobingpath <PATH>`

Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.

`-d|--diagnostics`

Tanılama çıkışını izin vermez.

`--fx-version <VERSION>`

Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.

`-h|--help`

Gibi belirli bir komutun `dotnet build --help`belgelerini yazdırır. `dotnet --help`kullanılabilir komutların bir listesini yazdırır.

`--info`

.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.

`--list-runtimes`

Yüklü .NET Core çalışma zamanlarını görüntüler.

`--list-sdks`

Yüklü .NET Core SDK 'larını görüntüler.

`--roll-forward-on-no-candidate-fx <N>`

Gerekli paylaşılan çerçeve kullanılabilir olmadığında davranışını tanımlar. `N` aşağıdakilerden biri olabilir:
* `0`-Hatta ikincil sürüm iletmeyi devre dışı bırakın.
* `1`-Önemli sürümde değil, küçük sürümde ilet. Bu varsayılan davranıştır.
* `2`-Küçük ve büyük sürümlerde ilet.

 Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]` Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.

`--version`

Kullanımda olan .NET Core SDK sürümünü yazdırır.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`--additional-deps <PATH>`

Ek *. Deps. JSON* dosyasının yolu.

`--additionalprobingpath <PATH>`

Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.

`-d|--diagnostics`

Tanılama çıkışını izin vermez.

`--fx-version <VERSION>`

Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.

`-h|--help`

Gibi belirli bir komutun `dotnet build --help`belgelerini yazdırır. `dotnet --help`kullanılabilir komutların bir listesini yazdırır.

`--info`

.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.

`--roll-forward-on-no-candidate-fx`

 , Olarak `0`ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır. Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]` Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.

`--version`

Kullanımda olan .NET Core SDK sürümünü yazdırır.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.

`-d|--diagnostics`

Tanılama çıkışını izin vermez.

`--fx-version <VERSION>`

Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.

`-h|--help`

Gibi belirli bir komutun `dotnet build --help`belgelerini yazdırır. `dotnet --help`kullanılabilir komutların bir listesini yazdırır.

`--info`

.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.

`-v|--verbosity <LEVEL>`

Komutun ayrıntı düzeyini ayarlar. İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]` Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.

`--version`

Kullanımda olan .NET Core SDK sürümünü yazdırır.

---

## <a name="dotnet-commands"></a>dotnet komutları

### <a name="general"></a>Genel

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

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

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

| Komut                             | İşlev                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | .NET Core uygulaması oluşturur.                                     |
| [dotnet clean](dotnet-clean.md)     | Derleme çıktılarını temizle.                                              |
| [dotnet help](dotnet-help.md)       | Komutu için çevrimiçi daha ayrıntılı belgeler gösterir.           |
| [dotnet migrate](dotnet-migrate.md) | Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.  |
| [dotnet msbuild](dotnet-msbuild.md) | MSBuild komut satırına erişim sağlar.                        |
| [dotnet new](dotnet-new.md)         | Belirli bir C# şablon F# için bir veya projesini başlatır.                |
| [dotnet pack](dotnet-pack.md)       | Kodunuzun bir NuGet paketini oluşturur.                               |
| [dotnet publish](dotnet-publish.md) | .NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md) | Belirli bir uygulama için bağımlılıkları geri yükler.                  |
| [dotnet run](dotnet-run.md)         | Uygulamayı kaynaktan çalıştırır.                                   |
| [dotnet sln](dotnet-sln.md)         | Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.       |
| [dotnet store](dotnet-store.md)     | Derlemeleri çalışma zamanı paket deposunda depolar.                     |
| [dotnet test](dotnet-test.md)       | Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

| Komut                             | İşlev                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | .NET Core uygulaması oluşturur.                                     |
| [dotnet clean](dotnet-clean.md)     | Derleme çıktılarını temizle.                                              |
| [dotnet migrate](dotnet-migrate.md) | Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.  |
| [dotnet msbuild](dotnet-msbuild.md) | MSBuild komut satırına erişim sağlar.                        |
| [dotnet new](dotnet-new.md)         | Belirli bir C# şablon F# için bir veya projesini başlatır.                |
| [dotnet pack](dotnet-pack.md)       | Kodunuzun bir NuGet paketini oluşturur.                               |
| [dotnet publish](dotnet-publish.md) | .NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar. |
| [dotnet restore](dotnet-restore.md) | Belirli bir uygulama için bağımlılıkları geri yükler.                  |
| [dotnet run](dotnet-run.md)         | Uygulamayı kaynaktan çalıştırır.                                   |
| [dotnet sln](dotnet-sln.md)         | Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.       |
| [dotnet test](dotnet-test.md)       | Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.                                     |

---

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

### <a name="global-tools-commands"></a>Küresel araçlar komutları

[.NET Core küresel araçlar](global-tools.md) .NET Core SDK 2.1.300 ile başlayarak kullanılabilir:

Komut | İşlev
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Makinenize küresel bir araç kurar.
[dotnet tool list](dotnet-tool-list.md) | Makinenizde varsayılan dizinde veya belirtilen yolda yüklü olan tüm genel araçları listeler.
[dotnet tool install](dotnet-tool-uninstall.md) | Bir genel aracı makinenizden kaldırır.
[dotnet tool update](dotnet-tool-update.md) | Makinenizde küresel bir aracı güncelleştirir.

### <a name="additional-tools"></a>Ek araçlar

.NET Core SDK 2.1.300 ' den itibaren, yalnızca kullanılarak `DotnetCliToolReference` proje bazında kullanılabilen birçok araç, .NET Core SDK bir parçası olarak kullanılabilir. Bu araçlar aşağıdaki tabloda listelenmiştir:

| Aracı                                              | İşlev                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| geliştirme-CERT                                         | Geliştirme sertifikaları oluşturur ve yönetir.                |
| [aşv](/ef/core/miscellaneous/cli/dotnet)           | Komut satırı araçlarını Entity Framework Core.                    |
| SQL-Cache                                         | Önbellek komut satırı araçlarını SQL Server.                         |
| [Kullanıcı gizli dizileri](/aspnet/core/security/app-secrets) | Geliştirme Kullanıcı gizli dizilerini yönetir.                            |
| [Servisi](/aspnet/core/tutorials/dotnet-watch)      | Dosyalar değiştiğinde bir komutu çalıştıran bir dosya İzleyicisi başlatır. |

Her araç hakkında daha fazla bilgi için, `dotnet <tool-name> --help`yazın.

## <a name="examples"></a>Örnekler

Yeni bir .NET Core konsol uygulaması oluşturur:

`dotnet new console`

Belirli bir uygulama için bağımlılıkları geri yükle:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Belirli bir dizinde bir proje ve onun bağımlılıklarını oluşturun:

`dotnet build`

Bir uygulama DLL 'SI çalıştırın, `myapp.dll`örneğin:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Ortam değişkenleri

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`DOTNET_PACKAGES`

Genel paketler klasörü. Ayarlanmamışsa, varsayılan `~/.nuget/packages` olarak UNIX veya `%userprofile%\.nuget\packages` Windows üzerinde olur.

`DOTNET_SERVICING`

Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir. Telemetri özelliğini `true` devre dışı bırakmak için olarak ayarlayın (değerler `true`, `1`veya `yes` kabul edildi). Aksi takdirde, telemetri `false` özelliklerini (değerler `false`, `0`veya `no` kabul edildi) kabul etmek için olarak ayarlayın. Ayarlanmamışsa, varsayılan `false` olarak ve telemetri özelliği etkindir.

`DOTNET_MULTILEVEL_LOOKUP`

.NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir. Ayarlanmamışsa, varsayılan olarak `true`olur. Genel konumdan `false` çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olacak şekilde ayarlayın (değerler `0` veya `false` kabul edilir). Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

, Olarak `0`ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır. Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`DOTNET_PACKAGES`

Birincil paket önbelleği. Ayarlanmamışsa, varsayılan `$HOME/.nuget/packages` olarak UNIX veya `%userprofile%\.nuget\packages` Windows üzerinde olur.

`DOTNET_SERVICING`

Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir. Telemetri özelliğini `true` devre dışı bırakmak için olarak ayarlayın (değerler `true`, `1`veya `yes` kabul edildi). Aksi takdirde, telemetri `false` özelliklerini (değerler `false`, `0`veya `no` kabul edildi) kabul etmek için olarak ayarlayın. Ayarlanmamışsa, varsayılan `false` olarak ve telemetri özelliği etkindir.

`DOTNET_MULTILEVEL_LOOKUP`

.NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir. Ayarlanmamışsa, varsayılan olarak `true`olur. Genel konumdan `false` çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olacak şekilde ayarlayın (değerler `0` veya `false` kabul edilir). Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

`DOTNET_PACKAGES`

Birincil paket önbelleği. Ayarlanmamışsa, varsayılan `$HOME/.nuget/packages` olarak UNIX veya `%userprofile%\.nuget\packages` Windows üzerinde olur.

`DOTNET_SERVICING`

Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.

`DOTNET_CLI_TELEMETRY_OPTOUT`

.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir. Telemetri özelliğini `true` devre dışı bırakmak için olarak ayarlayın (değerler `true`, `1`veya `yes` kabul edildi). Aksi takdirde, telemetri `false` özelliklerini (değerler `false`, `0`veya `no` kabul edildi) kabul etmek için olarak ayarlayın. Ayarlanmamışsa, varsayılan `false` olarak ve telemetri özelliği etkindir.

---
