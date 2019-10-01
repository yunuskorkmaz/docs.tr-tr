---
title: Project. json ' dan .NET Core geçişi
description: Project. JSON kullanarak eski bir .NET Core projesini geçirmeyi öğrenin
ms.date: 07/19/2017
ms.custom: seodec18
ms.openlocfilehash: 167f0707bbaf34ce12a1c56ee2320e7cc4f48bd3
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698926"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>Project. json ' dan .NET Core projelerini geçirme

Bu belgede .NET Core projeleri için aşağıdaki üç geçiş senaryosu ele alınmaktadır:

1. [*Project. JSON* ' un geçerli bir en son şemasından *csproj* 'a geçiş](#migration-from-projectjson-to-csproj)
2. [DNX 'ten csproj 'a geçiş](#migration-from-dnx-to-csproj)
3. [RC3 ve önceki .NET Core csproj projelerinden son biçime geçiş](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

Bu belge yalnızca Project. JSON kullanan eski .NET Core projelerine uygulanabilir. .NET Framework .NET Core 'a geçiş için geçerlidir.

## <a name="migration-from-projectjson-to-csproj"></a>Project. JSON 'dan csproj 'a geçiş

*Project. JSON* ' dan *. csproj* 'a geçiş, aşağıdaki yöntemlerden biri kullanılarak yapılabilir:

- [Visual Studio](#visual-studio)
- [DotNet geçiş komut satırı aracı](#dotnet-migrate)

Her iki yöntem de projeleri geçirmek için aynı temel altyapıyı kullanır, bu nedenle sonuçlar her ikisi için de aynı olacaktır. Çoğu durumda, projeyi geçirmek için şu iki yönden birini kullanmak yeterlidir *. JSON* , gereken tek şeydir ve proje dosyasının el ile düzenlenmesinin *gerekli değildir.* Elde edilen *. csproj* dosyası, kapsayan dizin adı ile aynı ada sahip olacaktır.

### <a name="visual-studio"></a>Visual Studio

Visual Studio 2017 veya Visual Studio 2019 sürüm 16,2 ve önceki sürümlerde *.* xproj dosyalarına başvuran bir *. xproj* dosyası veya çözüm dosyası açtığınızda **tek yönlü yükseltme** iletişim kutusu görüntülenir. İletişim kutusunda geçirilecek projeler görüntülenir. Bir çözüm dosyası açarsanız, çözüm dosyasında belirtilen tüm projeler listelenir. Geçirilecek projelerin listesini gözden geçirin ve **Tamam ' ı**seçin.

![Geçirilecek projelerin listesini gösteren tek yönlü yükseltme iletişim kutusu](media/one-way-upgrade.jpg)

Visual Studio seçilen projeleri otomatik olarak geçirir. Bir çözümü geçirirken, tüm projeler ' i seçmezseniz, bu çözümden kalan projeleri yükseltmenizi isteyen iletişim kutusu görüntülenir. Proje geçirildikten sonra, **Çözüm Gezgini** penceresinde projeye sağ tıklayıp, **\<proje adını >. csproj**öğesini seçerek içeriğini görebilir ve değiştirebilirsiniz.

Geçirilen dosyalar (*Project. JSON*, *Global. JSON*, *. xproj*ve çözüm dosyası) bir *yedekleme* klasörüne taşınır. Geçirilen çözüm dosyası Visual Studio 2017 veya Visual Studio 2019 sürümüne yükseltilir ve bu çözüm dosyasını Visual Studio 2015 veya önceki sürümlerde açamazsınız. Bir geçiş raporu içeren *UpgradeLog. htm* adlı bir dosya Ayrıca otomatik olarak kaydedilir ve açılır.

> [!IMPORTANT]
> Visual Studio 2015 kullanarak projelerinizi geçiremezsiniz.

### <a name="dotnet-migrate"></a>dotnet migrate

Komut satırı senaryosunda [`dotnet migrate`](../tools/dotnet-migrate.md) komutunu kullanabilirsiniz. Nerede bulunanlara bağlı olarak bir projeyi, çözümü veya bir klasör kümesini o sırada geçirir. Bir projeyi geçirdiğinizde, proje ve tüm bağımlılıkları geçirilir.

Geçirilen dosyalar (*Project. JSON*, *Global. JSON*ve *. xproj*) bir *yedekleme* klasörüne taşınır.

> [!NOTE]
> Visual Studio Code kullanıyorsanız, `dotnet migrate` komutu `tasks.json` gibi Visual Studio Code özgü dosyaları değiştirmez. Bu dosyaların el ile değiştirilmesi gerekir.
> Bu Ayrıca, Visual Studio dışında proje Ryder veya herhangi bir düzenleyici veya tümleşik geliştirme ortamı (IDE) kullanıyorsanız de geçerlidir.

Project. JSON ve csproj biçimlerinin karşılaştırması için [Project. JSON ve csproj özellikleri arasındaki eşlemeyi](../tools/project-json-to-csproj.md) inceleyin.

### <a name="common-issues"></a>Yaygın sorunlar

- Bir hata alırsanız: "" DotNet komutuyla eşleşen yürütülebilir dosya bulunamadı ":

Hangi sürümü kullandığınızı görmek için `dotnet --version` ' yı çalıştırın. [`dotnet migrate`](../tools/dotnet-migrate.md) .NET Core CLI RC3 veya üstünü gerektirir.
Geçerli veya üst dizinde *Global. JSON* dosyanız varsa ve `sdk` sürümü daha eski bir sürüme ayarlanmışsa bu hatayı alırsınız.

## <a name="migration-from-dnx-to-csproj"></a>DNX 'ten csproj 'a geçiş

.NET Core geliştirme için DNX kullanmaya devam ediyorsanız, geçiş işleminiz iki aşamada yapılmalıdır:

1. DNX 'ten Project-JSON etkin CLı 'ye geçiş yapmak için [mevcut DNX geçiş kılavuzunu](from-dnx.md) kullanın.
2. *Project. JSON* ' dan *. csproj*'a geçiş yapmak için önceki bölümdeki adımları izleyin.  

> [!NOTE]
> DNX, .NET Core CLI Preview 1 sürümü sırasında resmi kullanım dışı duruma geldi.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Önceki .NET Core csproj biçimlerinden RTM csproj 'e geçiş

.NET Core csproj biçimi, her yeni alet yayın öncesi sürümü ile değiştirilmiştir ve gelişiyor. Proje dosyanızı csproj 'ın önceki sürümlerinden en son sürümüne geçiren bir araç yoktur, bu nedenle proje dosyasını el ile düzenlemeniz gerekir. Asıl adımlar, geçirdiğiniz proje dosyasının sürümüne bağlıdır. Sürümler arasında gerçekleşen değişikliklere göre göz önünde bulundurmanız gereken bazı yönergeler aşağıda verilmiştir:

- Araçlar sürümü özelliğini, varsa `<Project>` öğesinden kaldırın.
- XML ad alanını (`xmlns`) `<Project>` öğesinden kaldırın.
- Yoksa, `Sdk` özniteliğini `<Project>` öğesine ekleyin ve `Microsoft.NET.Sdk` veya `Microsoft.NET.Sdk.Web` olarak ayarlayın. Bu öznitelik, projenin kullanılacak SDK 'Yı kullandığını belirtir. `Microsoft.NET.Sdk.Web`, Web uygulamaları için kullanılır.
- @No__t-0 ve `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` deyimlerini projenin üst ve alt kısmından kaldırın. Bu içeri aktarma deyimleri SDK tarafından kapsanıyor, bu nedenle projenin projede olması gerekmez.
- Projenizde `Microsoft.NETCore.App` veya `NETStandard.Library` `<PackageReference>` varsa, bunları kaldırmalısınız. Bu paket başvuruları [SDK tarafından kapsanıyor](https://aka.ms/sdkimplicitrefs).
- Varsa `Microsoft.NET.Sdk` `<PackageReference>` öğesini kaldırın. SDK başvurusu, `<Project>` öğesindeki `Sdk` özniteliği aracılığıyla gelir.
- [SDK tarafından kapsanan](../tools/csproj.md#default-compilation-includes-in-net-core-projects) [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) kaldırın. Derleme öğeleri yineleneceği için bu genelleştirmeler, projenizde bir hata oluşmasına neden olur.

Bu adımların ardından projenizin RTM .NET Core csproj biçimiyle tamamen uyumlu olması gerekir.

Eski csproj biçiminden yenisine geçişten önceki ve sonraki örneklere örnek olarak, .NET bloguna yönelik [Visual Studio 2017 RC – .NET Core Araçları ' nı güncelleştirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) makalesine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
