---
title: "'#ElseIf' öncesinde eşleşen bir '#If' veya '#ElseIf' olmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 4832fb80cfbe42c7a1303e0de69f36784711c05a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311064"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>'#ElseIf' öncesinde eşleşen bir '#If' veya '#ElseIf' olmalıdır
`#ElseIf` Koşullu derleme yönergesi ' dir. Bir `#ElseIf` yan tümcesi gerekir öncesinde eşleşen bir `#If` veya `#ElseIf` yan tümcesi.  
  
 **Hata Kimliği:** BC30014  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Bu maddeyi bir önceki `#If` veya `#ElseIf` bu ayrılmış değil `#ElseIf` bir müdahalede bulunan koşullu derleme blok veya yanlış yerleştirilmiş `#End If`.  
  
2. Varsa `#ElseIf` öncesinde bir `#Else` yönergesi, kaldırabilir ya da `#Else` veya değiştirmek için bir `#ElseIf`.  
  
3. Diğer her şey sırayla ekleyin bir `#If` koşullu derleme blok başına yönerge.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [#If...Then...#Else Yönergesi](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
