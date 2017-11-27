---
title: ".NET core geçiş csproj biçimine"
description: ".NET core project.json csproj geçiş"
keywords: ".NET, .NET core, .NET Core geçiş"
author: blackdwarf
ms.author: mairaw
ms.date: 07/19/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 1feadf3d-3cfc-41dd-abb5-a4fc303a7b53
ms.openlocfilehash: 1d972489536e929c8694bd6a4cab31c9f2d624a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="migrating-net-core-projects-to-the-csproj-format"></a>.Csproj biçimine geçirme .NET Core projeleri

Bu belge, .NET Core projeleri için geçiş senaryolarını kapsamakta ve aşağıdaki üç geçiş senaryoları geçer:

1. [Geçerli en son şeması geçişini *project.json* için *csproj*](#migration-from-projectjson-to-csproj)
2. [Csproj DNX geçiş](#migration-from-dnx-to-csproj)
3. [RC3 ve önceki .NET Core csproj projeleri son biçimi geçiş](#migration-from-earlier-net-core-csproj-formats-to-rtm-csproj)

## <a name="migration-from-projectjson-to-csproj"></a>Csproj project.json geçiş
Geçiş *project.json* için *.csproj* yapılabilir aşağıdaki yöntemlerden birini kullanarak:

- [Visual Studio 2017](#visual-studio-2017)
- [DotNet geçirmek komut satırı aracı](#dotnet-migrate)
 
Yöntemlerin her ikisi de aynı temel alınan altyapısı sonuçları her ikisi için aynı olması için projeleri geçirmek için kullanın. Çoğu durumda, geçirmek için aşağıdaki yollardan birini kullanarak *project.json* için *csproj* gereken tek şey ve proje dosyasını el ile'başka düzenleme gereklidir. Elde edilen *.csproj* adlı dosyasının bulunduğu dizin adı ile aynı.

### <a name="visual-studio-2017"></a>Visual Studio 2017

Açtığınızda bir *artık.xproj* dosya veya hangi girişlerin dosya bir çözüm *artık.xproj* dosyaları **tek yönlü yükseltme** iletişim kutusu görüntülenir. İletişim kutusu geçirilecek projeleri görüntüler. Bir çözüm dosyasını açın, çözüm dosyasında belirtilen tüm projeleri listelenir. Geçirilmesi ve seçmek için projeleri içeren listeyi gözden geçirin **Tamam**.

![Geçirilecek projelerinin listesini gösteren tek yönlü iletişim](media/one-way-upgrade.jpg)

Visual Studio otomatik olarak seçilen projeleri geçirirsiniz. Tüm projeleri seçmezseniz, bir çözüm geçirirken, bu çözüm kalan projelerini yükseltme isteyen aynı iletişim kutusu görüntülenir. Proje geçirildikten sonra bakın ve projeye sağ tıklayarak içeriğini değiştirme **Çözüm Gezgini** penceresi ve seçerek **Düzenle \<proje adı > .csproj**.

Geçirilen dosyaları (*project.json*, *global.json*, *artık.xproj* ve çözüm dosyasını) taşınacak bir *yedekleme* klasör. Geçirilen çözüm dosyasını Visual Studio 2017 yükseltilir ve Visual Studio'nun önceki sürümleri bu çözüm dosyasını açın yükleyemezsiniz. Adlı bir dosya *UpgradeLog.htm* da kaydedilmiş ve otomatik olarak açılmasını geçiş raporu içerir.

> [!IMPORTANT]
> Yeni araçları Visual Studio 2015'te kullanılabilir olmadığından projelerinizi Visual Studio'nun bu sürümü kullanarak geçiremezsiniz.

### <a name="dotnet-migrate"></a>DotNet geçirme

Komut satırı senaryosunda, kullandığınız [ `dotnet migrate` ](../tools/dotnet-migrate.md) komutu. Proje, bir çözüm ya da klasörleri hangi olanları bulunamadı, bu sırayla bir dizi geçirirsiniz. Bir proje geçirdiğinizde, proje ve tüm bağımlılıklarını geçirilir.

Geçirilen dosyaları (*project.json*, *global.json* ve *artık.xproj*) taşınacak bir *yedekleme* klasör.

> [!NOTE]
> Visual Studio Code kullanıyorsanız `dotnet migrate` komutu değil Değiştir Visual Studio kod özgü dosyaları gibi `tasks.json`. Bu dosyaları el ile değiştirilmesi gerekebilir. Bu aynı zamanda proje Ryder veya Düzenleyicisi veya Visual Studio dışında tümleşik geliştirme ortamı (IDE) kullanıyorsanız geçerlidir. 

Bkz: [project.json ve csproj özellikleri arasında bir eşleme](../tools/project-json-to-csproj.md) project.json ve csproj biçimlerinin karşılaştırması.

### <a name="common-issues"></a>Sık karşılaşılan sorunları

- Bir hata alırsanız: "hiçbir yürütülebilir eşleşen komutu dotnet bulunamadı-geçirmek":

Çalıştırma `dotnet --version` kullanmakta olduğunuz hangi sürümü görmek için. [`dotnet migrate`](../tools/dotnet-migrate.md).NET Core CLI RC3 gerektirir ya da daha yüksek.
Varsa bu hatayı alırsınız bir *global.json* geçerli dosya veya üst dizini ve `sdk` sürüm, daha eski bir sürüm olarak ayarlanır.

## <a name="migration-from-dnx-to-csproj"></a>Csproj DNX geçiş
.NET Core geliştirme için DNX hala kullanıyorsanız, iki aşamada, geçiş işlemi yapılması gerekir:

1. Kullanım [varolan DNX Geçiş Kılavuzu](from-dnx.md) DNX proje json etkin CLI geçirmek için.
2. Geçiş için önceki bölümdeki adımları *project.json* için *.csproj*.  

> [!NOTE]
> DNX hale resmi olarak kullanım dışı .NET Core CLI Preview 1 sürümü sırasında. 

## <a name="migration-from-earlier-net-core-csproj-formats-to-rtm-csproj"></a>Önceki .NET Core csproj geçişini RTM csproj biçimleri
.NET Core csproj biçimini değiştirme ve araçları ile her yeni yayın öncesi sürüm gelişen. Proje dosyası el ile düzenlemeniz gerekir böylece proje dosyanızın en son sürüme csproj önceki sürümlerinden geçiş yapacağınız aracı yoktur. Gerçek adımları geçirdiğiniz proje dosyası sürümüne bağlıdır. Aşağıda dikkate alınması gereken bazı yönergeler, sürümler arasında gerçekleşen değişikliklere göre verilmiştir:

* Araçları sürüm özellikten kaldırmak `<Project>` varsa öğesi. 
* XML ad alanı Kaldır (`xmlns`) gelen `<Project>` öğesi.
* Yoksa, ekleme `Sdk` özniteliğini `<Project>` öğesi ve ayarlamak `Microsoft.NET.Sdk` veya `Microsoft.NET.Sdk.Web`. Bu öznitelik, proje kullanılacak SDK kullandığını belirtir. `Microsoft.NET.Sdk.Web`Web uygulamaları için kullanılır.
* Kaldırma `<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\Microsoft.Common.props" />` ve `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` deyimleri üst ve alt projenin. Bu yüzden projede olmalarına gerek yoktur, deyimleri SDK tarafından kapsanan bu içeri aktarma. 
* Varsa `Microsoft.NETCore.App` veya `NETStandard.Library` `<PackageReference>` öğeleri projenizdeki kaldırmalısınız bunları. Bu paket başvuruları [SDK tarafından kapsanan](https://aka.ms/sdkimplicitrefs). 
* Kaldırma `Microsoft.NET.Sdk` `<PackageReference>` varsa öğesi. SDK'sı başvurusu geldiği `Sdk` özniteliği `<Project>` öğesi. 
* Kaldırma [globs](https://en.wikipedia.org/wiki/Glob_(programming)) olan [SDK tarafından kapsanan](../tools/csproj.md#default-compilation-includes-in-net-core-projects). Derleme öğeleri yinelenen olduğundan bu globs projenizde bırakarak derleme üzerinde bir hataya neden olur. 

Sonra şu adımları projeniz .NET Core RTM csproj biçimiyle tamamen uyumlu olması gerekir. 

Örnekleri eski csproj biçiminden yeni bir geçiş öncesinde ve sonrasında için bkz: [güncelleştirme Visual Studio 2017 RC – .NET Core Tooling geliştirmeleri](https://blogs.msdn.microsoft.com/dotnet/2016/12/12/updating-visual-studio-2017-rc-net-core-tooling-improvements/) .NET blogunda makalesi.

## <a name="see-also"></a>Ayrıca bkz.
[Bağlantı noktası, geçirme ve Visual Studio projelerini yükseltme](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)
