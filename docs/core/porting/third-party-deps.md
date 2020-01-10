---
title: .NET Core 'a bağlantı noktası kodu bağımlılıklarını çözümleyin
description: Projenizin .NET Framework .NET Core 'a bağlantı noktası olması için dış bağımlılıkları çözümlemeyi öğrenin.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 2aa09e551a99358d3a6961fafcfc0aa8dbd976b1
ms.sourcegitcommit: cbdc0f4fd39172b5191a35200c33d5030774463c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75777260"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>.NET Core 'a bağlantı noktası kodu için bağımlılıklarınızı çözümleyin

Kodunuzun .NET Core veya .NET Standard bağlantı noktası olması için bağımlılıklarınızı anlamanız gerekir. Dış bağımlılıklar, projenizde başvurduğunuz, ancak sizin oluşturmayan NuGet paketlerdir veya dosyaları `.dll`.

## <a name="migrate-your-nuget-packages-to-packagereference"></a>NuGet paketlerinizi `PackageReference` 'e geçirin

.NET Core, paket bağımlılıklarını belirtmek için [Packagereference](/nuget/consume-packages/package-references-in-project-files) kullanır. Kuruluşunuzda paketlerinizi belirtmek için [Packages. config](/nuget/reference/packages-config) kullanıyorsanız, `packages.config` .NET Core 'da desteklenmediğinden `PackageReference` biçimine dönüştürün.

Nasıl geçiş yapılacağını öğrenmek için, [Packages. config 'Ten PackageReference 'A geçiş](/nuget/reference/migrate-packages-config-to-package-reference) konusuna bakın.

## <a name="upgrade-your-nuget-packages"></a>NuGet paketlerinizi yükseltin

Projenizi `PackageReference` biçimine geçirdikten sonra, paketlerinizin .NET Core ile uyumlu olduğunu doğrulayın.

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

Şu desenleri kullanarak adlara sahip bir klasör arayın: `netstandardX.Y` veya `netcoreappX.Y`.

Bu değerler, .NET Core ile uyumlu [.NET Standard](../../standard/net-standard.md), .NET Core ve geleneksel taşınabilir sınıf KITAPLıĞı (PCL) profillerinin sürümleriyle eşlenen [hedef çerçeve takma adları (tfms)](../../standard/frameworks.md) .

> [!IMPORTANT]
> Bir paketin desteklediği TFMs 'e baktığınızda, `netcoreapp*`, uyumlu iken yalnızca .NET Core projeleri için olduğunu ve .NET Standard projelerine yönelik olduğunu unutmayın.
> Yalnızca `netcoreapp*` ve `netstandard*` hedefleyen bir kitaplık yalnızca diğer .NET Core uygulamaları tarafından tüketilebilir.

## <a name="net-framework-compatibility-mode"></a>Uyumluluk modu .NET Framework

NuGet paketlerini analiz ettikten sonra yalnızca .NET Framework hedeflemesini sağlayabilirsiniz.

.NET Standard 2,0 ' den başlayarak .NET Framework uyumluluk modu sunuldu. Bu uyumluluk modu, .NET Standard ve .NET Core projelerinin .NET Framework kitaplıklarına başvurmasına olanak tanır. .NET Framework kütüphaneleri, kitaplığın Windows Presentation Foundation (WPF) API 'Leri kullanması gibi tüm projeler için çalışmaz, ancak birçok taşıma senaryosunun engellemesini kaldırabilir.

Projenizde, [Kuban. PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections)gibi .NET Framework hedef olan NuGet paketlerine başvuruldığınızda, aşağıdaki örneğe benzer bir paket geri dönüş Uyarısı ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) alırsınız:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Bu uyarı, paketi eklediğinizde ve bu paketi projenizle test ettiğinizden emin olmak için her oluşturduğunuzda görüntülenir. Projeniz beklendiği gibi çalışıyorsa, Visual Studio 'da paket özelliklerini düzenleyerek veya proje dosyasını sık kullandığınız kod Düzenleyicinizde el ile düzenleyerek bu uyarıyı bastırın.

Proje dosyasını düzenleyerek uyarıyı bastırmak için, uyarıyı bastırmak istediğiniz paketin `PackageReference` girdisini bulun ve `NoWarn` özniteliğini ekleyin. `NoWarn` öznitelik, tüm uyarı kimliklerinin virgülle ayrılmış bir listesini kabul eder. Aşağıdaki örnek, proje dosyanızı el ile düzenleyerek `Huitian.PowerCollections` paketi için `NU1701` uyarısının nasıl bastıralınacağını gösterir:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Visual Studio 'da derleyici uyarılarını gösterme hakkında daha fazla bilgi için bkz. [NuGet paketleri uyarılarını gizleme](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>NuGet paket bağımlılığının .NET Core üzerinde çalıştırılmadıkça yapmanız gerekenler

Bağlı olduğunuz bir NuGet paketi .NET Core üzerinde çalıştırılmazsa, yapabileceğiniz birkaç şey vardır:

- Proje açık kaynaktır ve GitHub gibi bir yerde barındırılıyorsa, geliştiricilerle doğrudan etkileşim sağlayabilirsiniz.
- Yazarla doğrudan [NuGet.org](https://www.nuget.org/)üzerinde iletişim kurabilmeniz gerekir. Paketi arayın ve paketin sayfasının sol tarafındaki **kişi sahipleri** ' na tıklayın.
- Kullandığınız paketle aynı görevi gerçekleştiren .NET Core üzerinde çalışan başka bir paket arayabilirsiniz.
- Paketin kendi yaptığına yaptığı kodu yazmayı deneyebilirsiniz.
- En azından paketin uyumlu bir sürümü kullanılabilir hale gelene kadar, uygulamanızın işlevselliğini değiştirerek paketteki bağımlılığı ortadan kaldırabilirsiniz.

Açık kaynaklı proje bakım ve NuGet paket yayımcılarının genellikle gönüllü teers olduğunu unutmayın. Bunlar, belirli bir etki alanı hakkında ilgilendiğinden, ücretsiz olarak yaptığı ve genellikle farklı bir Daytime işi olan için katkıda bulunur. .NET Core desteği istemek için onlarla iletişim kurarken bu kişiden emin olun.

Sorununuzu bu seçeneklerden herhangi biriyle gideremezseniz, daha sonraki bir tarihte .NET Core 'a bağlantı noktası oluşturmanız gerekebilir.

.NET ekibi, .NET Core ile desteklemek için hangi kitaplıkların en önemli olduğunu bilmesini istiyor. Kullanmak istediğiniz kitaplıklar hakkında dotnet@microsoft.com bir e-posta gönderebilirsiniz.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>NuGet paketleri olmayan bağımlılıkları analiz etme

Dosya sistemindeki DLL gibi bir NuGet paketi olmayan bir bağımlılığa sahip olabilirsiniz. Bu bağımlılığın taşınabilirliği belirlemenin tek yolu [.net taşınabilirlik Çözümleyicisi](https://github.com/Microsoft/dotnet-apiport) aracını çalıştırmak içindir. Araç, .NET Framework hedef olan derlemeleri analiz eder ve .NET Core gibi diğer .NET platformlarına taşınabilir olan API 'Leri tanımlar. Aracı bir konsol uygulaması veya [Visual Studio uzantısı](../../standard/analyzers/portability-analyzer.md)olarak çalıştırabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

>[!div class="nextstepaction"]
>[Bağlantı noktası kitaplıkları](libraries.md)
