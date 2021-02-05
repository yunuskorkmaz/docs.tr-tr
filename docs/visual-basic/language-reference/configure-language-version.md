---
title: Visual Basic dil sürümünü seçin
description: Derleyiciyi belirli bir derleyici sürümünü kullanarak sözdizimi doğrulaması gerçekleştirecek şekilde yapılandırın.
ms.date: 05/24/2018
ms.openlocfilehash: 09503db726f9d993bc986860c57aa98652b696d1
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585461"
---
# <a name="select-the-visual-basic-language-version"></a>Visual Basic dil sürümünü seçin

Visual Basic derleyici varsayılan olarak yayınlanan dilin en son ana sürümüdür. Dilin yeni bir noktası sürümünü kullanarak herhangi bir projeyi derlemeyi seçebilirsiniz. Dilin daha yeni bir sürümünü seçmek, projenizin en son dil özelliklerini kullanmasını sağlar. Diğer senaryolarda, dilin eski bir sürümünü kullanırken bir projenin düzgün şekilde derlendiğini doğrulamanız gerekebilir.

Bu özellik, bir projedeki yeni dil özelliklerini birleştirme kararı vermeden geliştirme ortamınızda SDK ve araçların yeni sürümlerini yüklemeye yönelik kararı ayırır. Yapı makinenize en son SDK ve araçları yükleyebilirsiniz. Her proje, derlemesi için dilin belirli bir sürümünü kullanacak şekilde yapılandırılabilir.

Dil sürümünü ayarlamak için üç yol vardır:

- [ **. Vbproj** dosyanızı el ile düzenleme](#edit-the-vbproj-file)
- [Alt dizindeki birden çok proje için](#configure-multiple-projects) dil sürümünü ayarlama
- [ `-langversion` Derleyici seçeneğini](#set-the-langversion-compiler-option) yapılandırma

## <a name="edit-the-vbproj-file"></a>Vbproj dosyasını düzenleme

**. Vbproj** dosyanızdaki dil sürümünü ayarlayabilirsiniz. Şu öğeyi ekleyin:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Değer `latest` Visual Basic dilinin en son ikincil sürümünü kullanır. Geçerli değerler:

|Değer|Anlamı|
|------------|-------------|
|default|Derleyici, destekleyebileceği en son ana sürümden tüm geçerli dil sözdizimini kabul eder.|
|9|Derleyici yalnızca Visual Basic 9,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|10|Derleyici yalnızca Visual Basic 10,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|11|Derleyici yalnızca Visual Basic 11,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|12|Derleyici yalnızca Visual Basic 12,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|14|Derleyici yalnızca Visual Basic 14,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|15|Derleyici yalnızca Visual Basic 15,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|15.3|Derleyici yalnızca Visual Basic 15,3 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|15.5|Derleyici yalnızca Visual Basic 15,5 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|16|Derleyici yalnızca Visual Basic 16 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|16.9|Derleyici yalnızca Visual Basic 16,9 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|en son|Derleyici, destekleyebileceği tüm geçerli dil sözdizimini kabul eder.|

Özel dizeler, `default` `latest` sırasıyla derleme makinesinde yüklü en son büyük ve küçük dil sürümlerine çözümlenir.

## <a name="configure-multiple-projects"></a>Birden çok proje yapılandırma

Birden çok dizini yapılandırmak için öğesini içeren bir **Dizin. Build. props** dosyası oluşturabilirsiniz `<LangVersion>` . Bunu genellikle çözüm dizininizde yapabilirsiniz. Aşağıdakileri çözüm dizininizde bir **Dizin. Build. props** dosyasına ekleyin:

```xml
<Project>
 <PropertyGroup>
   <LangVersion>15.5</LangVersion>
 </PropertyGroup>
</Project>
```

Şimdi, bu dosyayı içeren dizinin her alt dizinindeki derlemeler Visual Basic sürüm 15,5 sözdizimini kullanacaktır. Daha fazla bilgi için, [yapınızı özelleştirme](/visualstudio/msbuild/customize-your-build)başlıklı makaleye bakın.

## <a name="set-the-langversion-compiler-option"></a>Langversion derleyici seçeneğini ayarlayın

`-langversion`Komut satırı seçeneğini kullanabilirsiniz. Daha fazla bilgi için, [-langversion](../reference/command-line-compiler/langversion.md) derleyici seçeneğinde makalesine bakın. Yazarak geçerli değerlerin bir listesini görebilirsiniz  `vbc -langversion:?` .
