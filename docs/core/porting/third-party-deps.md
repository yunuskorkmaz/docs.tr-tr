---
title: Taşıma için .NET Core -, üçüncü taraf bağımlılıklarını çözümleme
description: .NET Framework projenizden .NET Core için bağlantı noktası için üçüncü taraf bağımlılıkları analiz etmeyi öğrenin.
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.openlocfilehash: 06d8d36d8369680c54af4d16513b2b871b57079c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45529681"
---
# <a name="analyze-your-third-party-dependencies"></a>Üçüncü taraf bağımlılıklarını çözümleme

Kodunuzu .NET Core veya .NET Standard arıyorsanız, taşıma sürecinde ilk adım, üçüncü taraf bağımlılıklarının öğrenmektir. Üçüncü taraf bağımlılıklarıdır ya da [NuGet paketlerini](#analyze-referenced-nuget-packages-on-your-project) veya [DLL'leri](#analyze-dependencies-that-arent-nuget-packages) projenizde başvuran. Her bir bağımlılığın değerlendirin ve .NET Core ile uyumlu olmayan bağımlılıklarına bir yedek planını geliştirin. Bu makalede bağımlılık .NET Core ile uyumlu olup olmadığını belirlemek nasıl gösterir.

## <a name="analyze-referenced-nuget-packages-in-your-project"></a>Başvurulan NuGet paketlerini projenize analiz edin

Projenizdeki NuGet paketlerini başvuran, .NET Core ile uyumlu olup olmadıklarını doğrulamak gerekir.
Gerçekleştirmenin iki yolu vardır:

* [NuGet paket Gezgini uygulamasını kullanarak](#analyze-nuget-packages-using-nuget-package-explorer) (en güvenilir yöntemi).
* [Nuget.org sitesini kullanarak](#analyze-nuget-packages-using-nugetorg).

.NET Core ve yalnızca hedef .NET Framework ile uyumlu değillerse paketlerini çözümledikten sonra olursa denetleyebilirsiniz [.NET Framework uyumluluk modu](#net-framework-compatibility-mode) taşıma sürecinizi yardımcı olabilir.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>NuGet paket Gezgini kullanarak NuGet paketleri çözümleyin

Bir NuGet paketi kendisi bir platforma özgü derlemeleri içeren klasörleri kümesidir. Bu nedenle paketin içindeki uyumlu bir derlemeyi içeren bir klasör olup olmadığını denetlemek gerekir.

NuGet paketi klasörleri incelemek için en kolay yolu kullanmaktır [NuGet paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aracı. Yükledikten sonra klasör adlarını görmek için aşağıdaki adımları kullanın:

1. NuGet paket Gezgini açın.
2. Tıklayın **açık çevrimiçi akış paketinden**.
3. Paket adını arayın.
4. Arama sonuçlarından paket adını seçin ve tıklayın **açın**.
5. Genişletin *LIB* klasörünü sağ tarafı ve klasör adlarını bakın.

Aşağıdaki adlarından biriyle bir klasörü arayın:

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
netcoreapp2.1
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Bu değerler [hedef çerçeve bilinen adlar (Tfm'ler)](../../standard/frameworks.md) sürümleri için harita [.NET Standard](../../standard/net-standard.md), .NET Core ve .NET Core ile uyumlu olan geleneksel taşınabilir sınıf kitaplığı (PCL) profilleri.

> [!IMPORTANT]
> Bir paket destekleyen Tfm'ler baktığımda unutmayın `netcoreapp*`, uyumlu açıkken, yalnızca .NET Core projeleri için ve .NET Standard projeleri için değil.
> Yalnızca hedefleyen bir kitaplık `netcoreapp*` değil `netstandard*` yalnızca diğer .NET Core uygulamaları tarafından kullanılabilecek.

.NET Core, uyumlu olabilir, yayın öncesi sürümlerinde kullanılan bazı eski Tfm'ler vardır:

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

Bu büyük olasılıkla Tfm'ler kodunuzu ile çalışırken, uyumluluğu garanti yoktur. Aşağıdaki Tfm'ler paketlerle yayın öncesi .NET Core paketlerle oluşturulmuştur. Sırada (veya) not alın. Bu Tfm'ler kullanarak paketleri .NET Standard tabanlı olarak güncelleştirilir.

> [!NOTE]
> Geleneksel PCL veya yayın öncesi .NET Core hedef hedefleyen bir paketini kullanacak şekilde kullanmalısınız `PackageTargetFallback` proje dosyanızda MSBuild öğesi.
> Bu MSBuild öğesi hakkında daha fazla bilgi için bkz. [ `PackageTargetFallback` ](../tools/csproj.md#packagetargetfallback).

### <a name="analyze-nuget-packages-using-nugetorg"></a>NuGet paketleri nuget.org kullanarak Analiz

Alternatif olarak, her paket destekler Tfm'ler gördüğünüz [nuget.org](https://www.nuget.org/) altında **bağımlılıkları** paket bölümü.

Site kullanarak uyumluluğunu doğrulamak için daha kolay bir yöntem olmasına karşın **bağımlılıkları** bilgileri kullanılabilir değil tüm paketler için sitesinde.

### <a name="net-framework-compatibility-mode"></a>.NET framework uyumluluk modu

Birçok NuGet paketi olarak NuGet paketlerini çözümledikten sonra bunların yalnızca .NET Framework'ü hedefleyen bulabilirsiniz.

.NET Standard 2.0 ile başlayarak, .NET Framework uyumluluk modu sunulmuştur. Bu uyumluluk modu, .NET Framework kitaplıkları başvurmak .NET Standard ve .NET Core projeleri sağlar. .NET Framework kitaplıklarına başvuruda bulunan işe yaramazsa tüm projeler için örneğin Windows Presentation Foundation (WPF) API'leri kitaplığı kullanan, ancak birçok taşıma senaryosu engeli kaldırın.

Projenizde, .NET Framework gibi hedefleyen NuGet paketlerini başvurduğunuzda [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), bir paket geri dönüş uyarı alırsınız ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) aşağıdaki örneğe benzer:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Bu uyarı, paket eklediğinizde ve emin olmak için oluşturduğunuz her zaman bu paket projenizle test görüntülenir. Projenizi beklendiği gibi çalışıp çalışmadığını Visual Studio'da paket özelliklerini düzenleyerek veya sık kullandığınız kod proje dosyasında el ile düzenleme, uyarı gösterilmemesini sağlayabilirsiniz.

Proje dosyasını düzenleyerek uyarıyı bastırmak için bulma `PackageReference` giriş paketi için uyarıyı engellemek ve istediğiniz ekleme `NoWarn` özniteliği. `NoWarn` Özniteliği tüm uyarı kimliklerinin virgülle ayrılmış listesini kabul eder. Aşağıdaki örnek, gizlemek gösterilmektedir `NU1701` için uyarı `Huitian.PowerCollections` el ile proje dosyasını düzenleyerek paket:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Visual Studio'da Derleyici uyarılarını gizleme hakkında daha fazla bilgi için bkz: [NuGet paketleri için uyarıları gizleme](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>.NET Core üzerinde NuGet paket bağımlılık çalıştırmaz ne yapılacağını

.NET Core üzerinde bağımlı bir NuGet paketi çalışmazsa yapabileceğiniz birkaç şey vardır:

1. Proje açık kaynaklıdır ve GitHub gibi herhangi bir yerde barındırılan, geliştiricilerin doğrudan bağlantı kurabilirsiniz.
2. Doğrudan üzerinde Yazar başvurabilirsiniz [nuget.org](https://www.nuget.org/). Paketini arayın ve'ı tıklatın **kişi sahipleri** paketin sayfasının sol taraftaki.
3. Kullanmakta olduğunuz paket aynı görevi gerçekleştirir .NET Core üzerinde çalışan başka bir paket için arama yapabilirsiniz.
4. Paket kendiniz yapmakta olduğu kod yazma girişiminde bulunabilir.
5. Uygulamanızın işlevselliğini en az değiştirerek paket bağımlılığını ortadan kaldırabileceğiniz paket uyumlu bir sürümünün kullanılabilir olana kadar.

Açık kaynaklı proje maintainers ve NuGet paket yayımlayanlar genellikle gönüllüler olduğunu unutmayın. Çünkü bunlar belirli bir etki alanı hakkında dikkat edin, ücretsiz yapın ve genellikle farklı bir gündüz saatlerinde kullanılan iş sahip, katkıda bulunur. Bu nedenle bunları sormak için .NET Core desteği ile iletişim kurarken, oluşturduğunu unutmayın.

Yukarıdakilerden herhangi biri ile sorunu çözemezseniz, .NET Core için bağlantı noktası daha sonraki bir tarihte zorunda kalabilirsiniz.

.NET ekibi hangi kitaplıkların .NET Core ile desteklemek en önemli olduğunu bilmek istiyorsunuz. Bir e-posta gönderebilir dotnet@microsoft.com kullanmak istediğiniz kitaplıkları hakkında.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>NuGet paketlerini olmayan bağımlılıkları analiz edin

Dosya sistemindeki bir DLL gibi bir NuGet paketi olmayan bağımlılığa sahip. Bu bağımlılık taşınabilirliğinin belirlemek için tek yol [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) aracı. Araç, .NET Framework'ü hedefleyen derlemeler analiz edin ve .NET Core gibi diğer .NET platformları için taşınabilir olmayan API'leri tanımlayın. Aracı veya konsol uygulaması olarak çalıştırabilirsiniz bir [Visual Studio Uzantısı](../../standard/analyzers/portability-analyzer.md).

## <a name="next-steps"></a>Sonraki adımlar

Bir kitaplığı taşıma, kullanıma [Kitaplıklarınızı taşıma](libraries.md).
