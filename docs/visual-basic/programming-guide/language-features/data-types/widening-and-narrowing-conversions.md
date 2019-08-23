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
ms.openlocfilehash: 858b2b2e154b659470fa61b21f25ab61eabda012
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965648"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a>Genişletme ve Daraltma Dönüşümleri (Visual Basic)
Tür dönüştürmesinin sonucu, dönüştürme sonucunun hedef veri türünün aralığı içinde olup olmadığı konusunda önemli bir noktadır.  
  
 *Genişleyen dönüştürme* bir değeri, özgün verilerin olası bir değeri için izin verebilecek bir veri türüne dönüştürür.  Genişleyen dönüştürmeler kaynak değeri korur, ancak temsilini değiştirebilir. Bu, bir integral türünden `Decimal`veya ' `String`den `Char` ' ye dönüştürürseniz oluşur.  
  
 *Daraltma dönüştürmesi* bir değeri, olası değerlerden bazılarını tutabilecek bir veri türüne dönüştürür. Örneğin, bir tamsayı türüne dönüştürüldüğünde kesirli değer yuvarlanır ve dönüştürülecek `Boolean` sayısal bir tür ya `False`da `True` değerine düşürülür.  
  
## <a name="widening-conversions"></a>Dönüştürmeleri Genişletme  
 Aşağıdaki tabloda, standart genişletme dönüştürmeleri gösterilmektedir.  
  
|Veri türü|Widens-veri türleri <sup>1</sup>|  
|---|---|  
|[SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[Bayt](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Kısadır](../../../../visual-basic/language-reference/data-types/short-data-type.md)|`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`|  
|[UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`|  
|[Gir](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Kalacağını](../../../../visual-basic/language-reference/data-types/long-data-type.md)|`Long`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|['Tur](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Kategori](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`, `Single`, `Double`<sup>2</sup>|  
|[Sunuculu](../../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`, `Double`|  
|[Çift](../../../../visual-basic/language-reference/data-types/double-data-type.md)|`Double`|  
|Herhangi bir numaralandırılmış tür ([enum](../../../../visual-basic/language-reference/statements/enum-statement.md))|Temel alınan integral türü ve temel alınan tür widens olan herhangi bir tür.|  
|[Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`Char`, `String`|  
|`Char`dizide|`Char`dizide`String`|  
|Herhangi bir tür|[Nesne](../../../../visual-basic/language-reference/data-types/object-data-type.md)|  
|Türetilmiş herhangi bir tür|<sup>3</sup>' ün türetildiği temel tür.|  
|Herhangi bir tür|Uyguladığı herhangi bir arabirim.|  
|[Nothing](../../../../visual-basic/language-reference/nothing.md)|Herhangi bir veri türü veya nesne türü.|  
  
 <sup>1</sup> tanım, her veri türü ise widens.  
  
 <sup></sup> `Integer`, `Double` `Single` ,, veya`Decimal` ile arasındaki dönüşümler duyarlık kaybına neden olabilir, ancak hiçbir şekilde büyüklük kaybı olmaz. `UInteger` `Long` `ULong` Bu anlamda bilgi kaybı yoktur.  
  
 <sup>3</sup> bu, türetilmiş bir türden bir dönüştürmenin temel türlerinden birine dönüştürülmesinin genişleyen olduğunu ortaya çıkarmayabilir. Gerekçe, türetilmiş türün temel türün tüm üyelerini içermesinden dolayı temel türün bir örneği olarak nitelendirir. Ters yönde, temel tür türetilmiş tür tarafından tanımlanan yeni üyeleri içermez.  
  
 Genişletme dönüştürmeleri her zaman çalışma zamanında başarılı olur ve veri kaybına neden olmaz. Bağımsız olarak, [katı deyimin](../../../../visual-basic/language-reference/statements/option-strict-statement.md) tür denetleme anahtarını `On` veya olarak `Off`ayarlamadığını örtülü olarak yapabilirsiniz.  
  
## <a name="narrowing-conversions"></a>Daraltma dönüştürmeleri  
 Standart daraltma dönüştürmeleri şunları içerir:  
  
- Yukarıdaki tabloda genişleyen dönüştürmelerin ters yönleri (her tür widens kendisi hariç)  
  
- [Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) ve herhangi bir sayısal tür arasındaki iki yönde dönüştürme  
  
- Herhangi bir sayısal türden herhangi bir numaralandırılmış türe (`Enum`) dönüştürme  
  
- [Dize](../../../../visual-basic/language-reference/data-types/string-data-type.md) ile herhangi bir sayısal tür, `Boolean`ya da [Tarih](../../../../visual-basic/language-reference/data-types/date-data-type.md) arasındaki yönde dönüşümler  
  
- Veri türünden veya nesne türünden türetilmiş bir türe dönüşümler  
  
 Daraltma dönüştürmeleri her zaman çalışma zamanında başarılı olmaz ve veri kaybına neden olabilir. Hedef veri türü dönüştürülürken değeri alamadıysanız bir hata oluşur. Örneğin, sayısal bir dönüştürme taşmaya neden olabilir. [Kesin ifade](../../../../visual-basic/language-reference/statements/option-strict-statement.md) tür denetimi olarak `Off`ayarlarsa, derleyici daraltma dönüştürmelerini örtülü olarak gerçekleştirmenize izin vermez.  
  
> [!NOTE]
> Daraltma dönüştürme hatası, bir `For Each…Next` koleksiyondaki öğelerden döngü denetim değişkenine dönüşümler için bastırılır. Daha fazla bilgi ve örnek için, her biri Için içindeki "dönüştürmeleri daraltma" bölümüne bakın [... Sonraki Ifade](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
### <a name="when-to-use-narrowing-conversions"></a>Daraltma dönüştürmelerinde ne zaman kullanılır?  
 Kaynak değerin hata veya veri kaybı olmadan hedef veri türüne dönüştürülebileceğini bildiğiniz zaman bir daraltma dönüştürmesi kullanırsınız. Örneğin, "true" veya " `String` false" içeren bir bilginiz varsa, bunu öğesine `Boolean`dönüştürmek için `CBool` anahtar sözcüğünü kullanabilirsiniz.  
  
## <a name="exceptions-during-conversion"></a>Dönüştürme sırasında özel durumlar  
 Genişletme dönüştürmeleri her zaman başarılı olduğundan, özel durum oluşturmaz. Daraltma dönüştürmeleri, başarısız olduğunda, genellikle aşağıdaki özel durumları oluşturur:  
  
- <xref:System.InvalidCastException>— iki tür arasında dönüştürme tanımlanmazsa  
  
- <xref:System.OverflowException>— (yalnızca integral türleri) dönüştürülen değer hedef türü için çok büyükse  
  
 Bir sınıf veya yapı, bu sınıfa veya yapıya dönüştürme işleci olarak kullanılmak üzere bir [CType işlevi](../../../../visual-basic/language-reference/functions/ctype-function.md) tanımlıyorsa, `CType` uygun bir özel durum oluşturabilir. Ayrıca, Visual Basic işlevleri `CType` veya .NET Framework yöntemleri çağırabilir ve bu da çeşitli özel durumlar oluşturabilir.  
  
## <a name="changes-during-reference-type-conversions"></a>Başvuru türü dönüştürmeleri sırasında yapılan değişiklikler  
 *Başvuru türünden* bir dönüştürme yalnızca işaretçiyi değere kopyalar. Değerin kendisi hiçbir şekilde kopyalanmaz veya değiştirilmez. Değişebilir tek şey, işaretçiyi tutan değişkenin veri türüdür. Aşağıdaki örnekte, veri türü türetilmiş sınıftan taban sınıfına dönüştürülür, ancak her iki değişkenin de işaret eden nesnesi değiştirilmez.  
  
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
- [Visual Basic dönüşümler yazın](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Örtük ve Açık Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Dizeler ve Diğer Türler Arasında Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [Nasıl yapılır: Visual Basic bir nesneyi başka bir türe dönüştürme](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [Dizi Dönüştürmeler](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
- [Tür Dönüştürme İşlevleri](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
