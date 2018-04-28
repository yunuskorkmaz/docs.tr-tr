---
title: Bağlantı noktası oluşturma, üçüncü taraf bağımlılıkları için .NET Core - Çözümle
description: .NET Framework projenizden .NET Core için bağlantı noktası için üçüncü taraf bağımlılıkları çözümlemeyi öğrenin.
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.workload:
- dotnetcore
ms.openlocfilehash: be8d5a60977c7863136a1661a60e3bf23c0eb93e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="analyze-your-third-party-dependencies"></a>Üçüncü taraf bağımlılıkları analiz

Kodunuzu .NET Core veya .NET standart bağlantı noktasına arıyorsanız, taşıma işleminin ilk adımında, üçüncü taraf bağımlılıkları anlamaktır. Üçüncü taraf bağımlılıklarıdır ya da [NuGet paketlerini](#analyze-referenced-nuget-packages-on-your-project) veya [DLL'leri](#analyze-dependencies-that-arent-nuget-packages) projenizde başvuran. Her bir bağımlılığın değerlendirin ve .NET Core ile uyumlu değil bağımlılıklar için yedek bir plan geliştirin. Bu makalede bağımlılık .NET Core ile uyumlu olup olmadığını belirleme gösterilmektedir.

## <a name="analyze-referenced-nuget-packages-in-your-project"></a>Projenizdeki başvurulan NuGet paketleri analiz

Projenizdeki NuGet paketlerini başvuran, .NET Core ile uyumlu değilse doğrulamanız gerekir.
Bunu yapmaya yönelik iki yolu vardır:

* [NuGet paketi Gezgini uygulamasını kullanarak](#analyze-nuget-packages-using-nuget-package-explorer) (en güvenilir yöntemi).
* [Nuget.org site kullanarak](#analyze-nuget-packages-using-nugetorg).

.NET Core ve yalnızca hedef .NET Framework ile uyumlu değillerse paketlerini çözümledikten sonra varsa göz atabilirsiniz [.NET Framework uyumluluk modu](#net-framework-compatibility-mode) taşıma işlemine yardımcı olabilir.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>NuGet paket Gezgini'ni kullanarak NuGet paketleri analiz

Bir NuGet paketi kendisini platforma özgü derlemeleri içeren klasörleri kümesidir. Bu nedenle paketin içindeki uyumlu bir derleme içeren bir klasör olup olmadığını denetlemek gerekir.

NuGet paketi klasörleri incelemek için en kolay yolu kullanmaktır [NuGet paketi Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aracı. Yükledikten sonra klasör adlarını görmek için aşağıdaki adımları kullanın:

1. NuGet paketi Explorer'ı açın.
2. Tıklatın **çevrimiçi akış açık paketinden**.
3. Paketin adını arayın.
4. Arama sonuçlarından paket adını seçin ve tıklatın **açmak**.
5. Genişletme *lib* klasörünü sağ taraftaki ve klasör adlarını bakın.

Aşağıdaki adlarının herhangi biri bir klasörle arayın:

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
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Bu değerler [hedef Framework adlar (TFMs)](../../standard/frameworks.md) sürümleri için eşleme [.NET standart](../../standard/net-standard.md), .NET Core ve .NET Core ile uyumlu olan geleneksel taşınabilir sınıf kitaplığı (PCL) profilleri.

> [!IMPORTANT]
> Bir paketi destekler TFMs bakarken unutmayın `netcoreapp*`, uyumlu çalışırken, yalnızca .NET çekirdeği projelerde ve .NET standart projeleri için değil.
> Yalnızca hedefleyen bir kitaplık `netcoreapp*` ve `netstandard*` yalnızca diğer .NET Core uygulamaları tarafından kullanılabilecek.

Uyumlu olabilir .NET Core yayın öncesi sürümlerini kullanılan bazı eski TFMs vardır:

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

Büyük olasılıkla bu TFMs kodunuzu ile çalışırken, uyumluluk garantisi yoktur. Bu TFMs paketlerle yayın öncesi .NET Core paketlerle oluşturulmuştur. Zaman (veya varsa) not edin bu TFMs kullanarak paketleri .NET standart temelli olacak şekilde güncelleştirilir.

> [!NOTE]
> Geleneksel PCL veya yayın öncesi .NET Core hedef hedefleme paketini kullanmak için kullanmanız gerekir `PackageTargetFallback` MSBuild proje dosyası öğesinde.
> Bu MSBuild öğe hakkında daha fazla bilgi için bkz: [ `PackageTargetFallback` ](../tools/csproj.md#packagetargetfallback).

### <a name="analyze-nuget-packages-using-nugetorg"></a>Nuget.org kullanarak NuGet paketleri analiz

Alternatif olarak, her paketi üzerinde destekler TFMs görebilirsiniz [nuget.org](https://www.nuget.org/) altında **bağımlılıkları** paket sayfasının bölümünde.

Site kullanarak uyumluluğunu doğrulamak için daha kolay bir yöntem olsa **bağımlılıkları** bilgi kullanılabilir değil tüm paketler için sitesinde.

### <a name="net-framework-compatibility-mode"></a>.NET framework uyumluluk modu

Çoğu NuGet paketleri gibi NuGet paketlerini çözümledikten sonra bunlar yalnızca .NET Framework hedefleyen bulabilirsiniz.

.NET standart 2.0 ile başlayarak, .NET Framework uyumluluk modu sunulmuştur. Bu uyumluluk modu, .NET Framework kitaplıkları başvurmak .NET standart ve .NET Core projeleri sağlar. .NET Framework kitaplıklarına başvuruda bulunan işe yaramazsa tüm projelerde gelmesi gibi kitaplık Windows Presentation Foundation (WPF) API'lerini kullanır, ancak çok sayıda taşıma senaryoları engellemeyi.

Projeniz .NET Framework gibi hedef NuGet paketlerini başvuru yaptığınızda [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), bir paket geri dönüş uyarı alın ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) aşağıdaki örneğe benzer:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Paketi ekleyin ve emin olmak için oluşturduğunuz her zaman projenizi ile paket test bu uyarı görüntülenir. Projenizi beklendiği gibi çalışıp çalışmadığını Visual Studio'da paket özelliklerini düzenleyerek veya el ile sık kullanılan kod düzenleyicisinde proje dosyasını düzenleyerek bu uyarı gizleyebilirsiniz.

Proje dosyasını düzenleyerek gizlemek için bulma `PackageReference` giriş paketi için istediğiniz için gizlemek ve eklemek `NoWarn` özniteliği. `NoWarn` Özniteliği tüm uyarı kimliklerinin virgülle ayrılmış listesini kabul eder. Aşağıdaki örnek, gizlemek gösterilmiştir `NU1701` için uyarı `Huitian.PowerCollections` proje dosyanızı el ile düzenleyerek paketi:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Visual Studio'da Derleyici uyarılarını gizleme hakkında daha fazla bilgi için bkz: [NuGet paketleri için uyarıları gizleme](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>NuGet paket bağımlılığı .NET Core üzerinde çalıştırdığınızda değil yapmanız gerekenler

.NET Core üzerinde bağımlı bir NuGet paketi çalışmazsa yapabileceğiniz birkaç şey vardır:

1. Proje açık bir kaynaktır ve Github'da gibi herhangi bir yerde barındırılan, geliştiricilerin doğrudan devreye.
2. Yazarın doğrudan üzerinde başvurabilirsiniz [nuget.org](https://www.nuget.org/). Arama için paketi ve tıklayın **kişi sahipleri** paketin sayfasının sol taraftaki.
3. Kullanmakta olduğunuz paket gibi aynı görevi gerçekleştirir .NET Core üzerinde çalışan başka bir paket için arama yapabilirsiniz.
4. Paket kendiniz yapmakta olduğu için kod yazma girişiminde bulunabilir.
5. En az işlevselliği, uygulamanızın değiştirerek paket bağımlılığını ortadan paket uyumlu bir sürümü kullanılabilir duruma gelinceye kadar.

Açık kaynaklı proje maintainers ve NuGet paketi yayıncıları genellikle gönüllüsü olduğunu unutmayın. Çünkü bunlar belirli bir etki alanı hakkında dikkat edin, ücretsiz yapın ve genellikle farklı daytime iş sahip oldukları katkıda. Böylece bunları .NET Core desteği sorulacak iletişim kurarken, oluşturduğunu unutmayın.

Yukarıdakilerden herhangi biri ile sorunu çözemezseniz, .NET Core bağlantı noktasına daha sonraki bir tarihte zorunda kalabilirsiniz.

.NET ekibi hangi kitaplıkları ile .NET Core desteklemek en önemli olan bilmek ister misiniz? E-posta gönderebilirsiniz dotnet@microsoft.com kullanmak istediğiniz kitaplıklar hakkında.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>NuGet paketlerini olmayan bağımlılıklarını Çözümle

Dosya sistemi DLL'de gibi bir NuGet paketi olmayan bir bağımlılık olabilir. Bu bağımlılık taşınabilirlik belirlemek için tek yolu çalıştırmaktır [.NET taşınabilirlik Çözümleyicisi](https://github.com/Microsoft/dotnet-apiport) aracı. Aracı, .NET Framework hedefleyen derlemeleri çözümlemek ve .NET Core gibi diğer .NET platformları için taşınabilir olmayan API'leri tanımlayın. Bir konsol uygulaması veya olarak aracını çalıştırabilirsiniz bir [Visual Studio Uzantısı](../../standard/analyzers/portability-analyzer.md).

## <a name="next-steps"></a>Sonraki adımlar

Kitaplığa bağlantı noktası oluşturma, kullanıma [Kitaplıklarınızı taşıma](libraries.md).
