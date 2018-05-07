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
ms.openlocfilehash: 932b38d97b36292e66bfad91a9a3799459d3b73c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="special-characters-in-code-visual-basic"></a>Kod'da Özel Karakterler (Visual Basic)
Bazen alfabetik veya sayısal olmayan karakterler kodunuzda, diğer bir deyişle, özel karakterler kullanmak zorunda. Noktalama işaretleri ve özel karakterler Visual Basic karakter kümesinde derleyici ya derlenmiş program gerçekleştirdiği görevleri tanımlamak için program metin düzenleme gelen çeşitli kullanımlar vardır. Bir işlemin gerçekleştirilmesi için belirtmeyin.  
  
## <a name="parentheses"></a>Parantez  
 Bir yordam gibi tanımlarken parantez kullanmak bir `Sub` veya `Function`. Tüm yordam bağımsız değişken listeleri parantez içine almanız gerekir. Ayrıca parantez mantıksal gruplar halinde koyarak değişkenleri veya bağımsız değişkenler için özellikle karmaşık bir ifadede İşleç önceliği varsayılan sırasını geçersiz kılmak için kullanın. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 Değerini önceki kod yürütmeyi izleyen `d` 8.225 ve değerini `e` 3'tür. Hesaplama için `d` varsayılan önceliği kullanan `/` üzerinden `+` ve eşdeğerdir `d = b + (c / a)`. Hesaplama için parantezlerde `e` varsayılan önceliği geçersiz kılar.  
  
## <a name="separators"></a>Ayırıcı  
 Ayırıcılar yapmak ne adlarının önerir: kodun bölümlerini ayırın. Visual Basic'te iki nokta üst üste ayırıcı karakteridir (`:`). Birden çok deyime ayrı satırlara yerine tek bir satırda dahil etmek istediğiniz zaman ayırıcı kullanın. Bu alanı kaydeder ve kodunuzun okunabilirliğini artırır. Aşağıdaki örnekte, üç değerlerini virgüllerle ayrılmış gösterir.  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 Daha fazla bilgi için bkz: [nasıl yapılır: Break ve kodda deyimleri birleştirmek](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 İki nokta üst üste (`:`) karakter deyimi etiket tanımlamak için de kullanılır. Daha fazla bilgi için bkz: [nasıl yapılır: Etiket deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Bitiştirme  
 Kullanım `&` işleci için *birleştirme*, veya dizeleri birbirine bağlama. İle karıştırmayın `+` sayısal değerleri toplar işleci. Kullanırsanız `+` sayısal değerler üzerinde çalışır, birleştirmek için işleci hatalı sonuçlar elde edebilirsiniz. Aşağıdaki örnekte bu gösterir.  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 Değerini önceki kod yürütmeyi izleyen `resultA` 21.01 ve değeri `resultB` "10.0111" değil.  
  
## <a name="member-access-operators"></a>Üye erişimi işleçleri  
 Bir tür üyesi erişmek için nokta kullanın (`.`) veya ünlem işareti (`!`) arasında tür ve üye adı işleci.  
  
### <a name="dot--operator"></a>Nokta (.) İşleç  
 Kullanım `.` sınıfı, yapısı, arabirim veya numaralandırma operatör olarak bir üye erişimi işleci. Üye alan, özellik, olay veya yöntem olabilir. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a>Ünlem işareti (!) İşleç  
 Kullanım `!` işlecinin yalnızca bir sınıfta veya arabirimde bir sözlük erişim işleci olarak. Sınıf veya arabirim tek bir kabul eder ve varsayılan bir özellik olmalıdır `String` bağımsız değişkeni. Hemen ardından tanımlayıcı `!` işleci bir dize olarak varsayılan özelliği için geçirilen bağımsız değişken değeri olur. Aşağıdaki örnekte bu gösterir.  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 Üç satırlık çıktı `MsgBox` tüm değerini görüntülemek `32856`. Geleneksel erişim özelliğine ilk satırını kullanır `index`, ikinci kullanır olgu, `index` varsayılan sınıfın özelliğidir `hasDefault`, ve üçüncü sözlük erişim sınıfına kullanır.  
  
 Unutmayın, ikinci işlenen `!` işleci, çift tırnak işaretleri içine alınmamış geçerli bir Visual Basic tanımlayıcı olmalıdır (`" "`). Diğer bir deyişle, bir değişmez dize veya dize değişkeni kullanamazsınız. Şu son satırının değiştirin `MsgBox` çağrısı bir hata nedeniyle oluşturur `"X"` kapalı bir dize değişmez değer olduğunu.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  Varsayılan koleksiyon başvurularını açık olması gerekir. Özellikle, kullanamazsınız `!` geç bağlama değişken işleci.  
  
 `!` Karakter olarak da kullanılır `Single` karakteri yazın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Tür Karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
