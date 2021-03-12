---
title: Bağlantı noktası koduna bağımlılıkları çözümle
description: Projenizin .NET Framework ile .NET arasında bağlantı noktası için dış bağımlılıkları çözümlemeyi öğrenin.
author: cartermp
ms.date: 03/04/2021
ms.openlocfilehash: 4619243cf300e248be45e4b2a4d5541c3b3e1cb5
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604924"
---
# <a name="analyze-your-dependencies-to-port-code-from-net-framework-to-net"></a>.NET Framework 'ten .NET 'e bağlantı noktası kodu için bağımlılıklarınızı çözümleyin

Kodunuzun .NET veya .NET Standard bağlantı noktası olması için bağımlılıklarınızı anlamanız gerekir. Dış bağımlılıklar, `.dll` projenizde başvurduğunuz, ancak sizin oluşturmayan NuGet paketlerdir veya dosyalardır.

Kodunuzun .NET Standard 2,0 veya altına eklenmesi, hem .NET Framework hem de .NET ile kullanılmasını sağlar. Ancak, kitaplığı .NET Framework ile kullanmanız gerekmiyorsa, .NET 'in en son sürümünü belirlemeyi göz önünde bulundurun.

## <a name="migrate-your-nuget-packages-to-packagereference"></a>NuGet paketlerinizi geçirin `PackageReference`

.NET, NuGet başvuruları için [_packages.config_](/nuget/reference/packages-config) dosyasını kullanamıyor. Hem .NET hem de .NET Framework, paket bağımlılıklarını belirtmek için [Packagereference](/nuget/consume-packages/package-references-in-project-files) kullanabilir. Kuruluşunuzda paketlerinizi belirtmek için _packages.config_ kullanıyorsanız, bunu `PackageReference` biçimine dönüştürün.

Nasıl geçiş yapılacağını öğrenmek için [packages.config ' den PackageReference 'A geçiş](/nuget/reference/migrate-packages-config-to-package-reference) makalesine bakın.

## <a name="upgrade-your-nuget-packages"></a>NuGet paketlerinizi yükseltin

Projenizi biçimine geçirdikten sonra `PackageReference` , paketlerinizin .NET ile uyumlu olduğunu doğrulayın.

İlk olarak, paketlerinizi kullanabileceğiniz en son sürüme yükseltin. Bu, Visual Studio 'daki NuGet Paket Yöneticisi Kullanıcı arabirimi ile yapılabilir. Paket bağımlılıklarınızın daha yeni sürümleri zaten .NET Core ile uyumlu olabilir.

## <a name="analyze-your-package-dependencies"></a>Paket bağımlılıklarınızı çözümleyin

Dönüştürülen ve yükseltilen paket bağımlılıklarınızın .NET Core 'da çalıştığını henüz doğrulamadıysanız, bunu elde etmeniz için birkaç yol vardır:

### <a name="analyze-nuget-packages-using-nugetorg"></a>Nuget.org kullanarak NuGet paketlerini çözümleme

Her bir paketin [NuGet.org](https://www.nuget.org/) üzerinde desteklediği hedef çerçeve takma adlarını (tfms), paket sayfasının **Bağımlılıklar** bölümünde görebilirsiniz.

Siteyi kullanmak uyumluluğu doğrulamak için daha kolay bir yöntem olsa da, tüm paketler için sitede **Bağımlılıklar** bilgisi yok.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>NuGet paket gezginini kullanarak NuGet paketlerini çözümleme

Bir NuGet paketi, platforma özgü derlemeler içeren bir klasörler kümesidir. Paketin içinde uyumlu bir bütünleştirilmiş kod içeren bir klasör olup olmadığını denetleyin.

NuGet paket klasörlerini incelemeyi en kolay yolu, [NuGet Paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aracını kullanmaktır. Yükledikten sonra klasör adlarını görmek için aşağıdaki adımları kullanın:

1. NuGet paket Gezginini açın.
2. **Çevrimiçi akıştan paketi aç**' a tıklayın.
3. Paketin adını arayın.
4. Arama sonuçlarından paket adı ' nı seçin ve **Aç**' a tıklayın.
5. Sağ taraftaki *LIB* klasörünü genişletin ve klasör adlarına bakın.

Aşağıdaki desenleri kullanarak adlara sahip bir klasör arayın: `netstandardX.Y` , `netX.Y` veya `netcoreappX.Y` .

Bu değerler, .NET ile uyumlu olan [.NET Standard](../../standard/net-standard.md), .NET ve .NET Core sürümleriyle eşleyen [hedef çerçeve takma adları (tfms)](../../standard/frameworks.md) .

> [!IMPORTANT]
> Bir paketin desteklediği TFMs 'e baktığınızda, .net `netstandard*` 5, .NET Core veya .NET Framework gibi belirli bir .NET uygulamasını hedeflemeden başka BIR TFM 'nin olduğunu unutmayın. .NET 5 ' den itibaren `net*` TFI (bir işletim sistemi ataması olmadan) etkin bir şekilde `netstandard*` [Taşınabilir hedef](../../standard/net-standard.md#net-5-and-net-standard)olarak değiştirilir. Örneğin, `net5.0` .NET 5 API yüzeyini hedefler ve platformlar arası kullanımı kolay, ancak `net5.0-windows` Windows işletim sisteminde uygulanan .NET 5 API yüzeyini hedefler.

## <a name="net-framework-compatibility-mode"></a>Uyumluluk modu .NET Framework

NuGet paketlerini analiz ettikten sonra yalnızca .NET Framework hedeflemesini sağlayabilirsiniz.

.NET Standard 2,0 ' den başlayarak .NET Framework uyumluluk modu sunuldu. Bu uyumluluk modu, .NET Standard ve .NET Core projelerinin .NET Framework kitaplıklarına başvurmasına olanak tanır. .NET Framework kütüphaneleri, kitaplığın Windows Presentation Foundation (WPF) API 'Leri kullanması gibi tüm projeler için çalışmaz, ancak birçok taşıma senaryosunun engellemesini kaldırabilir.

Projenizde .NET Framework hedef olan NuGet paketlerine başvurduğunuzda, örneğin [`Huitian.PowerCollections`](https://www.nuget.org/packages/Huitian.PowerCollections) , aşağıdaki örneğe benzer bir paket geri dönüş Uyarısı ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) alırsınız:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Bu uyarı, paketi eklediğinizde ve bu paketi projenizle test ettiğinizden emin olmak için her oluşturduğunuzda görüntülenir. Projeniz beklendiği gibi çalışıyorsa, Visual Studio 'da paket özelliklerini düzenleyerek veya proje dosyasını sık kullandığınız kod Düzenleyicinizde el ile düzenleyerek bu uyarıyı bastırın.

Proje dosyasını düzenleyerek uyarıyı bastırmak için, `PackageReference` uyarıyı bastırmak istediğiniz paketin girdisini bulun ve `NoWarn` özniteliği ekleyin. `NoWarn`Öznitelik, tüm uyarı kimliklerinin virgülle ayrılmış bir listesini kabul eder. Aşağıdaki örnek, `NU1701` `Huitian.PowerCollections` proje dosyanızı el ile düzenleyerek paket için uyarının nasıl bastıralınacağını gösterir:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Visual Studio 'da derleyici uyarılarını gösterme hakkında daha fazla bilgi için bkz. [NuGet paketleri uyarılarını gizleme](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).

## <a name="if-nuget-packages-wont-run-on-net"></a>NuGet paketleri .NET üzerinde çalıştırılmayacaksa

Bağlı olduğunuz bir NuGet paketi .NET Core üzerinde çalıştırılmazsa, yapabileceğiniz birkaç şey vardır:

- Proje açık kaynaktır ve GitHub gibi bir yerde barındırılıyorsa, geliştiricilerle doğrudan etkileşim sağlayabilirsiniz.
- Yazarla doğrudan [NuGet.org](https://www.nuget.org/)üzerinde iletişim kurabilmeniz gerekir. Paketi arayın ve paketin sayfasının sol tarafındaki **kişi sahipleri** ' na tıklayın.
- Kullandığınız paketle aynı görevi gerçekleştiren .NET Core üzerinde çalışan başka bir paket arayabilirsiniz.
- Paketin kendi yaptığına yaptığı kodu yazmayı deneyebilirsiniz.
- En azından paketin uyumlu bir sürümü kullanılabilir hale gelene kadar, uygulamanızın işlevselliğini değiştirerek paketteki bağımlılığı ortadan kaldırabilirsiniz.

Açık kaynaklı proje bakım ve NuGet paket yayımcılarının genellikle gönüllü teers olduğunu unutmayın. Bunlar, belirli bir etki alanı hakkında ilgilendiğinden, ücretsiz olarak yaptığı ve genellikle farklı bir Daytime işi olan için katkıda bulunur. .NET Core desteği istemek için onlarla iletişim kurarken bu kişiden emin olun.

Sorununuzu bu seçeneklerden herhangi biriyle gideremezseniz, daha sonraki bir tarihte .NET Core 'a bağlantı noktası oluşturmanız gerekebilir.

.NET ekibi, .NET Core ile desteklemek için hangi kitaplıkların en önemli olduğunu bilmesini istiyor. Kullanmak istediğiniz kitaplıklar hakkında bir e-posta gönderebilirsiniz dotnet@microsoft.com .

## <a name="analyze-non-nuget-dependencies"></a>NuGet olmayan bağımlılıkları çözümle

Dosya sistemindeki DLL gibi bir NuGet paketi olmayan bir bağımlılığa sahip olabilirsiniz. Bu bağımlılığın taşınabilirliği belirlemenin tek yolu [.net taşınabilirlik Çözümleyicisi](https://github.com/Microsoft/dotnet-apiport) aracını çalıştırmak içindir. Araç, .NET Framework hedef olan derlemeleri analiz eder ve .NET Core gibi diğer .NET platformlarına taşınabilir olan API 'Leri tanımlar. Aracı bir konsol uygulaması veya [Visual Studio uzantısı](../../standard/analyzers/portability-analyzer.md)olarak çalıştırabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [.NET Framework .NET 'a taşıma hakkında genel bakış](index.md)
- [Taşıma kitaplıkları](libraries.md)
