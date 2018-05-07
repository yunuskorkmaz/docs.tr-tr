---
title: İç içe geçmiş işlev temsilciyle uyumlu bir imzası yok &#39; &lt;delegateName'in&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 94c53d30ad9aea9386fbb1be3e65fa31719f7a2f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>İç içe geçmiş işlev temsilciyle uyumlu bir imzası yok &#39; &lt;delegateName'in&gt;&#39;
Lambda ifadesi uyumsuz bir imzaya sahip bir temsilci atanmış durumda. Örneğin, aşağıdaki kodda temsilci `Del` iki tamsayı parametreye sahiptir.  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 Tek bağımsız değişkenli lambda ifadesi türü olarak bildirilmiş durumunda hataya neden `Del`:  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **Hata Kimliği:** BC36532  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   İmzaları uyumlu temsilci tanımı veya atanan lambda ifadesi ayarlayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gevşek Temsilci Dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
