---
title: project.js'den .NET Core geçişi
description: project.jskullanarak eski bir .NET Core projesini nasıl geçirebileceğinizi öğrenin
ms.date: 07/19/2017
ms.openlocfilehash: 0d4190a02389089a888d8b52dd8e7c412636b575
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538256"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>.NET Core projelerini project.js'tan geçirme

Bu belgede .NET Core projeleri için aşağıdaki üç geçiş senaryosu ele alınmaktadır:

1. [*project.js* geçerli bir en son şemadan *csproj* 'ya geçiş](#migration-from-projectjson-to-csproj)
2. [DNX 'ten csproj 'a geçiş](#migration-from-dnx-to-csproj)
3. [RC3 ve önceki .NET Core csproj projelerinden son biçime geçiş](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

Bu belge yalnızca project.jskullanan eski .NET Core projelerine uygulanabilir. .NET Framework .NET Core 'a geçiş için geçerlidir.

## <a name="migration-from-projectjson-to-csproj"></a>project.json csproj 'e geçiş

Aşağıdaki yöntemlerden biri kullanılarak *. csproj* 'a *project.js* geçişi yapılabilir:

- [Visual Studio](#visual-studio)
- [DotNet geçiş komut satırı aracı](#dotnet-migrate)

Her iki yöntem de projeleri geçirmek için aynı temel altyapıyı kullanır, bu nedenle sonuçlar her ikisi için de aynı olacaktır. Çoğu durumda, *project.jsüzerinde açık* olan tek şey gereken tek şeydir ve proje dosyasının el *csproj* ile düzenlenmesine gerek kalmaz. Elde edilen *. csproj* dosyası, kapsayan dizin adı ile aynı ada sahip olacaktır.

### <a name="visual-studio"></a>Visual Studio

Visual Studio 2017 veya Visual Studio 2019 sürüm 16,2 ve önceki sürümlerde *.* xproj dosyalarına başvuran bir *. xproj* dosyası veya çözüm dosyası açtığınızda **tek yönlü yükseltme** iletişim kutusu görüntülenir. İletişim kutusunda geçirilecek projeler görüntülenir. Bir çözüm dosyası açarsanız, çözüm dosyasında belirtilen tüm projeler listelenir. Geçirilecek projelerin listesini gözden geçirin ve **Tamam ' ı**seçin.

![Geçirilecek projelerin listesini gösteren tek yönlü yükseltme iletişim kutusu](media/one-way-upgrade.jpg)

Visual Studio seçilen projeleri otomatik olarak geçirir. Bir çözümü geçirirken, tüm projeler ' i seçmezseniz, bu çözümden kalan projeleri yükseltmenizi isteyen iletişim kutusu görüntülenir. Proje geçirildikten sonra, **Çözüm Gezgini** penceresinde projeye sağ tıklayıp, ** \<project name> . csproj Düzenle**' yi seçerek içeriğini görebilir ve değiştirebilirsiniz.

Geçirilen dosyalar (*project.json*, *global.json*, *. xproj*ve çözüm dosyası) bir *yedekleme* klasörüne taşınır. Geçirilen çözüm dosyası Visual Studio 2017 veya Visual Studio 2019 sürümüne yükseltilir ve bu çözüm dosyasını Visual Studio 2015 veya önceki sürümlerde açamazsınız. Geçiş raporu içeren *UpgradeLog.htm* adlı bir dosya de otomatik olarak kaydedilir ve açılır.

> [!IMPORTANT]
> Visual Studio 2019 sürüm 16,3 ve sonrasında, bir *. xproj* dosyasını yükleyemez veya geçiremezsiniz. Ayrıca, Visual Studio 2015 bir *. xproj* dosyasını geçirebilme olanağı sağlamaz. Bu Visual Studio sürümlerinden birini kullanıyorsanız, Visual Studio 'nun uygun bir sürümünü yükledikten sonra veya bir sonraki adımda açıklanan komut satırı geçiş aracını kullanın.

### <a name="dotnet-migrate"></a>dotnet migrate

Komut satırı senaryosunda [`dotnet migrate`](../tools/dotnet-migrate.md) komutunu kullanabilirsiniz. Nerede bulunanlara bağlı olarak bir projeyi, çözümü veya bir klasör kümesini o sırada geçirir. Bir projeyi geçirdiğinizde, proje ve tüm bağımlılıkları geçirilir.

Geçirilen dosyalar (*project.json*, *global.json*ve *. xproj*) bir *yedekleme* klasörüne taşınır.

> [!NOTE]
> Visual Studio Code kullanıyorsanız, `dotnet migrate` komut *tasks.js*gibi Visual Studio Code özel dosyaları değiştirmez. Bu dosyaların el ile değiştirilmesi gerekir.
> Bu, Visual Studio dışında bir düzenleyici veya tümleşik geliştirme ortamı (IDE) kullanıyorsanız de geçerlidir.

*project.json* ve *. csproj* biçimlerinin bir karşılaştırması için [project.json ve csproj özellikleri arasında bir eşlemeye](../tools/project-json-to-csproj.md) bakın.

Bir hata alırsanız:

> DotNet komutuyla eşleşen çalıştırılabilir bulunamadı-geçiş

`dotnet --version`Hangi sürümü kullandığınızı görmek için ' i çalıştırın. [`dotnet migrate`](../tools/dotnet-migrate.md) .NET Core SDK 1.0.0 ' de tanıtılmıştı ve sürüm 3.0.100 ' de kaldırılmıştır.
Geçerli veya üst dizinde bir *global.js* dosyanız varsa ve `sdk` belirttiği sürüm bu aralığın dışındaysa bu hatayı alırsınız.

## <a name="migration-from-dnx-to-csproj"></a>DNX 'ten csproj 'a geçiş

.NET Core geliştirme için DNX kullanmaya devam ediyorsanız, geçiş işleminiz iki aşamada yapılmalıdır:

1. DNX 'ten Project-JSON etkin CLı 'ye geçiş yapmak için [mevcut DNX geçiş kılavuzunu](from-dnx.md) kullanın.
2. Yukarıdaki *project.js'* den *. csproj*' a geçiş yapmak için önceki bölümde yer alan adımları izleyin.

> [!NOTE]
> DNX, .NET Core CLI Preview 1 sürümü sırasında resmi kullanım dışı duruma geldi.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Önceki .NET Core csproj biçimlerinden RTM csproj 'e geçiş

.NET Core csproj biçimi, her yeni alet yayın öncesi sürümü ile değiştirilmiştir ve gelişiyor. Proje dosyanızı csproj 'ın önceki sürümlerinden en son sürümüne geçiren bir araç yoktur, bu nedenle proje dosyasını el ile düzenlemeniz gerekir. Asıl adımlar, geçirdiğiniz proje dosyasının sürümüne bağlıdır. Sürümler arasında gerçekleşen değişikliklere göre göz önünde bulundurmanız gereken bazı yönergeler aşağıda verilmiştir:

- Varsa, Araçlar sürümü özelliğini öğesinden kaldırın `<Project>` .
- XML ad alanını ( `xmlns` ) `<Project>` öğeden kaldırın.
- Yoksa, `Sdk` özniteliğini `<Project>` öğesine ekleyin ve veya olarak ayarlayın `Microsoft.NET.Sdk` `Microsoft.NET.Sdk.Web` . Bu öznitelik, projenin kullanılacak SDK 'Yı kullandığını belirtir. `Microsoft.NET.Sdk.Web` Web uygulamaları için kullanılır.
- `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />`Ve `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` deyimlerini projenin üst ve alt kısmından kaldırın. Bu içeri aktarma deyimleri SDK tarafından kapsanıyor, bu nedenle projenin projede olması gerekmez.
- `Microsoft.NETCore.App`Projenizde veya öğeleriniz varsa `NETStandard.Library` `<PackageReference>` , bunları kaldırmanız gerekir. Bu paket başvuruları [SDK tarafından kapsanıyor](../tools/csproj.md).
- Varsa `Microsoft.NET.Sdk` `<PackageReference>` , öğeyi kaldırın. SDK başvurusu, `Sdk` öğesindeki özniteliği aracılığıyla gelir `<Project>` .
- [SDK tarafından kapsanan](../project-sdk/overview.md#default-compilation-includes) [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) kaldırın. Derleme öğeleri yineleneceği için bu genelleştirmeler, projenizde bir hata oluşmasına neden olur.

Bu adımların ardından projenizin RTM .NET Core csproj biçimiyle tamamen uyumlu olması gerekir.

Eski csproj biçiminden yenisine geçişten önceki ve sonraki örneklere örnek olarak, .NET bloguna yönelik [Visual Studio 2017 RC – .NET Core Araçları ' nı güncelleştirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) makalesine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
