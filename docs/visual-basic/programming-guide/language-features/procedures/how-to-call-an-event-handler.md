---
title: 'Nasıl yapılır: Visual Basic olay işleyicisi çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 6fc08e9f16753dc853daff0120661603571d9db4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717980"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Nasıl yapılır: Visual Basic olay işleyicisi çağırma
Bir *olay* bir eylem veya oluşum — gibi bir fare tıklatın veya kredi sınırına aşıldı —, tanınır bazı programı bileşeni için kod yazabilirsiniz ve yanıtlayın. Bir *olay işleyicisi* bir olaya yanıt vermek için yazdığınız kodu.  
  
 Visual Basic'te bir olay işleyicisi bir `Sub` yordamı. Ancak, genellikle bunu aynı şekilde diğer çağırmayın `Sub` yordamları. Bunun yerine, olay işleyicisi olarak yordamı tanımlayın. İle yapabilecekleriniz bir [işleme](../../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi ve [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) değişkeni veya bir [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Kullanarak bir `Handles` yan tümcesi ise bir olay işleyicisi Visual Basic'te bildirmek için varsayılan yolu. Bu, tümleşik geliştirme ortamında (IDE) programı, olay işleyicileri dosyanın tasarımcılar tarafından yazılan yoludur. `AddHandler` Deyimi olayları dinamik olarak çalışma zamanında düzeyine yükseltmek için uygundur.  
  
 Olay ortaya çıktığında, Visual Basic olay işleyicisi yordamı otomatik olarak çağırır. Olay erişimi olan herhangi bir kodu bu yürüterek oluşmasına neden olabilir bir [RaiseEvent deyimi](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).  
  
 Birden fazla olay işleyicisi aynı olay ile ilişkilendirebilirsiniz. Bazı durumlarda bir olay işleyicisinden ilişkisini kaldırın. Daha fazla bilgi için [olayları](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>WithEvents ve işler kullanarak bir olay işleyicisi çağırmak için  
  
1.  Emin olay ile bildirilmiş bir [Event deyimi](../../../../visual-basic/language-reference/statements/event-statement.md).  
  
2.  Düzeyi kullanarak modül veya sınıfının bir nesne değişkeni bildirme [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) anahtar sözcüğü. `As` Yan tümcesi için bu değişkeni, olayı yükselten sınıf belirtmeniz gerekir.  
  
3.  Olay işleme bildiriminde `Sub` yordam, ekleme bir [işleme](../../../../visual-basic/language-reference/statements/handles-clause.md) belirten yan tümcesi `WithEvents` değişkeni ve olay adı.  
  
4.  Olay ortaya çıktığında, Visual Basic otomatik olarak çağıran `Sub` yordamı. Kodunuzu kullanabilirsiniz bir `RaiseEvent` ortaya olayın deyimi.  
  
     Aşağıdaki örnek, bir olayı tanımlar ve `WithEvents` olayı yükselten sınıf başvuran değişkeni. Olay işleme `Sub` yordamı kullanan bir `Handles` yan sınıfı ve bunu işleyen olayı belirtin.  
  
     [!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>AddHandler kullanarak bir olay işleyicisi çağırmak için  
  
1.  Emin olay ile bildirilmiş bir `Event` deyimi.  
  
2.  Yürütme bir [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) olay işleme dinamik olarak bağlanmak için `Sub` olaylı yordamı.  
  
3.  Olay ortaya çıktığında, Visual Basic otomatik olarak çağıran `Sub` yordamı. Kodunuzu kullanabilirsiniz bir `RaiseEvent` ortaya olayın deyimi.  
  
     Aşağıdaki örnekte tanımlayan bir `Sub` işlemek için yordamı <xref:System.Windows.Forms.Form.Closing> formun olay. Ardından kullanır [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ilişkilendirilecek `catchClose` yordamı için bir olay işleyicisi olarak <xref:System.Windows.Forms.Form.Closing>.  
  
     [!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     Yürüterek bir olaydan bir olay işleyicisi ilişkilendirmesi [RemoveHandler deyimi](../../../../visual-basic/language-reference/statements/removehandler-statement.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Yordamlar](./index.md)
- [Alt Yordamlar](./sub-procedures.md)
- [Sub Deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [AddressOf İşleci](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Nasıl yapılır: Bir yordam oluşturma](./how-to-create-a-procedure.md)
- [Nasıl yapılır: Bir değer döndürmeyen bir yordam çağırma](./how-to-call-a-procedure-that-does-not-return-a-value.md)
