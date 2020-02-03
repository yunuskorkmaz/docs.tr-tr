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
ms.openlocfilehash: f8576790a2be08c623807e236d156e0e7f93dd14
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741598"
---
# <a name="general-naming-conventions"></a>Genel Adlandırma Kuralları
Bu bölümde, Word seçimiyle ilgili genel adlandırma kuralları, kısaltmalar ve kısaltmalar kullanma yönergeleri ve dile özgü adların kullanılmasıyla ilgili öneriler açıklanmaktadır.

## <a name="word-choice"></a>Sözcük seçimi
 ✔️ kolayca okunabilir tanımlayıcı adlarını seçin.

 Örneğin, `HorizontalAlignment` adlı bir özellik `AlignmentHorizontal`daha Ingilizce-okunabilir.

 ✔️, kısaltma üzerinde okunabilirliğini tercih edin.

 `CanScrollHorizontally` Özellik adı `ScrollableX` daha iyidir (X eksenine yönelik bir tam başvuru).

 ❌ alt çizgi, kısa çizgi veya alfasayısal olmayan karakterler kullanmayın.

 ❌, Macarca gösterimini kullanmaz.

 ❌, yaygın olarak kullanılan programlama dillerinin anahtar sözcükleriyle çakışan tanımlayıcılar kullanmaktan KAÇıNıN.

 Ortak dil belirtiminin (CLS) kural 4 ' e göre, tüm uyumlu dillerin, söz konusu dilin anahtar sözcüğünü tanımlayıcı olarak kullanan adlandırılmış öğelere erişime izin veren bir mekanizma sağlaması gerekir. C#Örneğin, bu durumda @ Sign 'ı kaçış mekanizması olarak kullanır. Ancak, bir yöntemi kaçış sırası olmadan kullanmak çok daha zor olduğundan ortak anahtar sözcüklerden kaçınmak iyi bir fikirdir.

## <a name="using-abbreviations-and-acronyms"></a>Kısaltmalar ve kısaltmalar kullanma
 ❌ tanımlayıcı adlarının bir parçası olarak kısaltmalar veya aykırılıkları kullanmayın.

 Örneğin, `GetWin`yerine `GetWindow` kullanın.

 ❌, yaygın olarak kabul edilmeyen ve yalnızca gerekli olduğunda bile olmayan kısaltmalar kullanmayın.

## <a name="avoiding-language-specific-names"></a>Dile özgü adlardan kaçınma
 ✔️, tür adları için dile özgü anahtar sözcükler yerine anlam açısından ilginç adlar kullanır.

 Örneğin, `GetLength` `GetInt`daha iyi bir addır.

 ✔️, bir tanımlayıcının türünün ötesinde anlam anlamı olmadığında nadir durumlarda, dile özgü bir ad yerine genel CLR türü adı kullanın.

 Örneğin, <xref:System.Int64> dönüştürme yöntemi `ToLong` değil `ToInt64`olarak adlandırılmalıdır (<xref:System.Int64> özel ad için C#bir clr adı olduğundan `long`). Aşağıdaki tabloda, CLR tür adlarını (Ayrıca, Visual Basic ve C# C++için karşılık gelen tür adlarını) kullanarak çeşitli temel veri türleri sunulmaktadır.

|C#|Visual Basic|C++|CLR|
|---------|------------------|-----------|---------|
|**sbyte**|**SByte**|**char**|**SByte**|
|**byte**|**Bayt**|**işaretsiz karakter**|**Bayt**|
|**short**|**Kısadır**|**short**|**Int16**|
|**ushort**|**Int16**|**işaretsiz kısa**|**Int16**|
|**int**|**Gir**|**int**|**Int32**|
|**uint**|**Int32**|**işaretsiz int**|**Int32**|
|**long**|**Kalacağını**|**__int64**|**Tutulamaz**|
|**ulong**|**Int64**|**imzasız __int64**|**Int64**|
|**float**|**Sunuculu**|**float**|**Sunuculu**|
|**double**|**Çift**|**double**|**Çift**|
|**bool**|**Boolean**|**bool**|**Boolean**|
|**char**|**Char**|**wchar_t**|**Char**|
|**string**|**Dize**|**Dize**|**Dize**|
|**object**|**Nesne**|**Nesne**|**Nesne**|

 ✔️, tür adını yinelemek yerine `value` veya `item`gibi ortak bir ad kullanın, nadir olarak bir tanımlayıcının anlam anlamı yoktur ve parametre türü önemli değildir.

## <a name="naming-new-versions-of-existing-apis"></a>Mevcut API 'lerin yeni sürümlerini adlandırma
 ✔️ var olan bir API 'nin yeni sürümlerini oluştururken eski API 'ye benzer bir ad kullanın.

 Bu, API 'Ler arasındaki ilişkiyi vurgulamaya yardımcı olur.

 ✔️ var olan bir API 'nin yeni bir sürümünü göstermek için önek yerine bir sonek eklemeyi tercih edebilirsiniz.

 Bu, belgelere gözatarken veya IntelliSense kullanılırken bulmaya yardımcı olur. Çoğu tarayıcı ve IntelliSense tanımlayıcıları alfabetik sırada göstertiğinden, API 'nin eski sürümü yeni API 'lere yakın şekilde düzenlenir.

 ✔️, bir sonek veya ön ek eklemek yerine yeni bir yepyeni, ancak anlamlı bir tanımlayıcı kullanmayı düşünün.

 ✔️ var olan bir API 'nin yeni bir sürümünü göstermek için sayısal bir sonek kullanın, özellikle de var olan API 'nin adı anlamlı olan tek addır (yani, bir sektör standardı ise) ve anlamlı bir sonek eklemek (veya adı değiştirmek) uygun bir Opti değilse dayanır.

 ❌, bir tanımlayıcı için "Ex" (veya benzer) sonekini, aynı API 'nin önceki bir sürümünden ayırt etmek için kullanmaz.

 ✔️, 32 bit tamsayı yerine 64 bit tamsayı (uzun tamsayı) üzerinde çalışan API sürümlerini ("64" sonekini) kullanıma sunuyor. Yalnızca var olan 32 bitlik API olduğunda bu yaklaşımı uygulamanız gerekir; Bunu yalnızca 64 bitlik bir sürümle yepyeni yeni API 'Ler için yapmayın.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
