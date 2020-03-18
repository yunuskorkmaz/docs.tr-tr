---
title: Bağlantı noktası koduna olan bağımlılıkları .NET Core'a çözümleme
description: Projenizi .NET Framework'den .NET Core'a taşımak için dış bağımlılıkları nasıl analiz edebilirsiniz öğrenin.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 2aa09e551a99358d3a6961fafcfc0aa8dbd976b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398967"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>Bağlantı noktası koduna olan bağımlılıklarınızı .NET Core olarak analiz edin

Kodunuzu .NET Core veya .NET Standard'a taşımanız için bağımlılıklarınızı anlamanız gerekir. Dışa bağımlılıklar, projenizde `.dll` başvuruladığınız ancak kendi oluşturduğunuz NuGet paketleri veya dosyalarıdır.

## <a name="migrate-your-nuget-packages-to-packagereference"></a>NuGet paketlerinizi`PackageReference`

.NET Core paket bağımlılıklarını belirtmek için [PackageReference'ı](/nuget/consume-packages/package-references-in-project-files) kullanır. Projenizde paketlerinizi belirtmek için [packages.config](/nuget/reference/packages-config) kullanıyorsanız, .NET `PackageReference` Core'da `packages.config` desteklenmediği için paketi biçime dönüştürün.

Nasıl geçirilmeyi öğrenmek [için, packages.config'den PackageReference makalesine geçiş makalesine](/nuget/reference/migrate-packages-config-to-package-reference) bakın.

## <a name="upgrade-your-nuget-packages"></a>NuGet paketlerinizi yükseltin

Projenizi `PackageReference` biçime geçirdikten sonra, paketlerinizin .NET Core ile uyumlu olup olmadığını doğrulayın.

İlk olarak, paketlerinizi en son sürüme yükseltin. Bu Visual Studio NuGet Paket Yöneticisi UI ile yapılabilir. Paket bağımlılıklarınızın yeni sürümlerinin .NET Core ile zaten uyumlu olması olasıdır.

## <a name="analyze-your-package-dependencies"></a>Paket bağımlılıklarınızı analiz edin

Dönüştürülmüş ve yükseltilmiş paket bağımlılıklarınızın .NET Core'da çalıştığını henüz doğrulamadıysanız, bunu başarmanın birkaç yolu vardır:

### <a name="analyze-nuget-packages-using-nugetorg"></a>nuget.org kullanarak NuGet paketlerini analiz edin

Her paketin [nuget.org](https://www.nuget.org/) destekverdiği Hedef Çerçeve Monikers'ı (TFM'ler) paket sayfasının **Bağımlılıklar** bölümü altında görebilirsiniz.

Siteyi kullanmak uyumluluğu doğrulamak için daha kolay bir yöntem olsa da, **Bağımlılıklar** bilgileri tüm paketler için sitede kullanılamaz.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>NuGet Paket Gezgini'ni kullanarak NuGet paketlerini analiz edin

NuGet paketi, platforma özgü derlemeler içeren klasörler kümesidir. Paketin içinde uyumlu bir derleme içeren bir klasör olup olmadığını denetleyin.

NuGet paket klasörlerini incelemenin en kolay yolu [NuGet Paket Gezgini](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) aracını kullanmaktır. Yükledikten sonra klasör adlarını görmek için aşağıdaki adımları kullanın:

1. NuGet Paket Gezgini'ni açın.
2. **Çevrimiçi akıştan Paketi Aç'a**tıklayın.
3. Paketin adını arayın.
4. Arama sonuçlarından paket adını seçin ve **aç'ı**tıklatın.
5. Sağ taraftaki *lib* klasörünü genişletin ve klasör adlarını inceleyin.

Aşağıdaki desenlerden birini kullanarak adiçeren `netstandardX.Y` bir `netcoreappX.Y`klasör arayın: veya .

Bu değerler, [.NET Standard](../../standard/net-standard.md), .NET Core ve .NET Core ile uyumlu geleneksel Taşınabilir Sınıf Kitaplığı (PCL) profillerinin sürümlerini eşleyen [Hedef Çerçeve Monikers (TFM'ler)](../../standard/frameworks.md) dir.

> [!IMPORTANT]
> Bir paketin desteklediği TFM'lere bakarken, uyumlu olmakla birlikte ,NET Standard projeleri için değil, yalnızca .NET Core projeleri için olduğunu unutmayın. `netcoreapp*`
> Yalnızca diğer .NET Core uygulamaları tarafından tüketilebilen ve yalnızca hedef `netcoreapp*` alan ve tüketilebilen `netstandard*` bir kitaplık.

## <a name="net-framework-compatibility-mode"></a>.NET Framework uyumluluk modu

NuGet paketlerini analiz ettikten sonra, yalnızca .NET Framework'u hedeflediklerini görebilirsiniz.

.NET Standard 2.0 ile başlayarak .NET Framework uyumluluk modu tanıtıldı. Bu uyumluluk modu .NET Standard ve .NET Core projelerinin .NET Framework kitaplıklarına başvurmasını sağlar. .NET Framework kitaplıklarına başvurmak, kitaplığın Windows Sunu Temeli (WPF) API'lerini kullanması gibi tüm projelerde çalışmaz, ancak birçok taşıma senaryosunun engelini kaldırmaz.

[Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections)gibi projenizde .NET Framework'ü hedefleyen NuGet paketlerine başvurulduğunızda, aşağıdaki örneğe benzer bir paket geri dönüş uyarısı[(NU1701)](/nuget/reference/errors-and-warnings/nu1701)alırsınız:

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Bu uyarı, paketi eklediğinizde ve bu paketi projenizle test ettiğinizden emin olmak için her oluşturduğunuzda görüntülenir. Projeniz beklendiği gibi çalışıyorsa, Visual Studio'daki paket özelliklerini düzenleyerek veya en sevdiğiniz kod düzenleyicisinde proje dosyasını el ile düzenleyerek bu uyarıyı bastırabilirsiniz.

Proje dosyasını düzenleyerek uyarıyı bastırmak `PackageReference` için, uyarıyı bastırmak istediğiniz paketin girişini `NoWarn` bulun ve özniteliği ekleyin. Öznitelik, `NoWarn` tüm uyarı işllerinin virgülle ayrılmışbir listesini kabul eder. Aşağıdaki örnek, proje dosyanızı el `Huitian.PowerCollections` ile düzenleyerek paket için uyarının `NU1701` nasıl bastırılabildiğini gösterir:

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Visual Studio'da derleyici uyarılarının nasıl bastırılanöğretilen hakkında daha fazla bilgi için [NuGet paketleri için bastırma uyarılarına](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages)bakın.

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>NuGet paket bağımlılığınız .NET Core'da çalışmadığında yapmanız gerekenler

Bağlı olduğunuz bir NuGet paketi .NET Core'da çalışmıyorsa yapabileceğiniz birkaç şey vardır:

- Proje açık kaynak kullanıyorsa ve GitHub gibi bir yerde barındırılırsa, geliştiricileri doğrudan etkileşime alabilirsiniz.
- [Nuget.org'da](https://www.nuget.org/)doğrudan yazarla iletişime geçebilirsiniz. Paketi arayın ve paketin sayfasının sol tarafındaki **İletişim Sahipleri'ni** tıklatın.
- .NET Core'da çalışan ve kullandığınız paketle aynı görevi yerine getiren başka bir paket arayabilirsiniz.
- Paketin kendi yaptığı kodu yazmayı deneyebilirsiniz.
- En azından paketin uyumlu bir sürümü kullanılabilir hale gelene kadar uygulamanızın işlevselliğini değiştirerek pakete olan bağımlılığı ortadan kaldırabilirsiniz.

Açık kaynak proje bakımcıları ve NuGet paket yayıncılarının genellikle gönüllü olduğunu unutmayın. Belirli bir etki alanını önemsedikleri, ücretsiz yaptıkları ve genellikle farklı bir gündüz işlerine sahip oldukları için katkıda bulunurlar. .NET Core desteği istemek için onlarla iletişime geçerken buna dikkat edin.

Sorununuzu bu seçeneklerden herhangi biriyle çözemezseniz, daha sonraki bir tarihte .NET Core bağlantı noktasına bağlantı da eklemeniz gerekebilir.

.NET Ekibi,.NET Core ile hangi kitaplıkların en önemli olduğunu bilmek ister. Kullanmak istediğiniz kitaplıklar dotnet@microsoft.com hakkında e-posta gönderebilirsiniz.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>NuGet paketleri olmayan bağımlılıkları çözümleme

Dosya sistemindeki DLL gibi NuGet paketi olmayan bir bağımlılığınız olabilir. Bu bağımlılığın taşınabilirliğini belirlemenin tek yolu [.NET Taşınabilirlik Çözümleyiciaracını](https://github.com/Microsoft/dotnet-apiport) çalıştırmaktır. Araç, .NET Framework'u hedefleyen derlemeleri analiz eder ve .NET Core gibi diğer .NET platformlarına taşınabilir olmayan API'leri tanımlar. Aracı konsol uygulaması olarak veya Visual [Studio uzantısı](../../standard/analyzers/portability-analyzer.md)olarak çalıştırabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

>[!div class="nextstepaction"]
>[Taşıma kitaplıkları](libraries.md)
