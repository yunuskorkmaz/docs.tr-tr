---
title: Bir 'Select Case' deyiminin ilk ifadesinde lambda ifadeleri geçerli değildir
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: e9bf248da980705f070be878208c55b0cc6dae01
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64589732"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-select-case-statement"></a>Bir 'Select Case' deyiminin ilk ifadesinde lambda ifadeleri geçerli değildir
Bir lambda ifadesi içindeki test ifade kullanamazsınız bir `Select Case` deyimi. Lambda ifadesi tanımlarına dönüş işlevleri ve test ifadesi bir `Select Case` deyimi, bir başlangıç veri türünde olmalıdır.  
  
 Aşağıdaki kod bu hataya neden olur:  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **Hata Kimliği:** BC36635  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Belirleme farklı bir koşullu yapı, programınızın kodunu incelemek gibi bir `If...Then...Else` deyimi, sizin için çalışması.  
  
- Bir işlevi çağırmak aşağıdaki kodda gösterildiği gibi amaçladığınız:  
  
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
