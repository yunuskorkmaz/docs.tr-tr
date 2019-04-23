---
title: Karar Yapıları (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 4a76b2565c343e69ac3c11441035a7682a8f08ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318942"
---
# <a name="decision-structures-visual-basic"></a>Karar Yapıları (Visual Basic)
Visual Basic koşulları test etmeye ve test sonuçlarına bağlı olarak farklı işlemler gerçekleştirmek olanak sağlar. True veya false, bir ifadenin çeşitli değerleri için veya bir deyimler serisini çalıştırdığınızda oluşturulan çeşitli özel durumlar için olan bir koşul için test edebilirsiniz.  
  
 Aşağıdaki çizim true olan bir koşulu sınar ve doğru veya yanlış olmasına bağlı olarak farklı eylemler geçen bir karar yapısını gösterir.  
  
 ![Eğer bir akış çizelgesi... Daha sonra... Başka oluşturma.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If... Daha sonra... Başka bir yapı  
 `If...Then...Else` yapılarını için bir veya daha fazla koşulları test etmeye ve bir veya daha fazla deyim her koşula bağlı çalıştırmanıza olanak tanır. Koşulları test etmeye ve eylemleri aşağıdaki yollarla kullanabilirsiniz:  
  
-   Bir koşul ise, bir veya daha fazla deyimleri çalıştırın `True`  
  
-   Bir koşul ise, bir veya daha fazla deyimleri çalıştırın `False`  
  
-   Bir koşul ise, bazı deyimleri çalıştırın `True` ve diğerleri ise `False`  
  
-   Önceki koşul ise, ek bir koşul testi `False`  
  
 Tüm bu olanaklar sunan denetim yapısı [varsa... Daha sonra... Else deyimi](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Sadece bir test ve çalıştırmak için bir ifade varsa, tek satır sürümü kullanabilirsiniz. Koşullar ve Eylemler daha karmaşık bir dizi varsa, birden çok satır sürümü kullanabilirsiniz.  
  
## <a name="selectcase-construction"></a>Seçin... Servis talebi oluşturma  
 `Select...Case` Yapım bir ifade bir kez ve farklı farklı olası değerlere dayalı ifadeler kümesi çalıştırmanıza olanak tanır. Daha fazla bilgi için [seçin... Case deyimi](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Deneyin... Catch... Son olarak oluşturma  
 `Try...Catch...Finally` yapılarını deyimler, deyim herhangi bir özel durum neden olursa denetimi elinde bir ortamda altında kümesi çalıştırmanıza olanak tanır. Farklı özel durumlar için farklı eylemleri gerçekleştirebilirsiniz. İsteğe bağlı olarak tüm çıkmadan önce çalışan bir kod bloğunu belirtebilirsiniz `Try...Catch...Finally` ne olacağını bağımsız olarak oluşturma,. Daha fazla bilgi için [deneyin... Catch... Finally deyimini](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Bir anahtar sözcük tıkladığınızda birçok denetim yapıları için anahtar sözcükleri yapısındaki tüm vurgulanır. Örneği için tıkladığınızda `If` içinde bir `If...Then...Else` oluşturma, tüm örneklerini `If`, `Then`, `ElseIf`, `Else`, ve `End If` yapısında vurgulanır. Sonraki veya önceki vurgulanan anahtar taşımak için CTRL + SHIFT + Aşağı Ok veya CTRL + SHIFT + Yukarı Ok tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Diğer Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [If İşleci](../../../../visual-basic/language-reference/operators/if-operator.md)
