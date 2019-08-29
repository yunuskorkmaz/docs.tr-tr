---
title: .NET Core komut satırı arabirimi (CLı) araçları
description: .NET Core komut satırı arabirimi (CLı) araçları ve özelliklerine genel bakış.
ms.date: 08/14/2017
ms.custom: seodec18
ms.openlocfilehash: 20a083f3e7496521243bebd6585a48c8a562c548
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105039"
---
# <a name="net-core-command-line-interface-cli-tools"></a>.NET Core komut satırı arabirimi (CLı) araçları

.NET Core komut satırı arabirimi (CLı), .NET uygulamaları geliştirmeye yönelik yeni bir platformlar arası araç zinciridir. CLı, tümleşik geliştirme ortamları (IDN 'ler), düzenleyiciler ve derleme yöneticileri gibi daha üst düzey araçların geri kalanı olan bir temelidir.

## <a name="installation"></a>Yükleme

Yerel yükleyicileri kullanın veya yükleme kabuğu betikleri kullanın:

- Yerel yükleyiciler öncelikle geliştiricinin makinelerinde kullanılır ve desteklenen her platformun yerel yükleme mekanizmasını kullanır. Örneğin, Windows üzerinde Ubuntu veya MSI paketlerinde DEB paketleri. Bu yükleyiciler, geliştirici tarafından anında kullanılmak üzere ortamı yükler ve yapılandırır, ancak makinede yönetici ayrıcalıkları gerektirir. Yükleme yönergelerini [.NET Core yükleme kılavuzunda](https://aka.ms/dotnetcoregs)görüntüleyebilirsiniz.
- Kabuk betikleri öncelikle yapı sunucularını ayarlamak için veya araçları yönetici ayrıcalıkları olmadan yüklemek istediğinizde kullanılır. Betikleri yükleme, el ile yüklenmesi gereken makineye önkoşulları yüklemez. Daha fazla bilgi için bkz. [komut dosyası başvurusunu install konusu](dotnet-install-script.md). Sürekli tümleştirme (CI) derleme sunucunuzda CLı 'yı ayarlama hakkında daha fazla bilgi için bkz. [.NET Core SDK ve araçları sürekli tümleştirme (CI) Içinde kullanma](using-ci-with-cli.md).

Varsayılan olarak, CLı yan yana (SxS) bir şekilde yüklenir. bu nedenle, CLı araçlarının birden çok sürümü tek bir makinede birlikte bulunabilir. Birden çok sürümün yüklü olduğu bir makinede hangi sürümün kullanıldığını belirleme, [sürücü](#driver) bölümünde daha ayrıntılı olarak açıklanmıştır.

## <a name="cli-commands"></a>CLı komutları

Aşağıdaki komutlar varsayılan olarak yüklenir:

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

CLı komut yapısı, [sürücüden ("DotNet")](#driver), [komuttan](#command)ve muhtemelen komut [bağımsız değişkenlerinden](#arguments) ve [seçeneklerden](#options)oluşur. Bu kalıbı, yeni bir konsol uygulaması oluşturma ve bunu komut satırından çalıştırma gibi, *my_app*adlı bir dizinden yürütüldüğünde gösterildiği gıbı birçok CLI işlemi içinde görürsünüz:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2. x](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1. x](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a>Sürücü

Sürücü [DotNet](dotnet.md) olarak adlandırılır ve [çerçeveye bağlı bir uygulama](../deploying/index.md) çalıştırarak ya da bir komut yürüten iki sorumluluklara sahiptir. 

Çerçeveye bağımlı bir uygulama çalıştırmak için, uygulamayı sürücüden sonra belirtin, örneğin, `dotnet /path/to/my_app.dll`. Komutu, uygulamanın DLL 'sinin bulunduğu klasörden yürütürken yalnızca yürütün `dotnet my_app.dll`. .NET Core çalışma zamanının belirli bir sürümünü kullanmak istiyorsanız, `--fx-version <VERSION>` seçeneğini kullanın ( [DotNet komut](dotnet.md) başvurusuna bakın).

Sürücüye bir komut sağlarsanız, `dotnet.exe` CLI komutu yürütme işlemini başlatır. Örneğin:

```bash
> dotnet build
```

İlk olarak, sürücü kullanılacak SDK sürümünü belirler. [' Global. json '](global-json.md)yoksa SDK 'nın kullanılabilir en son sürümü kullanılır. Bu, makinede en son nelerin olduğuna bağlı olarak önizleme veya kararlı bir sürüm olabilir.  SDK sürümü belirlendikten sonra, komutunu yürütür.

### <a name="command"></a>Komut

Komut bir eylem gerçekleştirir. Örneğin, `dotnet build` derleme kodu. `dotnet publish`kodu yayımlar. Komutlar, bir `dotnet {command}` kural kullanılarak konsol uygulaması olarak uygulanır.

### <a name="arguments"></a>Arguments

Komut satırında geçirdiğiniz bağımsız değişkenler çağrılan komutun bağımsız değişkenlerdir. Örneğin `dotnet publish my_app.csproj` `publish` , çalıştırdığınızda bağımsız değişkeni yayımlanacak projeyi belirtir ve komutuna geçirilir. `my_app.csproj`

### <a name="options"></a>Seçenekler

Komut satırında geçirdiğiniz seçenekler çağrılan komuta yönelik seçeneklerdir. Örneğin `dotnet publish --output /build_output` `publish` , çalıştırdığınızda seçeneği ve değeri komutuna geçirilir. `--output`

## <a name="migration-from-projectjson"></a>Project. JSON 'dan geçiş

*Project. JSON*tabanlı projeler oluşturmak için Preview 2 araçları 'nı kullandıysanız, sürüm araçları ile kullanmak üzere projenizi MSBuild/ *. csproj* 'a geçirme hakkında bilgi edinmek için [DotNet geçiş](dotnet-migrate.md) konusuna başvurun. Preview 2 araçları 'nın yayınlanmasından önce oluşturulan .NET Core projeleri için, [DNX 'ten .NET Core CLI (Project. JSON) ' den geçiş](../migration/from-dnx.md) yapma bölümündeki kılavuzdan sonra projeyi el ile güncelleştirin ve ardından projelerinizi kullanın `dotnet migrate` veya doğrudan yükseltin.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet/CLı GitHub deposu](https://github.com/dotnet/cli/)
- [.NET Core yükleme kılavuzu](https://aka.ms/dotnetcoregs)
