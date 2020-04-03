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
ms.openlocfilehash: ef4a8f571a67477739bbc59d3103ba78dea47177
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635914"
---
# <a name="general-naming-conventions"></a>Genel Adlandırma Kuralları

Bu bölümde, sözcük seçimiyle ilgili genel adlandırma kuralları, kısaltmalar ve kısaltmalar kullanılarak ilgili yönergeler ve dile özgü adlar kullanmaktan nasıl kaçınılabilen öneriler açıklanmaktadır.

## <a name="word-choice"></a>Kelime Seçimi
 ✔️ KOLAYCA okunabilir tanımlayıcı adlar seçin.

 Örneğin, adlı `HorizontalAlignment` bir özellik İngilizce'den `AlignmentHorizontal`daha okunabilir.

 ✔️ kısaltma üzerinde okunabilirlik lehine DO.

 Özellik adı `CanScrollHorizontally` (X `ScrollableX` eksenine belirsiz bir başvuru) daha iyidir.

 ❌Alt çizgi, tire veya diğer alfasayısal olmayan karakterleri KULLANMAYIN.

 ❌Macarca gösterimi KULLANMAYıN.

 ❌Yaygın olarak kullanılan programlama dillerinin anahtar kelimeleriyle çakışan tanımlayıcılar kullanmaktan kaçının.

 Ortak Dil Belirtimi'nin (CLS) Kural 4'e göre, tüm uyumlu dillerin söz tanımlayıcı olarak o dilin anahtar sözcüklerini kullanan adlandırılmış öğelere erişmesine izin veren bir mekanizma sağlaması gerekir. C#, örneğin, bu durumda bir kaçış mekanizması olarak @ işaretini kullanır. Ancak, kaçış sırası olan bir yöntemi onsuz kullanmaktan çok daha zor olduğu için ortak anahtar kelimelerden kaçınmak yine de iyi bir fikirdir.

## <a name="using-abbreviations-and-acronyms"></a>Kısaltmaları ve Kısaltmaları Kullanma
 ❌Tanımlayıcı adlarının bir parçası olarak kısaltmalar veya kasılmalar KULLANMAYIN.

 Örneğin, `GetWin`yerine `GetWindow` kullanın.

 ❌Yaygın olarak kabul edilmeyen kısaltmalar kullanmayın ve öyle olsalar bile, yalnızca gerektiğinde.

## <a name="avoiding-language-specific-names"></a>Dile Özgü Adlardan Kaçınma
 do✔️ tür adları için dile özgü anahtar kelimeler yerine anlamsal olarak ilginç adlar kullanır.

 Örneğin, `GetLength` daha iyi bir `GetInt`addır.

 ✔️ Bir tanımlayıcının türünden başka anlamsal anlamı olmadığı nadir durumlarda, dile özgü bir ad yerine genel bir CLR türü adı kullanın.

 Örneğin, dönüştürme yöntemi , <xref:System.Int64> değil `ToInt64` `ToLong` (c# <xref:System.Int64> özgü takma ad `long`için bir CLR adı olduğundan) adlı olmalıdır. Aşağıdaki tablo, CLR türü adlarını (c#, Visual Basic ve C++) için karşılık gelen tür adlarını kullanarak birkaç temel veri türü sunar.

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**Sbyte**|**Sbyte**|**char**|**Sbyte**|
|**Bayt**|**Bayt**|**unsigned char**|**Bayt**|
|**short**|**Kısa**|**short**|**Int16**|
|**ushort**|**UInt16**|**imzasız short**|**UInt16**|
|**int**|**Tamsayı**|**int**|**Int32**|
|**Uint**|**UInt32**|**unsigned int**|**UInt32**|
|**long**|**Uzun**|**__int64**|**Int64**|
|**ulong**|**UInt64**|**imzasız __int64**|**UInt64**|
|**float**|**Tek**|**float**|**Tek**|
|**double**|**Çift**|**double**|**Çift**|
|**bool**|**Boole**|**bool**|**Boole**|
|**char**|**Char**|**wchar_t**|**Char**|
|**Dize**|**Dize**|**Dize**|**Dize**|
|**Nesne**|**Nesne**|**Nesne**|**Nesne**|

 ✔️ bir tanımlayıcının anlamsal `value` `item`anlamı olmadığı ve parametrenin türü önemli olmadığı nadir durumlarda, tür adını yinelemek yerine ortak bir ad kullanın.

## <a name="naming-new-versions-of-existing-apis"></a>Varolan API'lerin Yeni Sürümlerini Adlandırma
 do ✔️, varolan bir API'nin yeni sürümlerini oluştururken eski API'ye benzer bir ad kullanın.

 Bu, API'ler arasındaki ilişkiyi vurgulamaya yardımcı olur.

 ✔️ VAROLAN API'nin yeni bir sürümünü belirtmek için önek yerine sonek eklemeyi tercih edin.

 Bu, belgelere göz atarken veya IntelliSense'i kullanırken keşfe yardımcı olur. Çoğu tarayıcı ve IntelliSense tanımlayıcıları alfabetik sırada gösterdiğinden, API'nin eski sürümü yeni API'lere yakın olarak düzenlenir.

 ✔️ bir sonek veya önek eklemek yerine yepyeni, ancak anlamlı bir tanımlayıcı kullanmayı düşünün.

 ✔️, özellikle API'nin varolan adı anlamlı olan tek ad (örneğin, bir endüstri standardıysa) ve anlamlı bir sonek eklemek (veya adı değiştirmek) uygun bir seçenek değilse, varolan bir API'nin yeni bir sürümünü belirtmek için sayısal bir sonek kullanın.

 ❌"Ex" (veya benzer) sonekini, aynı API'nin önceki bir sürümünden ayırt etmek için tanımlayıcı için KULLANMAYIN.

 ✔️ 32 bit tamsayı yerine 64 bit tamsayı (uzun bir tamsayı) üzerinde çalışan API sürümlerini tanıtırken "64" soneki kullanın. Bu yaklaşımı yalnızca varolan 32 bit API varsa almanız gerekir; sadece 64-bit sürümü ile yepyeni API'ler için bunu yapmayın.

 *Porsiyonlar &copy; 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Pearson Education, Inc.'in izniyle [Framework Design Guidelines: Conventions, Idioms and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina ve Brad Abrams tarafından 22 Ekim 2008'de Addison-Wesley Professional tarafından Microsoft Windows Geliştirme Serisi'nin bir parçası olarak yayımlandı.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma yönergeleri](../../../docs/standard/design-guidelines/naming-guidelines.md)
- [.NET, EditorConfig için adlandırma kuralları](/visualstudio/ide/editorconfig-naming-conventions)
