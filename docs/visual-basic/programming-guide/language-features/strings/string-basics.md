---
title: Dize Temelleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7141966e3c8a8cbce42111c56a85a00709e8fe1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344289"
---
# <a name="string-basics-in-visual-basic"></a>Visual Basic'de Dize Temelleri
`String` veri türü bir dizi karakteri temsil eder (her biri, `Char` veri türünün bir örneğini sırasıyla temsil eder). Bu konuda Visual Basic içindeki dizelerin temel kavramları tanıtılmaktadır.  
  
## <a name="string-variables"></a>Dize değişkenleri  
 Bir dizenin örneğine, bir dizi karakteri temsil eden bir sabit değer atanabilir. Örneğin:  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 Bir `String` değişkeni bir dize olarak değerlendirilen herhangi bir ifadeyi de kabul edebilir. Aşağıda örnekler gösterilmektedir:  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 Bir `String` değişkenine atanan tüm sabit değer tırnak işaretleri ("") içine alınmalıdır. Bu, bir dize içindeki tırnak işaretinin bir tırnak işaretiyle temsil edimeyeceği anlamına gelir. Örneğin, aşağıdaki kod bir derleyici hatasına neden olur:  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 Derleyici ikinci tırnak işaretinden sonra dizeyi sonlandırdığından ve dizenin geri kalanı kod olarak yorumlandığı için bu kod hataya neden olur. Bu sorunu çözmek için, dize sabit değerindeki iki tırnak işaretini dizedeki bir tırnak işareti olarak yorumlar Visual Basic. Aşağıdaki örnek, bir dizeye tırnak işareti eklemenin doğru yolunu göstermektedir:  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 Yukarıdaki örnekte, sözcükten önceki iki tırnak işareti `Look` dizedeki bir tırnak işareti haline gelir. Satırın sonundaki üç tırnak işareti, dizedeki bir tırnak işaretini ve dize sonlandırma karakterini temsil eder.  
  
 Dize sabit değerleri birden çok satır içerebilir:  
  
```vb  
Dim x = "hello  
world"  
```  
  
 Elde edilen dize, dize sabit değerinde kullandığınız yeni satır dizilerini içerir (vbCr, vbCrLf, vb.).  Artık eski geçici çözümü kullanmanız gerekmez:  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a>Dizelerdeki karakterler  
 Bir dize bir dizi `Char` değeri olarak düşünülebilir ve `String` türü, diziler tarafından izin verilen düzenlemelere benzer bir dizede birçok oluşturma gerçekleştirmenize olanak tanıyan yerleşik işlevlere sahiptir. .NET Framework tüm diziler gibi, bunlar sıfır tabanlı dizilerdir. Bir dizeye, dizede göründüğü konuma göre erişmek için bir yol sağlayan `Chars` özelliği aracılığıyla dizedeki belirli bir karaktere başvurabilirsiniz. Örneğin:  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 Yukarıdaki örnekte, dizenin `Chars` özelliği dizedeki dördüncü karakteri döndürür, bu `D`ve `myChar`atar. Ayrıca, `Length` özelliği aracılığıyla belirli bir dizenin uzunluğunu da alabilirsiniz. Bir dizede birden çok dizi türü işleyici gerçekleştirmeniz gerekiyorsa, dizenin `ToCharArray` işlevini kullanarak bunu bir `Char` örnekleri dizisine dönüştürebilirsiniz. Örneğin:  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 `myArray` değişkeni artık, her biri `myString`karakteri temsil eden bir `Char` değerleri dizisi içerir.  
  
## <a name="the-immutability-of-strings"></a>Dizelerin Imlebilirlik kullanılabilirliği  
 Bir dize *sabittir*, yani değeri oluşturulduktan sonra değiştirilemez. Ancak, bu, bir dize değişkenine birden fazla değer atanmasını engellemez. Aşağıdaki örnek göz önünde bulundurun:  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 Burada bir dize değişkeni oluşturulur, bir değer verilir ve sonra değeri değiştirilir.  
  
 Daha belirgin olarak, ilk satırda `String` türünde bir örnek oluşturulur ve `This string is immutable`değeri verilir. Örneğin ikinci satırında yeni bir örnek oluşturulur ve değer `Or is it?`verilir ve dize değişkeni, ilk örneğe başvurusunu atar ve yeni örneğe bir başvuru depolar.  
  
 Diğer iç veri türlerinden farklı olarak `String` bir başvuru türüdür. Bir başvuru türü değişkeni bir işleve veya alt yordama bağımsız değişken olarak geçirildiğinde, dizenin gerçek değeri yerine verilerin depolandığı bellek adresine yönelik bir başvuru geçirilir. Bu nedenle, önceki örnekte, değişkenin adı aynı kalır, ancak yeni değeri tutan `String` sınıfının yeni ve farklı bir örneğine işaret eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic dizelere giriş](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [String Veri Türü](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Char Veri Türü](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Temel Dize İşlemleri](../../../../standard/base-types/basic-string-operations.md)
