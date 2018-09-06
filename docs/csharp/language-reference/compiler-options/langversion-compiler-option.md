---
title: -langversion (C# Derleyici Seçenekleri)
ms.date: 05/14/2018
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 9ebc90b3d4f610aec58f950f375d97fd2abf3617
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724561"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (C# Derleyici Seçenekleri)

Seçilen C# dil belirtiminde dahil edilen sözdizimi kabul etmek derleyicinin neden olur.  
  
## <a name="syntax"></a>Sözdizimi  

```console
-langversion:option  
```

## <a name="arguments"></a>Arguments

 `option`  
 Aşağıdaki değerler geçerlidir:  
  
|Seçenek|Açıklama|  
|------------|-------------|  
|default|Derleyici, tüm geçerli dil sözdiziminden destekleyebileceği en son ana sürüm, kabul eder.|
|ISO-1|Derleyici ISO/IEC 23270:2003 C# (1.0/1.2) dahil edilen sözdizimi kabul eden <sup id="TISO1"> [ISO1](#FISO1)</sup>|  
|ISO-2|Derleyici ISO/IEC 23270:2006 C# (2.0) dahil edilen sözdizimi kabul eden <sup id="TISO2"> [ISO2](#FISO2)</sup>|
|3|Derleyici birlikte C# 3.0 veya daha düşük olan sözdizimi kabul eden <sup id="TCS3"> [CS3](#FCS3)</sup>|
|4|Derleyici birlikte C# 4.0 veya daha düşük olan sözdizimi kabul eden <sup id="TCS4"> [CS4](#FCS4)</sup>|
|5|Derleyici birlikte C# 5.0 veya daha düşük olan sözdizimi kabul eden <sup id="TCS5"> [CS5](#FCS5)</sup>|
|6|Derleyici dahil C# 6.0 veya daha düşük olan sözdizimi kabul eden <sup id="TCS6"> [CS6](#FCS6)</sup>|
|7|Derleyici C# 7.0 dahil veya daha düşük olan sözdizimi kabul eden <sup id="TCS7"> [CS7](#FCS7)</sup>|
|7.1|Derleyici C# 7.1 dahil veya daha düşük olan sözdizimi kabul eden <sup id="TCS71"> [CS71](#FCS71)</sup>|
|7.2|Derleyici C# 7.2 dahil veya daha düşük olan sözdizimi kabul eden <sup id="TCS72"> [CS72](#FCS72)</sup>|
|7.3|Derleyici C# 7.3 dahil veya daha düşük olan sözdizimi kabul eden <sup id="TCS73"> [CS73](#FCS73)</sup>|
|en son|Derleyici bunu destekleyen tüm geçerli dili söz dizimini kabul eder.|

<!--- Uncomment and move these above
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS8">[CS8](#FCS8)</sup>|
-->

## <a name="remarks"></a>Açıklamalar

 Meta verileri, C# uygulamanız tarafından başvurulan değil konusu **- langversion** derleyici seçeneği.  
  
 Her C# Derleyici sürümü uzantıları dil belirtimi içerdiğinden **- langversion** derleyicinin önceki bir sürümünü eşdeğer işlevselliğini sağlamaz.  

 C# sürüm güncelleştirmeleri genellikle önemli .NET Framework sürümleri ile çakıştığı karşın, ayrıca, özellikler ve yeni sözdizimini mutlaka bu belirli framework sürümüne bağlı olmak zorunda değildir. Yeni özelliklerin yanı sıra C# düzeltme de yayınlanan yeni bir derleyici güncelleştirme kesinlikle gerektirirken, belirli her özelliği kendi en düşük .NET API veya dahil ederek alt düzey çerçeveleri üzerinde çalışmasına izin verebilir ortak dil çalışma zamanı gereksinimleri vardır. NuGet paketlerini veya diğer kitaplıkları.
  
 Hangi **- langversion** ayarını kullanın, .exe veya .dll oluşturmak için geçerli ortak dil çalışma zamanı sürümü kullanacağı. Bir özel durumdur arkadaş bütünleştirilmiş kodları ve [- moduleassemblyname (C# derleyici seçeneği)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), hangi altında çalışan **- langversion: ISO-1**.  

 C# dili sürümü belirtmek üzere diğer yöntemler için bkz. [C# dil sürümünü seçin](../configure-language-version.md) konu.
  
 Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Derleyici Seçenekleri](index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)  

### <a name="c-language-specification"></a>C# Dil Belirtimi

|Sürüm|Bağlantı|Açıklama|
|-------|----|-----------|
|C# 1.0|[Belge indirin](https://download.microsoft.com/download/a/9/e/a9e229b9-fee5-4c3e-8476-917dee385062/csharp%20language%20specification%20v1.0.doc)|C# dil belirtimi Sürüm 1.0: Microsoft Corporation|
|C# 1.2|[Belge indirin](https://download.microsoft.com/download/5/e/5/5e58be0a-b02b-41ac-a4a3-7a22286214ff/csharp%20language%20specification%20v1.2.doc)|C# dili belirtimi Sürüm 1.2: Microsoft Corporation|
|C# 2.0|[PDF'yi indirin](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/Ecma-334%204th%20edition%20June%202006.pdf)|Standart ECMA-334 4 sürümü|
|C# 3.0|[Belge indirin](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C# dil belirtimi sürüm 3.0: Microsoft Corporation|
|C# 5.0|[PDF'yi indirin](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf)|Standart ECMA-334 5 sürüm|
|C# 6.0|[Bağlantı](../language-specification/index.md)|C# dil belirtimi sürüm 6 - terim ve kısaltmalarla taslak: .NET Foundation|
|C# 7.0 ve üzeri||şu anda kullanılamıyor|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>Tüm dil özellikleri desteklemek için gereken en düşük derleyici sürümü

[↩](#TISO1)<a name="FISO1">ISO1</a>: Microsoft Visual Studio/derleme araçları .net 2002 veya paketlenmiş .net Framework 1.0 derleyici [↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/derleme araçları 2005 veya birlikte .net Framework 2.0 derleyici [↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/derleme araçları 2008 veya paketlenmiş .net Framework 3.5 derleyici [↩](#TCS4) <a name="FCS4">CS4</a>: Microsoft Visual Studio/derleme araçları 2010 veya paketlenmiş .net Framework 4.0 derleyici [↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/derleme araçları 2012 veya paketlenmiş .net Framework 4.5 derleyici [↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/derleme araçları 2015 [↩](#TCS7)<a name="FCS7">CS7</a>: Microsoft Visual Studio / Derleme araçları 2017 [↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/derleme araçları 2017 sürüm 15.3 [↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/derleme araçları 2017 sürüm 15.5 [↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/derleme araçları 2017 sürüm 15.7

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS8)<a name="FCS8">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
