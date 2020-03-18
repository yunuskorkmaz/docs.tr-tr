---
title: C# dil sürümü - C# Kılavuzu
description: Projenize ve bu seçimin ardındaki nedenlere göre C# dil sürümünün nasıl belirlendiği hakkında bilgi edinin. Varsayılanı el ile nasıl geçersiz kısıkyavaş geçersiz kılılabildiğini öğrenin.
ms.date: 02/21/2020
ms.openlocfilehash: ef7275aad7638f52ecbfca1dfbdb962ae242fb48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399541"
---
# <a name="c-language-versioning"></a>C# dil sürümü

En son C# derleyicisi, projenizin hedef çerçevesine veya çerçevelerine dayalı varsayılan bir dil sürümünü belirler. Visual Studio değeri değiştirmek için bir ui sağlamaz, ancak *csproj* dosyasını düzenleyerek değiştirebilirsiniz. Varsayılan seçim, hedef çerçevenizle uyumlu en son dil sürümünü kullanmanızı sağlar. Projenizin hedefiyle uyumlu en son dil özelliklerine erişebilirsiniz. Bu varsayılan seçim, hedef çerçevenizde bulunmayan türler veya çalışma zamanı davranışı gerektiren bir dil kullanmamanızı da sağlar. Varsayılandan daha yeni bir dil sürümü seçmek derleme zamanı ve çalışma zamanı hatalarını tanılamak zor olabilir.

Bu makaledeki kurallar Visual Studio 2019 veya .NET Core 3.0 SDK ile teslim edilen derleyici için geçerlidir. Visual Studio 2017 kurulumunun bir parçası olan C# derleyicileri veya daha önceki .NET Core SDK sürümleri varsayılan olarak C# 7.0'ı hedeflemeyi hedeflemez.

C# 8.0 (ve daha yüksek) yalnızca .NET Core 3.x ve yeni sürümlerinde desteklenir. En yeni özelliklerin çoğu .NET Core 3.x'te tanıtılan kitaplık ve çalışma zamanı özellikleri gerektirir:

- Varsayılan arabirim üyesi uygulaması .NET Core 3.0 CLR'de yeni özellikler gerektirir.
- Async akışları yeni türleri <xref:System.IAsyncDisposable?displayProperty=nameWithType> <xref:System.Collections.Generic.IAsyncEnumerable%601?displayProperty=nameWithType>gerektirir <xref:System.Collections.Generic.IAsyncEnumerator%601?displayProperty=nameWithType>, ve .
- Dizinler ve Aralıklar <xref:System.Index?displayProperty=nameWithType> yeni <xref:System.Range?displayProperty=nameWithType>türleri gerektirir ve.
- Nullable başvuru türleri daha iyi uyarılar sağlamak için çeşitli [öznitelikleri](../nullable-attributes.md) kullanır. Bu özellikler .NET Core 3.0'a eklendi. Diğer hedef çerçeveler bu özniteliklerin herhangi biriyle açıklamalı değil. Bu, geçersiz uyarılar potansiyel sorunları doğru şekilde yansıtmayabileceği anlamına gelir.

## <a name="defaults"></a>Varsayılanları

Derleyici bu kurallara dayalı bir varsayılan belirler:

|Hedef çerçeve|version|C# dil sürümü varsayılan|
|----------------|-------|---------------------------|
|.NET Core|3.x|C# 8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|2.1|C# 8.0|
|.NET Standard|2,0|C# 7.3|
|.NET Standard|1.x|C# 7.3|
|.NET Framework|tümü|C# 7.3|

Projeniz karşılık gelen önizleme dili sürümüne sahip bir önizleme çerçevesi hedeflediğinde, kullanılan dil sürümü önizleme dili sürümüdür. Yayımlanan bir .NET Core sürümünü hedefleyen projeleri etkilemeden, bu önizlemeyle en son özellikleri herhangi bir ortamda kullanırsınız.

## <a name="override-a-default"></a>Varsayılanı geçersiz kılma

C# sürümünüzü açıkça belirtmeniz gerekiyorsa, bunu çeşitli şekillerde yapabilirsiniz:

- [Proje dosyanızı](#edit-the-project-file)el ile edin.
- Bir alt [dizinde birden çok proje için](#configure-multiple-projects)dil sürümünü ayarlayın.
- Derleyici seçeneğini yapılandırın. [ `-langversion` ](compiler-options/langversion-compiler-option.md)

### <a name="edit-the-project-file"></a>Proje dosyasını düzenlemesi

Proje dosyanızdaki dil sürümünü ayarlayabilirsiniz. Örneğin, önizleme özelliklerine açıkça erişmek istiyorsanız, şuna benzer bir öğe ekleyin:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Değer, `preview` derleyicinizin desteklediği en son kullanılabilir önizleme C# dil sürümünü kullanır.

### <a name="configure-multiple-projects"></a>Birden çok projeyi yapılandırma

Birden çok projeyi yapılandırmak için, öğeyi `<LangVersion>` içeren bir **Directory.Build.props** dosyası oluşturabilirsiniz. Bunu genellikle çözüm dizininizde yaparsınız. Çözüm **dizininizdeki Dizin.Build.prop dosyasına aşağıdakileri** ekleyin:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Bu dosyayı içeren dizinin tüm alt dizilişlerinde oluşturur önizleme C# sürümünü kullanır. Daha fazla bilgi için [yapınızı özelleştir'deki makaleye](/visualstudio/msbuild/customize-your-build)bakın.

## <a name="c-language-version-reference"></a>C# dil sürümü başvurusu

Aşağıdaki tablo, geçerli tüm C# dil sürümlerini gösterir. Derleyiciniz, daha eskiyse her değeri anlamaz. .NET Core 3.0 veya daha sonra yüklerseniz, listelenen her şeye erişebilirsiniz.

|Değer|Anlamı|
|------------|-------------|
|Önizleme|Derleyici, en son önizleme sürümünden tüm geçerli dil sözdizimini kabul eder.|
|en son|Derleyici, derleyicinin en son yayımlanan sürümünden (küçük sürüm dahil) sözdizimini kabul eder.|
|sonBüyük|Derleyici, derleyicinin en son yayımlanan ana sürümünden sözdizimini kabul eder.|
|8.0|Derleyici yalnızca C# 8.0 veya daha düşük bir fiyata dahil olan sözdizimini kabul eder.|
|7.3|Derleyici yalnızca C# 7.3 veya daha düşük bir sözdizimini kabul eder.|
|7.2|Derleyici yalnızca C# 7.2 veya daha düşük olan sözdizimini kabul eder.|
|7.1|Derleyici yalnızca C# 7.1 veya daha düşük bir yerde bulunan sözdizimini kabul eder.|
|7|Derleyici yalnızca C# 7.0 veya daha düşük bir fiyata dahil olan sözdizimini kabul eder.|
|6|Derleyici yalnızca C# 6.0 veya daha düşük bir fiyata dahil olan sözdizimini kabul eder.|
|5|Derleyici yalnızca C# 5.0 veya daha düşük bir fiyata dahil olan sözdizimini kabul eder.|
|4|Derleyici yalnızca C# 4.0 veya daha düşük bir sözdizimini kabul eder.|
|3|Derleyici yalnızca C# 3.0 veya daha düşük bir fiyata dahil olan sözdizimini kabul eder.|
|ISO-2|Derleyici yalnızca ISO/IEC 23270:2006 C# (2.0) ile ilgili sözdizimini kabul eder. |
|ISO-1|Derleyici yalnızca ISO/IEC 23270:2003 C# (1.0/1.2) içinde yer alan sözdizimini kabul eder. |
