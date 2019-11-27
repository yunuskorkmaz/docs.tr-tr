---
title: Kod'da Özel Karakterler
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: f4ab35b56d48ae86bdb024ffea27735b39decdc2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347263"
---
# <a name="special-characters-in-code-visual-basic"></a>Kod'da Özel Karakterler (Visual Basic)
Bazen kodunuzda özel karakterler kullanmanız gerekir, diğer bir deyişle, alfabetik veya sayısal olmayan karakterler. Visual Basic karakter kümesindeki noktalama ve özel karakterlerin çeşitli kullanımları vardır ve program metnini, derleyicinin ya da derlenmiş programın gerçekleştirdiği görevleri tanımlamaya yönelik olarak düzenler. Gerçekleştirilecek bir işlem belirtmez.  
  
## <a name="parentheses"></a>ayraçlar  
 `Sub` veya `Function`gibi bir yordam tanımlarken ayraçları kullanın. Tüm yordam bağımsız değişken listelerini parantez içine almalısınız. Ayrıca, özellikle karmaşık bir ifadede işleç önceliği varsayılan sırasını geçersiz kılmak için, değişkenleri veya bağımsız değişkenleri mantıksal gruplara koymak için parantez de kullanabilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 Önceki kodun yürütülmesi sırasında, `d` değeri 8,225 ve `e` değeri 3 ' dir. `d` hesaplama, `/` varsayılan önceliği `+` kullanır ve `d = b + (c / a)`eşdeğerdir. `e` hesaplamasında parantez varsayılan önceliği geçersiz kılar.  
  
## <a name="separators"></a>Ayırıcı  
 Ayırıcılar, adının ne gibi bir bölümünü ayırır: Visual Basic, ayırıcı karakter iki nokta olur (`:`). Ayrı satırlar yerine tek bir satıra birden çok deyim eklemek istediğinizde ayırıcılar kullanın. Bu, alanı kaydeder ve kodunuzun okunabilirliğini geliştirir. Aşağıdaki örnekte, iki nokta üst üste ile ayrılmış üç deyim gösterilmektedir.  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: kod Içinde deyimleri kesme ve birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 İki nokta (`:`) karakteri de bir ifade etiketini tanımlamak için kullanılır. Daha fazla bilgi için bkz. [nasıl yapılır: Label deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Birleştirme  
 *Birleştirmek*veya dizeleri birbirine bağlamak için `&` işlecini kullanın. Sayısal değerleri bir araya ekleyen `+` işleçle karıştırmayın. Sayısal değerler üzerinde çalışırken birleştirmek için `+` işlecini kullanırsanız, yanlış sonuçlar elde edebilirsiniz. Aşağıdaki örnek bunu gösterir.  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 Önceki kodun yürütülmesi sırasında, `resultA` değeri 21,01 ve `resultB` değeri "10,0111" olur.  
  
## <a name="member-access-operators"></a>Üye erişim Işleçleri  
 Bir türün üyesine erişmek için, tür adı ve üye adı arasında nokta (`.`) veya ünlem işareti (`!`) işlecini kullanırsınız.  
  
### <a name="dot--operator"></a>Nokta (.) İşlecinde  
 Bir sınıf, yapı, arabirim veya sabit listesi üzerinde `.` işlecini üye erişim işleci olarak kullanın. Üye bir alan, özellik, olay veya yöntem olabilir. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>Ünlem işareti (!) İşlecinde  
 `!` işlecini yalnızca bir sınıf veya arabirimde sözlük erişim işleci olarak kullanın. Sınıfın veya arabirimin tek bir `String` bağımsız değişkenini kabul eden bir varsayılan özelliği olmalıdır. `!` işlecinden hemen sonraki tanımlayıcı, varsayılan özelliğe dize olarak geçirilen bağımsız değişken değeri olur. Aşağıdaki örnek bunu gösterir.  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 `MsgBox` her birinin üç çıkış satırı `32856`değeri görüntüler. İlk satır, özellik `index`için geleneksel erişimi kullanır, ikincisi, `index` sınıfının varsayılan özelliği olan `hasDefault`ve üçüncü sözlük ise sınıfa erişimi kullanır.  
  
 `!` işlecinin ikinci işleneni, çift tırnak işaretleri (`" "`) içine alınmış geçerli bir Visual Basic tanımlayıcısı olmalıdır. Diğer bir deyişle, bir dize sabit değeri veya dize değişkeni kullanamazsınız. `MsgBox` çağrısının son satırına yapılan aşağıdaki değişiklik bir hata üretir çünkü `"X"` bir kapalı dize sabit değeri.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> Varsayılan koleksiyonlara yapılan başvurular açık olmalıdır. Özellikle, `!` işlecini geç bağlı bir değişkende kullanamazsınız.  
  
 `!` karakteri `Single` tür karakteri olarak da kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Tür Karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
