---
title: Karar Yapıları
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: d0d4039ff2edc61ee8b4b732c6adcb6e420d73ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353971"
---
# <a name="decision-structures-visual-basic"></a>Karar Yapıları (Visual Basic)
Visual Basic, test koşullarını test etmenizi ve bu testin sonuçlarına bağlı olarak farklı işlemler gerçekleştirmenizi sağlar. Bir koşulu doğru veya yanlış olarak, bir ifadenin çeşitli değerleri için ya da bir dizi deyim yürüttüğünüzde oluşturulan çeşitli özel durumlar için test edebilirsiniz.  
  
 Aşağıdaki çizimde, bir koşulu test eden ve doğru ya da yanlış olmasına bağlı olarak farklı eylemler alan bir karar yapısı gösterilmektedir.  
  
 ![Öğesinin akış grafiği If...Then...Else oluşturma.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If...Then...Else oluşturma  
 `If...Then...Else` kurulumlarını, bir veya daha fazla koşulu test etmenize ve her koşula bağlı olarak bir veya daha fazla deyim çalıştırmanıza izin verir. Koşulları test edebilir ve aşağıdaki yollarla işlem yapabilirsiniz:  
  
- Bir koşul `True` bir veya daha fazla deyim Çalıştır  
  
- Bir koşul `False` bir veya daha fazla deyim Çalıştır  
  
- Bir koşul `True`, diğerleri ise bazı deyimlerini çalıştırın `False`  
  
- Önceki bir koşul `False`, ek bir koşulu test edin  
  
 Tüm bu olasılıkları sunan denetim yapısı If.. [. Sonra... Else bildirisi](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Yalnızca bir testiniz ve çalıştırmak için bir deyiminiz varsa, tek satırlık bir sürüm kullanabilirsiniz. Daha karmaşık koşullar ve eylemler kümesine sahipseniz, çok satırlı sürümü kullanabilirsiniz.  
  
## <a name="selectcase-construction"></a>Select...Case oluşturma  
 `Select...Case` oluşturma, bir ifadeyi bir kez değerlendirmenizi ve farklı olası değerlere göre farklı deyim kümelerini çalıştırmanızı sağlar. Daha fazla bilgi için bkz [. Select... Case bildirisi](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try...Catch...Finally yapım  
 `Try...Catch...Finally` kurulumlarını, deyimlerinizin herhangi biri özel duruma neden olursa denetimi koruyan bir ortam altında deyim kümesi çalıştırmanızı sağlar. Farklı özel durumlar için farklı eylemler gerçekleştirebilirsiniz. Ne olursa olsun, tüm `Try...Catch...Finally` oluşturma işleminden çıkmadan önce çalışan bir kod bloğu belirtebilirsiniz. Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
> Birçok denetim yapısında, bir anahtar sözcüğe tıkladığınızda yapıdaki tüm anahtar sözcükler vurgulanır. Örneğin, `If...Then...Else` bir yapıta `If` tıklattığınızda, oluşturulmakta olan tüm `If`, `Then`, `ElseIf`, `Else`ve `End If` örnekleri vurgulanır. Sonraki veya önceki vurgulanmış anahtar sözcüğe geçmek için CTRL + SHIFT + aşağı ok veya CTRL + SHIFT + yukarı ok tuşlarına basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Diğer Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [If İşleci](../../../../visual-basic/language-reference/operators/if-operator.md)
