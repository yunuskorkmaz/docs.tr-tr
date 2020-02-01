---
title: -langversion (C# derleyici seçenekleri)
ms.date: 08/23/2019
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 007b10f6f27233c43caad4c1910e3d1158682950
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920360"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (C# derleyici seçenekleri)

Derleyicinin yalnızca seçilen C# dil belirtiminde bulunan sözdizimini kabul etmesine neden olur.

## <a name="syntax"></a>Sözdizimi

```console
-langversion:option
```

## <a name="arguments"></a>Arguments

`option`

Aşağıdaki değerler geçerlidir:

|Seçenek|Açıklama|
|------------|-------------|
|önizleme|Derleyici, destekleyebileceği en son önizleme sürümünden tüm geçerli dil sözdizimini kabul eder.|
|latest|Derleyici, destekleyebileceği en son sürümden (ikincil yayınlar dahil) tüm geçerli dil sözdizimini kabul eder.|
|Latestana|Derleyici, destekleyebileceği en son ana sürümden tüm geçerli dil sözdizimini kabul eder.|
|8.0|Derleyici yalnızca C# 8,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|7.3|Derleyici yalnızca C# 7,3 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|7.2|Derleyici yalnızca C# 7,2 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|7.1|Derleyici yalnızca C# 7,1 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|7|Derleyici yalnızca C# 7,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|6|Derleyici yalnızca C# 6,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|5|Derleyici yalnızca C# 5,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|4|Derleyici yalnızca C# 4,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|3|Derleyici yalnızca C# 3,0 veya daha düşük bir sözdiziminde bulunan sözdizimini kabul eder.|
|ISO-2|Derleyici yalnızca ISO/ıEC 23270:2006 C# (2,0) içinde bulunan söz dizimini kabul eder.|
|ISO-1|Derleyici yalnızca ISO/ıEC 23270:2003 C# (1.0/1.2) içinde bulunan söz dizimini kabul eder.|

Varsayılan dil sürümü, uygulamanız için hedef çerçeveye ve SDK 'nın veya Visual Studio 'nun yüklü olduğu sürüme bağlıdır. Bu kurallar, [dil sürümü yapılandırma](../configure-language-version.md#defaults) makalesinde tanımlanmıştır.

## <a name="remarks"></a>Açıklamalar

C# Uygulamanız tarafından başvurulan meta veriler, **-langversion** derleyici seçeneği değildir.

C# Derleyicinin her sürümü dil belirtimine uzantılar içerdiğinden, **-langversion** size derleyicinin önceki bir sürümünün eşdeğer işlevlerini sağlamaz.

Ayrıca, sürüm C# güncelleştirmeleri genellikle büyük .NET Framework sürümleriyle aynı olsa da yeni söz dizimi ve Özellikler ilgili Framework sürümüne bağlı değildir. Yeni özellikler, C# düzeltmeden sonra da yayınlanan yeni bir derleyici güncelleştirmesi gerektirirken, her bir özellik kendi minimum .NET API 'Sine veya NuGet paketlerini ya da diğer kitaplıkları ekleyerek alt düzey çerçeveler üzerinde çalışmasına izin veren ortak dil çalışma zamanı gereksinimlerine sahiptir.

Kullandığınız dil **sürümü** ayarı ne olursa olsun,. exe veya. dll dosyanızı oluşturmak için ortak dil çalışma zamanının güncel sürümünü kullanın. Tek bir özel durum, **-langversion: ISO-1**altında çalışan arkadaş derlemelerdir ve [-moduleassemblyname (C# derleyici seçeneği)](./moduleassemblyname-compiler-option.md).

C# Dil sürümünü belirtmek için diğer yollar için [ C# dil sürümünü seçme](../configure-language-version.md) makalesini inceleyin.

Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.

## <a name="c-language-specification"></a>C# dili belirtimi

|Sürüm|Bağlantı|Açıklama|
|-------|----|-----------|
|C#7,0 ve üzeri||Şu anda kullanılamıyor|
|C#6,0|[Bağlantı](/dotnet/csharp/language-reference/language-specification/introduction)|C#Dil belirtimi sürüm 6-resmi olmayan taslak: .NET Foundation|
|C#5,0|[PDF'yi indirin](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Standart ECMA-334 5 sürümü|
|C#3,0|[BELGEYI indir](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C#Dil belirtimi sürüm 3,0: Microsoft Corporation|
|C#2,0|[PDF'yi indirin](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|Standart ECMA-334 4 sürümü|
|C#1,2|[BELGEYI indir](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|C#Dil belirtimi sürüm 1,2: Microsoft Corporation|
|C#1,0|[BELGEYI indir](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|C#Dil belirtimi sürüm 1,0: Microsoft Corporation|

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Tüm dil özelliklerini desteklemek için gereken en düşük SDK sürümü

Aşağıdaki tabloda, karşılık gelen dil sürümünü destekleyen C# DERLEYICIYLE SDK 'nın en düşük sürümleri listelenmiştir:

|C#Sürüm|En düşük SDK sürümü|
|----------|-------------------|
|C# 8.0| Microsoft Visual Studio/derleme araçları 2019, sürüm 16,3 veya .NET Core 3,0 SDK |
|C# 7.3| Microsoft Visual Studio/derleme araçları 2017, sürüm 15,7 |
|C# 7.2| Microsoft Visual Studio/derleme araçları 2017, sürüm 15,5 |
|C# 7.1| Microsoft Visual Studio/derleme araçları 2017, sürüm 15,3 |
|C# 7.0| Microsoft Visual Studio/derleme araçları 2017 |
|C# 6| Microsoft Visual Studio/derleme araçları 2015 |
|C#e| Microsoft Visual Studio/derleme araçları 2012 veya paketlenmiş .NET Framework 4,5 derleyicisi |
|C# 4| Microsoft Visual Studio/derleme araçları 2010 veya paketlenmiş .NET Framework 4,0 derleyicisi |
|C#03| Microsoft Visual Studio/derleme araçları 2008 veya paketlenmiş .NET Framework 3,5 derleyicisi |
|C#iki| Microsoft Visual Studio/derleme araçları 2005 veya paketlenmiş .NET Framework 2,0 derleyicisi |
|C#1.0/1.2 | Microsoft Visual Studio/derleme araçları .NET 2002 veya paketlenmiş .NET Framework 1,0 derleyicisi |

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
