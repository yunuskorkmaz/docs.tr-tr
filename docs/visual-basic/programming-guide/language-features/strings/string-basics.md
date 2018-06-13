---
title: Visual Basic'de Dize Temelleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7d2477070dce558aa932c822852ac8ac9c6721e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654066"
---
# <a name="string-basics-in-visual-basic"></a>Visual Basic'de Dize Temelleri
`String` Veri türünü temsil eden bir karakter dizisi (her sırayla örneğini temsil eden `Char` veri türü). Bu konu, Visual Basic'de dizeleri temel kavramları tanıtır.  
  
## <a name="string-variables"></a>Dize değişkenleri  
 Bir dize örneği bir karakter dizisi temsil eden sabit bir değer atanabilir. Örneğin:  
  
 [!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]  
  
 A `String` değişkeni hesaplandığında bir dize sonucu herhangi bir ifade de kabul edebilir. Aşağıda örnekler gösterilmektedir:  
  
 [!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]  
  
 Atanan tüm sabit bir `String` değişkeni tırnak işaretleri içine alınmalıdır (""). Bu, tırnak işareti dize içinde bir tırnak işaretiyle gösterilen anlamına gelir. Örneğin, aşağıdaki kod derleyici hatasına neden olur:  
  
 [!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]  
  
 Bu kod, çünkü derleyici dize ikinci tırnağından sonra sonlandırır ve dizenin geri kalanı kodu olarak yorumlanır bir hataya neden olur. Bu sorunu çözmek için Visual Basic iki tırnak işaretleri içine bir dize sabit değeri dize tek tırnak işareti olarak yorumlar. Aşağıdaki örnek, bir tırnak işareti içindeki bir dizeye dahil etmek için doğru bir şekilde gösterir:  
  
 [!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]  
  
 Önceki örnekte, iki Word'ün önceki tırnak `Look` dizesindeki tek tırnak işareti haline gelir. Satırın sonundaki üç tırnak işaretleri dize ve dize sonlandırma karakter tek tırnak işareti temsil eder.  
  
 Dize değişmez değerleri birden fazla satır içerebilir:  
  
```vb  
Dim x = "hello  
world"  
```  
  
 Sonuç dizesini dizenizi içinde değişmez değer (vbcr, vbcrlf, vb.) kullanılan yeni satır sıraları içerir.  Artık eski geçici çözüm kullanmanız gerekir:  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a>Dizelerdeki karakterleri  
 Bir dize, bir dizi olarak düşünülebilir `Char` değerleri ve `String` türü diziler tarafından izin verilen işlemeleri benzer bir dizesine birçok işlemeleri gerçekleştirme olanak tanıyan yerleşik işlevler içeriyor. Tüm içinde dizi gibi [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], bu sıfır tabanlı dizidir. Belirli bir karakterin bir dizedeki bakabilirsiniz `Chars` özelliği bir karakter dizesini göründüğü konuma göre erişmek için bir yol sağlar. Örneğin:  
  
 [!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]  
  
 Yukarıdaki örnekte, `Chars` dize özelliği olan dizesinde dördüncü karakter döndürür `D`ve atar `myChar`. Belirli bir dizenin uzunluğunu elde edebilirsiniz `Length` özelliği. Bir dize üzerinde birden fazla dizi türü işlemeleri gerçekleştirme ihtiyacınız varsa, bir dizi için dönüştürebilirsiniz `Char` kullanarak örnekleri `ToCharArray` dize işlevi. Örneğin:  
  
 [!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]  
  
 Değişkeni `myArray` artık bir dizi içeren `Char` değerleri, her bir karakteri temsil eden `myString`.  
  
## <a name="the-immutability-of-strings"></a>Dizeleri girişi  
 Bir dize *değişmez*, değeri bir kez değiştirilemez anlamına oluşturuldu. Ancak, bu, dize değişkenine birden fazla değer atama engellemez. Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]  
  
 Burada, bir değeri verildiğinde bir dize değişkeni oluşturulur ve ardından değeri değiştirildi.  
  
 Daha açık belirtmek gerekirse, ilk satırda, türünün bir örneği `String` oluşturulur ve değeri verildiğinde `This string is immutable`. İkinci satırında Örneğin, yeni bir örneği oluşturulur ve değeri verildiğinde `Or is it?`, ve dize değişkeni, ilk örneğine başvuru atar ve yeni örneğine başvuru depolar.  
  
 Diğer iç veri türleri farklı `String` bir başvuru türüdür. Başvuru türünde bir değişken bağımsız değişken olarak bir işlev veya alt yordama geçirildiğinde, verilerinin depolandığı bellek adresi için bir başvuru dize gerçek değer yerine geçirilir. Önceki örnekte, değişkenin adını aynı kalır ancak bir yeni ve farklı örneğine işaret ediyor `String` yeni değeri tutan sınıfı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [String Veri Türü](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [Char Veri Türü](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Temel Dize İşlemleri](../../../../standard/base-types/basic-string-operations.md)
