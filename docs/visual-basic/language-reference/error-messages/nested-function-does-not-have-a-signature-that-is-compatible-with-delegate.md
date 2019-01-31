---
title: İç içe yerleştirilmiş işlevin imzası '<delegatename>' temsilcisiyle uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: ea6f230715520cb35809d57db76b300da326ec9a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283471"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>İç içe geçmiş işlev temsilcisiyle uyumlu bir imzası yok '\<delegateName'in >'
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
