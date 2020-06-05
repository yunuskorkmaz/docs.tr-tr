---
title: Dize Temelleri
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 935926b8b83afa47c20ea68aecd6bc8c40bd0234
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363703"
---
# <a name="string-basics-in-visual-basic"></a>Visual Basic'de Dize Temelleri
`String`Veri türü bir dizi karakteri temsil eder (her biri, veri türünün bir örneğini sırasıyla temsil eder `Char` ). Bu konuda Visual Basic içindeki dizelerin temel kavramları tanıtılmaktadır.  
  
## <a name="string-variables"></a>Dize değişkenleri  
 Bir dizenin örneğine, bir dizi karakteri temsil eden bir sabit değer atanabilir. Örnek:  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 Bir `String` değişken bir dize olarak değerlendirilen herhangi bir ifadeyi de kabul edebilir. Aşağıda örnekler gösterilmektedir:  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 Bir değişkene atanan tüm sabit değer `String` tırnak işaretleri ("") içine alınmalıdır. Bu, bir dize içindeki tırnak işaretinin bir tırnak işaretiyle temsil edimeyeceği anlamına gelir. Örneğin, aşağıdaki kod bir derleyici hatasına neden olur:  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 Derleyici ikinci tırnak işaretinden sonra dizeyi sonlandırdığından ve dizenin geri kalanı kod olarak yorumlandığı için bu kod hataya neden olur. Bu sorunu çözmek için, dize sabit değerindeki iki tırnak işaretini dizedeki bir tırnak işareti olarak yorumlar Visual Basic. Aşağıdaki örnek, bir dizeye tırnak işareti eklemenin doğru yolunu göstermektedir:  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 Yukarıdaki örnekte, sözcükten önceki iki tırnak `Look` işareti dizedeki bir tırnak işaretine dönüşür. Satırın sonundaki üç tırnak işareti, dizedeki bir tırnak işaretini ve dize sonlandırma karakterini temsil eder.  
  
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
 Bir dize bir dizi değer olarak düşünülebilir `Char` ve `String` tür, diziler tarafından izin verilen düzenlemelere benzer bir dizede birçok oluşturma gerçekleştirmenize olanak tanıyan yerleşik işlevlere sahiptir. .NET Framework tüm diziler gibi, bunlar sıfır tabanlı dizilerdir. Bir dizedeki belirli bir karaktere `Chars` , dizesinde göründüğü konuma göre erişmek için bir yol sağlayan özelliği aracılığıyla başvurabilirsiniz. Örnek:  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 Yukarıdaki örnekte, `Chars` dizesinin özelliği dizedeki dördüncü karakteri döndürür `D` ve bunu öğesine atar `myChar` . Ayrıca özelliği aracılığıyla belirli bir dizenin uzunluğunu da alabilirsiniz `Length` . Bir dizede birden çok dizi türü işleyici gerçekleştirmeniz gerekiyorsa, `Char` dizenin işlevini kullanarak bir örnek dizisine dönüştürebilirsiniz `ToCharArray` . Örnek:  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 Değişkeni `myArray` artık `Char` , her biri öğesinden bir karakteri temsil eden bir değer dizisi içerir `myString` .  
  
## <a name="the-immutability-of-strings"></a>Dizelerin Imlebilirlik kullanılabilirliği  
 Bir dize *sabittir*, yani değeri oluşturulduktan sonra değiştirilemez. Ancak, bu, bir dize değişkenine birden fazla değer atanmasını engellemez. Aşağıdaki örneği inceleyin:  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 Burada bir dize değişkeni oluşturulur, bir değer verilir ve sonra değeri değiştirilir.  
  
 Özellikle, ilk satırda, türünün bir örneği `String` oluşturulur ve değeri verilir `This string is immutable` . Örneğin ikinci satırında yeni bir örnek oluşturulur ve değeri verilir `Or is it?` ve dize değişkeni, ilk örneğe başvurusunu atar ve yeni örneğe bir başvuru depolar.  
  
 Diğer iç veri türlerinden farklı olarak, `String` bir başvuru türüdür. Bir başvuru türü değişkeni bir işleve veya alt yordama bağımsız değişken olarak geçirildiğinde, dizenin gerçek değeri yerine verilerin depolandığı bellek adresine yönelik bir başvuru geçirilir. Bu nedenle, önceki örnekte, değişkenin adı aynı kalır, ancak `String` yeni değeri tutan sınıfının yeni ve farklı bir örneğine işaret eder.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic'de Dizelere Giriş](introduction-to-strings.md)
- [Dize Veri Türü](../../../language-reference/data-types/string-data-type.md)
- [Char Veri Türü](../../../language-reference/data-types/char-data-type.md)
- [Temel dize Işlemleri](../../../../standard/base-types/basic-string-operations.md)
