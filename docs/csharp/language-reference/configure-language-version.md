---
title: C#dil sürümü oluşturma C# -kılavuz
description: C# Dil sürümünün projenize göre nasıl belirlendiği ve bu seçimin arkasındaki nedenler hakkında bilgi edinin. Varsayılanı el ile nasıl geçersiz kılacağınızı öğrenin.
ms.date: 02/21/2020
ms.openlocfilehash: 2be76fdac471a7175b661d896b0da2910b3609f3
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626770"
---
# <a name="c-language-versioning"></a>C#dil sürümü oluşturma

En son C# derleyici, projenizin hedef çerçevesine veya çerçevelerine göre varsayılan dil sürümünü belirler. Visual Studio, değeri değiştirmek için bir kullanıcı arabirimi sağlamaz, ancak *csproj* dosyasını düzenleyerek bunu değiştirebilirsiniz. Varsayılan seçenek, hedef çerçeveinizle uyumlu en son dil sürümünü kullanmanızı sağlar. Projenizin hedefi ile uyumlu olan en son dil özelliklerine erişim avantajına sahip olursunuz. Bu varsayılan seçenek ayrıca, hedef çerçeveinizden kullanılabilir olmayan türler veya çalışma zamanı davranışı gerektiren bir dil kullanmanıza da sağlar. Varsayılandan daha yeni bir dil sürümü seçmek, derleme zamanı ve çalışma zamanı hatalarının tanılanmasına neden olabilir.

C#8,0 (ve üzeri) yalnızca .NET Core 3. x ve daha yeni sürümlerde desteklenir. En yeni özelliklerin birçoğu .NET Core 3. x içinde tanıtılan kitaplık ve çalışma zamanı özellikleri gerektirir:

- Varsayılan arabirim üyesi uygulama, .NET Core 3,0 CLR 'de yeni özellikler gerektirir.
- Zaman uyumsuz akışlar <xref:System.IAsyncDisposable?displayProperty=nameWithType>, <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>ve <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>yeni türlerini gerektirir.
- Dizinler ve aralıklar <xref:System.Index?displayProperty=nameWithType> ve <xref:System.Range?displayProperty=nameWithType>yeni türler gerektirir.
- Null yapılabilir başvuru türleri, daha iyi uyarılar sağlamak için birkaç [özniteliği](../nullable-attributes.md) kullanır. Bu öznitelikler .NET Core 3,0 ' ye eklenmiştir. Diğer hedef çerçeveler bu özniteliklerin hiçbirinde açıklanmamış. Bu, null yapılabilir uyarıların olası sorunları doğru şekilde yansıtmayabileceği anlamına gelir.

## <a name="defaults"></a>Varsayılanları

Derleyici, bu kurallara göre bir varsayılan değer belirler:

|Hedef çerçeve|version|C#dil sürümü varsayılanı|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2,0|C# 7.3|
|.NET Standard|'in|C# 7.3|
|.NET Framework|tümü|C# 7.3|

Projeniz karşılık gelen önizleme dili sürümüne sahip bir önizleme çerçevesini hedefliyorsa, kullanılan dil sürümü önizleme dili sürümüdür. Yayınlanan bir .NET Core sürümünü hedefleyen projeleri etkilemeden, bu Önizlemedeki en son özellikleri herhangi bir ortamda kullanırsınız.

## <a name="override-a-default"></a>Varsayılanı geçersiz kıl

C# Sürümünüzü açıkça belirtmeniz gerekiyorsa, bunu birkaç şekilde yapabilirsiniz:

- [Proje dosyanızı](#edit-the-project-file)el ile düzenleyin.
- [Bir alt dizinde birden çok proje için](#configure-multiple-projects)dil sürümünü ayarlayın.
- [`-langversion` derleyici seçeneğini](compiler-options/langversion-compiler-option.md)yapılandırın.

### <a name="edit-the-project-file"></a>Proje dosyasını düzenleme

Proje dosyanızdaki dil sürümünü ayarlayabilirsiniz. Örneğin, önizleme özelliklerine açıkça erişim istiyorsanız, şöyle bir öğe ekleyin:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Değer `preview`, derleyicinizin desteklediği en son C# önizleme dili sürümünü kullanır.

### <a name="configure-multiple-projects"></a>Birden çok proje yapılandırma

Birden çok projeyi yapılandırmak için, `<LangVersion>` öğesini içeren bir **Dizin. Build. props** dosyası oluşturabilirsiniz. Bunu genellikle çözüm dizininizde yapabilirsiniz. Aşağıdakileri çözüm dizininizde bir **Dizin. Build. props** dosyasına ekleyin:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Bu dosyayı içeren dizinin tüm alt dizinlerindeki derlemeler Önizleme C# sürümünü kullanacaktır. Daha fazla bilgi için, [yapınızı özelleştirme](/visualstudio/msbuild/customize-your-build)başlıklı makaleye bakın.

## <a name="c-language-version-reference"></a>C#dil sürümü başvurusu

Aşağıdaki tabloda tüm geçerli C# dil sürümleri gösterilmektedir. Daha eski bir değer varsa, derleyicinizi her değeri anlayamayabilir. .NET Core 3,0 veya sonraki bir sürümünü yüklerseniz, listelenen her şeye erişebilirsiniz.

|Değer|Anlamı|
|------------|-------------|
|önizleme|Derleyici, en son önizleme sürümündeki tüm geçerli dil sözdizimini kabul eder.|
|en son|Derleyici derleyicinin en son yayınlanan sürümünden (ikincil sürüm dahil) söz dizimini kabul eder.|
|Latestana|Derleyici derleyicinin en son yayınlanan ana sürümünden söz dizimini kabul eder.|
|8.0|Derleyici yalnızca C# 8,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|7.3|Derleyici yalnızca C# 7,3 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|7.2|Derleyici yalnızca C# 7,2 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|7.1|Derleyici yalnızca C# 7,1 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|7|Derleyici yalnızca C# 7,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|6|Derleyici yalnızca C# 6,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|5|Derleyici yalnızca C# 5,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|4|Derleyici yalnızca C# 4,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|3|Derleyici yalnızca C# 3,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|ISO-2|Derleyici yalnızca ISO/ıEC 23270:2006 C# (2,0) içinde bulunan söz dizimini kabul eder. |
|ISO-1|Derleyici yalnızca ISO/ıEC 23270:2003 C# (1.0/1.2) içinde bulunan söz dizimini kabul eder. |
