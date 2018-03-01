---
title: "&#39; Özel &#39; değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 844bd033ea05e373b04a04f80777af77179c1263
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>&#39; Özel &#39; değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil
Özel olmayan olay aksine bir `Custom Event` bildirimi gerektiren bir `As` açıkça olayı için temsilci türünü belirten bir olay adından yan tümcesi.  
  
 Olmayan özel olayları olabilir ile tanımlanmış bir `As` yan tümcesi ve açık bir temsilci türü ya da bir parametre listesi hemen olay adından.  
  
 **Hata Kimliği:** BC31122  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Bir temsilci ile aynı parametre listesine özel olayı olarak tanımlayın.  
  
     Örneğin, varsa `Custom Event` tarafından tanımlanan `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, karşılık gelen temsilci şu şekilde olacaktır.  
  
     [!code-vb[VbVbalrEventError#18](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_1.vb)]  
  
2.  Özel olay ile parametre listesi yerine bir `As` temsilci türünü belirtme yan tümcesi.  
  
     Bu örnekle devam edersek `Custom Event` bildirimi yeniden yazılmıştır gibi.  
  
     [!code-vb[VbVbalrEventError#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_2.vb)]  
  
## <a name="example"></a>Örnek  
 Bu örnek bildiren bir `Custom Event` ve gerekli belirtir `As` bir temsilci türüyle yan tümcesi.  
  
 [!code-vb[VbVbalrEventError#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Olayları](../../../visual-basic/programming-guide/language-features/events/index.md)
