---
title: .NET Core CLI
titleSuffix: ''
description: .NET Core CLI ve özelliklerine genel bir bakış.
ms.date: 08/14/2017
ms.openlocfilehash: b0a8e0dd8cf77bb6f7567c27e9972f62515ec0f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920480"
---
# <a name="net-core-cli-overview"></a>.NET Core CLI genel bakış

.NET Core komut satırı arabirimi (CLı), .NET Core uygulamaları geliştirmeye, oluşturmaya, çalıştırmaya ve yayımlamaya yönelik platformlar arası bir araç zinciridir.

.NET Core CLI, [.NET Core SDK](../sdk.md)dahil edilir. .NET Core SDK nasıl yükleneceğini öğrenmek için bkz. [.NET Core SDK yüklemesi](../install/sdk.md).

## <a name="cli-commands"></a>CLı komutları

Aşağıdaki komutlar varsayılan olarak yüklenir:

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2. x](#tab/netcore2x)

**Temel komutlar**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [derlemeyi](dotnet-build.md)
- [yayınlamanız](dotnet-publish.md)
- [çalışmaz](dotnet-run.md)
- [sınamanız](dotnet-test.md)
- [VSTest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [geçiremezsiniz](dotnet-migrate.md)
- [temizlenemedi](dotnet-clean.md)
- [sln](dotnet-sln.md)
- [Yardım](dotnet-help.md)
- [saklayabilir](dotnet-store.md)

**Proje değiştirme komutları**

- [Paket ekle](dotnet-add-package.md)
- [Başvuru Ekle](dotnet-add-reference.md)
- [paketi kaldır](dotnet-remove-package.md)
- [başvuruyu kaldır](dotnet-remove-reference.md)
- [liste başvurusu](dotnet-list-reference.md)

**Gelişmiş komutlar**

- [NuGet silme](dotnet-nuget-delete.md)
- [NuGet Yereller](dotnet-nuget-locals.md)
- [NuGet gönderim](dotnet-nuget-push.md)
- [MSBUILD](dotnet-msbuild.md)
- [DotNet install betiği](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

**Temel komutlar**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [derlemeyi](dotnet-build.md)
- [yayınlamanız](dotnet-publish.md)
- [çalışmaz](dotnet-run.md)
- [sınamanız](dotnet-test.md)
- [VSTest](dotnet-vstest.md)
- [pack](dotnet-pack.md)
- [geçiremezsiniz](dotnet-migrate.md)
- [temizlenemedi](dotnet-clean.md)
- [sln](dotnet-sln.md)

**Proje değiştirme komutları**

- [Paket ekle](dotnet-add-package.md)
- [Başvuru Ekle](dotnet-add-reference.md)
- [paketi kaldır](dotnet-remove-package.md)
- [başvuruyu kaldır](dotnet-remove-reference.md)
- [liste başvurusu](dotnet-list-reference.md)

**Gelişmiş komutlar**

- [NuGet silme](dotnet-nuget-delete.md)
- [NuGet Yereller](dotnet-nuget-locals.md)
- [NuGet gönderim](dotnet-nuget-push.md)
- [MSBUILD](dotnet-msbuild.md)
- [DotNet install betiği](dotnet-install-script.md)

---

CLı, projeleriniz için ek araçlar belirtmenize olanak tanıyan bir genişletilebilirlik modeli benimsemektedir. Daha fazla bilgi için [.NET Core CLI genişletilebilirlik modeli](extensibility.md) konusuna bakın.

## <a name="command-structure"></a>Komut yapısı

CLı komut yapısı, [sürücüden ("DotNet")](#driver), [komuttan](#command)ve muhtemelen komut [bağımsız değişkenlerinden](#arguments) ve [seçeneklerden](#options)oluşur. Bu kalıbı, yeni bir konsol uygulaması oluşturma ve aşağıdaki komutlar *my_app*adlı bir dizinden yürütüldüğünde gösterildiği gibi komut satırından çalıştırma gıbı birçok CLI işlemi içinde görürsünüz:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2. x](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

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

### <a name="arguments"></a>Arguments

Komut satırında geçirdiğiniz bağımsız değişkenler çağrılan komutun bağımsız değişkenlerdir. Örneğin, `dotnet publish my_app.csproj`yürüttüğünüzde, `my_app.csproj` bağımsız değişkeni yayımlanacak projeyi belirtir ve `publish` komutuna geçirilir.

### <a name="options"></a>Seçenekler

Komut satırında geçirdiğiniz seçenekler çağrılan komuta yönelik seçeneklerdir. Örneğin `dotnet publish --output /build_output`yürüttüğünüzde, `--output` seçeneği ve değeri `publish` komutuna geçirilir.

## <a name="migration-from-projectjson"></a>Project. JSON 'dan geçiş

*Project. JSON*tabanlı projeler oluşturmak için Preview 2 araçları 'nı kullandıysanız, sürüm araçları ile kullanmak üzere projenizi MSBuild/ *. csproj* 'a geçirme hakkında bilgi edinmek için [DotNet geçiş](dotnet-migrate.md) konusuna başvurun. Preview 2 araçları 'nın yayınlanmasından önce oluşturulan .NET Core projeleri için, [DNX 'ten .NET Core CLI (Project. JSON) ' den geçiş yapma bölümündeki kılavuzdan](../migration/from-dnx.md) sonra projeyi el ile güncelleştirin ve `dotnet migrate` kullanın ya da projelerinizi doğrudan yükseltin.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet/SDK GitHub deposu](https://github.com/dotnet/sdk/)
- [.NET Core yükleme kılavuzu](https://aka.ms/dotnetcoregs)
