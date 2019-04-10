---
title: "'Custom' değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil"
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 169cb49cc5abc76b7c52785392d0083b81a99450
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59300950"
---
# <a name="custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>'Custom' değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil
Bir özel dışı olay aksine bir `Custom Event` bildirimi gerektirir bir `As` olayı için temsilci türünü açıkça belirten bir olay adından yan tümcesi.  
  
 Özel olmayan olaylar olabilir ile tanımlanmış bir `As` yan tümcesi ve açık bir temsilci türü veya bir parametre listesinde hemen aşağıdaki olay adı.  
  
 **Hata Kimliği:** BC31122  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Özel olay olarak aynı parametre listesiyle bir temsilci tanımlar.  
  
     Örneğin, varsa `Custom Event` tarafından tanımlanan `Custom Event Test(ByVal sender As Object, ByVal i As Integer)`, karşılık gelen temsilci şu şekilde olacaktır.  
  
     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]  
  
2. Özel olay ile parametre listesini değiştirin bir `As` temsilci türünü belirleme yan tümcesi.  
  
     Örneğiyle devam etmesini `Custom Event` bildirimi yazılan gibi.  
  
     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]  
  
## <a name="example"></a>Örnek  
 Bu örnek bildirir bir `Custom Event` ve gerekli belirtir `As` yan tümcesi bir temsilci türüne sahip.  
  
 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [Delegate Deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
