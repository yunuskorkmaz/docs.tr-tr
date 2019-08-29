---
title: Project. json ' dan .NET Core geçişi
description: Project. JSON kullanarak eski bir .NET Core projesini geçirmeyi öğrenin
ms.date: 07/19/2017
ms.custom: seodec18
ms.openlocfilehash: 6334f06a998054cfaf766654dda59d87f5d23ed8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105300"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>Project. json ' dan .NET Core projelerini geçirme

Bu belge, .NET Core projelerinin geçiş senaryolarını kapsar ve aşağıdaki üç geçiş senaryosunu ele alacak:

1. [*Project. JSON* ' un geçerli bir en son şemasından *csproj* 'a geçiş](#migration-from-projectjson-to-csproj)
2. [DNX 'ten csproj 'a geçiş](#migration-from-dnx-to-csproj)
3. [RC3 ve önceki .NET Core csproj projelerinden son biçime geçiş](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

Bu belge yalnızca, hala Project. JSON kullanan eski .NET Core projelerine uygulanabilir. .NET Framework .NET Core 'a geçiş için geçerli değildir.

## <a name="migration-from-projectjson-to-csproj"></a>Project. JSON 'dan csproj 'a geçiş

*Project. JSON* ' dan *. csproj* 'a geçiş, aşağıdaki yöntemlerden biri kullanılarak yapılabilir:

- [Visual Studio 2017](#visual-studio-2017)
- [DotNet geçiş komut satırı aracı](#dotnet-migrate)

Her iki yöntem de projeleri geçirmek için aynı temel altyapıyı kullanır, bu nedenle sonuçlar her ikisi için de aynı olacaktır. Çoğu durumda, projeyi geçirmek için bu iki yönden birini kullanmak yeterlidir *. JSON* , gereken tek şeydir ve proje dosyasının el ile düzenlenmesinin gerekli değildir. Elde edilen *. csproj* dosyası, kapsayan dizin adı ile aynı ada sahip olacaktır.

### <a name="visual-studio-2017"></a>Visual Studio 2017

. Xproj dosyası veya *. xproj* dosyalarına başvuran bir çözüm dosyası açtığınızda **tek yönlü yükseltme** iletişim kutusu görüntülenir. İletişim kutusunda geçirilecek projeler görüntülenir.
Bir çözüm dosyası açarsanız, çözüm dosyasında belirtilen tüm projeler listelenir. Geçirilecek projelerin listesini gözden geçirin ve **Tamam ' ı**seçin.

![Geçirilecek projelerin listesini gösteren tek yönlü yükseltme iletişim kutusu](media/one-way-upgrade.jpg)

Visual Studio otomatik olarak seçilen projeleri geçirecektir. Bir çözümü geçirirken, tüm projeler ' i seçmezseniz, kalan projeleri o çözümden yükseltmenizi isteyen iletişim kutusu görüntülenir. Proje geçirildikten sonra, **Çözüm Gezgini** penceresinde projeye sağ tıklayıp **proje adını Düzenle \<>. csproj**öğesini seçerek içeriğini görebilir ve değiştirebilirsiniz.

Geçirilen dosyalar (*Project. JSON*, *Global. JSON*, *. xproj* ve çözüm dosyası), bir *yedekleme* klasörüne taşınır. Geçirilen çözüm dosyası Visual Studio 2017 ' a yükseltilecektir ve bu çözüm dosyasını Visual Studio 'nun önceki sürümlerinde açamazsınız.
*UpgradeLog. htm* adlı bir dosya da kaydedilir ve bir geçiş raporu içeren otomatik olarak açılır.

> [!IMPORTANT]
> Yeni araç Visual Studio 2015 ' de mevcut olmadığından, bu Visual Studio sürümünü kullanarak projelerinizi geçiremezsiniz.

### <a name="dotnet-migrate"></a>dotnet migrate

Komut satırı senaryosunda [`dotnet migrate`](../tools/dotnet-migrate.md) komutunu kullanabilirsiniz. Bu işlem, bir projeyi, çözümü veya bir klasör kümesini, nerede bulunanlara bağlı olarak bu sırada geçirebilir.
Bir projeyi geçirdiğinizde, proje ve tüm bağımlılıkları geçirilir.

Geçirilen dosyalar (*Project. JSON*, *Global. JSON* ve *. xproj*), bir *yedekleme* klasörüne taşınır.

> [!NOTE]
> Visual Studio Code kullanıyorsanız, `dotnet migrate` komut gibi `tasks.json`Visual Studio Code özel dosyaları değiştirmez. Bu dosyaların el ile değiştirilmesi gerekir.
> Bu Ayrıca, Visual Studio dışında proje Ryder veya herhangi bir düzenleyici veya tümleşik geliştirme ortamı (IDE) kullanıyorsanız de geçerlidir.

Project. JSON ve csproj biçimlerinin karşılaştırması için [Project. JSON ve csproj özellikleri arasındaki eşlemeyi](../tools/project-json-to-csproj.md) inceleyin.

### <a name="common-issues"></a>Yaygın sorunlar

- Bir hata alırsanız: "DotNet-migrate komutuyla eşleşen yürütülebilir bulunamadı":

Hangi `dotnet --version` sürümü kullandığınızı görmek için ' i çalıştırın. [`dotnet migrate`](../tools/dotnet-migrate.md).NET Core CLI RC3 veya üstünü gerektirir.
Geçerli veya üst dizinde *Global. JSON* dosyanız varsa ve `sdk` sürüm daha eski bir sürüme ayarlanmışsa bu hatayı alırsınız.

## <a name="migration-from-dnx-to-csproj"></a>DNX 'ten csproj 'a geçiş

.NET Core geliştirme için DNX kullanmaya devam ediyorsanız, geçiş işleminiz iki aşamada yapılmalıdır:

1. DNX 'ten Project-JSON etkin CLı 'ye geçiş yapmak için [mevcut DNX geçiş kılavuzunu](from-dnx.md) kullanın.
2. *Project. JSON* ' dan *. csproj*'a geçiş yapmak için önceki bölümdeki adımları izleyin.  

> [!NOTE]
> DNX, .NET Core CLI Preview 1 sürümü sırasında resmi kullanım dışı duruma geldi.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Önceki .NET Core csproj biçimlerinden RTM csproj 'e geçiş

.NET Core csproj biçimi, her yeni alet yayın öncesi sürümü ile değiştirilmiştir ve gelişiyor. Proje dosyanızı csproj 'ın önceki sürümlerinden en son sürümüne geçiren bir araç yoktur, bu nedenle proje dosyasını el ile düzenlemeniz gerekir. Asıl adımlar, geçirdiğiniz proje dosyasının sürümüne bağlıdır. Sürümler arasında gerçekleşen değişikliklere göre göz önünde bulundurmanız gereken bazı yönergeler aşağıda verilmiştir:

- Varsa, Araçlar sürümü özelliğini `<Project>` öğesinden kaldırın.
- XML ad alanını (`xmlns`) `<Project>` öğeden kaldırın.
- Yoksa, `Sdk` özniteliğini `<Project>` öğesine ekleyin ve veya `Microsoft.NET.Sdk.Web`olarak `Microsoft.NET.Sdk` ayarlayın. Bu öznitelik, projenin kullanılacak SDK 'Yı kullandığını belirtir. `Microsoft.NET.Sdk.Web`Web uygulamaları için kullanılır.
- `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` Ve`<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` deyimlerini projenin üst ve alt kısmından kaldırın. Bu içeri aktarma deyimleri SDK tarafından kapsanıyor, bu nedenle projenin projede olması gerekmez.
- `Microsoft.NETCore.App` Projenizde veya `NETStandard.Library` öğeleriniz varsa,bunlarıkaldırmanızgerekir.`<PackageReference>` Bu paket başvuruları [SDK tarafından kapsanıyor](https://aka.ms/sdkimplicitrefs).
- `Microsoft.NET.Sdk` Varsa`<PackageReference>` , öğeyi kaldırın. SDK başvurusu, `Sdk` `<Project>` öğesindeki özniteliği aracılığıyla gelir.
- [SDK tarafından kapsanan](../tools/csproj.md#default-compilation-includes-in-net-core-projects) [genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) kaldırın. Derleme öğeleri yineleneceği için bu genelleştirmeler, projenizde bir hata oluşmasına neden olur.

Bu adımların ardından projenizin RTM .NET Core csproj biçimiyle tamamen uyumlu olması gerekir.

Eski csproj biçiminden yenisine geçişten önceki ve sonraki örneklere örnek olarak, .NET bloguna yönelik [Visual Studio 2017 RC – .NET Core Araçları ' nı güncelleştirme geliştirmeleri](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) makalesine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Taşıma, geçirme ve Visual Studio projelerini yükseltme](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
