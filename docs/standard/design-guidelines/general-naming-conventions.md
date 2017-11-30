---
title: "Genel adlandırma kuralları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dde3adbb7640978829dea4b977ed14eec38a9077
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="general-naming-conventions"></a>Genel adlandırma kuralları
Bu bölümde, sözcük seçimi için ilgili genel adlandırma kuralları kısaltmalar ve kısaltmalar ve öneriler dile özel adlar kullanmaktan kaçının nasıl kullanma hakkında yönergeler açıklanmaktadır.  
  
## <a name="word-choice"></a>Sözcük seçimi  
 **✓ YAPMAK** kolay okunabilir tanımlayıcı adlarını seçin.  
  
 Örneğin, adında bir özellik `HorizontalAlignment` daha İngilizce-okunamaz daha `AlignmentHorizontal`.  
  
 **✓ YAPMAK** okunabilirlik kısaltma ayrıcalık tanıma.  
  
 Özellik adı `CanScrollHorizontally` daha iyidir `ScrollableX` (x ekseni belirsiz bir referansı).  
  
 **X yok** alt çizgi, kısa çizgi veya herhangi bir alfasayısal olmayan karakterler kullanın.  
  
 **X yok** Macarca gösterimini kullanın.  
  
 **KAÇININ x** kullanılan programlama dilleri anahtar sözcükleriyle yaygın olarak çakışma kimlikleri kullanarak.  
  
 Ortak dil belirtimi (CLS), kural 4 göre tüm uyumlu diller söz konusu dilin anahtar sözcüğü bir tanımlayıcı olarak kullanmak adlandırılmış öğelere erişime izin veren bir mekanizma sağlamanız gerekir. Örneğin, C# ' ta, kullanır @ işareti bu durumda kaçış mekanizması olarak. Ancak, ortak anahtar sözcükleri olmadan birden kaçış sırası içeren bir yöntem kullanmak çok daha zor olduğundan önlemek için iyi bir fikir hala olduğu.  
  
## <a name="using-abbreviations-and-acronyms"></a>Kısaltmalar ve kısaltmalar kullanma  
 **X yok** kısaltmalar veya kısaltmalar tanımlayıcı adları bir parçası olarak kullanın.  
  
 Örneğin, `GetWindow` yerine `GetWin`.  
  
 **X yok** yaygın olarak kabul edilen ve, yalnızca gerekli olduğunda olmaları durumunda bile olmayan kısaltmalar kullanın.  
  
## <a name="avoiding-language-specific-names"></a>Dile özgü adları önleme  
 **✓ YAPMAK** dile özgü anahtar sözcükler yerine anlamsal olarak ilginç adları için tür adları kullanın.  
  
 Örneğin, `GetLength` daha iyi bir adı `GetInt`.  
  
 **✓ YAPMAK** bir tanımlayıcı türü ötesinde anlamsal anlamı olduğunda nadir durumlarda dile özgü adı yerine bir genel CLR türü adı kullanın.  
  
 Örneğin, dönüştürülürken bir yöntem <xref:System.Int64> adlı olmalıdır `ToInt64`değil `ToLong` (çünkü <xref:System.Int64> için C# bir CLR ad-belirli diğer `long`). Aşağıdaki tabloda, CLR türü adları (C#, Visual Basic ve C++ için karşılık gelen tür adları için olduğu gibi) kullanarak birden fazla temel veri türlerini gösterir.  
  
|C#|Visual Basic|C++|CLR|  
|---------|------------------|-----------|---------|  
|**sbyte**|**SByte**|**char**|**SByte**|  
|**bayt**|**Bayt**|**İmzasız char**|**Bayt**|  
|**kısa**|**Kısa**|**kısa**|**Int16**|  
|**ushort**|**UInt16**|**İmzasız short**|**UInt16**|  
|**int**|**Tamsayı**|**int**|**Int32**|  
|**uint**|**UInt32**|**İmzasız int**|**UInt32**|  
|**uzun**|**Uzun**|**__int64**|**Int64**|  
|**ulong**|**UInt64**|**İmzasız __int64**|**UInt64**|  
|**kayan nokta**|**Tek**|**kayan nokta**|**Tek**|  
|**çift**|**Çift**|**çift**|**Çift**|  
|**bool**|**Boole değeri**|**bool**|**Boole değeri**|  
|**char**|**Char**|**wchar_t**|**Char**|  
|**dize**|**Dize**|**Dize**|**Dize**|  
|**Nesne**|**Nesne**|**Nesne**|**Nesne**|  
  
 **✓ YAPMAK** gibi ortak bir ad kullanın `value` veya `item`, tür adı bir tanımlayıcı bir anlam anlamı yoktur ve parametresinin türü önemli olmadığında nadir durumlarda yinelenen yerine.  
  
## <a name="naming-new-versions-of-existing-apis"></a>Mevcut API'lerini yeni sürümlerini adlandırma  
 **✓ YAPMAK** var olan bir API yeni sürümlerini oluştururken eski API için benzer bir ad kullanın.  
  
 Bu API'ları arasındaki ilişkiyi vurgulamaya yardımcı olur.  
  
 **✓ YAPMAK** var olan bir API yeni bir sürümünü belirtmek için bir önek yerine bir sonek ekleme tercih eder.  
  
 Bu belge, göz atarken bulma yardımcı olur veya IntelliSense kullanma. Çoğu tarayıcılar ve IntelliSense tanımlayıcıları alfabetik olarak göstermek için API eski sürümü yeni API'leri yakın düzenleneceğini.  
  
 **✓ DÜŞÜNÜN** sonek veya bir önek eklemek yerine yepyeni, ancak anlamlı tanımlayıcısını kullanarak.  
  
 **✓ YAPMAK** sayısal bir sonek özellikle, API varolan adı (yani, sektör standardı ise) mantıklı yalnızca bir ad ve her anlamlı ekleme soneki (veya adının değiştirilmesi) bir uygulama değilse varolan bir API yeni bir sürümünü belirtmek için kullanın ropriate seçeneği.  
  
 **X yok** "Eski" (veya benzeri) kullanmak aynı API önceki bir sürümünden ayırt etmek bir tanımlayıcı için soneki.  
  
 **✓ YAPMAK** 32 bit tamsayı yerine 64 bit tamsayı (uzun tamsayı) üzerinde çalışan API sürümleri Tanıtımı "64" soneki kullanın. Varolan 32-bit API varsa bu yaklaşımı benimsemeye yeterlidir; yapma, yalnızca 64-bit sürümü ile yepyeni API'leri için.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Framework tasarım yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Adlandırma yönergeleri](../../../docs/standard/design-guidelines/naming-guidelines.md)
