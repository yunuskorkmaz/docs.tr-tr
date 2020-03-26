---
title: .NET Core CLI
titleSuffix: ''
description: .NET Core CLI ve özelliklerine genel bakış.
ms.date: 02/13/2020
ms.openlocfilehash: ac5988bacbef41326f2501a2cff6c3f5aa0be798
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110847"
---
# <a name="net-core-cli-overview"></a>.NET Core CLI’ya genel bakış

**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler

.NET Core komut satırı arabirimi (CLI), .NET Core uygulamalarını geliştirmek, oluşturmak, çalıştırmak ve yayınlamak için bir çapraz platform araç zinciridir.

.NET Çekirdek CLI [.NET Çekirdek SDK](../sdk.md)ile birlikte verilir. .NET Core SDK'yı nasıl yükleyin, [bkz.](../install/sdk.md)

## <a name="cli-commands"></a>CLI komutları

Aşağıdaki komutlar varsayılan olarak yüklenir:

### <a name="basic-commands"></a>Temel komutlar

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a>Proje değişikliği komutları

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a>Gelişmiş komutlar

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a>Araç yönetimi komutları

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- [`tool restore`](global-tools.md#install-a-local-tool).NET Çekirdek SDK 3.0'dan beri mevcuttur.
- [`tool run`](global-tools.md#invoke-a-local-tool).NET Çekirdek SDK 3.0'dan beri mevcuttur.
- [`tool uninstall`](dotnet-tool-uninstall.md)

Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır. Araçları kendiniz yazabilir veya üçüncü şahıslar tarafından yazılmış araçları yükleyebilirsiniz. Araçlar, genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir. Daha fazla bilgi için [.NET Core araçlarına genel bakış](global-tools.md)ala.

## <a name="command-structure"></a>Komut yapısı

CLI komut yapısı [sürücü ("dotnet")](#driver)oluşur, [komutu](#command)ve muhtemelen komut [bağımsız değişkenleri](#arguments) ve [seçenekleri](#options). Bu deseni, yeni bir konsol uygulaması oluşturma ve komut satırından çalıştırmak gibi çoğu CLI işlemlerinde *my_app*adlı bir dizinden yürütüldüğünde aşağıdaki komutların gösterdiği gibi görürsünüz:

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>Sürücü

Sürücü [dotnet](dotnet.md) olarak adlandırılır ve iki sorumlulukları vardır, ya [bir çerçeve bağımlı uygulama](../deploying/index.md) çalıştırarak veya bir komut yürütme.

Çerçeveye bağımlı bir uygulamayı çalıştırmak için, uygulamayı sürücüden `dotnet /path/to/my_app.dll`sonra belirtin, örneğin. Uygulamayın DLL'sinin bulunduğu klasörden komutu çalıştırırken, `dotnet my_app.dll`yürütmenizi yeterli .NET Core Runtime'ın belirli bir sürümünü kullanmak `--fx-version <VERSION>` istiyorsanız, seçeneği kullanın [(dotnet komut](dotnet.md) başvurusuna bakın).

Sürücüye bir komut verdiyseniz, `dotnet.exe` CLI komut yürütme işlemini başlatır. Örnek:

```dotnetcli
dotnet build
```

İlk olarak, sürücü SDK'nın kullanacağı sürümü belirler. [Global.json](global-json.md) dosyası yoksa, Kullanılabilir SDK'nın en son sürümü kullanılır. Bu, makinede en son ne olduğuna bağlı olarak bir önizleme veya kararlı sürüm olabilir.  SDK sürümü belirlendikten sonra komutu yürütür.

### <a name="command"></a>Komut

Komut bir eylem gerçekleştirir. Örneğin, `dotnet build` kod oluşturur. `dotnet publish`kod yayımlar. Komutlar bir `dotnet {command}` kuralkuralı kullanılarak konsol uygulaması olarak uygulanır.

### <a name="arguments"></a>Bağımsız Değişkenler

Komut satırında geçirdiğiniz bağımsız değişkenler çağrılan komutun bağımsız değişkenleridir. Örneğin, yürüttuğunuzda, `dotnet publish my_app.csproj` `my_app.csproj` bağımsız değişken yayımlanacak projeyi `publish` gösterir ve komuta geçirilir.

### <a name="options"></a>Seçenekler

Komut satırında geçirdiğiniz seçenekler, çağrılan komutun seçenekleridir. Örneğin, çalıştırdığınızda, `dotnet publish --output /build_output` `--output` seçenek ve değeri komuta `publish` geçirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [dotnet/sdk GitHub deposu](https://github.com/dotnet/sdk/)
- [.NET Core kurulum kılavuzu](../install/sdk.md)
