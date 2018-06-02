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
ms.openlocfilehash: 2a9501c883fec7478932b22ea2cdcad70865e0fd
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696292"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (C# Derleyici Seçenekleri)
Derleyicinin yalnızca seçilen C# dil belirtimi dahil sözdizimini kabul etmesine neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-langversion:option  
```  
  
## <a name="arguments"></a>Arguments  
 `option`  
 Aşağıdaki değerler geçerlidir:  
  
|Seçenek|Açıklama|  
|------------|-------------|  
|default|Derleyici destekleyebileceği en son sürümle gelen tüm geçerli dil sözdizimini kabul eder.|
|ISO-1|ISO/IEC 23270:2003 C# (1.0/1.2) dahil sözdizimi derleyici kabul <sup id="TISO1"> [ISO1](#FISO1)</sup>|  
|ISO-2|ISO/IEC 23270:2006 C# (2.0) dahil sözdizimi derleyici kabul <sup id="TISO2"> [ISO2](#FISO2)</sup>|
|3|C# 3.0 dahil ya da daha düşük olan sözdizimi derleyici kabul <sup id="TCS3"> [CS3](#FCS3)</sup>|
|4|Derleyici dahil C# 4.0 veya daha düşük olan sözdizimini kabul eder <sup id="TCS4"> [CS4](#FCS4)</sup>|
|5|Derleyici dahil C# 5.0 veya daha düşük olan sözdizimini kabul eder <sup id="TCS5"> [CS5](#FCS5)</sup>|
|6|Derleyici dahil C# 6. 0 veya daha düşük olan sözdizimini kabul eder <sup id="TCS6"> [CS6](#FCS6)</sup>|
|7|Derleyici dahil C# 7. 0 veya daha düşük olan sözdizimini kabul eder <sup id="TCS7"> [CS7](#FCS7)</sup>|
|7.1|C# 7.1 dahil ya da daha düşük olan sözdizimi derleyici kabul <sup id="TCS71"> [CS71](#FCS71)</sup>|
|7.2|C# 7.2 dahil ya da daha düşük olan sözdizimi derleyici kabul <sup id="TCS72"> [CS72](#FCS72)</sup>|
|7.3|C# 7.3 dahil ya da daha düşük olan sözdizimi derleyici kabul <sup id="TCS73"> [CS73](#FCS73)</sup>|
|en son|Derleyici destekleyebileceği tüm geçerli dil söz dizimini kabul eder.|

<!--- Uncomment and move these above
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS8">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a>Açıklamalar  
 C# uygulamanız tarafından başvurulan meta veri değil tabi **- langversion** derleyici seçeneği.  
  
 C# Derleyici her sürümü uzantıları dil belirtimi içerdiğinden **- langversion** Derleyici önceki bir sürümünü eşdeğer işlevselliğini sağlamaz.  
 
 C# sürüm güncelleştirmelerini genellikle ana .NET Framework sürümleri ile çakıştığı olsa da, ayrıca, özellikleri ve yeni sözdizimini mutlaka bu belirli framework sürümüne bağlı olmak zorunda değildir. Yeni özelliklerin yanı sıra C# düzeltme de serbest yeni bir derleyici güncelleştirme kesinlikle gerektirirken her belirli özelliği kendi minimum .NET API veya alt düzey çerçevesinde dahil ederek çalışmasına izin verebilir ortak dil çalışma zamanı gereksinimleri vardır. NuGet paketlerini veya diğer kitaplıkları.
  
 Hangi **- langversion** ayarını kullanın, .exe veya .dll dosyası oluşturmak için geçerli ortak dil çalışma zamanı sürümünü kullanacak. Tek istisnası arkadaş derlemeleri ve [- moduleassemblyname (C# derleyici seçeneği)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md), hangi altında çalışan **- langversion: ISO-1**.  
 
 C# dil sürümü belirtmek üzere diğer yöntemler için bkz: [C# dil sürümünü seçin](../configure-language-version.md) konu.
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>.  
    
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a>C# Dil Belirtimi

|Sürüm|Bağlantı|Açıklama|
|-------|----|-----------|
|C# 1.0|[Belge indirme](http://download.microsoft.com/download/a/9/e/a9e229b9-fee5-4c3e-8476-917dee385062/csharp%20language%20specification%20v1.0.doc)|C# dil belirtimi Sürüm 1.0: Microsoft Corporation'ın|
|C# 1.2|[Belge indirme](http://download.microsoft.com/download/5/e/5/5e58be0a-b02b-41ac-a4a3-7a22286214ff/csharp%20language%20specification%20v1.2.doc)|C# dil belirtimi Sürüm 1.2: Microsoft Corporation'ın|
|C# 2.0|[PDF indirin](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/Ecma-334%204th%20edition%20June%202006.pdf)|Standart ECMA 334 4 Edition|
|C# 3.0|[Belge indirme](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C# dil belirtimi sürüm 3.0: Microsoft Corporation'ın|
|C# 5.0|[PDF indirin](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf)|Standart ECMA 334 5 Edition|
|C# 6.0|[Bağlantı](../language-specification/index.md)|C# dil belirtimi sürüm 6 - resmi olmayan taslak: .NET Foundation|
|C# 7.0 ve üzeri||Şu anda kullanılamıyor|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>Tüm dil özellikleri desteklemek için gereken en düşük derleyici sürümü   
[↩](#TISO1)<a name="FISO1">ISO1</a>: Microsoft Visual Studio/derleme araçları .net 2002 veya ile birlikte gelen .net Framework 1.0 derleyici     
[↩](#TISO2)<a name="FISO2">ISO2</a>: Microsoft Visual Studio/derleme araçları 2005 veya ile birlikte gelen .net Framework 2.0 derleyici    
[↩](#TCS3)<a name="FCS3">CS3</a>: Microsoft Visual Studio/derleme araçları 2008 ya da ile birlikte gelen .net Framework 3.5 derleyici    
[↩](#TCS4)<a name="FCS4">CS4</a>: Microsoft Visual Studio/derleme araçları 2010 veya ile birlikte gelen .net Framework 4.0 derleyici    
[↩](#TCS5)<a name="FCS5">CS5</a>: Microsoft Visual Studio/derleme araçları 2012 ya da ile birlikte gelen .net Framework 4.5 derleyici    
[↩](#TCS6)<a name="FCS6">CS6</a>: Microsoft Visual Studio/derleme araçları 2015    
[↩](#TCS7)<a name="FCS7">CS7</a>: Microsoft Visual Studio/derleme araçları 2017   
[↩](#TCS71)<a name="FCS71">CS71</a>: Microsoft Visual Studio/derleme araçları 2017, sürüm 15.3    
[↩](#TCS72)<a name="FCS72">CS72</a>: Microsoft Visual Studio/derleme araçları 2017, sürüm 15,5    
[↩](#TCS73)<a name="FCS73">CS73</a>: Microsoft Visual Studio/derleme araçları 2017, sürüm 15.7    

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS8)<a name="FCS8">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
