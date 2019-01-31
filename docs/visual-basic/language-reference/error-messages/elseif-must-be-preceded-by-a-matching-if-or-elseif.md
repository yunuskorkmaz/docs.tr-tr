---
title: "'#ElseIf' öncesinde eşleşen bir '#If' veya '#ElseIf' olmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: d6fa76b2aba45e3455cef6ceafc0f737ef56225d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271557"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>'#ElseIf' öncesinde eşleşen bir '#If' veya '#ElseIf' olmalıdır
`#ElseIf` Koşullu derleme yönergesi ' dir. Bir `#ElseIf` yan tümcesi gerekir öncesinde eşleşen bir `#If` veya `#ElseIf` yan tümcesi.  
  
 **Hata Kimliği:** BC30014  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Bu maddeyi bir önceki `#If` veya `#ElseIf` bu ayrılmış değil `#ElseIf` bir müdahalede bulunan koşullu derleme blok veya yanlış yerleştirilmiş `#End If`.  
  
2.  Varsa `#ElseIf` öncesinde bir `#Else` yönergesi, kaldırabilir ya da `#Else` veya değiştirmek için bir `#ElseIf`.  
  
3.  Diğer her şey sırayla ekleyin bir `#If` koşullu derleme blok başına yönerge.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
