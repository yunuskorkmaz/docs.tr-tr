---
title: Visual Basic'de Dize Temelleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 9d2d3c82f5512bc1e37e3b05086fbd364ee12298
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938339"
---
# <a name="string-basics-in-visual-basic"></a>Visual Basic'de Dize Temelleri
`String` Veri türünü temsil eden bir karakter dizisi (her sırayla örneğini temsil eden `Char` veri türü). Bu konu Visual Basic'de dizeleri temel kavramları tanıtır.  
  
## <a name="string-variables"></a>Dize değişkenleri  
 Bir dizenin bir örneğini temsil eden bir karakter dizisi değişmez değer atanabilir. Örneğin:  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 A `String` değişkeni de bir dizeye değerlendirilen bir ifade kabul edin. Aşağıda örnekler gösterilmektedir:  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 Atanan tüm sabit bir `String` değişkeni tırnak içine alınmalıdır (""). Bu, bir dize içindeki bir tırnak işareti bir tırnak işareti temsil edilemeyen anlamına gelir. Örneğin, aşağıdaki kod bir derleyici hatasına neden olur:  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 Bu kod, çünkü derleyici dize ikinci bir tırnak işaretinden sonra sona erer ve dizenin geri kalanı, kod olarak yorumlanır, bir hataya neden olur. Bu sorunu çözmek için Visual Basic, iki tırnak işaretleri dize değişmez değeri tek tırnak işareti içinde dize olarak yorumlar. Aşağıdaki örnek, bir dizedeki bir tırnak işareti eklemek için doğru şekilde gösterir:  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 Yukarıdaki örnekte, iki tırnak işaretleri Word'ün önceki `Look` dizesinde tek tırnak işareti haline gelir. Satır sonundaki üç tırnak işaretleri dize ve dize sonlandırma karakter bir tırnak işareti temsil eder.  
  
 Çok satırlı dize değişmez değerleri içerebilir:  
  
```vb  
Dim x = "hello  
world"  
```  
  
 Ortaya çıkan dize, dize sabit değerinde (vbcr, vbcrlf, vb.) kullanılan yeni satır dizilerinin içerir.  Artık eski geçici çözümü kullanmanız gerekir:  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a>Dizelerdeki karakterleri  
 Bir dize, bir dizi olarak düşünülebilir `Char` değerleri ve `String` türü diziler tarafından izin verilen işlemeleri benzer bir dizesine birçok işlemeleri gerçekleştirme olanak tanıyan yerleşik işlevleri vardır. İçindeki tüm dizi gibi [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], sıfır tabanlı diziler şunlardır. Bir dize içinde belirli bir karakter bakabilirsiniz `Chars` özelliği bir karakter dizesi içinde göründüğü konumu erişmek için bir yol sağlar. Örneğin:  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 Yukarıdaki örnekte, `Chars` dize özelliğini döndürür dördüncü karakter olan dizesinde `D`ve buna atayan `myChar`. Belirli bir dizenin uzunluğunu da edinebilirsiniz `Length` özelliği. Bir dize üzerinde birden fazla dizi türü değişikliklerini gerçekleştirmeniz gerekiyorsa, bunu bir dizisi olarak dönüştürebilirsiniz `Char` kullanarak örnekler `ToCharArray` dize işlevi. Örneğin:  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 Değişken `myArray` artık bir dizi içeren `Char` değerleri, her bir karakteri temsil eden `myString`.  
  
## <a name="the-immutability-of-strings"></a>Değiştirilemezlik dizeler  
 Bir dizedir *değişmez*, değeri bir kez değiştirilemez anlamına oluşturuldu. Ancak, bu, birden fazla değer bir dize değişkenine atamanızı engellemez. Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 Burada verilen bir değer bir dize değişkeni oluşturulur ve ardından değeri değiştirilir.  
  
 Özellikle, ilk satırda, türün bir örneğini `String` oluşturulur ve değerin `This string is immutable`. Örneğin ikinci satırda yeni bir örneği oluşturulur ve değerin `Or is it?`, string değişkeni, ilk örneğine başvuru atar ve yeni örneğe bir başvuru depolar.  
  
 Diğer iç veri türleri farklı `String` bir başvuru türüdür. Verilerin depolandığı bellek adresi başvurusu, başvuru türünde bir değişken bağımsız değişken olarak bir işlev veya alt yordamı geçirildiğinde, gerçek dize değerini yerine geçirilir. Önceki örnekte, değişken adı aynı kalır, ancak bir yeni ve farklı örneğine işaret `String` yeni değeri tutan sınıfı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [String Veri Türü](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Char Veri Türü](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Temel Dize İşlemleri](../../../../standard/base-types/basic-string-operations.md)
