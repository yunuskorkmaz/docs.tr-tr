---
title: Değişken &#39; &lt;variablename&gt; &#39; kapsayan bir bloktaki bir değişken gizler
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 58e09caeb477d6b1df7f3be17e0a8ee05be3551e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="variable-39ltvariablenamegt39-hides-a-variable-in-an-enclosing-block"></a>Değişken &#39; &lt;variablename&gt; &#39; kapsayan bir bloktaki bir değişken gizler
Bir blok içine bir değişken başka bir yerel değişken aynı ada sahiptir.  
  
 **Hata Kimliği:** BC30616  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Böylece, aynı herhangi bir yerel değişkenler değil kapalı bloğundaki değişken yeniden adlandırın. Örneğin:  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
-   Bu hatanın sık karşılaşılan bir nedeni kullanımıdır `Catch e As Exception` olay işleyici içinde. Bu durumda, ad `Catch` bloğu değişkeni `ex` yerine `e`.  
  
-   Bu hatanın ortak başka bir kaynak içinde bildirilen yerel bir değişkene erişme girişimi olan bir `Try` ayrı bir engelleme `Catch` bloğu. Bu sorunu gidermek için dışında değişkeni bildirme `Try...Catch...Finally` yapısı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Try...Catch...Finally Deyimi](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [Değişken Bildirimi](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
