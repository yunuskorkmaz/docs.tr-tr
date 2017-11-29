---
title: ".NET core komut satırı arabirimi (CLI) araçları"
description: ".NET Core komut satırı arabirimi (CLI) araçları ve özelliklerinin genel bakış."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: d66738593a1542affc956e08bbc38a3b2b1841b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="net-core-command-line-interface-cli-tools"></a>.NET core komut satırı arabirimi (CLI) araçları

.NET Core komut satırı arabirimi (CLI) .NET uygulamaları geliştirmek için bir yeni çapraz platform araç zinciri ' dir. Tümleşik geliştirme ortamlarını (IDE), düzenleyiciler ve yapı orchestrators tuttuğunuzda gibi CLI üst düzey hangi araçların üzerine temelidir.

## <a name="installation"></a>Yükleme

Yerel yükleyicileri kullanın ya da yükleme Kabuk komut dosyalarını kullanın:

* Yerel yükleyicileri öncelikle Geliştirici makinelerinde kullanılır ve desteklenen kullanım her platformun yerel mekanizması, örneğin, Windows Ubuntu veya MSI paketleri DEB paketlerini yükleyin. Bu yükleyiciler yüklemek ve geliştirici tarafından hemen kullanmak için ortamı yapılandırmak ancak makine üzerinde yönetim ayrıcalıkları gerektirir. ' Ndaki yükleme yönergelerine görüntüleyebilirsiniz [.NET Core Yükleme Kılavuzu'na](https://aka.ms/dotnetcoregs).
* Kabuk komut dosyalarını öncelikle yapı sunucuları veya yönetim ayrıcalıklarına kalmadan araçları yüklemek istediğiniz zaman ayarlamak için kullanılır. Yükleme betikleri el ile yüklenmesi gereken makinede Önkoşulları Yükleme yok. Daha fazla bilgi için bkz: [betik başvuru konusu yüklemek](dotnet-install-script.md). Sürekli Tümleştirme (CI) derleme sunucunuzda CLI'yı ayarlama hakkında daha fazla bilgi için bkz: [kullanarak .NET Core SDK'yı ve araçları, sürekli tümleştirme (CI)](using-ci-with-cli.md).

Varsayılan olarak, CLI bir yan yana (SxS) şekilde yüklediği CLI araçlarını birden fazla sürümünü tek bir makinede bulunabilir. Birden çok sürümü yüklü olduğu bir makineye kullanılan hangi sürümünün belirleme açıklanmıştır daha ayrıntılı olarak [sürücü](#driver) bölümü.

## <a name="cli-commands"></a>CLI komutları

Aşağıdaki komutlar, varsayılan olarak yüklenir:

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

**Temel komutları**

* [Yeni](dotnet-new.md)
* [geri yükleme](dotnet-restore.md)
* [derleme](dotnet-build.md)
* [Yayımlama](dotnet-publish.md)
* [çalıştırma](dotnet-run.md)
* [test etme](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [Paketi](dotnet-pack.md)
* [geçirme](dotnet-migrate.md)
* [Temizleme](dotnet-clean.md)
* [sln](dotnet-sln.md)
* [Yardım](dotnet-help.md)
* [Depolama](dotnet-store.md)

**Proje değişikliği komutları**

* [Paket ekleme](dotnet-add-package.md)
* [başvuru ekleme](dotnet-add-reference.md)
* [paketi kaldırma](dotnet-remove-package.md)
* [başvurusunu kaldırın](dotnet-remove-reference.md)
* [listesi başvurusu](dotnet-list-reference.md)

**Gelişmiş komutları**

* [nuget Sil](dotnet-nuget-delete.md)
* [nuget yerel öğeler](dotnet-nuget-locals.md)
* [nuget gönderme](dotnet-nuget-push.md)
* [MSBuild](dotnet-msbuild.md)
* [DotNet yükleme betiği](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**Temel komutları**

* [Yeni](dotnet-new.md)
* [geri yükleme](dotnet-restore.md)
* [derleme](dotnet-build.md)
* [Yayımlama](dotnet-publish.md)
* [çalıştırma](dotnet-run.md)
* [test etme](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [Paketi](dotnet-pack.md)
* [geçirme](dotnet-migrate.md)
* [Temizleme](dotnet-clean.md)
* [sln](dotnet-sln.md)

**Proje değişikliği komutları**

* [Paket ekleme](dotnet-add-package.md)
* [başvuru ekleme](dotnet-add-reference.md)
* [paketi kaldırma](dotnet-remove-package.md)
* [başvurusunu kaldırın](dotnet-remove-reference.md)
* [listesi başvurusu](dotnet-list-reference.md)

**Gelişmiş komutları**

* [nuget Sil](dotnet-nuget-delete.md)
* [nuget yerel öğeler](dotnet-nuget-locals.md)
* [nuget gönderme](dotnet-nuget-push.md)
* [MSBuild](dotnet-msbuild.md)
* [DotNet yükleme betiği](dotnet-install-script.md)

---

CLI projeleriniz için ek araçlar belirtmenize olanak sağlayan genişletilebilirlik modeli devralır. Daha fazla bilgi için bkz: [.NET Core CLI genişletilebilirlik modeli](extensibility.md) konu.

## <a name="command-structure"></a>Komut yapısı

CLI komut yapısını oluşur [("dotnet") sürücü](#driver), [komutu (veya "eylem")](#command-verb)ve büyük olasılıkla komut [bağımsız değişkenleri](#arguments) ve [seçenekleri](#options). Adlı bir dizinden çalıştırıldığında Göster bu modelinde yeni bir konsol uygulaması oluşturma ve aşağıdaki komutları komut satırından çalıştırma gibi CLI işlemlerinin çoğu, gördüğünüz *my_app_3.sft*:

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

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

Sürücü adlı [dotnet](dotnet.md) ve iki sorumlulukları, ya da çalışan bir [framework bağımlı uygulama](../deploying/index.md) veya bir komut yürütülürken. Yalnızca bir kez `dotnet` bir uygulamayı başlatmak için kullanıldığında bir komuttur olmadan kullanılır.

Framework bağımlı uygulamayı çalıştırın, örneğin, sürücü sonra uygulamayı belirlemek için `dotnet /path/to/my_app.dll`. Uygulamanın DLL bulunduğu klasöründen komutu yürütülürken, yalnızca yürütme `dotnet my_app.dll`.

Sürücü için bir komut sağladığında `dotnet.exe` CLI komutu yürütme işlemi başlatır. İlk olarak, sürücü kullanmak için SDK sürümü belirler. Sürüm komutu seçeneklerinde belirtilmezse, sürücü en son sürümünü kullanır. Son yüklü olan sürümü dışında bir sürüm belirtmek için kullanın `--fx-version <VERSION>` seçeneği (bkz [dotnet komutu](dotnet.md) başvuru). SDK sürümü belirlendikten sonra sürücü komutu yürütür.

### <a name="command-verb"></a>Komut ("eylem")

Komut (veya "eylem"), bir eylem gerçekleştiren yalnızca bir komuttur. Örneğin, `dotnet build` kodunuzu oluşturur. `dotnet publish`kodunuzu yayımlar. Komutlar bir konsol uygulaması kullanarak olarak uygulanan bir `dotnet {verb}` kuralı.

### <a name="arguments"></a>Arguments

Komut satırında geçirdiğiniz bağımsız çağrılan komut için bağımsız değişkenler. Örneğin, yürütülürken `dotnet publish my_app.csproj`, `my_app.csproj` bağımsız değişkeni yayımlanacak projeyi gösterir ve geçirilir `publish` komutu.

### <a name="options"></a>Seçenekler

Komut satırında geçirdiğiniz çağrılan komut seçenekleri seçeneklerdir. Örneğin, yürütülürken `dotnet publish --output /build_output`, `--output` seçeneği ve değerini için geçirilir `publish` komutu. 

## <a name="migration-from-projectjson"></a>Project.json geçiş

Önizleme üretmek için tooling 2 kullandıysanız *project.json*-tabanlı projeler başvurun [dotnet geçirmek](dotnet-migrate.md) projeniz için MSBuild geçirme hakkında bilgi için konu /*.csproj*yayın araçları ile kullanım için. Önizleme 2 araç sürümünden önce oluşturulan .NET Core projeler için ya da el ile güncelleştirmeniz yer alan yönergeleri izleyerek proje [.NET Core CLI (project.json) DNX geçiş](../migration/from-dnx.md) ve sonra da `dotnet migrate` veya doğrudan projelerinizi yükseltin.

## <a name="see-also"></a>Ayrıca bkz.

 [DotNet/CLI GitHub deposunu](https://github.com/dotnet/cli/)  
 [.NET core Yükleme Kılavuzu](https://aka.ms/dotnetcoregs)  