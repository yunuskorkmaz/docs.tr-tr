---
title: '&#39;#ElseIf&#39; eşleşen bir gelmelidir &#39;#If&#39; veya &#39;#ElseIf&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: ef904173b1791309f6c2722bd959cabdad1d71da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588154"
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a>&#39;#ElseIf&#39; eşleşen bir gelmelidir &#39;#If&#39; veya &#39;#ElseIf&#39;
`#ElseIf` Koşullu derleme yönergesi değil. Bir `#ElseIf` yan tümcesi olmalıdır öncesinde eşleşen bir `#If` veya `#ElseIf` yan tümcesi.  
  
 **Hata Kimliği:** BC30014  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Denetleyin bir önceki `#If` veya `#ElseIf` öğesinden ayrılmış değil `#ElseIf` bir araya giren koşullu derleme bloğu ya da yanlış yerleştirilmiş `#End If`.  
  
2.  Varsa `#ElseIf` öncesinde bir `#Else` yönergesi, kaldırın veya `#Else` veya değiştirmek için bir `#ElseIf`.  
  
3.  Şey sırayla ise ekleyin bir `#If` koşullu derleme blok başına yönerge.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
