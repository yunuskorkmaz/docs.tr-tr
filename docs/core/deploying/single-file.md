---
title: Tek dosya uygulaması
description: Tek bir dosya uygulamasının ne olduğunu ve neden bu uygulama dağıtım modelini kullanmayı düşünmeniz gerektiğini öğrenin.
author: lakshanf
ms.author: lakshanf
ms.date: 08/28/2020
ms.openlocfilehash: 8149f912c2d92c3eff8d248353e11c01bcfc24ba
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91573676"
---
# <a name="single-file-deployment-and-executable"></a>Tek dosya dağıtımı ve yürütülebilir dosya

Uygulamaya bağımlı tüm dosyaları tek bir ikiliye paketlemek, uygulamayı tek bir dosya olarak dağıtmak ve dağıtmak için çekici bir seçeneğe sahip bir uygulama geliştiricisi sağlar. Bu dağıtım modeli .NET Core 3,0 ' den beri kullanılabilir ve .NET 5,0 ' de geliştirilmiştir. Daha önce .NET Core 3,0 ' de, bir kullanıcı tek dosya uygulamanızı çalıştırdığında, .NET Core ana bilgisayarı önce uygulamayı çalıştırmadan önce tüm dosyaları geçici bir dizine ayıklar. .NET 5,0, dosyaları uygulamadan çıkarmaya gerek olmadan doğrudan kodu çalıştırarak bu deneyimi geliştirir.

Tek dosya dağıtımı, hem [çerçeveye bağımlı dağıtım modeli](index.md#publish-framework-dependent) hem de [kendi içinde bulunan uygulamalar](index.md#publish-self-contained)için kullanılabilir. Bağımsız bir uygulamadaki tek dosyanın boyutu, çalışma zamanı ve çerçeve kitaplıklarını dahil edecek şekilde büyük olacaktır. Tek dosya dağıtım seçeneği, [Readytorun](../tools/dotnet-publish.md) ve [Trim (.NET 5,0 ' de deneysel bir özellik)](trim-self-contained.md) yayımlama seçenekleri ile birleştirilebilir.

## <a name="api-incompatibility"></a>API uyumsuzluğu

Bazı API 'Ler tek dosya dağıtımıyla uyumlu değildir ve uygulamalar bu API 'Leri kullanıyorsa değişiklik yapılmasını gerektirebilir. Üçüncü taraf bir Framework veya paket kullanıyorsanız, bu API 'lerden birini de kullanabilir ve değişiklik yapmanız gerekebilir. Sorunların en yaygın nedeni, uygulamayla birlikte gelen dosyalar veya dll 'Ler için dosya yollarında bağımlılığını temel alır.

Aşağıdaki tabloda, tek dosya kullanımı için ilgili çalışma zamanı kitaplığı API 'SI ayrıntıları bulunur.

| API                            | Not                                                                   |
|--------------------------------|------------------------------------------------------------------------|
| `Assembly.Location`            | Boş bir dize döndürür.                                               |
| `Module.FullyQualifiedName`    | Değerine sahip bir dize döndürür `<Unknown>` veya bir özel durum oluşturur. |
| `Module.Name`                  | Değerine sahip bir dize döndürür `<Unknown>` .                        |
| `Assembly.GetFile`             | Atar <xref:System.IO.IOException> .                                   |
| `Assembly.GetFiles`            | Atar <xref:System.IO.IOException> .                                   |
| `Assembly.CodeBase`            | Atar <xref:System.PlatformNotSupportedException> .                    |
| `Assembly.EscapedCodeBase`     | Atar <xref:System.PlatformNotSupportedException> .                    |
| `AssemblyName.CodeBase`        | `null` döndürür.                                                        |
| `AssemblyName.EscapedCodeBase` | `null` döndürür.                                                        |

Yaygın senaryoları düzeltmeye yönelik bazı önerileriniz var:

* Yürütülebilir dosyanın yanındaki dosyalara erişmek için şunu kullanın <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>

* Yürütülebilir dosyanın dosya adını bulmak için ilk öğesini kullanın <xref:System.Environment.GetCommandLineArgs()?displayProperty=nameWithType>

* Gevşek dosyaları tamamen sevk etmeyi önlemek için, [ekli kaynakları](https://docs.microsoft.com/en-us/dotnet/framework/resources/creating-resource-files-for-desktop-apps) kullanmayı düşünün

## <a name="other-considerations"></a>Diğer önemli noktalar

Tek dosya varsayılan olarak yerel kitaplıkları paketetmez. Linux 'ta çalışma zamanını pakete önceden bağlayacağız ve yalnızca uygulama yerel kitaplıkları tek dosya uygulamasıyla aynı dizine dağıtılır. Windows 'da, yalnızca barındırma kodunu ön bağlantımız ve hem çalışma zamanı hem de uygulama yerel kitaplıkları tek dosya uygulamasıyla aynı dizine dağıtılır. Bu, yerel dosyaların tek dosyadan dışlanması gereken iyi bir hata ayıklama deneyimi sağlamaktır. `IncludeNativeLibrariesForSelfExtract`Tek dosya paketine yerel kitaplıkları dahil etmek için bir bayrak ayarlama seçeneği vardır, ancak tek dosya uygulaması çalıştırıldığında bu dosyalar istemci makinesindeki geçici bir dizine çıkarılır.

Tek dosya uygulama onunla ilgili tüm PDB dosyalarını ve varsayılan olarak paketlendirilecektir. Oluşturduğunuz projeler için derlemenin içine pdb 'leri eklemek istiyorsanız, ' yi `DebugType` `embedded` [aşağıda](#include-pdb-files-inside-the-bundle) açıklandığı gibi olarak ayarlayın.

Yönetilen C++ bileşenleri tek dosya dağıtımına uygun değildir ve tek dosya uyumlu olması için C# veya yönetilmeyen bir C++ dilinde uygulama yazmanızı öneririz.

## <a name="exclude-files-from-being-embedded"></a>Dosyaların gömülmesini hariç tut

Belirli dosyalar, aşağıdaki meta veriler ayarlanarak tek dosyaya katıştırılmayana açık bir şekilde dışlanamaz:

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

Örneğin, yayınlama dizinine bazı dosyalar yerleştirmek, ancak onları tek dosyada paketlemenize izin vermek için:

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="include-pdb-files-inside-the-bundle"></a>Paket içine PDB dosyalarını dahil et

Bir bütünleştirilmiş kod için PDB dosyası, aşağıdaki ayarı kullanılarak derlemeye gömülebilir ( `.dll` ). Semboller derlemenin bir parçası olduğundan, tek dosya uygulamasının bir parçası de olur:

```xml
<DebugType>embedded</DebugType>
```

Örneğin, bu derlemeye PDB dosyasını katıştırmak için bir derlemenin proje dosyasına aşağıdaki özelliği ekleyin:

```xml
<PropertyGroup>
  <DebugType>embedded</DebugType>
</PropertyGroup>
```

## <a name="publish-a-single-file-app---cli"></a>Tek bir dosya uygulaması yayımlama-CLı

[DotNet Publish](../tools/dotnet-publish.md) komutunu kullanarak tek bir dosya uygulaması yayımlayın. Uygulamanızı yayımladığınızda, aşağıdaki özellikleri ayarlayın:

- Belirli bir çalışma zamanı için yayımlama: `-r win-x64`
- Tek dosya olarak yayımla: `-p:PublishSingleFile=true`

Aşağıdaki örnek, Windows için bir uygulamayı kendi içinde tek bir dosya uygulaması olarak yayımlar.

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

Aşağıdaki örnek, Framework 'e bağımlı tek dosya uygulaması olarak Linux için bir uygulama yayımlar.

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).

## <a name="publish-a-single-file-app---visual-studio"></a>Tek bir dosya uygulaması yayımlama-Visual Studio

Visual Studio, uygulamanızın nasıl yayımlandığını denetleyen yeniden kullanılabilir yayımlama profilleri oluşturur.

01. **Çözüm Gezgini** bölmesinde, yayımlamak istediğiniz projeye sağ tıklayın. **Yayımla**’yı seçin.

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

    Zaten bir yayımlama profiliniz yoksa, bir tane oluşturmak için yönergeleri izleyin ve hedef türü **klasörünü** seçin.

01. **Düzenle**' yi seçin.

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

01. **Profil ayarları** iletişim kutusunda, aşağıdaki seçenekleri ayarlayın:

    - **Dağıtım modunu** **kendi kendine dahil**olarak ayarlayın.
    - **Hedef çalışma zamanını** , yayımlamak istediğiniz platforma ayarlayın.
    - **Tek bir dosya üret**' i seçin.

    Ayarları kaydetmek ve **Yayımla** iletişim kutusuna dönmek için **Kaydet** ' i seçin.

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="Yayımla seçeneğini vurgulayan sağ tıklama menüsüyle Çözüm Gezgini.":::

01. Uygulamanızı tek bir dosya olarak yayımlamak için **Yayımla** ' yı seçin.

Daha fazla bilgi için bkz. [Visual Studio ile .NET Core uygulamalarını yayımlama](deploy-with-vs.md).

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a>Tek bir dosya uygulaması yayımlama-Mac için Visual Studio

Mac için Visual Studio uygulamanızı tek bir dosya olarak yayımlamak için seçenek sağlamıyor. [Tek dosya App-CLI Yayımla](#publish-a-single-file-app---cli) bölümündeki yönergeleri izleyerek el ile yayımlamanız gerekir. Daha fazla bilgi için bkz. [.NET Core uygulamalarını .NET Core CLI yayımlama](deploy-with-cli.md).

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Core uygulama dağıtımı](index.md).
- [.NET Core uygulamalarını .NET Core CLI yayımlayın](deploy-with-cli.md).
- [Visual Studio ile .NET Core uygulamaları yayımlayın](deploy-with-vs.md).
- [ `dotnet publish` komutu](../tools/dotnet-publish.md).
