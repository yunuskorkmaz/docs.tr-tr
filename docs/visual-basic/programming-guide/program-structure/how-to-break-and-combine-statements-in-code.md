---
title: 'Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
ms.openlocfilehash: 6bca3d62cb3e886ee08b9169d63d4c3a38247f3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651024"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a>Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme (Visual Basic)
Kodunuzu yazarken, bazen Kod düzenleyicisinde yatay kaydırma başlatılmalarını uzun deyimleri oluşturabilirsiniz. Bu şekilde etkilemez, ancak kodunuzun çalıştığı, onu başkalarının veya monitörde göründüğü gibi kodunu okumak zorlaştırır. Böyle durumlarda, tek uzun deyimi birkaç satırlara ayırma göz önünde bulundurmalısınız.  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a>Tek bir deyimde birden çok çizgiye bölün için  
  
-   Alt çizgi olan satır devamlılığı karakteri kullanın (`_`), satır sonu için istediğiniz noktada. Alt çizgi boşlukla hemen önünde ve bir satır Sonlandırıcı (başı) hemen ardından gerekir.  
  
    > [!NOTE]
    >  Satır devamlılığı karakteri atlarsanız, bazı durumlarda, Visual Basic derleyici örtük olarak deyim kodun sonraki satırında devam eder. Kendisi için kullanmayabilir satır devamlılığı karakteri söz dizimi öğeleri listesi için bkz: "Örtük satır devamlılığı" [deyimleri](../../../visual-basic/programming-guide/language-features/statements.md).  
  
     Aşağıdaki örnekte, tüm sonlandırma satır devamlılığı karakteri dört satırıyla ancak son satırında deyim ayrılır.  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     Bu sırayı kullanarak kodunuzu okumak hem çevrimiçi hem de zaman yazdırılan kolaylaştırır.  
  
     Satır devamlılığı karakteri son karakter bir satırda olmalıdır. Bunu başka bir şey ile aynı satırda izlenemiyor.  
  
     Satır devamlılığı karakteri burada kullanabilirsiniz ilişkin bazı sınırlamalar var; Örneğin, ortasında bir bağımsız değişken adı olarak kullanamazsınız. Satır devamlılığı karakteri ile bir bağımsız değişken listesi bozulabilir, ancak bağımsız değişkenler tek tek adlarını değişmeden kalmalıdır.  
  
     Satır devamlılığı karakteri kullanarak bir yorum devam edemiyor. Derleyici özel bir anlamı için bir açıklama karakterleri inceleyin değil. Birden çok satırlı açıklaması için Yorum simgesinin yineleyin (`'`) her satırda.  
  
 Ayrı bir satırda her deyimi yerleştirme önerilen yöntem olsa da, Visual Basic aynı çizgi üzerinde birden çok deyime yerleştirmek sağlar.  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a>Aynı çizgi üzerinde birden çok deyime yerleştirmek için  
  
-   İki nokta üst üste ile deyimleri ayırın (`:`), aşağıdaki örnekte olduğu gibi.  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
