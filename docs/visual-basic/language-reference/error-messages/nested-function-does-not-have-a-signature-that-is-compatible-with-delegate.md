---
title: İç içe geçmiş işlev temsilcisiyle uyumlu bir imzası yok &#39; &lt;delegateName'in&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: abfda4ee6064ec9ea54b8a3c383d10f8263a1458
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506413"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>İç içe geçmiş işlev temsilcisiyle uyumlu bir imzası yok &#39; &lt;delegateName'in&gt;&#39;
Bir lambda ifadesi, uyumlu bir imzası olan bir temsilci atanmış durumda. Örneğin, aşağıdaki kodda, temsilci `Del` iki tamsayı parametre yok.  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 Bir bağımsız değişkenli lambda ifadesi türü olarak bildirilirse hataya neden `Del`:  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **Hata Kimliği:** BC36532  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Temsilci tanımı veya atanmış bir lambda ifadesi, imzaları uyumlu olacak şekilde ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Gevşek Temsilci Dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
