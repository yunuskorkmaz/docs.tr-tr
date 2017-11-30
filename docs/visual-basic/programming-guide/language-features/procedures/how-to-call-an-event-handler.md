---
title: "Nasıl yapılır: Olay İşleyicisi Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 52b4b6ca8b03d8301535d6aeedc3bd0190d8527f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>Nasıl yapılır: Olay İşleyicisi Çağırma (Visual Basic)
Bir *olay* bir eylem veya geçişi — fare gibi tıklatın ya da bir kredi sınırı aşıldı —, tanınmasını bazı programı bileşeni tarafından ve kod yazabilirsiniz yanıtlayın. Bir *olay işleyicisi* bir olaya yanıt yazma kodudur.  
  
 Bir olay işleyicisi [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] olan bir `Sub` yordamı. Ancak, normal olarak, aynı yolla diğer çağırmayın `Sub` yordamlar. Bunun yerine, olay işleyicisi olarak yordamı tanımlayın. İle ya da bunu yapabilirsiniz bir [işleme](../../../../visual-basic/language-reference/statements/handles-clause.md) yan tümcesi ve [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) , değişken veya ile bir [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md). Kullanarak bir `Handles` yan tümcesi olan bir olay işleyici bildirmek için varsayılan yolu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Tümleşik geliştirme ortamı (IDE) programı olduğunda olay işleyicileri tasarımcıları tarafından yazılan yolu budur. `AddHandler` Açıklamadır olaylar dinamik olarak çalışma zamanında oluşturma için uygun.  
  
 Olay ortaya çıktığında [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] otomatik olarak olay işleyicisi yordamı çağırır. Olay erişimi olan herhangi bir kod yürüterek oluşmasına neden bir [RaiseEvent deyimi](../../../../visual-basic/language-reference/statements/raiseevent-statement.md).  
  
 Birden fazla olay işleyicisi aynı olay ile ilişkilendirebilirsiniz. Bazı durumlarda bir olay işleyiciden ilişkisini kaldırın. Daha fazla bilgi için bkz: [olayları](../../../../visual-basic/programming-guide/language-features/events/index.md).  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>İşler ve WithEvents kullanarak bir olay işleyicisi çağırmak için  
  
1.  Emin olun olay ile bildirilmiş bir [Event deyimi](../../../../visual-basic/language-reference/statements/event-statement.md).  
  
2.  Bir nesne değişkeni modülü veya sınıfı kullanarak düzeyi bildirme [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md) anahtar sözcüğü. `As` Yan tümcesi bu değişken için olayını sınıfı belirtmeniz gerekir.  
  
3.  Olay işleme bildiriminde `Sub` yordamı, ekleme bir [işleme](../../../../visual-basic/language-reference/statements/handles-clause.md) belirten yan tümcesi `WithEvents` değişkeni ve olay adı.  
  
4.  Olay ortaya çıktığında [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] otomatik olarak çağırır `Sub` yordamı. Kodunuzu kullanabilirsiniz bir `RaiseEvent` ortaya olay yapmak için deyimi.  
  
     Aşağıdaki örnek, bir olay tanımlar ve `WithEvents` olayını sınıfına başvuruyor değişkeni. Olay işleme `Sub` yordamı kullanan bir `Handles` yan tümcesini sınıfı ve bunu işleyen olayı belirtin.  
  
     [!code-vb[VbVbcnProcedures#4](./codesnippet/VisualBasic/how-to-call-an-event-handler_1.vb)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>AddHandler kullanarak bir olay işleyicisi çağırmak için  
  
1.  Emin olun olay ile bildirilmiş bir `Event` deyimi.  
  
2.  Yürütme bir [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) olay işleme dinamik olarak bağlanmak için `Sub` olay yordamı.  
  
3.  Olay ortaya çıktığında [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] otomatik olarak çağırır `Sub` yordamı. Kodunuzu kullanabilirsiniz bir `RaiseEvent` ortaya olay yapmak için deyimi.  
  
     Aşağıdaki örnek tanımlayan bir `Sub` işlemek için yordamına <xref:System.Windows.Forms.Form.Closing> olay bir biçimde. Daha sonra kullanır [AddHandler deyimi](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ilişkilendirilecek `catchClose` yordamı için bir olay işleyicisi olarak <xref:System.Windows.Forms.Form.Closing>.  
  
     [!code-vb[VbVbcnProcedures#5](./codesnippet/VisualBasic/how-to-call-an-event-handler_2.vb)]  
  
     Bir olay Olay işleyiciden yürüterek ilişkisini [RemoveHandler deyimi](../../../../visual-basic/language-reference/statements/removehandler-statement.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yordamları](./index.md)  
 [Alt yordamlar](./sub-procedures.md)  
 [Sub deyimi](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [AddressOf işleci](../../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Nasıl yapılır: bir yordam oluşturma](./how-to-create-a-procedure.md)  
 [Nasıl yapılır: bir değer döndürmeyen bir yordam çağırma](./how-to-call-a-procedure-that-does-not-return-a-value.md)
