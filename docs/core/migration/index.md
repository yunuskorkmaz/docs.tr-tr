---
title: .PROJECT.json'dan NET Çekirdek geçişi
description: Project.json'u kullanarak eski bir .NET Core projesini nasıl geçirebilirsiniz öğrenin
ms.date: 07/19/2017
ms.openlocfilehash: 8a9dc05c82fd5476a70ee36a294a287abbfb68c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77450693"
---
# <a name="migrating-net-core-projects-from-projectjson"></a>Project.json'dan .NET Çekirdek projelerini geçirmek

Bu belge,.NET Core projeleri için aşağıdaki üç geçiş senaryosunu kapsar:

1. [*Project.json'un* geçerli bir son şemasından *csproj'a* geçiş](#migration-from-projectjson-to-csproj)
2. [DNX'ten csproj'a geçiş](#migration-from-dnx-to-csproj)
3. [RC3 ve önceki .NET Core csproj projelerinden son formata geçiş](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

Bu belge yalnızca project.json kullanan eski .NET Core projeleri için geçerlidir. .NET Framework'den .NET Core'a geçiş için geçerli değildir.

## <a name="migration-from-projectjson-to-csproj"></a>project.json'dan csproj'a geçiş

*Project.json'dan* *.csproj'a* geçiş aşağıdaki yöntemlerden biri kullanılarak yapılabilir:

- [Visual Studio](#visual-studio)
- [dotnet geçiş komut satırı aracı](#dotnet-migrate)

Her iki yöntem de projeleri geçirmek için aynı altta yatan altyapıyı kullanır, bu nedenle sonuçlar her ikisi için de aynı olacaktır. Çoğu durumda, *csproj* *için project.json* geçirmek için bu iki yoldan birini kullanarak gerekli olan tek şey, ve proje dosyasının daha fazla el ile düzenleme gereklidir. Elde edilen *.csproj* dosyası, içeren dizin adı ile aynı adlandırılacaktır.

### <a name="visual-studio"></a>Visual Studio

*.xproj* dosyasını veya Visual Studio 2017 veya Visual Studio 2019 sürüm 16.2 ve daha önceki sürümlerinde *.xproj* dosyalarına başvuruyapan bir çözüm dosyasını açtığınızda, **Tek yönlü yükseltme** iletişim kutusu görüntülenir. İletişim, geçirilecek projeleri görüntüler. Bir çözüm dosyası açarsanız, çözüm dosyasında belirtilen tüm projeler listelenir. Geçirilecek projelerin listesini gözden geçirin ve **Tamam'ı**seçin.

![Geçirilecek projelerin listesini gösteren tek yönlü yükseltme iletişim kutusu](media/one-way-upgrade.jpg)

Visual Studio seçili projeleri otomatik olarak geçirmektedir. Bir çözümü geçirterken, tüm projeleri seçmezseniz, aynı iletişim kutusu bu çözümden kalan projeleri yükseltmenizi ister. Proje geçirildikten sonra, **Çözüm Gezgini** penceresinde projeyi sağ tıklayarak ve **proje adını>.csproj'u edin'i \<** seçerek içeriğini görebilir ve değiştirebilirsiniz.

Geçirilen dosyalar *(project.json*, *global.json*, *.xproj*ve çözüm dosyası) *Yedek* klasörüne taşınır. Geçirilen çözüm dosyası Visual Studio 2017 veya Visual Studio 2019'a yükseltilir ve bu çözüm dosyasını Visual Studio 2015 veya önceki sürümlerde açamazsınız. Geçiş raporu içeren *UpgradeLog.htm* adlı bir dosya da kaydedilir ve otomatik olarak açılır.

> [!IMPORTANT]
> Visual Studio 2019 sürüm 16.3 ve sonraki sürümlerde bir *.xproj* dosyayı yükleyemez veya geçiremezsiniz. Ayrıca Visual Studio 2015, *bir .xproj* dosyasını geçirme olanağı sağlamaz. Bu Visual Studio sürümlerinden birini kullanıyorsanız, Visual Studio'nun uygun bir sürümünü yükleyin veya daha sonra açıklanan komut satırı geçiş aracını kullanın.

### <a name="dotnet-migrate"></a>dotnet migrate

Komut satırı senaryosunda, komutu [`dotnet migrate`](../tools/dotnet-migrate.md) kullanabilirsiniz. Hangilerinin bulunduğuna bağlı olarak, bir projeyi, bir çözümü veya bu sırayla bir klasör kümesini geçirin. Bir projeyi geçirdiğinizde, proje ve tüm bağımlılıkları geçirilir.

Geçirilen dosyalar *(project.json*, *global.json*, ve *.xproj)* *yedek* klasörüne taşınır.

> [!NOTE]
> Visual Studio Code kullanıyorsanız, `dotnet migrate` komut visual studio koduna özel *görevleri değiştirmez.json*. Bu dosyaların el ile değiştirilmesi gerekir.
> Visual Studio dışında bir editör veya Entegre Geliştirme Ortamı (IDE) kullanıyorsanız bu da geçerlidir.

Project.json ve *.csproj* biçimlerinin karşılaştırılması *project.json* için [project.json ve csproj özellikleri arasında](../tools/project-json-to-csproj.md) bir eşleme bakın.

Bir hata alırsanız:

> Yürütülebilir bulunan komut dotnet-migrate bulunamadı

Hangi `dotnet --version` sürümü kullandığınızı görmek için çalıştırın. [`dotnet migrate`](../tools/dotnet-migrate.md).NET Core SDK 1.0.0 olarak tanıtıldı ve 3.0.100 sürümünde kaldırıldı.
Geçerli veya üst dizinde *global.json* dosyanız varsa ve belirttiği sürüm `sdk` bu aralığın dışındaysa bu hatayı alırsınız.

## <a name="migration-from-dnx-to-csproj"></a>DNX'ten csproj'a geçiş

.NET Core geliştirme için Hala DNX kullanıyorsanız, geçiş işleminiz iki aşamada yapılmalıdır:

1. DNX'ten project-json etkin CLI'ye geçiş yapmak için [varolan DNX geçiş kılavuzunu](from-dnx.md) kullanın.
2. *Project.json'dan* *.csproj'a*geçiş yapmak için önceki bölümden adımları izleyin.

> [!NOTE]
> DNX, .NET Core CLI'nin Önizleme 1 sürümü sırasında resmen amortismana ulaşmış olur.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Önceki .NET Core csproj formatlarından RTM csproj'a geçiş

.NET Core csproj formatı, aracın her yeni ön sürüm sürümüyle birlikte değişiyor ve gelişiyor. Proje dosyanızı csproj'un önceki sürümlerinden en son sürümüne geçirebilecek bir araç yoktur, bu nedenle proje dosyasını el ile düzenlemeniz gerekir. Gerçek adımlar, geçiş yaptığınız proje dosyasının sürümüne bağlıdır. Sürümler arasında gerçekleşen değişikliklere göre göz önünde bulundurulması gereken bazı kılavuzlar şunlardır:

- Varsa, araçlar sürüm `<Project>` özelliğini öğeden kaldırın.
- XML ad alanını`xmlns`( ) `<Project>` öğeden kaldırın.
- `Sdk` Yoksa, `<Project>` öğeye öznitelik ekleyin ve onu ayarlayın `Microsoft.NET.Sdk` veya `Microsoft.NET.Sdk.Web`. Bu öznitelik, projenin kullanılmak üzere SDK'yı kullandığını belirtir. `Microsoft.NET.Sdk.Web`web uygulamaları için kullanılır.
- `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` Ve `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` ifadeleri projenin üst ve alt kısmından kaldırın. Bu ithalat beyanları SDK tarafından ima edilmektedir, bu nedenle projede yer almalarına gerek yoktur.
- Projenizde `Microsoft.NETCore.App` öğeler `NETStandard.Library` `<PackageReference>` varsa, bunları kaldırmanız gerekir. Bu paket referansları [SDK tarafından ima](https://aka.ms/sdkimplicitrefs)edilmektedir.
- Varsa `Microsoft.NET.Sdk` `<PackageReference>` öğeyi kaldırın. SDK `Sdk` `<Project>` başvurusu, öğedeki öznitelik üzerinden gelir.
- [SDK tarafından ima](../project-sdk/overview.md#default-compilation-includes)edilen [globs](https://en.wikipedia.org/wiki/Glob_(programming)) kaldırın. Bu kümesleri projenizde bırakmak, derleme öğeleri çoğaltılacağı için yapıda bir hataya neden olur.

Bu adımlardan sonra projeniz RTM .NET Core csproj formatı ile tam uyumlu olmalıdır.

Eski csproj formatından yenisine geçiş öncesi ve sonrası örnekleri için ,.NET blogundaki [Visual Studio 2017 RC – .NET Core Tooling geliştirmeleri](https://devblogs.microsoft.com/dotnet/updating-visual-studio-2017-rc-net-core-tooling-improvements/) makalesine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Port, Geçiş ve Görsel Stüdyo Projelerini Yükseltme](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
