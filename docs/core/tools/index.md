---
title: .NET Core CLI
titleSuffix: ''
description: .NET Core CLI ve özelliklerine genel bir bakış.
ms.date: 02/13/2020
ms.openlocfilehash: 1078d68ddc088274fa14b0094a81765f7af69dad
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543320"
---
# <a name="net-core-cli-overview"></a>.NET Core CLI genel bakış

**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri

.NET Core komut satırı arabirimi (CLı), .NET Core uygulamaları geliştirmeye, oluşturmaya, çalıştırmaya ve yayımlamaya yönelik platformlar arası bir araç zinciridir.

.NET Core CLI, [.NET Core SDK](../sdk.md)dahil edilir. .NET Core SDK nasıl yükleneceğini öğrenmek için bkz. [.NET Core SDK yüklemesi](../install/sdk.md).

## <a name="cli-commands"></a>CLı komutları

Aşağıdaki komutlar varsayılan olarak yüklenir:

### <a name="basic-commands"></a>Temel komutlar

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [derlemeyi](dotnet-build.md)
- [publish](dotnet-publish.md)
- [çalışmaz](dotnet-run.md)
- [sınamanız](dotnet-test.md)
- [VSTest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [geçirme](dotnet-migrate.md)
- [temizlenemedi](dotnet-clean.md)
- [sln](dotnet-sln.md)
- [Yardım](dotnet-help.md)
- [saklayabilir](dotnet-store.md)

### <a name="project-modification-commands"></a>Proje değişikliği komutları

- [Paket ekle](dotnet-add-package.md)
- [Başvuru Ekle](dotnet-add-reference.md)
- [paketi kaldır](dotnet-remove-package.md)
- [başvuruyu kaldır](dotnet-remove-reference.md)
- [liste başvurusu](dotnet-list-reference.md)

### <a name="advanced-commands"></a>Gelişmiş komutlar

- [NuGet silme](dotnet-nuget-delete.md)
- [NuGet Yereller](dotnet-nuget-locals.md)
- [NuGet gönderim](dotnet-nuget-push.md)
- [MSBUILD](dotnet-msbuild.md)
- [DotNet install betiği](dotnet-install-script.md)

### <a name="tool-management-commands"></a>Araç yönetimi komutları

- [Araç yüklemesi](dotnet-tool-install.md)
- [araç listesi](dotnet-tool-list.md)
- [Araç güncelleştirmesi](dotnet-tool-update.md)
- [araç geri yükleme](global-tools.md#install-a-local-tool) **.NET Core SDK 3,0 ile başlayarak kullanılabilir**
- **.NET Core SDK 3,0 ' den başlayarak** [araç çalıştırma](global-tools.md#invoke-a-local-tool) kullanılabilir
- [araç kaldırma](dotnet-tool-uninstall.md)

Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır. Araçları kendiniz yazabilir veya üçüncü taraflarca yazılmış Araçları yükleyebilirsiniz. Araçlar genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir. Daha fazla bilgi için bkz. [.NET Core araçlarına genel bakış](global-tools.md).

## <a name="command-structure"></a>Komut yapısı

CLı komut yapısı, [sürücüden ("DotNet")](#driver), [komuttan](#command)ve muhtemelen komut [bağımsız değişkenlerinden](#arguments) ve [seçeneklerden](#options)oluşur. Bu kalıbı, yeni bir konsol uygulaması oluşturma ve aşağıdaki komutlar *my_app*adlı bir dizinden yürütüldüğünde gösterildiği gibi komut satırından çalıştırma gıbı birçok CLI işlemi içinde görürsünüz:

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>Sürücü

Sürücü [DotNet](dotnet.md) olarak adlandırılır ve [çerçeveye bağlı bir uygulama](../deploying/index.md) çalıştırarak ya da bir komut yürüten iki sorumluluklara sahiptir. 

Çerçeveye bağımlı bir uygulama çalıştırmak için, uygulamayı sürücüden sonra belirtin, örneğin, `dotnet /path/to/my_app.dll`. Uygulamanın DLL 'sinin bulunduğu klasörden komutu yürütürken `dotnet my_app.dll`yürütmek yeterlidir. .NET Core çalışma zamanının belirli bir sürümünü kullanmak istiyorsanız, `--fx-version <VERSION>` seçeneğini kullanın ( [DotNet komut](dotnet.md) başvurusuna bakın).

Sürücüye bir komut sağlarsanız, `dotnet.exe` CLı komutu yürütme işlemini başlatır. Örneğin:

```dotnetcli
dotnet build
```

İlk olarak, sürücü kullanılacak SDK sürümünü belirler. [' Global. json '](global-json.md)yoksa SDK 'nın kullanılabilir en son sürümü kullanılır. Bu, makinede en son nelerin olduğuna bağlı olarak önizleme veya kararlı bir sürüm olabilir.  SDK sürümü belirlendikten sonra, komutunu yürütür.

### <a name="command"></a>Komut

Komut bir eylem gerçekleştirir. Örneğin, `dotnet build` derleme kodu. `dotnet publish` kodu yayınlar. Komutlar bir `dotnet {command}` kuralı kullanılarak konsol uygulaması olarak uygulanır.

### <a name="arguments"></a>Bağımsız Değişkenler

Komut satırında geçirdiğiniz bağımsız değişkenler çağrılan komutun bağımsız değişkenlerdir. Örneğin, `dotnet publish my_app.csproj`yürüttüğünüzde, `my_app.csproj` bağımsız değişkeni yayımlanacak projeyi belirtir ve `publish` komutuna geçirilir.

### <a name="options"></a>Seçenekler

Komut satırında geçirdiğiniz seçenekler çağrılan komuta yönelik seçeneklerdir. Örneğin `dotnet publish --output /build_output`yürüttüğünüzde, `--output` seçeneği ve değeri `publish` komutuna geçirilir.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet/SDK GitHub deposu](https://github.com/dotnet/sdk/)
- [.NET Core yükleme kılavuzu](../install/sdk.md)
