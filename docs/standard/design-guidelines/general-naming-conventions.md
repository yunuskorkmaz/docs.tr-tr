---
title: Genel adlandırma kuralları
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd3defd969b5f26fb95e7feca9c3d533e67272b1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209517"
---
# <a name="general-naming-conventions"></a>Genel adlandırma kuralları
Bu bölümde, sözcük seçimi için ilgili genel adlandırma kuralları kısaltmalar ve kısaltmalar ve öneriler hakkında dile özgü adlarını kullanmaktan kaçınmak kullanma hakkında yönergeler açıklanmaktadır.  
  
## <a name="word-choice"></a>Sözcük seçimi  
 **✓ DO** kolay okunabilir tanımlayıcı adlarını seçin.  
  
 Örneğin, adında bir özellik `HorizontalAlignment` daha İngilizce-daha okunabilirdir `AlignmentHorizontal`.  
  
 **✓ DO** okunabilirlik kısaltma ayrıcalık tanıma.  
  
 Özellik adı `CanScrollHorizontally` göre daha iyidir `ScrollableX` (x ekseni için belirsiz bir başvuru).  
  
 **X DO NOT** alt çizgi, kısa çizgi veya herhangi bir alfasayısal olmayan karakterler kullanın.  
  
 **X DO NOT** Macarca gösterimini kullanın.  
  
 **X AVOID** kullanılan programlama dilleri anahtar sözcükleriyle yaygın olarak çakışma kimlikleri kullanarak.  
  
 Ortak dil belirtimi (CLS), kural 4 göre tüm uyumlu dilin dilin bir anahtar sözcük tanımlayıcı olarak kullanan adlandırılmış öğeleri erişmesini sağlayan bir mekanizma sağlamanız gerekir. Kullanan C# ' ta, örneğin, bu durumda bir kaçış mekanizması olarak oturum @. Ancak, yine de bir yöntemi olmadan bir kaçış dizisi ile kullanmak çok daha zor olduğundan, ortak anahtar sözcükleri önlemek için iyi bir fikirdir.  
  
## <a name="using-abbreviations-and-acronyms"></a>Kısaltmalar ve kısaltmalar kullanma  
 **X DO NOT** kısaltmalar veya kısaltmalar tanımlayıcı adları bir parçası olarak kullanın.  
  
 Örneğin, `GetWindow` yerine `GetWin`.  
  
 **X DO NOT** yaygın olarak kabul edilen ve, yalnızca gerekli olduğunda olmaları durumunda bile olmayan kısaltmalar kullanın.  
  
## <a name="avoiding-language-specific-names"></a>Dile özgü adları kaçınma  
 **✓ DO** dile özgü anahtar sözcükler yerine anlamsal olarak ilginç adları için tür adları kullanın.  
  
 Örneğin, `GetLength` daha iyi bir addır `GetInt`.  
  
 **✓ DO** bir tanımlayıcı türü ötesinde anlamsal anlamı olduğunda nadir durumlarda dile özgü adı yerine bir genel CLR türü adı kullanın.  
  
 Örneğin, bir dönüştürme yöntemi <xref:System.Int64> adlandırılmalıdır `ToInt64`değil `ToLong` (çünkü <xref:System.Int64> C# için bir CLR ad-belirli bir diğer ad `long`). Aşağıdaki tabloda, CLR tür adları (C#, Visual Basic ve C++ için karşılık gelen tür adları için olduğu gibi) kullanarak birkaç temel veri türlerini gösterir.  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**byte**|**Bayt**|**İmzasız char**|**Bayt**|  
|**short**|**kısa**|**short**|**Int16**|  
|**ushort**|**UInt16**|**İmzasız short**|**UInt16**|  
|**int**|**tamsayı**|**int**|**Int32**|  
|**uint**|**UInt32**|**işaretsiz int**|**UInt32**|  
|**long**|**uzun**|**__int64**|**Int64**|  
|**ulong**|**UInt64**|**imzalanmamış __int64**|**UInt64**|  
|**float**|**Tek**|**float**|**Tek**|  
|**double**|**çift**|**double**|**çift**|  
|**bool**|**Boole değeri**|**bool**|**Boole değeri**|  
|**char**|**Char**|**wchar_t**|**Char**|  
|**string**|**dize**|**dize**|**dize**|  
|**object**|**Nesne**|**Nesne**|**Nesne**|  
  
 **✓ DO** gibi ortak bir ad kullanın `value` veya `item`, tür adı bir tanımlayıcı bir anlam anlamı yoktur ve parametresinin türü önemli olmadığında nadir durumlarda yinelenen yerine.  
  
## <a name="naming-new-versions-of-existing-apis"></a>Mevcut API'lere yeni sürümlerini adlandırma  
 **✓ DO** var olan bir API yeni sürümlerini oluştururken eski API için benzer bir ad kullanın.  
  
 Bu API'ler arasındaki ilişkiyi vurgulamaya yardımcı olur.  
  
 **✓ DO** var olan bir API yeni bir sürümünü belirtmek için bir önek yerine bir sonek ekleme tercih eder.  
  
 Bu keşif belgeleri, göz atarken size yardımcı olacak veya IntelliSense kullanma. Çoğu tarayıcı ve IntelliSense tanımlayıcıları alfabetik sırada gösterir çünkü yakın yeni API'leri, API eski sürümü düzenlenecektir.  
  
 **✓ CONSIDER** sonek veya bir önek eklemek yerine yepyeni, ancak anlamlı tanımlayıcısını kullanarak.  
  
 **✓ DO** sayısal bir sonek özellikle, API varolan adı (yani, sektör standardı ise) mantıklı yalnızca bir ad ve her anlamlı ekleme soneki (veya adının değiştirilmesi) bir uygulama değilse varolan bir API yeni bir sürümünü belirtmek için kullanın ropriate seçeneği.  
  
 **X DO NOT** "Eski" (veya benzeri) kullanmak aynı API önceki bir sürümünden ayırt etmek bir tanımlayıcı için soneki.  
  
 **✓ DO** 32 bit tamsayı yerine 64 bit tamsayı (uzun tamsayı) üzerinde çalışan API sürümleri Tanıtımı "64" soneki kullanın. Var olan 32-bit API varsa bu yaklaşımı yeterlidir; yapma, yalnızca 64 bit sürümüne sahip yeni API'ler için.  
  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
- [Adlandırma Kuralları](../../../docs/standard/design-guidelines/naming-guidelines.md)
