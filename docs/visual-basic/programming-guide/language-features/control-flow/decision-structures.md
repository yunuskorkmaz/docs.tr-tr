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
ms.openlocfilehash: aac9844240defc5a21a3f4e6090fa8f49e6348a1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403529"
---
# <a name="decision-structures-visual-basic"></a>Karar Yapıları (Visual Basic)
Visual Basic, test koşullarını test etmenizi ve bu testin sonuçlarına bağlı olarak farklı işlemler gerçekleştirmenizi sağlar. Bir koşulu doğru veya yanlış olarak, bir ifadenin çeşitli değerleri için ya da bir dizi deyim yürüttüğünüzde oluşturulan çeşitli özel durumlar için test edebilirsiniz.  
  
 Aşağıdaki çizimde, bir koşulu test eden ve doğru ya da yanlış olmasına bağlı olarak farklı eylemler alan bir karar yapısı gösterilmektedir.  
  
 ![If... öğesinin akış grafiği Sonra... Başka oluşturma.](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If... Sonra... Başka oluşturma  
 `If...Then...Else`kurulumlarını bir veya daha fazla koşulu test etmenize ve her koşula bağlı olarak bir veya daha fazla deyim çalıştırmanıza izin verir. Koşulları test edebilir ve aşağıdaki yollarla işlem yapabilirsiniz:  
  
- Bir koşul varsa bir veya daha fazla deyimi çalıştırma`True`  
  
- Bir koşul varsa bir veya daha fazla deyimi çalıştırma`False`  
  
- Bir koşul varsa `True` ve diğer durumlarda bazı deyimleri Çalıştır`False`  
  
- Önceki bir koşul varsa, daha fazla durum test edin`False`  
  
 Tüm bu olasılıkları sunan denetim yapısı If.. [. Sonra... Else bildirisi](../../../language-reference/statements/if-then-else-statement.md). Yalnızca bir testiniz ve çalıştırmak için bir deyiminiz varsa, tek satırlık bir sürüm kullanabilirsiniz. Daha karmaşık koşullar ve eylemler kümesine sahipseniz, çok satırlı sürümü kullanabilirsiniz.  
  
## <a name="selectcase-construction"></a>Seç... Örnek oluşturma  
 `Select...Case`Oluşturma, bir ifadeyi bir kez değerlendirmenizi ve farklı olası değerlere göre farklı deyim kümelerini çalıştırmanızı sağlar. Daha fazla bilgi için bkz [. Select... Case bildirisi](../../../language-reference/statements/select-case-statement.md).  
  
## <a name="trycatchfinally-construction"></a>Deneyin... Yakala... Son yapım  
 `Try...Catch...Finally`kurulumlarını, deyimlerinizin herhangi biri özel duruma neden olursa denetimi koruyan bir ortam altında deyim kümesi çalıştırmanızı sağlar. Farklı özel durumlar için farklı eylemler gerçekleştirebilirsiniz. Ne olursa olsun, tüm oluşturma işleminden çıkmadan önce çalışan bir kod bloğu belirtebilirsiniz `Try...Catch...Finally` . Daha fazla bilgi için bkz [. TRY... Yakala... Finally ekstresi](../../../language-reference/statements/try-catch-finally-statement.md).  
  
> [!NOTE]
> Birçok denetim yapısında, bir anahtar sözcüğe tıkladığınızda yapıdaki tüm anahtar sözcükler vurgulanır. Örneğin, bir yapıya tıkladığınızda,,,, `If` `If...Then...Else` `If` `Then` `ElseIf` `Else` ve `End If` oluşturma içindeki tüm örnekleri vurgulanır. Sonraki veya önceki vurgulanmış anahtar sözcüğe geçmek için CTRL + SHIFT + aşağı ok veya CTRL + SHIFT + yukarı ok tuşlarına basın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Denetim akışı](index.md)
- [Döngü Yapıları](loop-structures.md)
- [Diğer Denetim Yapıları](other-control-structures.md)
- [İç İçe Geçmiş Denetim Yapıları](nested-control-structures.md)
- [If İşleci](../../../language-reference/operators/if-operator.md)
