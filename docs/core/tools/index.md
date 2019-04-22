---
title: .NET core komut satırı arabirimi (CLI) araçları
description: .NET Core komut satırı arabirimi (CLI) araçları ve özellikleri genel bakış.
ms.date: 08/14/2017
ms.custom: seodec18
ms.openlocfilehash: e174867ce06e573fc85579183df0196d8276fb37
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826320"
---
# <a name="net-core-command-line-interface-cli-tools"></a>.NET core komut satırı arabirimi (CLI) araçlarını

.NET Core komut satırı arabirimi (CLI), .NET uygulamaları geliştirmek için yeni bir platformlar arası zincirinin ' dir. Tümleşik geliştirme ortamlarından (IDE'ler), düzenleyiciler ve derleme düzenleyicileri tuttuğunuzda gibi CLI hangi üst düzey araçları temel altyapıdır.

## <a name="installation"></a>Yükleme

Yerel yükleyicilerden kullanabilir veya yükleme Kabuk betikleri kullanın:

* Yerel yükleyicilerden öncelikle geliştiricinin makinelerde kullanılır ve desteklenen kullanımı her platformun yerel mekanizması, örneğin, Ubuntu veya MSI paketleri Windows üzerinde DEB paketleri yükleyin. Bu yükleyicilerden yükleyin ve geliştirici tarafından anında kullanmak için ortamı yapılandırmak ancak makinedeki yönetici ayrıcalıkları gerektirir. Yükleme yönergeleri görüntüleyebileceğiniz [.NET Core Yükleme Kılavuzu](https://aka.ms/dotnetcoregs).
* Kabuk betikleri, öncelikle yapı sunucuları veya yönetici ayrıcalıklarına gerek kalmadan araçları yüklemek istediğiniz zaman ayarlamak için kullanılır. Yükleme betikleri el ile yüklenmesi gereken makine Önkoşulları Yükleme yok. Daha fazla bilgi için [yükleme komut dosyası başvuru konusu](dotnet-install-script.md). Sürekli Tümleştirme (CI) yapılandırma sunucunuzda CLI'yı ayarlama hakkında daha fazla bilgi için bkz: [kullanarak .NET Core SDK'sı ve araçları, sürekli tümleştirme (CI)](using-ci-with-cli.md).

Varsayılan olarak, CLI yan yana (SxS) şekilde yüklediği CLI araçları birden çok sürümünü tek bir makinede bulunabilir. Birden çok sürümünün yüklü olduğu bir makinede kullanılan hangi sürümünü belirleme bölümünde daha ayrıntılı olarak açıklanmıştır [sürücü](#driver) bölümü.

## <a name="cli-commands"></a>CLI komutları

Aşağıdaki komutlar, varsayılan olarak yüklenir:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Temel komutlar**

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [Derleme](dotnet-build.md)
* [Yayımlama](dotnet-publish.md)
* [run](dotnet-run.md)
* [Test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pack](dotnet-pack.md)
* [Geçirme](dotnet-migrate.md)
* [Temizleme](dotnet-clean.md)
* [sln](dotnet-sln.md)
* [Yardım](dotnet-help.md)
* [Store](dotnet-store.md)

**Proje değişikliği komutları**

* [Paket Ekle](dotnet-add-package.md)
* [Başvuru ekleme](dotnet-add-reference.md)
* [Paketi Kaldır](dotnet-remove-package.md)
* [başvuru Kaldır](dotnet-remove-reference.md)
* [Liste başvurusu](dotnet-list-reference.md)

**Gelişmiş komutları**

* [nuget Sil](dotnet-nuget-delete.md)
* [nuget yerel öğeler](dotnet-nuget-locals.md)
* [nuget anında iletme](dotnet-nuget-push.md)
* [MSBuild](dotnet-msbuild.md)
* [DotNet yükleme betiği](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**Temel komutlar**

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [Derleme](dotnet-build.md)
* [Yayımlama](dotnet-publish.md)
* [run](dotnet-run.md)
* [Test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pack](dotnet-pack.md)
* [Geçirme](dotnet-migrate.md)
* [Temizleme](dotnet-clean.md)
* [sln](dotnet-sln.md)

**Proje değişikliği komutları**

* [Paket Ekle](dotnet-add-package.md)
* [Başvuru ekleme](dotnet-add-reference.md)
* [Paketi Kaldır](dotnet-remove-package.md)
* [başvuru Kaldır](dotnet-remove-reference.md)
* [Liste başvurusu](dotnet-list-reference.md)

**Gelişmiş komutları**

* [nuget Sil](dotnet-nuget-delete.md)
* [nuget yerel öğeler](dotnet-nuget-locals.md)
* [nuget anında iletme](dotnet-nuget-push.md)
* [MSBuild](dotnet-msbuild.md)
* [DotNet yükleme betiği](dotnet-install-script.md)

---

CLI'yı projeleriniz için ek araçlar belirtmenizi sağlar bir genişletilebilirlik modeli devralır. Daha fazla bilgi için [.NET Core CLI genişletilebilirlik modeli](extensibility.md) konu.

## <a name="command-structure"></a>Komut yapısı

CLI komut yapısını oluşur [("dotnet") sürücü](#driver), [komutu (veya "eylem")](#command-verb)ve büyük olasılıkla komut [bağımsız değişkenleri](#arguments) ve [seçenekleri](#options). Adlı bir dizinden çalıştırıldığında Göster yeni bir konsol uygulaması oluşturma ve aşağıdaki komutları komut satırından çalıştırma gibi çoğu CLI işlemi bu düzende gördüğünüz *my_app_3.sft*:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a>Sürücü

Sürücü adlı [dotnet](dotnet.md) ve iki sorumlulukları, ya da çalışan bir [framework bağımlı uygulama](../deploying/index.md) veya bir komut yürütülüyor. 

Framework bağımlı uygulamayı çalıştırın, sonra sürücüsü, örneğin, uygulamayı belirtmek için `dotnet /path/to/my_app.dll`. Uygulamanın DLL bulunduğu klasörün komutu yürütülürken, yalnızca yürütme `dotnet my_app.dll`. Belirli bir .NET Core çalışma zamanı sürümünü kullanmak istiyorsanız, kullanın `--fx-version <VERSION>` seçeneği (bkz [dotnet komut](dotnet.md) başvuru).

Sürücü komut sağladığında `dotnet.exe` CLI komut yürütme işlemi başlatır. Örneğin:

```bash
> dotnet build
```

İlk olarak, sürücü kullanmak için SDK'sı sürümünü belirler. Yoksa hiçbir ['global.json'](global-json.md), kullanılabilir SDK'sının en son sürümü kullanılır. Bu bir önizleme veya kararlı bir sürüm makinede en son nedir bağlı olarak, olabilir.  SDK sürümü belirlendikten sonra komutu yürütür.

### <a name="command-verb"></a>Komut ("eylem")

Komutu (veya "eylem") bir eylem gerçekleştiren yalnızca bir komuttur. Örneğin, `dotnet build` kod oluşturur. `dotnet publish` kodunuzu yayımlar. Konsolunu kullanarak bir uygulama olarak komutlar uygulanan bir `dotnet {verb}` kuralı.

### <a name="arguments"></a>Arguments

Çağrılan komut bağımsız değişkenleri komut satırında geçirdiğiniz bağımsız değişkenler. Yürüttüğünüzde örneğin `dotnet publish my_app.csproj`, `my_app.csproj` bağımsız değişken geçirilir ve yayımlanacak projeyi belirtir `publish` komutu.

### <a name="options"></a>Seçenekler

Komut satırında geçirdiğiniz çağrılan komut seçenekleri seçeneklerdir. Yürüttüğünüzde örneğin `dotnet publish --output /build_output`, `--output` seçeneği ve değerini geçirilir `publish` komutu.

## <a name="migration-from-projectjson"></a>Project.json geçiş

Preview 2'de üretmek için kullanılan *project.json*-tabanlı projeler başvurun [dotnet geçirme](dotnet-migrate.md) projenizi MSBuild'e geçirme hakkında bilgi için konu /*.csproj*yayın araçları ile kullanmak için. .NET Core için Önizleme 2 araçlarının sürümden önce ya da el ile oluşturulan projeleri kılavuzunda aşağıdaki proje güncelleştirmesi [: .NET Core CLI (project.json) DNX'ten geçiş](../migration/from-dnx.md) ve ardından `dotnet migrate` veya doğrudan yükseltme projelerinizi.

## <a name="see-also"></a>Ayrıca bkz.

- [DotNet/CLI GitHub deposu](https://github.com/dotnet/cli/)
- [.NET core Yükleme Kılavuzu](https://aka.ms/dotnetcoregs)
