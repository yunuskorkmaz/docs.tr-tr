---
title: Kod'da Özel Karakterler (Visual Basic)
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
ms.openlocfilehash: 95bef937912e35cd828bf0090b4cf48ccb3290cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962475"
---
# <a name="special-characters-in-code-visual-basic"></a>Kod'da Özel Karakterler (Visual Basic)
Bazen kodunuzda özel karakterler kullanmanız gerekir, diğer bir deyişle, alfabetik veya sayısal olmayan karakterler. Visual Basic karakter kümesindeki noktalama ve özel karakterlerin çeşitli kullanımları vardır ve program metnini, derleyicinin ya da derlenmiş programın gerçekleştirdiği görevleri tanımlamaya yönelik olarak düzenler. Gerçekleştirilecek bir işlem belirtmez.  
  
## <a name="parentheses"></a>Ayraçlar  
 `Sub` Veya`Function`gibi bir yordam tanımladığınızda ayraçları kullanın. Tüm yordam bağımsız değişken listelerini parantez içine almalısınız. Ayrıca, özellikle karmaşık bir ifadede işleç önceliği varsayılan sırasını geçersiz kılmak için, değişkenleri veya bağımsız değişkenleri mantıksal gruplara koymak için parantez de kullanabilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 Önceki kodun yürütülmesi sonrasında, değeri `d` 8,225 ve `e` değeri 3 ' dir. İçin `d` hesaplama, '`+` ın `/` ' de `d = b + (c / a)`varsayılan önceliğini kullanır. Hesaplama içindeki parantezler varsayılan önceliği `e` geçersiz kılar.  
  
## <a name="separators"></a>Ayırıcı  
 Ayırıcılar, adının ne gibi bir bölümünü ayırır: Visual Basic, ayırıcı karakter iki nokta (`:`) ' dır. Ayrı satırlar yerine tek bir satıra birden çok deyim eklemek istediğinizde ayırıcılar kullanın. Bu, alanı kaydeder ve kodunuzun okunabilirliğini geliştirir. Aşağıdaki örnekte, iki nokta üst üste ile ayrılmış üç deyim gösterilmektedir.  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 Daha fazla bilgi için [nasıl yapılır: Koddaki](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)deyimleri bölün ve birleştirin.  
  
 İki nokta (`:`) karakteri de bir ifade etiketini tanımlamak için kullanılır. Daha fazla bilgi için [nasıl yapılır: Label deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Bitiştirme  
 Birleştirmek veya dizeleri birbirinebağlamak için işlecinikullanın.`&` Sayısal değerleri bir araya ekleyen `+` işleçle karıştırmayın. Sayısal değerler üzerinde çalışırken `+` birleştirme için işlecini kullanırsanız, yanlış sonuçlar elde edebilirsiniz. Aşağıdaki örnek bunu gösterir.  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 Önceki kodun yürütülmesi sonrasında, değeri `resultA` 21,01 ve `resultB` değeri "10,0111" olur.  
  
## <a name="member-access-operators"></a>Üye erişim Işleçleri  
 Bir türün üyesine erişmek için, tür adı ve üye adı arasında nokta`.`() veya ünlem işareti`!`() işlecini kullanırsınız.  
  
### <a name="dot--operator"></a>Nokta (.) İşleç  
 `.` İşleci bir sınıf, yapı, arabirim veya sabit listesi üzerinde üye erişim işleci olarak kullanın. Üye bir alan, özellik, olay veya yöntem olabilir. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>Ünlem işareti (!) İşleç  
 `!` İşleci yalnızca bir sınıf veya arabirimde sözlük erişim işleci olarak kullanın. Sınıfın veya arabirimin tek `String` bir bağımsız değişkeni kabul eden bir varsayılan özelliği olmalıdır. `!` İşlecinden hemen sonraki tanımlayıcı, varsayılan özelliğe dize olarak geçirilen bağımsız değişken değeri olur. Aşağıdaki örnek bunu gösterir.  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 Her birinin `MsgBox` üç çıkış satırı değeri `32856`görüntüler. İlk satır geleneksel erişim özelliğini `index`kullanır, ikincisi sınıfının `hasDefault`varsayılan özelliği olan `index` olguyu kullanır ve üçüncüsü ise sınıfa sözlük erişimi sağlar.  
  
 `!` İşlecin ikinci işleneninin, çift tırnak işaretleri (`" "`) içine alınmış geçerli bir Visual Basic tanımlayıcı olması gerektiğini unutmayın. Diğer bir deyişle, bir dize sabit değeri veya dize değişkeni kullanamazsınız. `MsgBox` Çağrının son satırına yapılan aşağıdaki değişiklik bir hata oluşturur çünkü `"X"` bir kapalı dize sabit değeri.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> Varsayılan koleksiyonlara yapılan başvurular açık olmalıdır. Özellikle, `!` işlecini geç bağlı bir değişkende kullanamazsınız.  
  
 Karakter, `Single` tür karakteri olarak da kullanılır. `!`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Tür Karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
