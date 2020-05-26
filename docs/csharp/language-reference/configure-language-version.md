---
title: C# dil sürümü oluşturma-C# Kılavuzu
description: C# dil sürümünün projenize göre nasıl belirlendiği ve bu seçimin arkasındaki nedenler hakkında bilgi edinin. Varsayılanı el ile nasıl geçersiz kılacağınızı öğrenin.
ms.date: 05/20/2020
ms.openlocfilehash: bbe5b12e378cf47b7c9b2c8576088e949e526a9a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803003"
---
# <a name="c-language-versioning"></a>C# dil sürümü oluşturma

En son C# derleyicisi, projenizin hedef çerçevesine veya çerçevelerine göre varsayılan dil sürümünü belirler. Visual Studio, değeri değiştirmek için bir kullanıcı arabirimi sağlamaz, ancak *csproj* dosyasını düzenleyerek bunu değiştirebilirsiniz. Varsayılan seçenek, hedef çerçeveinizle uyumlu en son dil sürümünü kullanmanızı sağlar. Projenizin hedefi ile uyumlu olan en son dil özelliklerine erişim avantajına sahip olursunuz. Bu varsayılan seçenek ayrıca, hedef çerçeveinizden kullanılabilir olmayan türler veya çalışma zamanı davranışı gerektiren bir dil kullanmanıza da sağlar. Varsayılandan daha yeni bir dil sürümü seçmek, derleme zamanı ve çalışma zamanı hatalarının tanılanmasına neden olabilir.

Bu makaledeki kurallar, Visual Studio 2019 veya .NET Core 3,0 SDK ile sunulan derleyici için geçerlidir. Visual Studio 2017 yüklemesinin veya önceki bir sürümünün parçası olan C# derleyicileri .NET Core SDK, varsayılan olarak c# 7,0 ' dir.

C# 8,0 (ve üzeri) yalnızca .NET Core 3. x ve daha yeni sürümlerde desteklenir. En yeni özelliklerin birçoğu .NET Core 3. x içinde tanıtılan kitaplık ve çalışma zamanı özellikleri gerektirir:

- [Varsayılan arabirim uygulamasına](../whats-new/csharp-8.md#default-interface-methods) .net Core 3,0 clr 'de yeni özellikler gerekir.
- [Zaman uyumsuz akışlar](../whats-new/csharp-8.md#asynchronous-streams) , ve gibi yeni türler gerektirir <xref:System.IAsyncDisposable?displayProperty=nameWithType> <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType> <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType> .
- [Dizinler ve aralıklar](../whats-new/csharp-8.md#indices-and-ranges) yeni türler ve gerektirir <xref:System.Index?displayProperty=nameWithType> <xref:System.Range?displayProperty=nameWithType> .
- [Null yapılabilir başvuru türleri](../whats-new/csharp-8.md#nullable-reference-types) , daha iyi uyarılar sağlamak için birkaç [özniteliği](attributes/nullable-analysis.md) kullanır. Bu öznitelikler .NET Core 3,0 ' ye eklenmiştir. Diğer hedef çerçeveler bu özniteliklerin hiçbirinde açıklanmamış. Bu, null yapılabilir uyarıların olası sorunları doğru şekilde yansıtmayabileceği anlamına gelir.

## <a name="defaults"></a>Varsayılanları

Derleyici, bu kurallara göre bir varsayılan değer belirler:

| Hedef çerçeve | sürüm | C# dil sürümü varsayılanı |
|------------------|---------|-----------------------------|
| .NET Core        | 3.x     | C# 8.0                      |
| .NET Core        | 2.x     | C# 7.3                      |
| .NET Standard    | 2.1     | C# 8.0                      |
| .NET Standard    | 2.0     | C# 7.3                      |
| .NET Standard    | 'in     | C# 7.3                      |
| .NET Framework   | tümü     | C# 7.3                      |

Projeniz karşılık gelen önizleme dili sürümüne sahip bir önizleme çerçevesini hedefliyorsa, kullanılan dil sürümü önizleme dili sürümüdür. Yayınlanan bir .NET Core sürümünü hedefleyen projeleri etkilemeden, bu Önizlemedeki en son özellikleri herhangi bir ortamda kullanırsınız.

## <a name="override-a-default"></a>Varsayılanı geçersiz kıl

C# sürümünüzü açık bir şekilde belirtmeniz gerekiyorsa, bunu birkaç şekilde yapabilirsiniz:

- [Proje dosyanızı](#edit-the-project-file)el ile düzenleyin.
- [Bir alt dizinde birden çok proje için](#configure-multiple-projects)dil sürümünü ayarlayın.
- [ `-langversion` Derleyici seçeneğini](compiler-options/langversion-compiler-option.md)yapılandırın.

### <a name="edit-the-project-file"></a>Proje dosyasını düzenleme

Proje dosyanızdaki dil sürümünü ayarlayabilirsiniz. Örneğin, önizleme özelliklerine açıkça erişim istiyorsanız, şöyle bir öğe ekleyin:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Bu değer, `preview` derleyicinizin desteklediği en son Preview C# dil sürümünü kullanır.

### <a name="configure-multiple-projects"></a>Birden çok proje yapılandırma

Birden çok proje yapılandırmak için, öğesini içeren bir **Dizin. Build. props** dosyası oluşturabilirsiniz `<LangVersion>` . Bunu genellikle çözüm dizininizde yapabilirsiniz. Aşağıdakileri çözüm dizininizde bir **Dizin. Build. props** dosyasına ekleyin:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Bu dosyayı içeren dizinin tüm alt dizinlerindeki derlemeler, Preview C# sürümünü kullanacaktır. Daha fazla bilgi için, [yapınızı özelleştirme](/visualstudio/msbuild/customize-your-build)başlıklı makaleye bakın.

## <a name="c-language-version-reference"></a>C# dil sürümü başvurusu

Aşağıdaki tabloda tüm geçerli C# dil sürümleri gösterilmektedir. Daha eski bir değer varsa, derleyicinizi her değeri anlayamayabilir. .NET Core 3,0 veya sonraki bir sürümünü yüklerseniz, listelenen her şeye erişebilirsiniz.

[!INCLUDE [langversion-table](includes/langversion-table.md)]

> [!TIP]
> [Visual Studio için geliştirici komut istemi](../../framework/tools/developer-command-prompt-for-vs.md)açın ve makinenizde kullanılabilen dil sürümlerinin listesini görmek için aşağıdaki komutu çalıştırın.
>
> ```CMD
> csc -langversion:?
> ```
>
> Bunun gibi [-langversion](compiler-options/langversion-compiler-option.md) derleme seçeneğini Sorga benzemekle, aşağıdakine benzer bir şey yazdıracaktır:
>
> ```CMD
> Supported language versions:
> default
> 1
> 2
> 3
> 4
> 5
> 6
> 7.0
> 7.1
> 7.2
> 7.3
> 8.0 (default)
> latestmajor
> preview
> latest
> ```
