---
title: Koddaki Özel Karakterler
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
ms.openlocfilehash: c9b170ed812474cdeee100f1dc388d5c7e85f2cc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400597"
---
# <a name="special-characters-in-code-visual-basic"></a>Kod'da Özel Karakterler (Visual Basic)
Bazen kodunuzda özel karakterler kullanmanız gerekir, diğer bir deyişle, alfabetik veya sayısal olmayan karakterler. Visual Basic karakter kümesindeki noktalama ve özel karakterlerin çeşitli kullanımları vardır ve program metnini, derleyicinin ya da derlenmiş programın gerçekleştirdiği görevleri tanımlamaya yönelik olarak düzenler. Gerçekleştirilecek bir işlem belirtmez.  
  
## <a name="parentheses"></a>Parantez  
 Veya gibi bir yordam tanımladığınızda ayraçları kullanın `Sub` `Function` . Tüm yordam bağımsız değişken listelerini parantez içine almalısınız. Ayrıca, özellikle karmaşık bir ifadede işleç önceliği varsayılan sırasını geçersiz kılmak için, değişkenleri veya bağımsız değişkenleri mantıksal gruplara koymak için parantez de kullanabilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 Önceki kodun yürütülmesi sonrasında, değeri `d` 8,225 ve değeri 3 ' dir `e` . İçin hesaplama, `d` `/` ' ın ' de varsayılan önceliğini kullanır `+` `d = b + (c / a)` . Hesaplama içindeki parantezler `e` varsayılan önceliği geçersiz kılar.  
  
## <a name="separators"></a>Ayırıcı  
 Ayırıcılar, adının ne gibi bir bölümünü ayırır: Visual Basic, ayırıcı karakter iki nokta () ' dır `:` . Ayrı satırlar yerine tek bir satıra birden çok deyim eklemek istediğinizde ayırıcılar kullanın. Bu, alanı kaydeder ve kodunuzun okunabilirliğini geliştirir. Aşağıdaki örnekte, iki nokta üst üste ile ayrılmış üç deyim gösterilmektedir.  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 Daha fazla bilgi için bkz. [nasıl yapılır: kod Içinde deyimleri kesme ve birleştirme](how-to-break-and-combine-statements-in-code.md).  
  
 İki nokta ( `:` ) karakteri de bir ifade etiketini tanımlamak için kullanılır. Daha fazla bilgi için bkz. [nasıl yapılır: Label deyimleri](how-to-label-statements.md).  
  
## <a name="concatenation"></a>Birleştirme  
 `&` *Birleştirmek*veya dizeleri birbirine bağlamak için işlecini kullanın. `+`Sayısal değerleri bir araya ekleyen işleçle karıştırmayın. `+`Sayısal değerler üzerinde çalışırken birleştirme için işlecini kullanırsanız, yanlış sonuçlar elde edebilirsiniz. Aşağıdaki örnek bunu gösterir.  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 Önceki kodun yürütülmesi sonrasında, değeri `resultA` 21,01 ve değeri `resultB` "10,0111" olur.  
  
## <a name="member-access-operators"></a>Üye erişim Işleçleri  
 Bir türün üyesine erişmek için, `.` `!` tür adı ve üye adı arasında nokta () veya ünlem işareti () işlecini kullanırsınız.  
  
### <a name="dot--operator"></a>Nokta (.) İşlecinde  
 `.`İşleci bir sınıf, yapı, arabirim veya sabit listesi üzerinde üye erişim işleci olarak kullanın. Üye bir alan, özellik, olay veya yöntem olabilir. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>Ünlem işareti (!) İşlecinde  
 `!`İşleci yalnızca bir sınıf veya arabirimde sözlük erişim işleci olarak kullanın. Sınıfın veya arabirimin tek bir bağımsız değişkeni kabul eden bir varsayılan özelliği olmalıdır `String` . İşlecinden hemen sonraki tanımlayıcı, `!` varsayılan özelliğe dize olarak geçirilen bağımsız değişken değeri olur. Aşağıdaki örnek bunu gösterir.  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 Her birinin üç çıkış satırı `MsgBox` değeri görüntüler `32856` . İlk satır geleneksel erişim özelliğini kullanır `index` , ikincisi sınıfının varsayılan özelliği olan olguyu kullanır `index` `hasDefault` ve üçüncüsü ise sınıfa sözlük erişimi sağlar.  
  
 İşlecin ikinci işleneninin, `!` çift tırnak işaretleri () içine alınmış geçerli bir Visual Basic tanımlayıcı olması gerektiğini unutmayın `" "` . Diğer bir deyişle, bir dize sabit değeri veya dize değişkeni kullanamazsınız. Çağrının son satırına yapılan aşağıdaki değişiklik `MsgBox` bir hata oluşturur çünkü `"X"` bir kapalı dize sabit değeri.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> Varsayılan koleksiyonlara yapılan başvurular açık olmalıdır. Özellikle, `!` işlecini geç bağlı bir değişkende kullanamazsınız.  
  
 `!`Karakter, tür karakteri olarak da kullanılır `Single` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Program yapısı ve kod kuralları](program-structure-and-code-conventions.md)
- [Tür Karakterleri](../language-features/data-types/type-characters.md)
