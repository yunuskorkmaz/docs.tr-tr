---
title: C#Dil sürümü oluşturma - C# Kılavuzu
description: Hakkında nasıl bilgi C# dil sürümü, projenizi temel alarak belirlenir ve farklı değerler, el ile şekilde ayarlayabilirsiniz.
ms.date: 07/10/2019
ms.openlocfilehash: e35fdf2bcdb1a31b752c760f3f6df59232e498a4
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68236090"
---
# <a name="c-language-versioning"></a>C#Dil sürümü oluşturma

C# Derleyici, proje hedef Framework'ü veya çerçeveleri göre varsayılan dil sürümü belirler. Bunun nedeni, C# dil türleri veya her bir .NET uygulamasında kullanılabilir olmayan bir çalışma zamanı bileşenlerini kullanan özellikler olabilir. Bu ayrıca, projenizin karşı yerleşik her hedef için en yüksek uyumlu dil sürümünü varsayılan olarak almasını sağlar.

## <a name="defaults"></a>Varsayılanları

Derleyici, bu kurallara dayalı bir varsayılan belirler:

|Hedef Çerçeve|sürüm|C#Dil sürümü varsayılan|
|----------------|-------|---------------------------|
|.NET Core|3.x|C#8.0|
|.NET Core|2.x|C# 7.3|
|.NET Standard|tüm|C# 7.3|
|.NET Framework|tüm|C# 7.3|

## <a name="default-for-previews"></a>Preview sürümleri için varsayılan

Projenize karşılık gelen bir önizleme dil sürümü olan bir önizleme framework hedeflediğinde, kullanılan dil sürümü Önizleme dil sürümüdür. Bu, her türlü ortamda bu Önizleme ile projelerinizi etkilemeden yayımlanmış bir .NET Core sürümünü hedefleyen çalışacağı garanti en son özellikleri kullanabileceğiniz sağlar.

## <a name="overriding-a-default"></a>Varsayılan bir geçersiz kılma

Belirtmeniz gerekiyorsa, C# sürüm açıkça çeşitli yollarla bunu yapabilirsiniz:

- El ile düzenlemeniz, [proje dosyası](#edit-the-project-file).
- Dil sürümünü ayarlama [bir alt dizinde birden çok proje için](#configure-multiple-projects).
- Yapılandırma [ `-langversion` derleyici seçeneği](compiler-options/langversion-compiler-option.md)

### <a name="edit-the-project-file"></a>Proje dosyası Düzenle

Dil sürümü, proje dosyasında ayarlayabilirsiniz. Açıkça özelliklerin önizlemesini sağlamak erişim istediyseniz, örneğin, şunun gibi bir öğe ekleyebilirsiniz:

```xml
<PropertyGroup>
   <LangVersion>preview</LangVersion>
</PropertyGroup>
```

Değer `preview` kullanılabilir en son Önizleme kullanan C# derleyicinizin destekleyen dili.

### <a name="configure-multiple-projects"></a>Birden çok proje yapılandırma

Oluşturabileceğiniz bir **Directory.Build.props** içeren dosya `<LangVersion>` birden çok dizini yapılandırma öğesi. Genellikle, çözüm dizininizde yaparsınız. Ekleyin bir **Directory.Build.props** çözüm dizininizde dosya:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>preview</LangVersion>
 </PropertyGroup>
</Project>
```

Bu dosyayı içeren dizine her alt yapılarında Önizleme artık, kullanacak C# sürümü. Daha fazla bilgi için makaleye bakın [derlemenizi özelleştirme](/visualstudio/msbuild/customize-your-build).

## <a name="c-language-version-reference"></a>C#Dil sürümü başvurusu

Aşağıdaki tablo geçerli tüm gösterir C# dil sürümleri. Eski ise, derleyici her değer mutlaka anlamayabilir. .NET Core 3.0 yüklerseniz, listelenen her şeye erişimi gerekir.

|Değer|Açıklama|
|------------|-------------|
|önizleme|Derleyici, en son Önizleme sürümünden tüm geçerli dili söz dizimini kabul eder.|
|latest|Bir derleyici sürümünden en son yayımlanan (alt sürümü dahil) derleyici sözdizimini kabul eder.|
|latestMajor|Bir derleyici sürümünden en son yayımlanan önemli derleyici sözdizimini kabul eder.|
|8.0|Dahil edilen sözdizimi derleyici kabul C# 8.0 veya daha düşük.|
|7.3|Dahil edilen sözdizimi derleyici kabul C# 7.3 ya da daha düşük.|
|7.2|Dahil edilen sözdizimi derleyici kabul C# 7.2 veya daha düşük.|
|7.1|Dahil edilen sözdizimi derleyici kabul C# 7.1 veya daha düşük.|
|7|Dahil edilen sözdizimi derleyici kabul C# 7.0 ya da daha düşük.|
|6|Dahil edilen sözdizimi derleyici kabul C# 6.0 veya daha düşük.|
|5|Dahil edilen sözdizimi derleyici kabul C# 5.0 veya daha düşük.|
|4|Dahil edilen sözdizimi derleyici kabul C# 4.0 veya daha düşük.|
|3|Dahil edilen sözdizimi derleyici kabul C# 3.0 veya daha düşük.|
|ISO-2|Derleyici ISO/IEC 23270:2006 dahil edilen sözdizimi kabul eden C# (2.0) |
|ISO-1|Derleyici ISO/IEC 23270:2003 dahil edilen sözdizimi kabul eden C# (1.0/1.2) |
