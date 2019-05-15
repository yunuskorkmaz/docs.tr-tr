---
title: Genişletme ve Daraltma Dönüşümleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
ms.openlocfilehash: e2dbbd63be07a19c6e05c7ec8f94bdcd8f50c902
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586309"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Genişletme ve Daraltma Dönüşümleri (Visual Basic)
Önemli bir tür dönüştürme ile dönüştürmenin sonucu hedef veri türü aralık içinde olup olmadığını noktadır.  
  
 A *dönüştürme genişletme* özgün veriler için bir olası değer sağlayan bir veri türü için bir değerini değiştirir.  Genişletme dönüştürmeleri, kaynak değeri korumak ancak gösterimine değiştirebilirsiniz. İçin bir integral türünden dönüştürürseniz böyle `Decimal`, veya `Char` için `String`.  
  
 A *daraltma dönüştürmesi* bazı olası değerlerini tutabilecek özellikte olmayabilecek bir veri türü için bir değerini değiştirir. Örneğin, bir tamsayı türü ve dönüştürülen bir sayı türüne dönüştürülür, kesirli değer yuvarlanır `Boolean` ya da azaltılır `True` veya `False`.  
  
## <a name="widening-conversions"></a>Dönüştürmeleri Genişletme  
 Aşağıdaki tabloda dönüşümlerdir standart gösterilmektedir.  
  
|Veri türü|Veri türleri için widens <sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Bayt](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[kısa](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[tamsayı](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Uınteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[uzun](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Ondalık](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Tek](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[çift](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Tüm numaralandırılan tür ([Enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|Temel alınan integral türü ve, temel alınan türü widens herhangi bir tür.|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char` Dizi|`Char` dizi `String`|  
|Herhangi bir türü|[Nesne](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Türetilmiş bir tür|Herhangi bir temel türü, türetilmiş <sup>3</sup>.|  
|Herhangi bir türü|Herhangi bir arabirimi uygular.|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|Tüm veri türü veya nesne türü.|  
  
 <sup>1</sup> tanımı gereği, her veri türü kendisine widens.  
  
 <sup>2</sup> Dönüştürmelere `Integer`, `UInteger`, `Long`, `ULong`, veya `Decimal` için `Single` veya `Double` kesinlik kaybı, ancak büyüklüğünü hiçbir zaman kaybına neden olabilir. Bu anlamda bunlar bilgi kaybı durumunda değil.  
  
 <sup>3</sup> türetilmiş bir tür dönüştürme temel türlerinden birine genişletme, şaşırtıcı görünebilir. Gerekçe temel türün bir örneği uygun şekilde türetilmiş tür temel türünün tüm üyelerini içermesidir. Ters yönde, türetilmiş bir tür tarafından tanımlanan tüm yeni üyeleri taban türü içermiyor.  
  
 Genişletme dönüştürmeleri, çalışma zamanında her zaman başarılı ve hiçbir zaman veri kaybına neden. Her zaman bunları örtük olarak gerçekleştirebileceğiniz, ister [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) anahtara denetimi türünü ayarlar `On` veya `Off`.  
  
## <a name="narrowing-conversions"></a>Daraltma dönüşümleri  
 Standart daraltma dönüştürmelerini şunları içerir:  
  
- (Her türün kendisine widens dışında) önceki içinde genişletme dönüştürmeleri, ters yönde tablo  
  
- Dönüştürmeleri arasında herhangi bir yönde [Boole](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) ve herhangi bir sayısal tür  
  
- Herhangi bir sayısal tür dönüştürmelerinde herhangi numaralandırılmış tür (`Enum`)  
  
- Dönüştürmeleri arasında herhangi bir yönde [dize](../../../../visual-basic/language-reference/data-types/string-data-type.md) ve herhangi bir sayısal tür `Boolean`, veya [tarihi](../../../../visual-basic/language-reference/data-types/date-data-type.md)  
  
- Bu türden türetilmiş türe türü bir veri türü veya nesne dönüşümleri  
  
 Daraltma dönüştürmeleri her zaman çalışma zamanında başarılı ve başarısız veya veri kaybına neden. Hedef veri türüne dönüştürülen değer alamaz, bir hata meydana gelir. Örneğin, bir sayısal dönüştürme bir taşma neden olabilir. Derleyicisi daraltma dönüştürmelerini örtülü olarak sürece izin vermiyor [Option Strict deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md) anahtara denetimi türünü ayarlar `Off`.  
  
> [!NOTE]
>  Öğeleri dönüştürmelerinde daraltmaya dönüştürme hatası gizlenen bir `For Each…Next` döngü denetim değişkeni koleksiyonu. Daha fazla bilgi ve örnekler için "Daraltma dönüştürmeleri" bölümüne bakın. [her biri için... Sonraki deyimi](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Daraltma dönüştürmeleri kullanma zamanı  
 Kaynak değeri hedef veri türü hatası veya veri kaybı olmadan dönüştürülebilir bildiğiniz durumlarda bir daraltma dönüşümü kullanın. Örneğin, bir `String` kullanabileceğiniz içeren "True" veya "False" bildiğinizden, `CBool` öğesine dönüştürmek için anahtar sözcüğü `Boolean`.  
  
## <a name="exceptions-during-conversion"></a>Dönüşüm sırasında özel durumlar  
 Genişletme dönüştürmeleri her zaman başarılı, özel durumlar oluşturmayın. Daraltma dönüştürmeleri, başarısız olduğunda, en yaygın olarak aşağıdaki özel durumlar:  
  
- <xref:System.InvalidCastException> — iki tür arasında dönüştürme tanımlanmadıysa  
  
- <xref:System.OverflowException> — (sadece integral türleri) dönüştürülen değer hedef türü için çok büyük ise  
  
 Bir sınıf veya yapı tanımlıyorsa bir [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) , sınıf veya yapı, gelen veya dönüştürme işleci olarak görev yapacak, `CType` , uygun gördüğü herhangi bir özel durum oluşturabilir. Ayrıca, `CType` Visual Basic işlevleri veya hangi sırayla çeşitli özel durumlar oluşturabilir ve .NET Framework yöntemlerini çağırabilirsiniz.  
  
## <a name="changes-during-reference-type-conversions"></a>Başvuru türü dönüşümleri sırasında değişiklikleri  
 Dönüştürme bir *başvuru türüne* yalnızca işaretçi değerine kopyalar. Değer ne kopyalanamaz ya da herhangi bir şekilde değiştirildi. İşaretçi tutan değişken veri türünü değiştirmek için gereken tek şey var. Aşağıdaki örnekte, veri türü temel sınıfı için türetilen bir sınıftan dönüştürülür, ancak her iki değişken için artık işaret nesnesi değiştirilmez.  
  
```  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Dizeler ve Diğer Türler Arasında Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Nasıl yapılır: Bir nesneyi Visual Basic'de başka bir türe dönüştürme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Dizi Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
