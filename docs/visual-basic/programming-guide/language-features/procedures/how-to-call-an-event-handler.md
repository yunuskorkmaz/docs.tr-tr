---
title: Olay işleyicisini çağırma
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
no-loc:
- WithEvents
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 3762c79dd3d883ae2ccfe76b335cf98ac87d4246
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89464967"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Visual Basic bir olay işleyicisini çağırma

Bir *olay* , bir program bileşeni tarafından tanınan ve yanıt vermek için kod yazabileceğiniz bir fare tıklaması veya kredi limiti gibi bir eylem veya oluşumdır. *Olay işleyicisi* , bir olaya yanıt vermek için yazdığınız koddur.

Visual Basic bir olay işleyicisi bir `Sub` yordamdır. Ancak, normalde bunu diğer yordamlarla aynı şekilde çağırmayın `Sub` . Bunun yerine, yordamı olay için bir işleyici olarak belirlersiniz. Bunu bir [`Handles`](../../../language-reference/statements/handles-clause.md) yan tümce ve bir değişkenle ya da bir [`WithEvents`](../../../language-reference/modifiers/withevents.md) [AddHandler ifadesiyle](../../../language-reference/statements/addhandler-statement.md)yapabilirsiniz. `Handles`Yan tümcesinin kullanılması, Visual Basic bir olay işleyicisini bildirmek için varsayılan yoldur. Bu, tümleşik geliştirme ortamında (IDE) programlama yaparken, tasarımcı tarafından yazılan olay işleyicilerinin yoludur. `AddHandler`İfade, olayları çalışma zamanında dinamik olarak yükseltmek için uygundur.

Olay gerçekleştiğinde, Visual Basic olay işleyicisi yordamını otomatik olarak çağırır. Olaya erişimi olan herhangi bir kod, bir [RaiseEvent ifadesiyle](../../../language-reference/statements/raiseevent-statement.md)yürütülerek oluşmasına neden olabilir.

Birden fazla olay işleyicisini aynı olayla ilişkilendirebilirsiniz. Bazı durumlarda, bir etkinliğin bir olaydan ilişkisini kaldırabilirsiniz. Daha fazla bilgi için bkz. [Olaylar](../events/index.md).

## <a name="call-an-event-handler-using-no-loc-texthandles-and-no-locwithevents"></a>Ve kullanarak bir olay işleyicisi çağırma :::no-loc text="Handles":::WithEvents

1. Olayın bir [Event ifadesiyle](../../../language-reference/statements/event-statement.md)bildiriminin bulunduğundan emin olun.

2. Anahtar sözcüğünü kullanarak modül veya sınıf düzeyinde bir nesne değişkeni bildirin [`WithEvents`](../../../language-reference/modifiers/withevents.md) . `As`Bu değişkenin yan tümcesi, olayı oluşturan sınıfı belirtmelidir.

3. Olay işleme `Sub` yordamının bildiriminde, [`Handles`](../../../language-reference/statements/handles-clause.md) `WithEvents` değişkeni ve olay adını belirten bir yan tümce ekleyin.

4. Olay gerçekleştiğinde, Visual Basic yordamı otomatik olarak çağırır `Sub` . Kodunuz `RaiseEvent` olay oluşmasını sağlamak için bir ifade kullanabilir.

    Aşağıdaki örnek, olayını oluşturan sınıfa başvuran bir olayı ve `WithEvents` değişkeni tanımlar. Olay işleme yordamı, `Sub` `Handles` işleyen sınıfı ve olayı belirtmek için bir yan tümce kullanır.

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="4":::

## <a name="call-an-event-handler-using-addhandler"></a>AddHandler kullanarak olay işleyicisini çağırma

1. Olayın bir ifadesiyle bildirildiği emin olun `Event` .

2. Olay işleme yordamını olaya dinamik olarak bağlamak için bir [AddHandler ekstresi](../../../language-reference/statements/addhandler-statement.md) yürütün `Sub` .

3. Olay gerçekleştiğinde, Visual Basic yordamı otomatik olarak çağırır `Sub` . Kodunuz `RaiseEvent` olay oluşmasını sağlamak için bir ifade kullanabilir.

    Aşağıdaki örnek, yordamını bir olay işleyicisi olarak ilişkilendirmek için oluşturucuda [AddHandler ifadesini](../../../language-reference/statements/addhandler-statement.md) kullanır `OnFormClosing` <xref:System.Windows.Forms.Form.FormClosing> .

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="5":::

    [RemoveHandler ifadesini](../../../language-reference/statements/removehandler-statement.md)yürüterek bir olay işleyicisinin bir olaydan ilişkisini kaldırabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yordamlar](index.md)
- [Alt Yordamlar](sub-procedures.md)
- [Sub Deyimi](../../../language-reference/statements/sub-statement.md)
- [AddressOf İşleci](../../../language-reference/operators/addressof-operator.md)
- [Nasıl yapılır: Yordam Oluşturma](how-to-create-a-procedure.md)
- [Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma](how-to-call-a-procedure-that-does-not-return-a-value.md)
