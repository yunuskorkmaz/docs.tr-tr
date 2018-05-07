---
title: '&#39;Özel&#39; değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil'
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 3f08bbbbbac4a01dfbac8d15cf9285c01262618a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="39custom39-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>&#39;Özel&#39; değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil
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
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
