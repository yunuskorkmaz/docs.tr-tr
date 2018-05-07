---
title: Lambda ifadeleri ilk ifadesinde geçerli olmayan bir &#39;Select Case&#39; deyimi
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: c492615850ec089fe35c1ae4eaba90a741e30f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>Lambda ifadeleri ilk ifadesinde geçerli olmayan bir &#39;Select Case&#39; deyimi
Test ifadesinde lambda ifadesi kullanamaz bir `Select Case` deyimi. Lambda ifadesi tanımları dönüş işlevler ve test ifadesi bir `Select Case` deyimi bir başlangıç veri türünde olması gerekir.  
  
 Aşağıdaki kod bu hataya neden olur:  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **Hata Kimliği:** BC36635  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Farklı bir koşullu yapım olup olmadığını belirlemek için kodunuzu inceleyin gibi bir `If...Then...Else` deyimi, sizin için çalışması.  
  
-   Bir işlevi çağırmak aşağıdaki kodda gösterildiği gibi amaçladığınız:  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Select...Case Deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md)
