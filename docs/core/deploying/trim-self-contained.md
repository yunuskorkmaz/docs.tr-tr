---
title: Kendi içindeki uygulamaları kırpma
description: Kendi boyutlarını azaltmak için kendi içindeki uygulamaları nasıl kırpacağınızı öğrenin. .NET Core paketleri kendi içinde yayınlanan ve genellikle çalışma zamanının daha fazlasını içeren bir uygulamayla çalışma zamanı gereklidir.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: 1ebcac51331407069e26b49e40bb6e071cefb752
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770461"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Kendi içinde bulunan dağıtımları ve yürütülebilir dosyaları kırp

[Framework 'e bağımlı dağıtım modeli](index.md#publish-framework-dependent) , .net 'in başlangıcından bu yana en başarılı dağıtım modelidir. Bu senaryoda, uygulama geliştiricisi yalnızca, .NET çalışma zamanı ve çerçeve kitaplıklarının istemci makinede kullanılabilir olacağı beklentisiyle yalnızca uygulama ve üçüncü taraf derlemeler sunan. Bu dağıtım modeli, .NET Core 'da baskın bir tane olmaya devam eder ancak çerçeveye bağımlı modelin en iyi durumda olmadığı bazı senaryolar vardır. Alternatif olarak, .NET Core çalışma zamanı ve çerçevesinin uygulama ve üçüncü taraf Derlemeleriyle birlikte paketlenmiş olduğu, [kendi kendine içerilen bir uygulama](index.md#publish-self-contained)yayımlamaktır.

Kırpma Self-içerilen dağıtım modeli, dağıtım boyutunu azaltmak için optimize edilmiş, kendine dahil edilen dağıtım modelinin özelleşmiş bir sürümüdür. Dağıtım boyutunu en aza indirmek Blazor uygulamaları gibi bazı istemci tarafı senaryolar için kritik bir gereksinimdir. Uygulamanın karmaşıklığına bağlı olarak, yalnızca çerçeve derlemelerinin bir alt kümesine başvurulur ve uygulamayı çalıştırmak için her derleme içindeki kodun bir alt kümesi gereklidir. Kitaplıkların kullanılmayan bölümleri gereksizdir ve paketlenmiş uygulamadan kırpılabilecek.

Ancak, uygulamanın derleme zamanı analizinin, çeşitli sorunlu kod düzenlerini güvenilir bir şekilde çözümleyemedikleri için çalışma zamanında hatalara neden olabileceği bir risk vardır (büyük ölçüde yansıma kullanımı üzerinde ortalandı). Güvenilirlik güvencesi verilmediğinden, bu dağıtım modeli bir önizleme özelliği olarak sunulur.

Derleme zamanı Çözümleme altyapısı, hangi diğer kodun gerekli olduğunu tespit etmek için sorunlu kod desenlerinin geliştiricisine uyarı sağlar. Koda, başka nelerin dahil edileceğini söylemek için koda açıklama eklenebilir. Birçok yansıma deseni, [kaynak](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md)oluşturucuları kullanılarak derleme zamanı kod üretimi ile değiştirilebilir.

Uygulamalar için kırpma modu ayarı ile yapılandırılır `TrimMode` . Varsayılan değer ve, `copyused` uygulamayla birlikte başvurulan derlemelerdir. `link`Değer, Blazor WebAssembly uygulamalarıyla kullanılır ve derlemeler içinde kullanılmayan kodu kırpar. Kırpma Analizi uyarıları, tam bağımlılık analizinin mümkün olmadığı kod desenleri hakkında bilgi verir. Bu uyarılar varsayılan olarak bastırılır ve bayrağı olarak ayarlanarak açılabilir `SuppressTrimAnalysisWarnings` `false` . Kullanılabilir kırpma seçenekleri hakkında daha fazla bilgi için bkz. [kırpma seçenekleri](trimming-options.md).

> [!NOTE]
> Kırpma, .NET Core 3,1 ve .NET 5,0 ' de deneysel bir özelliktir. Kırpma _yalnızca_ kendi içinde yayımlanan uygulamalar için kullanılabilir.

## <a name="prevent-assemblies-from-being-trimmed"></a>Derlemelerin kırpılmasına engel

Kırpma işlevinin başvuruları algılayamayacağı senaryolar vardır. Örneğin, yansıma bir çalışma zamanı derlemesinde, uygulamanız veya uygulamanız tarafından başvurulan bir kitaplıkda kullanıldığında, derlemeye doğrudan başvurulmuyor demektir. Kırpma, bu dolaylı başvuruların farkında değildir ve kitaplığı yayımlanan klasörden hariç tutar.

Kod, yansıma aracılığıyla bir derlemeye dolaylı olarak başvurduğunda, derlemenin ayarla kırpılmasına engel olabilirsiniz `<TrimmerRootAssembly>` . Aşağıdaki örnek, derleme adlı derlemenin kırpılmasını nasıl önleyekullanacağınızı gösterir `System.Security` :

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a>Uygulamanızı kırpın-CLı

[DotNet Publish](../tools/dotnet-publish.md) komutunu kullanarak uygulamanızı kırpın. Uygulamanızı yayımladığınızda, aşağıdaki özellikleri ayarlayın:

- Belirli bir çalışma zamanı için kendi kendine kapsanan uygulama olarak yayımla: `-r win-x64`
- Kırpmayı etkinleştir: `/p:PublishTrimmed=true`

Aşağıdaki örnek, Windows için bir uygulamayı kendi içinde yayınlar ve çıktıyı kırpar.

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

Aşağıdaki örnek, derleme içinde kullanılmayan kodun kırpılıp kırpılmayabileceği, agresif kırpma modunda bir uygulama yayımlar.

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</PropertyGroup>
```

Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).

## <a name="trim-your-app---visual-studio"></a>Uygulamanızı kırpın-Visual Studio

Visual Studio, uygulamanızın nasıl yayımlandığını denetleyen yeniden kullanılabilir yayımlama profilleri oluşturur.

01. **Çözüm Gezgini** bölmesinde, yayımlamak istediğiniz projeye sağ tıklayın. Yayımla ' yı seçin.. **.**

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

    Zaten bir yayımlama profiliniz yoksa, bir tane oluşturmak için yönergeleri izleyin ve hedef türü **klasörünü** seçin.

01. **Düzenle**' yi seçin.

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Visual Studio Profili Düzenle düğmesi ile Yayımla.":::

01. **Profil ayarları** iletişim kutusunda, aşağıdaki seçenekleri ayarlayın:

    - **Dağıtım modunu** **kendi kendine dahil**olarak ayarlayın.
    - **Hedef çalışma zamanını** , yayımlamak istediğiniz platforma ayarlayın.
    - **Kullanılmayan derlemeleri Kırp (önizlemede)** seçeneğini belirleyin.

    Ayarları kaydetmek ve **Yayımla** iletişim kutusuna dönmek için **Kaydet** ' i seçin.

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Dağıtım modu, hedef çalışma zamanı ve kullanılmayan derlemeleri Kırp seçeneklerinin vurgulandığı profil ayarları iletişim kutusu.":::

01. Uygulamanızı yayımlamak için **Yayımla** ' yı seçin.

Daha fazla bilgi için bkz. [Visual Studio ile .NET Core uygulamalarını yayımlama](deploy-with-vs.md).

## <a name="trim-your-app---visual-studio-for-mac"></a>Uygulamanızı kırpın-Mac için Visual Studio

Mac için Visual Studio yayımlama sırasında uygulamanızı kırpmak için seçenek sağlamıyor. [Uygulamanızı Kırp-CLI](#trim-your-app---cli) bölümündeki yönergeleri izleyerek el ile yayımlamanız gerekir. Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core uygulama dağıtımı](index.md).
- [.NET Core uygulamalarını .NET Core CLI yayımlayın](deploy-with-cli.md).
- [Visual Studio ile .NET Core uygulamaları yayımlayın](deploy-with-vs.md).
- [DotNet Publish komutu](../tools/dotnet-publish.md).
