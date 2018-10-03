---
title: .NET core csproj biçimine geçiş
description: .NET core Project.json'yi csproj'a geçiş
author: blackdwarf
ms.author: mairaw
ms.date: 07/19/2017
ms.openlocfilehash: da1995ed3b77cb802d1f3d04e6d741809de20927
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027948"
---
# <a name="migrating-net-core-projects-to-the-csproj-format"></a>.Csproj biçimine geçirme .NET Core projeleri

Bu belgede, .NET Core projeleri için geçiş senaryolarını kapsamakta ve aşağıdaki üç geçiş senaryoları geçer:

1. [Geçerli bir en son şema geçişini *project.json* için *csproj*](#migration-from-projectjson-to-csproj)
2. [DNX csproj'a geçiş](#migration-from-dnx-to-csproj)
3. [En son biçime RC3 ve önceki .NET Core csproj'a geçiş projeleri](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

## <a name="migration-from-projectjson-to-csproj"></a>Project.json csproj'a geçiş

Geçiş *project.json* için *.csproj* yapılabilir aşağıdaki yöntemlerden birini kullanarak:

- [Visual Studio 2017](#visual-studio-2017)
- [DotNet geçiş komut satırı aracı](#dotnet-migrate)

Her iki yöntem de aynı temel alınan altyapı projeleri, her ikisi için de aynı sonuçları olacak geçirmek için kullanın. Çoğu durumda, geçirmek için şu iki yoldan biriyle kullanarak *project.json* için *csproj* gereken tek şey ve proje dosyasını el ile'başka düzenleme gereklidir. Ortaya çıkan *.csproj* dosyasını içeren dizin adıyla aynı adlandırılacak.

### <a name="visual-studio-2017"></a>Visual Studio 2017

Açtığınızda bir *.xproj* dosya veya dosya başvuran bir çözüm *.xproj* dosyaları **tek yönlü yükseltme** iletişim kutusu görüntülenir. Geçirilecek projeleri iletişim kutusunu görüntüler.
Bir çözüm dosyasını açın, çözümü dosyasında belirtilen tüm projeler listelenir. Gözden geçirilmesi ve seçmek için projelerinin listesini **Tamam**.

![Geçirilecek projeleri listesini gösteren tek yönlü yükseltme iletişim](media/one-way-upgrade.jpg)

Visual Studio otomatik olarak seçilen projeler geçirir. Tüm projeleri seçmezseniz, bir çözüm geçirirken, Kalan projeler bu çözümünden yükseltme yapmanızı isteyen aynı iletişim kutusu görünür. Proje geçirildikten sonra bakın ve projeye sağ tıklayarak içeriğini değiştirme **Çözüm Gezgini** penceresi ve seçerek **Düzenle \<proje adı > .csproj**.

Geçirilen dosyaları (*project.json*, *global.json*, *.xproj* ve çözüm dosyası) taşınacak bir *yedekleme* klasör. Geçirilen çözüm dosyasını Visual Studio 2017'ye yükseltilir ve Visual Studio'nun önceki sürümlerinde bu çözüm dosyasını açmak mümkün olmayacaktır.
Adlı bir dosya *UpgradeLog.htm* de kaydedilir ve otomatik olarak açılır, geçiş raporu içerir.

> [!IMPORTANT]
> Projelerinizi Visual Studio'nun bu sürümünü kullanarak geçiremezsiniz. Bu nedenle yeni araçlar Visual Studio 2015'te kullanılamıyor.

### <a name="dotnet-migrate"></a>DotNet geçirme

Komut satırı senaryoda kullanabileceğiniz [ `dotnet migrate` ](../tools/dotnet-migrate.md) komutu. Bir proje, bir çözüm ya da klasörleri, bağlı olarak olanları bulunamadı, bu sırayla bir dizi geçirir.
Bir proje geçirdiğinizde, projeyi ve tüm bağımlılıklarını geçirilir.

Geçirilen dosyaları (*project.json*, *global.json* ve *.xproj*) taşınacak bir *yedekleme* klasör.

> [!NOTE]
> Visual Studio Code kullanıyorsanız `dotnet migrate` komut değişiklik yapılmaz Visual Studio kod özgü dosyaları gibi `tasks.json`. Bu dosyaları el ile değişitirilmesi gerekiyor.
> Bu seçenek de proje Ryder veya düzenleyici veya tümleşik geliştirme ortamı (IDE) Visual Studio dışında kullanıyorsanız geçerlidir.

Bkz: [özellikleri project.json ile csproj arasında eşleme](../tools/project-json-to-csproj.md) bir karşılaştırma project.json ile csproj biçimi.

### <a name="common-issues"></a>Sık karşılaşılan sorunları

- Bir hata alırsanız: "hiçbir yürütülebilir bulunan eşleşen komut dotnet-geçirme":

Çalıştırma `dotnet --version` kullanmakta olduğunuz hangi sürümü görmek için. [`dotnet migrate`](../tools/dotnet-migrate.md) .NET Core CLI RC3 gerektirir veya üzeri.
Varsa bu hatayı alırsınız bir *global.json* geçerli dosya ya da üst dizini ve `sdk` sürümünü daha eski bir sürüme ayarlayın.

## <a name="migration-from-dnx-to-csproj"></a>DNX csproj'a geçiş

.NET Core geliştirme için hala DNX kullanıyorsanız, iki aşamada, geçiş işlemi yapılmalıdır:

1. Kullanım [mevcut DNX geçiş kılavuzuna](from-dnx.md) DNX'ten etkin proje json CLI sürümüne geçirmek için.
2. Geçiş için önceki bölümdeki adımları *project.json* için *.csproj*.  

> [!NOTE]
> DNX hale resmi olarak kullanım dışı sırasında .NET Core CLI Önizleme 1 sürümü.

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Önceki .NET Core csproj biçimleri RTM csproj'a geçiş

.NET Core csproj biçimine değiştirme ve araç ile her yeni yayın öncesi sürüm gelişen. Proje dosyasını el ile düzenlemeniz gerekir, böylece proje dosyanızda en son sürüme csproj'ın önceki sürümlerinden geçiş yapacağınız aracı yoktur. Gerçek adımlar geçişin kaynağı olan proje dosyasının sürümüne bağlıdır. Aşağıda dikkate alınması gereken bazı yönergeler, sürümler arasında gerçekleşen değişikliklere göre verilmiştir:

* Araçları sürümü özelliğinden kaldırılacak `<Project>` varsa öğe.
* XML ad alanı kaldırın (`xmlns`) öğesinden `<Project>` öğesi.
* Yoksa, ekleme `Sdk` özniteliğini `<Project>` öğesi ve `Microsoft.NET.Sdk` veya `Microsoft.NET.Sdk.Web`. Bu öznitelik projenin, kullanılacak SDK kullandığını belirtir. `Microsoft.NET.Sdk.Web` Web apps için kullanılır.
* Kaldırma `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` ve `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` üst ve alt projenin deyimlerini. Bu içeri aktarma deyimlerini projede olmalarına gerek bu nedenle SDK tarafından kapsanan.
* Varsa `Microsoft.NETCore.App` veya `NETStandard.Library` `<PackageReference>` öğeleri, projenizdeki kaldırmalısınız bunları. Bu paket başvuruları [SDK tarafından kapsanan](https://aka.ms/sdkimplicitrefs).
* Kaldırma `Microsoft.NET.Sdk` `<PackageReference>` varsa öğe. SDK başvurusu geldiği `Sdk` özniteliği `<Project>` öğesi.
* Kaldırma [eğik çizgi genelleştirmeler](https://en.wikipedia.org/wiki/Glob_(programming)) olan [SDK tarafından kapsanan](../tools/csproj.md#default-compilation-includes-in-net-core-projects). Derleme öğeleri yinelenen çünkü projenizde bu eğik çizgi genelleştirmeler bırakarak derlemeyi hataya neden olur.

Bu adımlardan sonra projeniz .NET Core RTM csproj biçimi ile tamamen uyumlu olmalıdır.

Örnekleri önce ve sonra yeni bir tane eski csproj biçimine geçiş için bkz: [güncelleştirme Visual Studio 2017 RC – .NET Core araçları geliştirmeleri](https://blogs.msdn.microsoft.com/dotnet/2016/12/12/updating-visual-studio-2017-rc-net-core-tooling-improvements/) .NET blogunda makalesi.

## <a name="see-also"></a>Ayrıca bkz.

- [Taşıma, geçirme ve Visual Studio projelerini yükseltme](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
