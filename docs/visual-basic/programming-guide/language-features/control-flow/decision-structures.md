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
ms.openlocfilehash: f0df649c4be50e9cadd51258c89137b68b4ffe22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963193"
---
# <a name="decision-structures-visual-basic"></a>Karar Yapıları (Visual Basic)
Visual Basic, test koşullarını test etmenizi ve bu testin sonuçlarına bağlı olarak farklı işlemler gerçekleştirmenizi sağlar. Bir koşulu doğru veya yanlış olarak, bir ifadenin çeşitli değerleri için ya da bir dizi deyim yürüttüğünüzde oluşturulan çeşitli özel durumlar için test edebilirsiniz.  
  
 Aşağıdaki çizimde, bir koşulu test eden ve doğru ya da yanlış olmasına bağlı olarak farklı eylemler alan bir karar yapısı gösterilmektedir.  
  
 ![Öğesinin akış grafiği If...Then...Else oluşturma.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If...Then...Else oluşturma  
 `If...Then...Else`kurulumlarını bir veya daha fazla koşulu test etmenize ve her koşula bağlı olarak bir veya daha fazla deyim çalıştırmanıza izin verir. Koşulları test edebilir ve aşağıdaki yollarla işlem yapabilirsiniz:  
  
- Bir koşul varsa bir veya daha fazla deyimi çalıştırma`True`  
  
- Bir koşul varsa bir veya daha fazla deyimi çalıştırma`False`  
  
- Bir koşul `True` varsa ve diğer durumlarda bazı deyimleri Çalıştır`False`  
  
- Önceki bir koşul varsa, daha fazla durum test edin`False`  
  
 Tüm bu olasılıkları sunan denetim yapısı [If...Then...Else bildirisi](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Yalnızca bir testiniz ve çalıştırmak için bir deyiminiz varsa, tek satırlık bir sürüm kullanabilirsiniz. Daha karmaşık koşullar ve eylemler kümesine sahipseniz, çok satırlı sürümü kullanabilirsiniz.  
  
## <a name="selectcase-construction"></a>Select...Case oluşturma  
 Oluşturma `Select...Case` , bir ifadeyi bir kez değerlendirmenizi ve farklı olası değerlere göre farklı deyim kümelerini çalıştırmanızı sağlar. Daha fazla bilgi için bkz [Select...Case bildirisi](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try...Catch...Finally yapım  
 `Try...Catch...Finally`kurulumlarını, deyimlerinizin herhangi biri özel duruma neden olursa denetimi koruyan bir ortam altında deyim kümesi çalıştırmanızı sağlar. Farklı özel durumlar için farklı eylemler gerçekleştirebilirsiniz. Ne olursa olsun, tüm `Try...Catch...Finally` oluşturma işleminden çıkmadan önce çalışan bir kod bloğu belirtebilirsiniz. Daha fazla bilgi için bkz [Try...Catch...Finally ekstresi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
> Birçok denetim yapısında, bir anahtar sözcüğe tıkladığınızda yapıdaki tüm anahtar sözcükler vurgulanır. `If` Örneğin, bir `ElseIf` `Then` `Else` yapıyatıkladığınızda`End If` ,,,, ve oluşturma içindeki tüm örnekleri vurgulanır.`If` `If...Then...Else` Sonraki veya önceki vurgulanmış anahtar sözcüğe geçmek için CTRL + SHIFT + aşağı ok veya CTRL + SHIFT + yukarı ok tuşlarına basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Diğer Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [İç İçe Geçmiş Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [If İşleci](../../../../visual-basic/language-reference/operators/if-operator.md)
