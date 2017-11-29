---
title: "&#39; #ElseIf &#39; eşleşen bir &#39; #If &#39;tarafından gelmelidir; ya &#39; #ElseIf &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords: BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b3a4e809e1108fcd6e116538a1947057e9548ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a>&#39; #ElseIf &#39; eşleşen bir &#39; #If &#39;tarafından gelmelidir; ya &#39; #ElseIf &#39;
`#ElseIf`Koşullu derleme yönergesi değil. Bir `#ElseIf` yan tümcesi olmalıdır öncesinde eşleşen bir `#If` veya `#ElseIf` yan tümcesi.  
  
 **Hata Kimliği:** BC30014  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Denetleyin bir önceki `#If` veya `#ElseIf` öğesinden ayrılmış değil `#ElseIf` bir araya giren koşullu derleme bloğu ya da yanlış yerleştirilmiş `#End If`.  
  
2.  Varsa `#ElseIf` öncesinde bir `#Else` yönergesi, kaldırın veya `#Else` veya değiştirmek için bir `#ElseIf`.  
  
3.  Şey sırayla ise ekleyin bir `#If` koşullu derleme blok başına yönerge.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [#If... Then... #Else yönergeleri](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
