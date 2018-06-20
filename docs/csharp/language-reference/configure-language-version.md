---
title: C# dil sürümünü - C# Kılavuzu seçin
description: Belirli derleyici sürümü kullanılarak sözdizimi doğrulama gerçekleştirmek için derleyici yapılandırma
ms.date: 05/24/2018
ms.openlocfilehash: 9b91e62168ced0f373e1a55def8b279dc64833d8
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208415"
---
# <a name="select-the-c-language-version"></a>C# dil sürümünü seçin

C# Derleyici yayımlandı dil ana en son sürümü varsayılan olarak ayarlanır. Yeni noktası bir dil sürümünü kullanarak Projeyi derlemek tercih edebilirsiniz. Dili, yeni bir sürümünü seçerek sağlar yapmak projenizin en son dil özelliklerini kullanın. Diğer senaryolarda bir proje dili daha eski bir sürümünü kullanırken düzgün bir şekilde derler doğrulamanız gerekebilir.

Bu özelliği geliştirme ortamınızı bir projede yeni dil özellikleri içerecek şekilde karar den yeni sürümlerini SDK'yı ve araçları yüklemek için karar ayrıştırır. En son SDK'yı ve araçları, yapı makinenizde yükleyebilirsiniz. Her proje, derleme için belirli bir dil sürümünü kullanacak şekilde yapılandırılabilir.

Dil sürümünü ayarlamak için birkaç yolu vardır:

- Bağlı bir [Visual Studio hızlı eylem](#visual-studio-quick-action).
- Dil sürümü kümesinde [Visual Studio kullanıcı Arabirimi](#set-the-language-version-in-visual-studio).
- El ile düzenleme, [ **.csproj** dosya](#edit-the-csproj-file).
- Dil sürümü [alt dizindeki birden çok proje için](#configure-multiple-projects).
- Yapılandırma [ `-langversion` derleyici seçeneği](#set-the-langversion-compiler-option).

## <a name="visual-studio-quick-action"></a>Visual Studio hızlı eylemi

Visual Studio, ihtiyacınız olan dil sürümü belirlemenize yardımcı olur. Şu anda yapılandırılmış sürümü için kullanılabilir olmayan bir dil özelliğini kullanırsanız, Visual Studio projesi için dil sürümünü güncelleştirmek için olası bir düzeltme gösterir.

## <a name="set-the-language-version-in-visual-studio"></a>Visual Studio'da dil sürümünü ayarlayın

Visual Studio'daki sürüm ayarlayabilirsiniz. Çözüm Gezgini'nde proje düğümüne sağ tıklayın ve **özellikleri**. Seçin **yapı** sekmesinde ve seçin **Gelişmiş** düğmesi. Açılır listede sürümü seçin. Aşağıdaki resimde "en son" ayarı gösterir:

![Gelişmiş derleme ayarları dil sürümü belirtebileceğiniz ekran görüntüsü](./media/configure-language-version/advanced-build-settings.png)

> [!NOTE]
> Csproj dosyalarınızı güncelleştirmek için Visual Studio IDE kullanırsanız, IDE her yapı yapılandırması için ayrı düğüm oluşturur. Genellikle değerini aynı tüm yapı yapılandırmalarında ayarlamanız, ancak her yapı yapılandırması için açıkça ayarlamak veya bu ayarı değiştirdikten sonra "Tüm yapılandırmaları" seçmek gerekir. Aşağıdaki csproj dosyanızda görürsünüz:
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

## <a name="edit-the-csproj-file"></a>Csproj dosyayı düzenleyin.

Dil sürümü ayarlayabileceğiniz, **.csproj** dosya. Aşağıdaki gibi bir öğe ekleyin:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Değer `latest` C# dili son alt sürümü kullanır. Geçerli değerler şunlardır:

|Değer|Açıklama|
|------------|-------------|
|default|Derleyici destekleyebileceği en son sürümle gelen tüm geçerli dil sözdizimini kabul eder.|
|ISO-1|Derleyici ISO/IEC 23270:2003 C# (1.0/1.2) dahil söz dizimini kabul eder |
|ISO-2|Derleyici ISO/IEC 23270:2006 C# (2.0) dahil söz dizimini kabul eder |
|3|Derleyici dahil C# 3.0 veya daha düşük olan sözdizimini kabul eder.|
|4|Derleyici dahil C# 4.0 veya daha düşük olan sözdizimini kabul eder.|
|5|Derleyici dahil C# 5.0 veya daha düşük olan sözdizimini kabul eder.|
|6|Derleyici dahil C# 6. 0 veya daha düşük olan sözdizimini kabul eder.|
|7|Derleyici dahil C# 7. 0 veya daha düşük olan sözdizimini kabul eder.|
|7.1|Derleyici C# 7.1 dahil ya da daha düşük olan sözdizimini kabul eder.|
|7.2|Derleyici C# 7.2 dahil ya da daha düşük olan sözdizimini kabul eder.|
|7.3|Derleyici C# 7.3 dahil ya da daha düşük olan sözdizimini kabul eder.|
|en son|Derleyici destekleyebileceği tüm geçerli dil söz dizimini kabul eder.|

Özel dizeler `default` ve `latest` son ana (C# 7.0) ve ikincil (C# 7.3) dil sürümleri yapı makinesinde sırasıyla yüklü çözme.

## <a name="configure-multiple-projects"></a>Birden çok proje yapılandırın

Oluşturabileceğiniz bir **Directory.build.props** içeren dosya `<LangVersion>` öğesi birden fazla dizine yapılandırın. Genellikle, çözüm dizininizde yaptığınız. Aşağıdakileri ekleyin bir **Directory.build.props** çözüm dizininize dosyasında:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>7.3</LangVersion>
 </PropertyGroup>
</Project>
```

Şimdi, bu dosyayı içeren dizinin her alt derlemelerde C# sürüm 7.3 sözdizimini kullanır. Daha fazla bilgi için üzerinde makalesine bakın. [yapınızın özelleştirme](/visualstudio/msbuild/customize-your-build).

## <a name="set-the-langversion-compiler-option"></a>Langversion derleyici seçeneği ayarlama

Kullanabileceğiniz `-langversion` komut satırı seçeneği. Daha fazla bilgi için üzerinde makalesine bakın. [- langversion](../language-reference/compiler-options/langversion-compiler-option.md) derleyici seçeneği. Geçerli değerler listesi yazarak görebilirsiniz `csc -langversion:?`.
