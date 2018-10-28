---
title: Visual Basic dil sürümünü seçin
description: Belirli bir derleyici sürümü kullanarak söz dizimi doğrulama gerçekleştirmek için derleyicinin yapılandırın.
ms.date: 05/24/2018
ms.openlocfilehash: 7628b5a7c27f5b26171d42e44a58598ef3d5d49f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194728"
---
# <a name="select-the-visual-basic-language-version"></a>Visual Basic dil sürümünü seçin

Visual Basic derleyici varsayılan olarak en son ana sürüm dilinin kullanıma sundu. Yeni noktası bir dil sürümünü kullanarak herhangi bir projeyi derlemek tercih edebilirsiniz. Daha yeni bir dil sürümü seçme sağlayan sağlamak için projenizi en son dil özelliklerini kullanabilirsiniz. Diğer senaryolarda, bir proje dili daha eski bir sürümünü kullanırken düzgün bir şekilde derlendiğinden doğrulamanız gerekebilir.

Bu özellik, bir projede yeni dil özellikleri eklemelerine kararı geliştirme ortamınızdan araçları ve SDK'sı yeni sürümlerini yüklemek için karar ayırır. En son SDK'sı ve araçları, yapı makinesinde yükleyebilirsiniz. Her proje, derleme için belirli bir dil sürümünü kullanmak için yapılandırılabilir.

Dil sürümünü ayarlamak için üç yolu vardır:

- El ile düzenlemeniz, [ **.vbproj** dosyası](#edit-the-vbproj-file)
- Dil sürümünü ayarlama [bir alt dizinde birden çok proje için](#configure-multiple-projects)
- Yapılandırma [ `-langversion` derleyici seçeneği](#set-the-langversion-compiler-option)

## <a name="edit-the-vbproj-file"></a>Vbproj dosyayı Düzenle

Dil sürümü ayarlayabilirsiniz, **.vbproj** dosya. Aşağıdaki öğeyi ekleyin:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Değer `latest` Visual Basic dili küçük en son sürümünü kullanır. Geçerli değerler şunlardır:

|Değer|Açıklama|
|------------|-------------|
|default|Derleyici, tüm geçerli dil sözdiziminden destekleyebileceği en son ana sürüm, kabul eder.|
|9|Derleyici, Visual Basic 9.0 dahil veya daha düşük olan söz dizimini kabul eder.|
|10|Derleyici, Visual Basic 10.0 dahil veya daha düşük olan söz dizimini kabul eder.|
|11|Derleyici dahil Visual Basic 11.0 veya daha düşük olan söz dizimini kabul eder.|
|12|Derleyici dahil Visual Basic 12.0 veya daha düşük olan söz dizimini kabul eder.|
|14|Derleyici, Visual Basic 14.0 dahil veya daha düşük olan söz dizimini kabul eder.|
|15|Derleyici, Visual Basic 15.0 dahil veya daha düşük olan söz dizimini kabul eder.|
|15.3|Derleyici, Visual Basic 15.3 dahil veya daha düşük olan söz dizimini kabul eder.|
|15.5|Derleyici, Visual Basic 15.5 dahil veya daha düşük olan söz dizimini kabul eder.|
|en son|Derleyici bunu destekleyen tüm geçerli dili söz dizimini kabul eder.|

Özel dizeler `default` ve `latest` sırasıyla yapı makinesinde yüklü en son büyük ve küçük dil sürümleri.

## <a name="configure-multiple-projects"></a>Birden çok proje yapılandırma

Oluşturabileceğiniz bir **Directory.build.props** içeren dosya `<LangVersion>` birden çok dizini yapılandırma öğesi. Genellikle, çözüm dizininizde yaparsınız. Ekleyin bir **Directory.build.props** çözüm dizininizde dosya:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

Artık, her alt bu dosyayı içeren dizine yapılarında Visual Basic sürüm 15.5 sözdizimi kullanır. Daha fazla bilgi için makaleye bakın [derlemenizi özelleştirme](/visualstudio/msbuild/customize-your-build.md).

## <a name="set-the-langversion-compiler-option"></a>Langversion derleyici seçeneği ayarlama

Kullanabileceğiniz `-langversion` komut satırı seçeneği. Daha fazla bilgi için makaleye bakın [- langversion](../reference/command-line-compiler/langversion.md) derleyici seçeneği. Yazarak geçerli değerlerin bir listesini görebilirsiniz `vbc -langversion:?` .
