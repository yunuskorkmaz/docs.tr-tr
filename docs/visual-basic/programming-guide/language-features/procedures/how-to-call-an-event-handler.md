---
title: 'Nasıl yapılır: Visual Basic bir olay Işleyicisini çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: a9e090e83b180686ccb832aa6efb314c7e0fcc9a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216621"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Nasıl yapılır: Visual Basic bir olay Işleyicisini çağırma

Bir *olay* , bir program bileşeni tarafından tanınan ve yanıt vermek için kod yazabileceğiniz bir fare tıklaması veya kredi limiti gibi bir eylem veya oluşumdır. *Olay işleyicisi* , bir olaya yanıt vermek için yazdığınız koddur.

 Visual Basic bir olay işleyicisi bir `Sub` yordamdır. Ancak, normalde bunu diğer `Sub` yordamlarla aynı şekilde çağırmayın. Bunun yerine, yordamı olay için bir işleyici olarak belirlersiniz. Bunu bir [Handles](../../../language-reference/statements/handles-clause.md) yan tümcesi ve [WithEvents](../../../language-reference/modifiers/withevents.md) değişkeniyle ya da bir [AddHandler ifadesiyle](../../../language-reference/statements/addhandler-statement.md)yapabilirsiniz. `Handles` Yan tümcesinin kullanılması, Visual Basic bir olay işleyicisini bildirmek için varsayılan yoldur. Bu, tümleşik geliştirme ortamında (IDE) programlama yaparken, tasarımcı tarafından yazılan olay işleyicilerinin yoludur. İfade `AddHandler` , olayları çalışma zamanında dinamik olarak yükseltmek için uygundur.

 Olay gerçekleştiğinde, Visual Basic olay işleyicisi yordamını otomatik olarak çağırır. Olaya erişimi olan herhangi bir kod, bir [RaiseEvent ifadesiyle](../../../language-reference/statements/raiseevent-statement.md)yürütülerek oluşmasına neden olabilir.

 Birden fazla olay işleyicisini aynı olayla ilişkilendirebilirsiniz. Bazı durumlarda, bir etkinliğin bir olaydan ilişkisini kaldırabilirsiniz. Daha fazla bilgi için bkz. [Olaylar](../events/index.md).

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>Handles ve WithEvents kullanarak bir olay işleyicisini çağırmak için

1. Olayın bir [Event ifadesiyle](../../../language-reference/statements/event-statement.md)bildiriminin bulunduğundan emin olun.

2. [WithEvents](../../../language-reference/modifiers/withevents.md) anahtar sözcüğünü kullanarak modül veya sınıf düzeyinde bir nesne değişkeni bildirin. Bu `As` değişkenin yan tümcesi, olayı oluşturan sınıfı belirtmelidir.

3. Olay işleme `Sub` yordamının bildiriminde, `WithEvents` değişkeni ve olay adını belirten bir [Handles](../../../language-reference/statements/handles-clause.md) yan tümcesi ekleyin.

4. Olay gerçekleştiğinde, Visual Basic `Sub` yordamı otomatik olarak çağırır. Kodunuz olay oluşmasını sağlamak için `RaiseEvent` bir ifade kullanabilir.

     Aşağıdaki örnek, olayını oluşturan sınıfa başvuran bir `WithEvents` olayı ve değişkeni tanımlar. Olay işleme `Sub` yordamı, işleyen sınıfı ve `Handles` olayı belirtmek için bir yan tümce kullanır.

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a>AddHandler kullanarak bir olay işleyicisini çağırmak için

1. Olayın bir `Event` ifadesiyle bildirildiği emin olun.

2. Olay işleme `Sub` yordamını olaya dinamik olarak bağlamak için bir [AddHandler ekstresi](../../../language-reference/statements/addhandler-statement.md) yürütün.

3. Olay gerçekleştiğinde, Visual Basic `Sub` yordamı otomatik olarak çağırır. Kodunuz olay oluşmasını sağlamak için `RaiseEvent` bir ifade kullanabilir.

     Aşağıdaki örnek, bir formun `Sub` <xref:System.Windows.Forms.Form.Closing> olayını işlemek için bir yordam tanımlar. Daha sonra, `catchClose` yordamını <xref:System.Windows.Forms.Form.Closing>bir olay işleyicisi olarak ilişkilendirmek için [AddHandler ifadesini](../../../language-reference/statements/addhandler-statement.md) kullanır.

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     [RemoveHandler ifadesini](../../../language-reference/statements/removehandler-statement.md)yürüterek bir olay işleyicisinin bir olaydan ilişkisini kaldırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](index.md)
- [Alt Yordamlar](sub-procedures.md)
- [Sub Deyimi](../../../language-reference/statements/sub-statement.md)
- [AddressOf İşleci](../../../language-reference/operators/addressof-operator.md)
- [Nasıl yapılır: Yordam oluşturma](how-to-create-a-procedure.md)
- [Nasıl yapılır: Değer döndürmeyen bir yordam çağırma](how-to-call-a-procedure-that-does-not-return-a-value.md)
