---
description: "Daha fazla bilgi edinin: BC30014: ' #ElseIf ' öncesinde eşleşen bir ' #If ' veya ' #ElseIf olmalıdır"
title: "'#ElseIf' öncesinde eşleşen bir '#If' veya '#ElseIf' olmalıdır"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 5eeb9c2fc0fd7267d95a8713a7071cd08788e48b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796567"
---
# <a name="bc30014-elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>BC30014: ' #ElseIf ' öncesinde eşleşen bir ' #If ' veya ' #ElseIf ' olmalıdır

`#ElseIf` , koşullu bir derleme yönergedir. Bir `#ElseIf` yan tümcesinin önünde bir eşleşen `#If` or `#ElseIf` yan tümcesi gelmelidir.

 **Hata kimliği:** BC30014

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Önceki `#If` veya `#ElseIf` bunun, bir `#ElseIf` araya giren koşullu derleme bloğu veya hatalı bir şekilde yerleştirilmiş olduğunu kontrol edin `#End If` .

2. `#ElseIf`Önünde bir yönerge varsa, `#Else` veya öğesini kaldırın ya da `#Else` bir olarak değiştirin `#ElseIf` .

3. Başka her şey sıralamayla, `#If` koşullu derleme bloğunun başlangıcına bir yönerge ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [#If... Sonra... #Else yönergeler](../directives/if-then-else-directives.md)
