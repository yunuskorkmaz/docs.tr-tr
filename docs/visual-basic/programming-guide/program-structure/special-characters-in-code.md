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
ms.openlocfilehash: 65fcd10521742e287c7934080b3352a06668df7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967992"
---
# <a name="special-characters-in-code-visual-basic"></a>Kod'da Özel Karakterler (Visual Basic)
Bazen özel karakterler kodunuzda, diğer bir deyişle, alfabetik veya sayısal olmayan karakterler kullanmak gerekir. Noktalama işaretleri ve özel karakterler Visual temel karakter kümesinde derleyici veya derlenmiş programın gerçekleştirdiği görevler tanımlama program metni düzenleme gelen çeşitli kullanımlar sahip. Gerçekleştirilecek bir işlemi belirtmeyin.  
  
## <a name="parentheses"></a>Parantez  
 Bir yordam gibi tanımlarken parantez kullanan bir `Sub` veya `Function`. Tüm yordam bağımsız değişken listeleri parantez içine almalısınız. De parantez değişkenleri ya da bağımsız değişkenler mantıksal gruplar halinde koymak için özellikle karmaşık bir ifadede İşleç önceliği varsayılan düzenini geçersiz kılmak için kullanabilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 Değerini önceki kodu yürütülmesinin `d` 8.225 ve değerini `e` 3'tür. Hesaplama için `d` varsayılan önceliği kullanan `/` üzerinden `+` ve eşdeğerdir `d = b + (c / a)`. Hesaplama için parantezler `e` varsayılan önceliği geçersiz kılar.  
  
## <a name="separators"></a>Ayırıcı  
 Ayırıcılar yapmak ne kendi adından da anlaşılacağı: Bunlar kod bölümlerini ayırın. Visual Basic'te iki nokta üst üste ayırıcı karakteridir (`:`). Birden çok deyime ayrı satırlara yerine tek bir satırda dahil etmek istediğiniz zaman ayırıcı kullanın. Bu alan tasarrufu yapılmasını sağlar ve kodunuzun okunabilirliği geliştirir. Aşağıdaki örnek, üç deyimi virgülle ayırarak gösterir.  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 Daha fazla bilgi için [nasıl yapılır: Kodda deyimleri bölme ve birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 İki nokta üst üste (`:`) karakter deyimi etiketi belirlemek için de kullanılır. Daha fazla bilgi için [nasıl yapılır: Etiket deyimleri](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>Bitiştirme  
 Kullanım `&` işleci için *birleştirme*, veya dizeleri birbirine bağlayarak. İle karıştırmayın `+` işleci, sayısal değerleri toplar. Kullanırsanız `+` işleci sayısal değerler üzerinde çalışır, birleştirmek için hatalı sonuçlar elde edebilirsiniz. Aşağıdaki örnekte bu gösterir.  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 Değerini önceki kodu yürütülmesinin `resultA` 21.01 ve değerini `resultB` "10.0111" olduğu.  
  
## <a name="member-access-operators"></a>Üye erişim işleçleri  
 Türünün bir üyesine erişmek için nokta kullanın (`.`) ya da ünlem işareti (`!`) arasında tür adı ve üye adı işleci.  
  
### <a name="dot--operator"></a>Nokta (.) İşleç  
 Kullanım `.` sınıfı, yapı, arabirim ya da numaralandırma işlecinin bir üye erişim işleci olarak. Üye bir alan, özelliği, olay veya yöntemi olabilir. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>Ünlem işareti (!) İşleç  
 Kullanım `!` sözlük erişim işleci olarak yalnızca bir sınıf veya arabirim üzerinde işleci. Sınıf veya arabirim kabul eden tek bir varsayılan özellik olmalıdır `String` bağımsız değişken. Hemen tanımlayıcısı `!` işleci bir dize olarak varsayılan özelliği için geçirilen bağımsız değişken değeri olur. Aşağıdaki örnekte bu gösterir.  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 Üç satır çıkış `MsgBox` tüm görüntüleme `32856`. Geleneksel erişim özelliği ilk satırını kullanır `index`, ikinci kullanır olgu, `index` sınıfın varsayılan özelliğidir `hasDefault`, ve üçüncü sözlük erişimi sınıfı kullanır.  
  
 Unutmayın, ikinci işlenenin `!` işleci, çift tırnak işaretleri arasına değil, geçerli bir Visual Basic tanımlayıcı olmalıdır (`" "`). Diğer bir deyişle, bir dize sabit değeri veya dize değişkeni kullanamazsınız. Şu son satırını değiştirin `MsgBox` çağrı olduğundan hata oluşturur `"X"` kapalı bir dize sabitidir.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  Varsayılan koleksiyon başvuruları açık olması gerekir. Özellikle, kullanamazsınız `!` geç bağlanan bir değişken üzerinde işleci.  
  
 `!` Karakter olarak kullanılan ayrıca `Single` karakter yazın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Tür Karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
