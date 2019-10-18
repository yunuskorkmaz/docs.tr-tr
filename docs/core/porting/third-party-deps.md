---
title: .NET Core 'a bağlantı noktası kodu bağımlılıklarını çözümleyin
description: Projenizin .NET Framework .NET Core 'a bağlantı noktası olması için dış bağımlılıkları çözümlemeyi öğrenin.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 36d1c1d2090a0fb9e6f48fe519d15897579df2d5
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72521477"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>.NET Core 'a bağlantı noktası kodu için bağımlılıklarınızı çözümleyin

Kodunuzun .NET Core veya .NET Standard bağlantı noktası olması için bağımlılıklarınızı anlamanız gerekir. Dış bağımlılıklar, projenizde başvurduğunuz, ancak derlemeniz gereken [NuGet paketlerdir](#analyze-referenced-nuget-packages-in-your-projects) veya [DLL 'lardır](#analyze-dependencies-that-arent-nuget-packages) . Her bağımlılığı değerlendirin ve .NET Core ile uyumlu olmayan bir yedek plan geliştirin. Bir bağımlılığın .NET Core ile uyumlu olup olmadığını belirleme hakkında daha fazla bilgiyi burada bulabilirsiniz.

## <a name="analyze-referenced-nuget-packages-in-your-projects"></a>Projelerinizde başvurulan NuGet paketlerini çözümleyin

Projenizde NuGet paketlerine başvursanız, .NET Core ile uyumlu olup olmadığını doğrulamanız gerekir.
Bunu yapmanın iki yolu vardır:

- [NuGet Paket Gezgini uygulamasını kullanma](#analyze-nuget-packages-using-nuget-package-explorer)
- [Nuget.org sitesini kullanma](#analyze-nuget-packages-using-nugetorg)

Paketler çözümlendikten sonra, .NET Core ile uyumlu olmadıkları ve yalnızca hedef .NET Framework, [.NET Framework uyumluluk modunun](#net-framework-compatibility-mode) taşıma süreciyle ilgili olup olmadığını kontrol edebilirsiniz.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>NuGet paket gezginini kullanarak NuGet paketlerini çözümleme

Bir NuGet paketi, platforma özgü derlemeler içeren bir klasörler kümesidir. Bu nedenle, paketin içinde uyumlu bir derlemeyi içeren bir klasör olup olmadığını denetlemeniz gerekir.

NuGet paket klasörlerini incelemeyi en kolay yolu, [NuGet Paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aracını kullanmaktır. Yükledikten sonra klasör adlarını görmek için aşağıdaki adımları kullanın:

1. NuGet paket Gezginini açın.
2. **Çevrimiçi akıştan paketi aç**' a tıklayın.
3. Paketin adını arayın.
4. Arama sonuçlarından paket adı ' nı seçin ve **Aç**' a tıklayın.
5. Sağ taraftaki *LIB* klasörünü genişletin ve klasör adlarına bakın.

Aşağıdaki adlardan birini içeren bir klasör arayın:

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
netcoreapp2.2
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

Bu değerler, .NET Core ile uyumlu [.NET Standard](../../standard/net-standard.md), .NET Core ve geleneksel taşınabilir sınıf KITAPLıĞı (PCL) profillerinin sürümleriyle eşlenen [hedef çerçeve takma adları (tfms)](../../standard/frameworks.md) .

> [!IMPORTANT]
> Bir paketin desteklediği TFMs 'e baktığınızda, `netcoreapp*`, uyumlu iken yalnızca .NET Core projeleri için olduğunu ve .NET Standard projelerine yönelik olduğunu unutmayın.
> Yalnızca `netcoreapp*` ve `netstandard*` hedefleyen bir kitaplık yalnızca diğer .NET Core uygulamaları tarafından tüketilebilir.

### <a name="analyze-nuget-packages-using-nugetorg"></a>Nuget.org kullanarak NuGet paketlerini çözümleme

Alternatif olarak, paket sayfasındaki **Bağımlılıklar** bölümünde her bir paketin [NuGet.org](https://www.nuget.org/) üzerinde desteklediği tfms 'yi görebilirsiniz.

Siteyi kullanmak uyumluluğu doğrulamak için daha kolay bir yöntem olsa da, tüm paketler için sitede **Bağımlılıklar** bilgisi yok.

### <a name="net-framework-compatibility-mode"></a>Uyumluluk modu .NET Framework

NuGet paketlerini analiz ettikten sonra, çoğu NuGet paketi olduğu için yalnızca .NET Framework hedeflemesini sağlayabilirsiniz.

.NET Standard 2,0 ' den başlayarak .NET Framework uyumluluk modu sunuldu. Bu uyumluluk modu, .NET Standard ve .NET Core projelerinin .NET Framework kitaplıklarına başvurmasına olanak tanır. .NET Framework kütüphaneleri, kitaplığın Windows Presentation Foundation (WPF) API 'Leri kullanması gibi tüm projeler için çalışmaz, ancak birçok taşıma senaryosunun engellemesini kaldırabilir.

Projenizde, [Kuban. PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections)gibi .NET Framework hedefleyen NuGet paketlerine başvurduğunuzda, aşağıdaki örneğe benzer bir paket geri dönüş Uyarısı ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) alırsınız:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Bu uyarı, paketi eklediğinizde ve bu paketi projenizle test ettiğinizden emin olmak için her oluşturduğunuzda görüntülenir. Projeniz beklendiği gibi çalışıyorsa, Visual Studio 'da paket özelliklerini düzenleyerek veya en sevdiğiniz kod düzenleyicinizdeki proje dosyasını el ile düzenleyerek söz konusu uyarıyı gizleyebilirsiniz.

Proje dosyasını düzenleyerek uyarıyı bastırmak için, uyarıyı bastırmak istediğiniz paketin `PackageReference` girdisini bulun ve `NoWarn` özniteliğini ekleyin. @No__t_0 öznitelik, tüm uyarı kimliklerinin virgülle ayrılmış bir listesini kabul eder. Aşağıdaki örnek, proje dosyanızı el ile düzenleyerek `Huitian.PowerCollections` paketi için `NU1701` uyarısının nasıl bastıralınacağını gösterir:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Visual Studio 'da derleyici uyarılarını gösterme hakkında daha fazla bilgi için bkz. [NuGet paketleri uyarılarını gizleme](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).

## <a name="port-your-packages-to-packagereference"></a>Paketlerinizin `PackageReference` için bağlantı noktası

.NET Core, paket bağımlılıklarını belirtmek için [Packagereference](/nuget/consume-packages/package-references-in-project-files) kullanır. Paketlerinizi belirtmek için [Packages. config](/nuget/reference/packages-config) kullanıyorsanız, `PackageReference` ' ye dönüştürmeniz gerekir.

[Packages. config biçiminden PackageReference 'A geçiş](/nuget/reference/migrate-packages-config-to-package-reference)sırasında daha fazla bilgi edinebilirsiniz.

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>NuGet paket bağımlılığının .NET Core üzerinde çalıştırılmadıkça yapmanız gerekenler

Bağlı olduğunuz bir NuGet paketi .NET Core üzerinde çalıştırılmazsa, yapabileceğiniz birkaç şey vardır:

1. Proje açık kaynaktır ve GitHub gibi bir yerde barındırılıyorsa, geliştiricilerle doğrudan etkileşim sağlayabilirsiniz.
2. Yazarla doğrudan [NuGet.org](https://www.nuget.org/)üzerinde iletişim kurabilmeniz gerekir. Paketi arayın ve paketin sayfasının sol tarafındaki **kişi sahipleri** ' na tıklayın.
3. Kullandığınız paketle aynı görevi gerçekleştiren .NET Core üzerinde çalışan başka bir paket arayabilirsiniz.
4. Paketin kendi yaptığına yaptığı kodu yazmayı deneyebilirsiniz.
5. En azından paketin uyumlu bir sürümü kullanılabilir hale gelene kadar, uygulamanızın işlevselliğini değiştirerek paketteki bağımlılığı ortadan kaldırabilirsiniz.

Açık kaynaklı proje bakım ve NuGet paket yayımcılarının genellikle gönüllü teers olduğunu unutmayın. Bunlar, belirli bir etki alanı hakkında ilgilendiğinden, ücretsiz olarak yaptığı ve genellikle farklı bir Daytime işi olan için katkıda bulunur. Bu nedenle, .NET Core desteği istemek için onlara başvururken bu, en az bir anlayış olmalıdır.

Yukarıdaki sorunları giderebiliyorsanız, daha sonraki bir tarihte .NET Core 'a bağlantı noktası yazmanız gerekebilir.

.NET ekibi, .NET Core ile desteklemek için hangi kitaplıkların en önemli olduğunu bilmesini istiyor. Kullanmak istediğiniz kitaplıklar hakkında dotnet@microsoft.com bir e-posta gönderebilirsiniz.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>NuGet paketleri olmayan bağımlılıkları analiz etme

Dosya sistemindeki DLL gibi bir NuGet paketi olmayan bir bağımlılığa sahip olabilirsiniz. Bu bağımlılığın taşınabilirliği belirlemenin tek yolu [.net taşınabilirlik Çözümleyicisi](https://github.com/Microsoft/dotnet-apiport) aracını çalıştırmak içindir. Araç, .NET Framework hedef olan derlemeleri çözümleyebilir ve .NET Core gibi diğer .NET platformlarına taşınmayan API 'Leri tanımlayabilir. Aracı bir konsol uygulaması veya [Visual Studio uzantısı](../../standard/analyzers/portability-analyzer.md)olarak çalıştırabilirsiniz.

>[!div class="step-by-step"]
>[Next](libraries.md)
