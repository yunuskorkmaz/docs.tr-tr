---
title: Lambda ifadeleri ilk ifadesinde geçerli olmayan bir &#39;Select Case&#39; deyimi
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: afefa821f9695dbbfe2a96aee5afd3171ae5b1db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700227"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>Lambda ifadeleri ilk ifadesinde geçerli olmayan bir &#39;Select Case&#39; deyimi
Bir lambda ifadesi içindeki test ifade kullanamazsınız bir `Select Case` deyimi. Lambda ifadesi tanımlarına dönüş işlevleri ve test ifadesi bir `Select Case` deyimi, bir başlangıç veri türünde olmalıdır.  
  
 Aşağıdaki kod bu hataya neden olur:  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **Hata Kimliği:** BC36635  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Belirleme farklı bir koşullu yapı, programınızın kodunu incelemek gibi bir `If...Then...Else` deyimi, sizin için çalışması.  
  
-   Bir işlevi çağırmak aşağıdaki kodda gösterildiği gibi amaçladığınız:  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Select...Case Deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md)
