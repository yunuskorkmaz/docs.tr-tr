---
title: -langversion (C# Derleyici Seçenekleri)
ms.date: 08/23/2019
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 007b10f6f27233c43caad4c1910e3d1158682950
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920360"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (C# Derleyici Seçenekleri)

Derleyicinin yalnızca seçilen C# dil belirtimine dahil olan sözdizimini kabul etmesini n için neden olur.

## <a name="syntax"></a>Sözdizimi

```console
-langversion:option
```

## <a name="arguments"></a>Bağımsız Değişkenler

`option`

Aşağıdaki değerler geçerlidir:

|Seçenek|Anlamı|
|------------|-------------|
|Önizleme|Derleyici, desteklenebildiği en son önizleme sürümünden tüm geçerli dil sözdizimini kabul eder.|
|en son|Derleyici, desteklenebildiği en son sürümdeki tüm geçerli dil sözdizimini (küçük sürümler dahil) kabul eder.|
|sonBüyük|Derleyici, desteklenebildiği en son ana sürümden tüm geçerli dil sözdizimini kabul eder.|
|8.0|Derleyici yalnızca C# 8.0 veya daha düşük bir fiyata dahil olan sözdizimini kabul eder.|
|7.3|Derleyici yalnızca C# 7.3 veya daha düşük bir sözdizimini kabul eder.|
|7.2|Derleyici yalnızca C# 7.2 veya daha düşük olan sözdizimini kabul eder.|
|7.1|Derleyici yalnızca C# 7.1 veya daha düşük bir yerde bulunan sözdizimini kabul eder.|
|7|Derleyici yalnızca C# 7.0 veya daha düşük bir fiyata dahil olan sözdizimini kabul eder.|
|6|Derleyici yalnızca C# 6.0 veya daha düşük bir fiyata dahil olan sözdizimini kabul eder.|
|5|Derleyici yalnızca C# 5.0 veya daha düşük bir fiyata dahil olan sözdizimini kabul eder.|
|4|Derleyici yalnızca C# 4.0 veya daha düşük bir sözdizimini kabul eder.|
|3|Derleyici yalnızca C# 3.0 veya daha düşük bir fiyata dahil olan sözdizimini kabul eder.|
|ISO-2|Derleyici yalnızca ISO/IEC 23270:2006 C# (2.0) ile ilgili sözdizimini kabul eder.|
|ISO-1|Derleyici yalnızca ISO/IEC 23270:2003 C# (1.0/1.2) içinde yer alan sözdizimini kabul eder.|

Varsayılan dil sürümü, uygulamanızın hedef çerçevesine ve Yüklü SDK veya Visual Studio sürümüne bağlıdır. Bu [kurallar, dil sürümü makalesinin yapılandırılmasında](../configure-language-version.md#defaults) tanımlanır.

## <a name="remarks"></a>Açıklamalar

C# uygulamanız tarafından başvurulan meta veriler **-langversion** derleyiciseçeneğine tabi değildir.

C# derleyicisinin her sürümü dil belirtimine uzantıları içerdiğinden, **-langversion** size derleyicinin önceki bir sürümünün eşdeğer işlevselliğini vermez.

Ayrıca, C# sürüm güncelleştirmeleri genellikle büyük .NET Framework sürümleriyle çakışsa da, yeni sözdizimi ve özellikleri bu belirli çerçeve sürümüne bağlı değildir. Yeni özellikler kesinlikle C# revizyonuyla birlikte yayımlanan yeni bir derleyici güncelleştirmesi gerektirir, ancak her özel özelliğin kendi minimum .NET API'si veya NuGet paketlerini veya diğer kitaplıkları ekleyerek alt düzey çerçevelerde çalışmasına izin veren ortak dil çalışma süresi gereksinimleri vardır.

Hangi **-langversion** ayarını kullandığınızdan bağımsız olarak, .exe veya .dll'nizi oluşturmak için ortak dil çalışma zamanının geçerli sürümünü kullanın. Bir istisna arkadaş derlemeleri ve [-moduleassemblyname (C# Derleyici Seçeneği)](./moduleassemblyname-compiler-option.md), altında çalışan **-langversion:ISO-1**.

C# dil sürümünü belirtmenin diğer yolları için [C# dil sürümünü seç makalesine](../configure-language-version.md) bakın.

Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>

## <a name="c-language-specification"></a>C# dili belirtimi

|Sürüm|Bağlantı|Açıklama|
|-------|----|-----------|
|C# 7.0 ve sonrası||şu anda mevcut değil|
|C# 6.0|[Bağlantı](/dotnet/csharp/language-reference/language-specification/introduction)|C# Dil Belirtimi Sürüm 6 - Resmi Olmayan Taslak: .NET Vakfı|
|C# 5.0|[PDF’yi İndir](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Standart ECMA-334 5.Baskı|
|C# 3.0|[DOC'u İndir](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C# Dil Belirtimi Sürüm 3.0: Microsoft Corporation|
|C# 2.0|[PDF’yi İndir](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|Standart ECMA-334 4.Baskı|
|C# 1.2|[DOC'u İndir](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|C# Dil Belirtimi Sürüm 1.2: Microsoft Corporation|
|C# 1.0|[DOC'u İndir](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|C# Dil Belirtimi Sürüm 1.0: Microsoft Corporation|

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>Tüm dil özelliklerini desteklemek için gereken minimum SDK sürümü

Aşağıdaki tabloda, SDK'nın ilgili dil sürümünü destekleyen C# derleyicisi ile en az sürümleri listelenmiştir:

|C# sürümü|Minimum SDK sürümü|
|----------|-------------------|
|C# 8.0| Microsoft Visual Studio/Build Tools 2019, sürüm 16.3 veya .NET Core 3.0 SDK |
|C# 7.3| Microsoft Visual Studio/Build Tools 2017, sürüm 15.7 |
|C# 7.2| Microsoft Visual Studio/Build Tools 2017, sürüm 15.5 |
|C# 7.1| Microsoft Visual Studio/Build Tools 2017, sürüm 15.3 |
|C# 7.0| Microsoft Visual Studio/Build Tools 2017 |
|C# 6| Microsoft Visual Studio/Build Tools 2015 |
|C# 5| Microsoft Visual Studio/Build Tools 2012 veya birlikte verilen .NET Framework 4.5 derleyicisi |
|C# 4| Microsoft Visual Studio/Build Tools 2010 veya birlikte verilen .NET Framework 4.0 derleyicisi |
|C# 3| Microsoft Visual Studio/Build Tools 2008 veya birlikte verilen .NET Framework 3.5 derleyicisi |
|C# 2| Microsoft Visual Studio/Build Tools 2005 veya birlikte verilen .NET Framework 2.0 derleyicisi |
|C# 1.0/1.2 | Microsoft Visual Studio/Build Tools .NET 2002 veya birlikte .NET Framework 1.0 derleyicisi |

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
