---
title: "'<variablename>' değişkeni, kapsayan bir bloktaki değişkeni gizliyor"
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 04538be3431fb06518051db4378e986ea5711219
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875055"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>'\<variablename>' değişkeni, kapsayan bir bloktaki değişkeni gizliyor

Bir blok içine alınmış bir değişken, başka bir yerel değişkenle aynı ada sahiptir.  
  
 **Hata kimliği:** BC30616  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Diğer yerel değişkenlerle aynı olmaması için, ekteki bloktaki değişkeni yeniden adlandırın. Örnek:  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- Bu hatanın yaygın bir nedeni, `Catch e As Exception` bir olay işleyicisinin içinde kullanıma yöneliktir. Bu durumda, `Catch` blok değişkenini `ex` yerine adlandırın `e` .  
  
- Bu hatanın daha yaygın bir kaynağı, farklı bir blokta bir blok içinde belirtilen yerel bir değişkene erişme girişiminde bulunur `Try` `Catch` . Bunu düzeltmek için değişkeni yapının dışında bildirin `Try...Catch...Finally` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Try...Catch...Finally Deyimi](../statements/try-catch-finally-statement.md)
- [Değişken Bildirimi](../../programming-guide/language-features/variables/variable-declaration.md)
