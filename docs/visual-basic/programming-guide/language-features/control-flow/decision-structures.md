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
ms.openlocfilehash: 1ede40d196b470a351aca4c60b33f074df14b86a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648203"
---
# <a name="decision-structures-visual-basic"></a>Karar Yapıları (Visual Basic)
Visual Basic koşullarda test ve test sonuçlarını bağlı olarak farklı işlemler gerçekleştirmek olanak sağlar. True veya false ifade çeşitli değerleri için veya bir dizi deyimi yürüttüğünüzde oluşturulan çeşitli özel durumlar için olan bir koşul için test edebilirsiniz.  
  
 Aşağıdaki çizimde, true olan bir koşulu sınar ve doğru veya yanlış olmasına bağlı olarak farklı eylemleri gerçekleştirir karar yapısını gösterir.  
  
 ![Akış Çizelgesi bir if... Then... Else yapım](../../../../visual-basic/programming-guide/language-features/control-flow/media/ifthenelse.gif "IfThenElse")  
Bir koşul true ve false olduğunda olduğunda farklı eylemler alma  
  
## <a name="ifthenelse-construction"></a>If... Then... Else yapımı  
 `If...Then...Else` kurulumlarını için bir veya daha fazla koşullarda test ve her koşul bağlı olarak bir veya daha fazla deyimleri çalıştırmanıza olanak sağlar. Koşullarda test ve aşağıdaki yollarla eylemleri gerçekleştirin:  
  
-   Bir koşul ise, bir veya daha fazla deyimlerini çalıştırın `True`  
  
-   Bir koşul ise, bir veya daha fazla deyimlerini çalıştırın `False`  
  
-   Bir koşul ise, bazı deyimleri çalıştırmak `True` ve diğerleri etkinleştirilmişse `False`  
  
-   Önceki bir koşul ise, ek bir koşulu test `False`  
  
 Bu olanakları sunar denetim yapısı [varsa... Then... Else deyimi](../../../../visual-basic/language-reference/statements/if-then-else-statement.md). Yalnızca bir test ve çalıştırmak için bir deyim varsa tek satırlı sürüm kullanabilirsiniz. Koşullar ve Eylemler daha karmaşık bir dizi varsa, birden çok satır sürümü kullanabilirsiniz.  
  
## <a name="selectcase-construction"></a>Seçin... Örnek oluşturma  
 `Select...Case` Yapım bir ifadenin bir kez değerlendirmek ve çalışma farklı olası değerlerine göre deyimlerinin farklı ayarlar sağlar. Daha fazla bilgi için bkz: [seçin... Case deyimi](../../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Try... Catch... Son olarak oluşturma  
 `Try...Catch...Finally` kurulumlarını deyimleri altında bir özel durum, deyimleri herhangi biri neden olursa, Denetim korur bir ortam kümesi çalıştırmanıza izin. Farklı özel durumlar için farklı işlemler yapabilirsiniz. İsteğe bağlı olarak tüm çıkmadan önce çalışan bir kod bloğunu belirtebilirsiniz `Try...Catch...Finally` neler bağımsız olarak oluşturma. Daha fazla bilgi için bkz: [deneyin... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
>  Bir anahtar sözcüğü tıklattığınızda birçok denetim yapıları için tüm anahtar sözcükleri yapısında vurgulanır. Örneği için tıkladığınızda `If` içinde bir `If...Then...Else` yapım, tüm örneklerini `If`, `Then`, `ElseIf`, `Else`, ve `End If` yapısında vurgulanır. Sonraki veya önceki vurgulanan anahtar sözcüğe taşımak için CTRL + SHIFT + Aşağı Ok veya CTRL + SHIFT + Yukarı Ok tuşuna basın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Denetim Akışı](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [Döngü Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [Diğer Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [İç İçe Geçmiş Denetim Yapıları](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [If İşleci](../../../../visual-basic/language-reference/operators/if-operator.md)
