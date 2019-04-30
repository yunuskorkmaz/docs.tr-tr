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
ms.openlocfilehash: af30095c18a333d5ac3089fe3bf201c32739d9cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662809"
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
|önizleme|Derleyici, tüm geçerli dil sözdiziminden destekleyebileceği en son Önizleme sürümü, kabul eder.|
|en son|Derleyici, tüm geçerli dil sözdiziminde destekleyebileceği en son sürümünü (küçük sürümleri dahil) kabul eder.|
|latestMajor|Derleyici, tüm geçerli dil sözdiziminden destekleyebileceği en son ana sürüm, kabul eder.|
|8.0|Dahil edilen sözdizimi derleyici kabul C# 8.0 veya daha düşük. <sup id="TCS80">[CS80](#FCS80)</sup>|
|7.3|Derleyici C# 7.3 dahil veya daha düşük olan sözdizimi kabul eden <sup id="TCS73"> [CS73](#FCS73)</sup>|
|7.2|Derleyici C# 7.2 dahil veya daha düşük olan sözdizimi kabul eden <sup id="TCS72"> [CS72](#FCS72)</sup>|
|7.1|Derleyici C# 7.1 dahil veya daha düşük olan sözdizimi kabul eden <sup id="TCS71"> [CS71](#FCS71)</sup>|
|7|Derleyici C# 7.0 dahil veya daha düşük olan sözdizimi kabul eden <sup id="TCS7"> [CS7](#FCS7)</sup>|
|6|Derleyici dahil C# 6.0 veya daha düşük olan sözdizimi kabul eden <sup id="TCS6"> [CS6](#FCS6)</sup>|
|5|Derleyici birlikte C# 5.0 veya daha düşük olan sözdizimi kabul eden <sup id="TCS5"> [CS5](#FCS5)</sup>|
|4|Derleyici birlikte C# 4.0 veya daha düşük olan sözdizimi kabul eden <sup id="TCS4"> [CS4](#FCS4)</sup>|
|3|Derleyici birlikte C# 3.0 veya daha düşük olan sözdizimi kabul eden <sup id="TCS3"> [CS3](#FCS3)</sup>|
|ISO-2|Derleyici ISO/IEC 23270:2006 C# (2.0) dahil edilen sözdizimi kabul eden <sup id="TISO2"> [ISO2](#FISO2)</sup>|
|ISO-1|Derleyici ISO/IEC 23270:2003 C# (1.0/1.2) dahil edilen sözdizimi kabul eden <sup id="TISO1"> [ISO1](#FISO1)</sup>|  

## <a name="remarks"></a>Açıklamalar

 Meta verileri, C# uygulamanız tarafından başvurulan değil konusu **- langversion** derleyici seçeneği.  
  
 Her C# Derleyici sürümü uzantıları dil belirtimi içerdiğinden **- langversion** derleyicinin önceki bir sürümünü eşdeğer işlevselliğini sağlamaz.  

 C# sürüm güncelleştirmeleri genellikle önemli .NET Framework sürümleri ile çakıştığı karşın, ayrıca, özellikler ve yeni sözdizimini mutlaka bu belirli framework sürümüne bağlı olmak zorunda değildir. Yeni özelliklerin yanı sıra C# düzeltme de yayınlanan yeni bir derleyici güncelleştirme kesinlikle gerektirirken, belirli her özelliği kendi en düşük .NET API veya dahil ederek alt düzey çerçeveleri üzerinde çalışmasına izin verebilir ortak dil çalışma zamanı gereksinimleri vardır. NuGet paketlerini veya diğer kitaplıkları.
  
 Hangi **- langversion** ayarını kullanın, .exe veya .dll oluşturmak için geçerli ortak dil çalışma zamanı sürümü kullanacağı. Bir özel durumdur arkadaş bütünleştirilmiş kodları ve [- moduleassemblyname (C# derleyici seçeneği)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), hangi altında çalışan **- langversion: ISO-1**.  

 C# dili sürümü belirtmek üzere diğer yöntemler için bkz. [C# dil sürümünü seçin](../configure-language-version.md) konu.
  
 Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  

## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)

### <a name="c-language-specification"></a>C# Dil Belirtimi

|Sürüm|Bağlantı|Açıklama|
|-------|----|-----------|
|C# 7.0 ve üzeri||şu anda kullanılamıyor|
|C# 6.0|[Bağlantı](../language-specification/index.md)|C# dil belirtimi sürüm 6 - terim ve kısaltmalarla taslak: .NET Foundation|
|C# 5.0|[PDF'yi indirin](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|Standart ECMA-334 5 sürüm|
|C# 3.0|[Belge indirin](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C#Dil belirtimi sürüm 3.0: Microsoft Corporation|
|C# 2.0|[PDF'yi indirin](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|Standart ECMA-334 4 sürümü|
|C# 1.2|[Belge indirin](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|C#Dil belirtimi Sürüm 1.2: Microsoft Corporation|
|C# 1.0|[Belge indirin](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|C#Dil belirtimi Sürüm 1.0: Microsoft Corporation|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>Tüm dil özellikleri desteklemek için gereken en düşük derleyici sürümü

[↩](#TCS80)<a name="FCS80">CS80</a>: Microsoft Visual Studio/derleme araçları 2019, sürüm 16 veya .NET Core 3.0 SDK [↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/derleme araçları 2017 sürüm 15.7  
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/derleme araçları 2017 sürüm 15.5  
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/derleme araçları 2017 sürüm 15.3  
[↩](#TCS7)<a name="FCS7">CS7</a>: Microsoft Visual Studio/derleme araçları 2017  
[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/derleme araçları 2015  
[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/derleme araçları 2012 ya da .NET Framework 4.5 ile birlikte gelen derleyici  
[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/derleme araçları 2010 veya .NET Framework 4.0 ile birlikte gelen derleyici  
[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/derleme araçları 2008 ya da .NET Framework 3.5 ile birlikte gelen derleyici  
[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/derleme araçları 2005 ya da .NET Framework 2.0 ile birlikte gelen derleyici  
[↩](#TISO1)<a name="FISO1">ISO1</a>: Microsoft Visual Studio/derleme araçları .NET 2002 veya paket. N Framework 1.0 derleyici  
