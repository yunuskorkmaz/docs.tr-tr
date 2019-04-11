---
title: Seçin C# dil sürümü - C# Kılavuzu
description: Belirli bir derleyici sürümü kullanarak söz dizimi doğrulama gerçekleştirmek için derleyici yapılandırma
ms.date: 02/28/2019
ms.openlocfilehash: feb3e51a107f9830071b55c7985f202edc842f4a
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480748"
---
# <a name="select-the-c-language-version"></a>Seçin C# dil sürümü

C# Derleyici, proje hedef Framework'ü veya çerçeveleri göre varsayılan dil sürümü belirler. Projenize karşılık gelen bir önizleme dil sürümü olan bir önizleme framework hedeflediğinde, kullanılan dil sürümü Önizleme dil sürümüdür. Bir önizleme çerçeve proje hedeflemiyor, kullanılan dil son alt sürüm sürümüdür.

Örneğin, .NET Core 3.0 Önizleme dönemi boyunca herhangi hedefleyen bir proje `netcoreapp3.0` veya `netstandard2.1` (hem de Önizleme) kullanacağı C# 8.0 Dil (Ayrıca önizlemede). Herhangi bir kullanıma sunulan sürümünü hedefleyen projelerin kullanacağı C# 7.3 (son yayımlanan sürümü). Bu davranışı, .NET Framework'ü hedefleyen herhangi bir projenin son kullanacağı anlamına gelir (C# 7.3). 

Bu özellik, bir projede yeni dil özellikleri eklemelerine kararı geliştirme ortamınızdan araçları ve SDK'sı yeni sürümlerini yüklemek için karar ayırır. En son SDK'sı ve araçları, yapı makinesinde yükleyebilirsiniz. Her proje, derleme için belirli bir dil sürümünü kullanmak için yapılandırılabilir. Varsayılan davranış, yalnızca projeleri bu çerçeveleri hedeflediğinizde yeni türleri veya yeni bir CLR davranış dayalı tüm dil özelliklerinin etkin olduğu anlamına gelir.

Bir dil sürümü belirterek varsayılan davranışı geçersiz kılabilirsiniz. Dil sürümünü ayarlamak için birkaç yol vardır:

- Dayanan bir [Visual Studio hızlı eylem](#visual-studio-quick-action).
- Dil sürümü ayarlama [Visual Studio UI](#set-the-language-version-in-visual-studio).
- El ile düzenlemeniz, [ **.csproj** dosya](#edit-the-csproj-file).
- Dil sürümünü ayarlama [bir alt dizinde birden çok proje için](#configure-multiple-projects).
- Yapılandırma [ `-langversion` derleyici seçeneği](#set-the-langversion-compiler-option).

## <a name="visual-studio-quick-action"></a>Visual Studio hızlı eylem

Visual Studio ihtiyacınız olan dil sürümü belirlemenize yardımcı olur. Şu anda yapılandırılmış sürümü için kullanılabilir olmayan bir dil özelliğini kullanırsanız, Visual Studio projesi için dil sürümünü güncelleştirmek için bir olası düzeltme gösterir.

## <a name="set-the-language-version-in-visual-studio"></a>Visual Studio'da dil sürümünü ayarlama

Visual Studio'da sürüm ayarlayabilirsiniz. Çözüm Gezgini'nde proje düğümüne sağ tıklayıp **özellikleri**. Seçin **derleme** sekmenize **Gelişmiş** düğmesi. Açılır menüden sürümü seçin. Aşağıdaki görüntüde "son" ayarı gösterilmektedir:

![Dil sürümü belirleyebileceğiniz Gelişmiş derleme ayarları görüntüsü](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> Csproj dosyalarınızı güncelleştirmek için Visual Studio IDE kullanırsanız, IDE her derleme yapılandırması için ayrı bir düğüm oluşturur. Genellikle aynı tüm derleme yapılandırmalarında ayarlamanız, ancak her derleme yapılandırması için açık olarak veya bu ayarı değiştirdiğinizde "Tüm yapılandırmaları" gerekir. Csproj dosyanıza aşağıdaki görüntüyle karşılaşırsınız:
>
>```xml
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
>  <LangVersion>latest</LangVersion>
></PropertyGroup>
>
> <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
>  <LangVersion>latest</LangVersion>
> </PropertyGroup>
> ```
>

## <a name="edit-the-csproj-file"></a>Csproj dosyasını düzenleyin

Dil sürümü ayarlayabilirsiniz, **.csproj** dosya. Aşağıdaki gibi bir öğe ekleyin:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Değer `latest` en son sürümü kullanan C# dili. Geçerli değerler şunlardır:

|Değer|Açıklama|
|------------|-------------|
|önizleme|Derleyici, en son Önizleme sürümünden tüm geçerli dili söz dizimini kabul eder.|
|en son|Bir derleyici sürümünden en son yayımlanan (alt sürümü dahil) derleyici sözdizimini kabul eder.|
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

## <a name="configure-multiple-projects"></a>Birden çok proje yapılandırma

Oluşturabileceğiniz bir **Directory.Build.props** içeren dosya `<LangVersion>` birden çok dizini yapılandırma öğesi. Genellikle, çözüm dizininizde yaparsınız. Ekleyin bir **Directory.Build.props** çözüm dizininizde dosya:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

Artık, her alt bu dosyayı içeren dizine yapılarında kullanacak C# sürüm 7.3 söz dizimi. Daha fazla bilgi için makaleye bakın [derlemenizi özelleştirme](/visualstudio/msbuild/customize-your-build).

## <a name="set-the-langversion-compiler-option"></a>Langversion derleyici seçeneği ayarlama

Kullanabileceğiniz `-langversion` komut satırı seçeneği. Daha fazla bilgi için makaleye bakın [- langversion](../language-reference/compiler-options/langversion-compiler-option.md) derleyici seçeneği. Yazarak geçerli değerlerin bir listesini görebilirsiniz `csc -langversion:?`.
