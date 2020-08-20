---
title: Kendi içindeki uygulamaları kırpma
description: Kendi boyutlarını azaltmak için kendi içindeki uygulamaları nasıl kırpacağınızı öğrenin. .NET Core paketleri kendi içinde yayınlanan ve genellikle çalışma zamanının daha fazlasını içeren bir uygulamayla çalışma zamanı gereklidir.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: 2bb0f03994468bbad3096ebf0b141bc1f47b867e
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656722"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Kendi içinde bulunan dağıtımları ve yürütülebilir dosyaları kırp

[Framework 'e bağımlı dağıtım modeli](index.md#publish-framework-dependent) , .net 'in başlangıcından bu yana en başarılı dağıtım modelidir. Bu senaryoda, uygulama geliştiricisi yalnızca, .NET çalışma zamanı ve çerçeve kitaplıklarının istemci makinede kullanılabilir olacağı beklentisiyle yalnızca uygulama ve üçüncü taraf derlemeler sunan. Bu dağıtım modeli, .NET Core 'da baskın bir tane olmaya devam eder ancak çerçeveye bağımlı modelin en iyi durumda olmadığı bazı senaryolar vardır. Alternatif olarak, .NET Core çalışma zamanı ve çerçevesinin uygulama ve üçüncü taraf Derlemeleriyle birlikte paketlenmiş olduğu, [kendi kendine içerilen bir uygulama](index.md#publish-self-contained)yayımlamaktır.

Kırpma Self-içerilen dağıtım modeli, dağıtım boyutunu azaltmak için optimize edilmiş, kendine dahil edilen dağıtım modelinin özelleşmiş bir sürümüdür. Dağıtım boyutunu en aza indirmek Blazor uygulamaları gibi bazı istemci tarafı senaryolar için kritik bir gereksinimdir. Uygulamanın karmaşıklığına bağlı olarak, uygulamayı çalıştırmak için çerçeve derlemelerinin yalnızca bir alt kümesi gereklidir. Kitaplığın kullanılmayan bu bölümleri gereksizdir ve paketlenmiş uygulamadan kırpılabilecek. Ancak, uygulamanın derleme zamanı analizinin, çeşitli sorunlu kod düzenlerini güvenilir bir şekilde çözümleyemedikleri için çalışma zamanında hatalara neden olabileceği bir risk vardır (büyük ölçüde yansıma kullanımı üzerinde ortalandı). Güvenilirlik güvencesi verilmediğinden, bu dağıtım modeli bir önizleme özelliği olarak sunulur. Derleme zamanı Çözümleme altyapısı, sorunlu kod desenlerinin geliştiricisine uyarı sağlar ve bu kod desenlerinin düzeltilme beklentisi olur. Mümkün olduğunda, aynı gereksinimleri karşılayan kodu kullanarak zaman oluşturmak için uygulamanızdaki çalışma zamanı yansıma bağımlılıklarını taşımanızı öneririz.

Uygulamalar için kırpma modu, Kırım modu aracılığıyla yapılandırılabilir ve `copyused` uygulamada kullanılan derlemeleri paketleyip varsayılan () olur. Blazor WebAssembly uygulamaları, `link` derlemeler içinde kullanılmayan kodu kırpacak daha agresif bir mod () kullanır. Kırpma Analizi uyarıları, tam bağımlılık analizinin mümkün olmadığı kod desenleri hakkında bilgi verir. Bu uyarılar varsayılan olarak bastırılır ve bayrağı `SuppressTrimAnalysisWarnings` false olarak ayarlanarak açılabilir. Kullanılabilir kırpma seçenekleri hakkında daha fazla bilgi için [ılbağlayıcı sayfasında](https://github.com/mono/linker/blob/master/docs/illink-options.md)bulabilirsiniz.

> [!NOTE]
> Kırpma, .NET Core 3,1, 5,0 ' deki deneysel bir özelliktir ve _yalnızca_ kendi içinde yayımlanan uygulamalar tarafından kullanılabilir.

## <a name="prevent-assemblies-from-being-trimmed"></a>Derlemelerin kırpılmasına engel

Kırpma işlevinin başvuruları algılayamayacağı senaryolar vardır. Örneğin, yansıma bir çalışma zamanı derlemesinde, uygulamanız veya uygulamanız tarafından başvurulan bir kitaplıkda kullanıldığında, derlemeye doğrudan başvurulmuyor demektir. Kırpma, bu dolaylı başvuruların farkında değildir ve kitaplığı yayımlanan klasörden hariç tutar.

Kod, yansıma aracılığıyla bir derlemeye dolaylı olarak başvurduğunda, derlemenin ayarla kırpılmasına engel olabilirsiniz `<TrimmerRootAssembly>` . Aşağıdaki örnek, derleme adlı derlemenin kırpılmasını nasıl önleyekullanacağınızı gösterir `System.Security` :

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a>Uygulamanızı kırpın-CLı

[DotNet Publish](../tools/dotnet-publish.md) komutunu kullanarak uygulamanızı kırpın. Uygulamanızı yayımladığınızda, aşağıdaki üç ayarı ayarlayın:

- Kendi içinde Yayımla: `--self-contained true`
- Kırpmayı etkinleştir: `p:PublishTrimmed=true`

Aşağıdaki örnek, Windows için bir uygulamayı kendi içinde yayınlar ve çıktıyı kırpar.

```xml
<ItemGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <PublishTrimmed>true</PublishTrimmed>
</ItemGroup>
```

Aşağıdaki örnek, kullanılmayan kod oluşturma derlemelerinin kırpılıp kırpılmayabileceği, agresif kırpma modunda bir uygulamayı yayınlar.

```xml
<ItemGroup>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</ItemGroup>
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
