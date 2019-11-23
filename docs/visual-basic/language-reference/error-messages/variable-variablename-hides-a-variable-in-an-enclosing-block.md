---
title: "'<variablename>' değişkeni, kapsayan bir bloktaki değişkeni gizliyor"
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 4312abef83728f432e2f6a492e5acad3450719b1
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592059"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>'\<VariableName > ' değişkeni kapsayan bir blokta bir değişkeni gizliyor
Bir blok içine alınmış bir değişken, başka bir yerel değişkenle aynı ada sahiptir.  
  
 **Hata kimliği:** BC30616  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Diğer yerel değişkenlerle aynı olmaması için, ekteki bloktaki değişkeni yeniden adlandırın. Örneğin:  
  
    ```vb  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- Bu hatanın yaygın bir nedeni, bir olay işleyicisi içinde `Catch e As Exception` kullanmaktır. Bu durumda, `Catch` blok değişkenini `e`yerine `ex` olarak adlandırın.  
  
- Bu hatanın daha yaygın bir kaynağı, farklı bir `Catch` bloğunda `Try` bloğu içinde belirtilen yerel bir değişkene erişme girişiminde bulunur. Bunu düzeltmek için değişkeni `Try...Catch...Finally` yapısı dışında bildirin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
