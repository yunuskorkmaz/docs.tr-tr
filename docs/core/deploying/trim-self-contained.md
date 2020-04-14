---
title: Kendi kendine yeten uygulamaları kırpma
description: Boyutlarını azaltmak için bağımsız uygulamaları nasıl kırptığınızı öğrenin. .NET Core, çalışma süresini kendi kendine çalışan bir uygulamayla paketler ve genellikle çalışma süresinin daha fazlasını içerir ve o zaman gereklidir.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bb8ac88c5e16b7fd20a7670e4ad76dbe4b44da1b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242936"
---
# <a name="trim-self-contained-deployments-and-executables"></a>Kendi içinde bulunan dağıtımları ve yürütülebilir dosyaları kırp

Bir uygulama bağımsız yayımlanırken,.NET Core çalışma süresi uygulamayla birlikte paketlenir. Bu birleştirme, paket uygulamanıza önemli miktarda içerik ekler. Uygulamanızı dağıtma söz konusu olduğunda, boyut genellikle önemli bir faktördür. Paket uygulamasının boyutunu mümkün olduğunca küçük tutmak genellikle uygulama geliştiricileri için bir hedeftir.

Uygulamanın karmaşıklığına bağlı olarak, uygulamayı çalıştırmak için yalnızca çalışma zamanının bir alt kümesi gerekir. Çalışma zamanının bu kullanılmayan bölümleri gereksizdir ve paket uygulamadan kesilebilir.

Kırpma özelliği, gerekli çalışma zamanı derlemelerinin bir grafiğini keşfetmek ve oluşturmak için uygulama ikililerini inceleyerek çalışır. Başvurulamayan kalan çalışma zamanı derlemeleri hariç tutulur.

> [!NOTE]
> Kırpma ,NET Core 3.1'de deneysel bir özelliktir ve _yalnızca_ bağımsız olarak yayınlanan uygulamalar için kullanılabilir.

## <a name="prevent-assemblies-from-being-trimmed"></a>Montajların kırpılmasını önleyin

Kırpma işlevinin başvuruları algılayamadığı senaryolar vardır. Örneğin, uygulamanız veya uygulamanız tarafından başvurulan bir kitaplık tarafından bir çalışma zamanı derlemesi üzerinde yansıma kullanıldığında, derleme doğrudan başvurulmuyor. Kırpma bu dolaylı başvurulardan habersizdir ve kitaplığı yayımlanmış klasöründen dışlar.

Kod dolaylı olarak yansıma yoluyla bir derlemeye başvururken, derlemenin `<TrimmerRootAssembly>` ayarla birlikte kırpılmasını engelleyebilirsiniz. Aşağıdaki örnek, derleme adı verilen `System.Security` bir derlemenin nasıl kırpılmasının önlenişretilenin ilerler:

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a>Uygulamanızı kırpın - CLI

[Dotnet yayımlama](../tools/dotnet-publish.md) komutunu kullanarak uygulamanızı kırpın. Uygulamanızı yayımladığınızda aşağıdaki üç ayarı ayarlayın:

- Bağımsız olarak yayımlayın:`--self-contained true`
- Tek dosyalı yayımlamayı devre dışı:`-p:PublishSingleFile=false`
- Kırpma yı etkinleştirme:`p:PublishTrimmed=true`

Aşağıdaki örnek, Windows 10 için bir uygulamayı bağımsız olarak yayımlar ve çıktıyı kırpar.

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true -p:PublishSingleFile=false -p:PublishTrimmed=true
```

Daha fazla bilgi için [bkz.](deploy-with-cli.md)

## <a name="trim-your-app---visual-studio"></a>Uygulamanızı kırpın - Visual Studio

Visual Studio, uygulamanızın nasıl yayımlandığını denetleyen yeniden kullanılabilir yayımlama profilleri oluşturur.

01. Çözüm **Gezgini** bölmesine, yayımlamak istediğiniz projeye sağ tıklayın. **Yayımla'yı seçin...**.

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

    Zaten bir yayımlama profiliniz yoksa, bir tane oluşturmak için yönergeleri izleyin ve **Klasör** hedef türünü seçin.

01. **Edit'i**seçin.

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Visual studio, profili edit düğmesiyle yayımlar.":::

01. Profil **ayarları** iletişim kutusunda aşağıdaki seçenekleri ayarlayın:

    - **Dağıtım modunu** **Bağımsız**olarak ayarlayın.
    - **Hedef çalışma zamanını** yayınlamak istediğiniz platforma ayarlayın.
    - **Kullanılmayan derlemeleri Kırp'ı (önizlemede)** seçin.

    Ayarları kaydetmek ve **Yayımla** iletişim kutusuna dönmek için **Kaydet'i** seçin.

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Dağıtım modu, hedef çalışma zamanı ve kullanılmayan derlemeleri kırpma seçenekleri vurgulanan profil ayarları iletişim kutusu.":::

01. Kesilmiş uygulamanızı yayınlamak için **Yayımla'yı** seçin.

Daha fazla bilgi için [bkz.](deploy-with-vs.md)

## <a name="trim-your-app---visual-studio-for-mac"></a>Uygulamanızı kırpın - Mac için Visual Studio

Mac için Visual Studio, yayın sırasında uygulamanızı kırpma seçenekleri sağlamaz. [Uygulamanızı Kırpma - CLI](#trim-your-app---cli) bölümündeki yönergeleri izleyerek el ile yayınlamanız gerekir. Daha fazla bilgi için [bkz.](deploy-with-cli.md)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Çekirdek uygulama dağıtımı](index.md).
- [.NET Core CLI ile .NET Core uygulamalarını yayımlayın.](deploy-with-cli.md)
- [.NET Core uygulamalarını Visual Studio ile yayımlayın.](deploy-with-vs.md)
- [dotnet yayımlama komutu](../tools/dotnet-publish.md).
