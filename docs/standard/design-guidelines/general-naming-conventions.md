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
ms.openlocfilehash: c90987fd28d5157cfb7f7eea4680b5ab4be1a200
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290960"
---
# <a name="general-naming-conventions"></a>Genel Adlandırma Kuralları

Bu bölümde, Word seçimiyle ilgili genel adlandırma kuralları, kısaltmalar ve kısaltmalar kullanma yönergeleri ve dile özgü adların kullanılmasıyla ilgili öneriler açıklanmaktadır.

## <a name="word-choice"></a>Sözcük seçimi
 ✔️ kolayca okunabilir tanımlayıcı adlarını seçin.

 Örneğin, adlı bir özellik, `HorizontalAlignment` daha fazla İngilizce-okunabilir `AlignmentHorizontal` .

 ✔️, kısaltma üzerinde okunabilirliğini tercih edin.

 Özellik adı `CanScrollHorizontally` şundan daha iyidir `ScrollableX` (X eksenine yönelik bir tam başvuru).

 ❌Alt çizgi, kısa çizgi veya alfasayısal olmayan karakterler kullanmayın.

 ❌Macarca gösterimini kullanmayın.

 ❌Yaygın olarak kullanılan programlama dillerinin anahtar sözcükleriyle çakışan tanımlayıcılar kullanmaktan KAÇıNıN.

 Ortak dil belirtiminin (CLS) kural 4 ' e göre, tüm uyumlu dillerin, söz konusu dilin anahtar sözcüğünü tanımlayıcı olarak kullanan adlandırılmış öğelere erişime izin veren bir mekanizma sağlaması gerekir. Örneğin, C#, bu durumda @ Sign 'ı kaçış mekanizması olarak kullanır. Ancak, bir yöntemi kaçış sırası olmadan kullanmak çok daha zor olduğundan ortak anahtar sözcüklerden kaçınmak iyi bir fikirdir.

## <a name="using-abbreviations-and-acronyms"></a>Kısaltmalar ve kısaltmalar kullanma
 ❌Tanımlayıcı adlarının parçası olarak kısaltmalar veya aykırılıkları kullanmayın.

 Örneğin, yerine kullanın `GetWindow` `GetWin` .

 ❌Yaygın olarak kabul edilmeyen ve yalnızca gerekli olduğunda bile olmayan kısaltmalar kullanmayın.

## <a name="avoiding-language-specific-names"></a>Dile özgü adlardan kaçınma
 ✔️, tür adları için dile özgü anahtar sözcükler yerine anlam açısından ilginç adlar kullanır.

 Örneğin, `GetLength` daha iyi bir addır `GetInt` .

 ✔️, bir tanımlayıcının türünün ötesinde anlam anlamı olmadığında nadir durumlarda, dile özgü bir ad yerine genel CLR türü adı kullanın.

 Örneğin, öğesine dönüştürme yöntemi <xref:System.Int64> `ToInt64` , değil, olarak adlandırılmalıdır `ToLong` (çünkü <xref:System.Int64> C# özel DIĞER adı için bir clr adıdır `long` ). Aşağıdaki tabloda, CLR tür adlarını (Ayrıca C#, Visual Basic ve C++ için karşılık gelen tür adlarını) kullanan çeşitli temel veri türleri gösterilmektedir.

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**SByte**|**SByte**|**char**|**SByte**|
|**bayt**|**Bayt**|**unsigned char**|**Bayt**|
|**short**|**Kısadır**|**short**|**Int16**|
|**ushort**|**UInt16**|**imzasız short**|**UInt16**|
|**int**|**Gir**|**int**|**Int32**|
|**u**|**UInt32**|**unsigned int**|**UInt32**|
|**long**|**Kalacağını**|**__int64**|**Tutulamaz**|
|**ulong**|**UInt64**|**imzasız __int64**|**UInt64**|
|**float**|**Tek**|**float**|**Tek**|
|**double**|**Çift**|**double**|**Çift**|
|**bool**|**Boole**|**bool**|**Boole**|
|**char**|**Char**|**wchar_t**|**Char**|
|**string**|**Dize**|**Dize**|**Dize**|
|**nesne**|**Nesne**|**Nesne**|**Nesne**|

 ✔️, tür adını yinelemek yerine veya gibi ortak bir ad kullanın, `value` `item` nadir olarak bir tanımlayıcının anlam anlamı yoktur ve parametre türü önemli değildir.

## <a name="naming-new-versions-of-existing-apis"></a>Mevcut API 'lerin yeni sürümlerini adlandırma
 ✔️ var olan bir API 'nin yeni sürümlerini oluştururken eski API 'ye benzer bir ad kullanın.

 Bu, API 'Ler arasındaki ilişkiyi vurgulamaya yardımcı olur.

 ✔️ var olan bir API 'nin yeni bir sürümünü göstermek için önek yerine bir sonek eklemeyi tercih edebilirsiniz.

 Bu, belgelere gözatarken veya IntelliSense kullanılırken bulmaya yardımcı olur. Çoğu tarayıcı ve IntelliSense tanımlayıcıları alfabetik sırada göstertiğinden, API 'nin eski sürümü yeni API 'lere yakın şekilde düzenlenir.

 ✔️, bir sonek veya ön ek eklemek yerine yeni bir yepyeni, ancak anlamlı bir tanımlayıcı kullanmayı düşünün.

 ✔️ var olan bir API 'nin yeni bir sürümünü göstermek için sayısal bir sonek kullanın, özellikle de var olan API 'nin adı anlamlı olan tek addır (yani, bir sektör standardı ise) ve anlamlı bir sonek eklemek (veya adı değiştirmek) uygun bir seçenek değildir.

 ❌Aynı API 'nin önceki bir sürümünden ayırt etmek için bir tanımlayıcı için "Ex" (ya da benzer) sonekini kullanmayın.

 ✔️, 32 bit tamsayı yerine 64 bit tamsayı (uzun tamsayı) üzerinde çalışan API sürümlerini ("64" sonekini) kullanıma sunuyor. Yalnızca var olan 32 bitlik API olduğunda bu yaklaşımı uygulamanız gerekir; Bunu yalnızca 64 bitlik bir sürümle yepyeni yeni API 'Ler için yapmayın.

 *Bölüm &copy; 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Adlandırma yönergeleri](naming-guidelines.md)
- [EditorConfig için .NET adlandırma kuralları](/visualstudio/ide/editorconfig-naming-conventions)
