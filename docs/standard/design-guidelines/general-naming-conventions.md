---
title: Genel Adlandırma Kuralları
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], conflicts
- type names, conflicts
- language-specific type names
- names [.NET Framework], about naming guidelines
- names [.NET Framework], abbreviations
- abbreviation naming guidelines
- acronym naming guidelines
- Hungarian notation
- names [.NET Framework], type names
- names [.NET Framework], acronyms
ms.assetid: d3a77ea1-75d2-4969-a8c3-3e1e3e1aaedc
ms.openlocfilehash: d1b01fac7368ffeceb554c6f12aecb8f8760fa1d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709341"
---
# <a name="general-naming-conventions"></a>Genel Adlandırma Kuralları
Bu bölümde, Word seçimiyle ilgili genel adlandırma kuralları, kısaltmalar ve kısaltmalar kullanma yönergeleri ve dile özgü adların kullanılmasıyla ilgili öneriler açıklanmaktadır.  
  
## <a name="word-choice"></a>Sözcük seçimi  
 **✓ DO** kolay okunabilir tanımlayıcı adlarını seçin.  
  
 Örneğin, `HorizontalAlignment` adlı bir özellik `AlignmentHorizontal`daha Ingilizce-okunabilir.  
  
 **✓ DO** okunabilirlik kısaltma ayrıcalık tanıma.  
  
 `CanScrollHorizontally` Özellik adı `ScrollableX` daha iyidir (X eksenine yönelik bir tam başvuru).  
  
 **X DO NOT** alt çizgi, kısa çizgi veya herhangi bir alfasayısal olmayan karakterler kullanın.  
  
 **X DO NOT** Macarca gösterimini kullanın.  
  
 **X AVOID** kullanılan programlama dilleri anahtar sözcükleriyle yaygın olarak çakışma kimlikleri kullanarak.  
  
 Ortak dil belirtiminin (CLS) kural 4 ' e göre, tüm uyumlu dillerin, söz konusu dilin anahtar sözcüğünü tanımlayıcı olarak kullanan adlandırılmış öğelere erişime izin veren bir mekanizma sağlaması gerekir. C#Örneğin, bu durumda @ Sign 'ı kaçış mekanizması olarak kullanır. Ancak, bir yöntemi kaçış sırası olmadan kullanmak çok daha zor olduğundan ortak anahtar sözcüklerden kaçınmak iyi bir fikirdir.  
  
## <a name="using-abbreviations-and-acronyms"></a>Kısaltmalar ve kısaltmalar kullanma  
 **X DO NOT** kısaltmalar veya kısaltmalar tanımlayıcı adları bir parçası olarak kullanın.  
  
 Örneğin, `GetWin`yerine `GetWindow` kullanın.  
  
 **X DO NOT** yaygın olarak kabul edilen ve, yalnızca gerekli olduğunda olmaları durumunda bile olmayan kısaltmalar kullanın.  
  
## <a name="avoiding-language-specific-names"></a>Dile özgü adlardan kaçınma  
 **✓ DO** dile özgü anahtar sözcükler yerine anlamsal olarak ilginç adları için tür adları kullanın.  
  
 Örneğin, `GetLength` `GetInt`daha iyi bir addır.  
  
 **✓ DO** bir tanımlayıcı türü ötesinde anlamsal anlamı olduğunda nadir durumlarda dile özgü adı yerine bir genel CLR türü adı kullanın.  
  
 Örneğin, <xref:System.Int64> dönüştürme yöntemi `ToLong` değil `ToInt64`olarak adlandırılmalıdır (<xref:System.Int64> özel ad için C#bir clr adı olduğundan `long`). Aşağıdaki tabloda, CLR tür adlarını (Ayrıca, Visual Basic ve C# C++için karşılık gelen tür adlarını) kullanarak çeşitli temel veri türleri sunulmaktadır.  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Bayt**|**işaretsiz karakter**|**Bayt**|  
|**short**|**Kısadır**|**short**|**Int16**|  
|**ushort**|**Int16**|**işaretsiz kısa**|**Int16**|  
|**int**|**Tamsayı**|**int**|**Int32**|  
|**uint**|**Int32**|**işaretsiz int**|**Int32**|  
|**long**|**Kalacağını**|**__int64**|**Tutulamaz**|  
|**ulong**|**Int64**|**imzasız __int64**|**Int64**|  
|**float**|**Sunuculu**|**float**|**Sunuculu**|  
|**double**|**Çift**|**double**|**Çift**|  
|**bool**|**Boole değeri**|**bool**|**Boole değeri**|  
|**char**|**Char**|**wchar_t**|**Char**|  
|**string**|**Dize**|**Dize**|**Dize**|  
|**object**|**Nesne**|**Nesne**|**Nesne**|  
  
 **✓ DO** gibi ortak bir ad kullanın `value` veya `item`, tür adı bir tanımlayıcı bir anlam anlamı yoktur ve parametresinin türü önemli olmadığında nadir durumlarda yinelenen yerine.  
  
## <a name="naming-new-versions-of-existing-apis"></a>Mevcut API 'lerin yeni sürümlerini adlandırma  
 **✓ DO** var olan bir API yeni sürümlerini oluştururken eski API için benzer bir ad kullanın.  
  
 Bu, API 'Ler arasındaki ilişkiyi vurgulamaya yardımcı olur.  
  
 **✓ DO** var olan bir API yeni bir sürümünü belirtmek için bir önek yerine bir sonek ekleme tercih eder.  
  
 Bu, belgelere gözatarken veya IntelliSense kullanılırken bulmaya yardımcı olur. Çoğu tarayıcı ve IntelliSense tanımlayıcıları alfabetik sırada göstertiğinden, API 'nin eski sürümü yeni API 'lere yakın şekilde düzenlenir.  
  
 **✓ CONSIDER** sonek veya bir önek eklemek yerine yepyeni, ancak anlamlı tanımlayıcısını kullanarak.  
  
 **✓ DO** sayısal bir sonek özellikle, API varolan adı (yani, sektör standardı ise) mantıklı yalnızca bir ad ve her anlamlı ekleme soneki (veya adının değiştirilmesi) bir uygulama değilse varolan bir API yeni bir sürümünü belirtmek için kullanın ropriate seçeneği.  
  
 **X DO NOT** "Eski" (veya benzeri) kullanmak aynı API önceki bir sürümünden ayırt etmek bir tanımlayıcı için soneki.  
  
 **✓ DO** 32 bit tamsayı yerine 64 bit tamsayı (uzun tamsayı) üzerinde çalışan API sürümleri Tanıtımı "64" soneki kullanın. Yalnızca var olan 32 bitlik API olduğunda bu yaklaşımı uygulamanız gerekir; Bunu yalnızca 64 bitlik bir sürümle yepyeni yeni API 'Ler için yapmayın.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
