---
title: İç içe yerleştirilmiş işlevin imzası '<delegatename>' temsilcisiyle uyumlu değil
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 912962e2ab39c4811294ccc225814b230100e12a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592006"
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
  
- Temsilci tanımı veya atanmış bir lambda ifadesi, imzaları uyumlu olacak şekilde ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gevşek Temsilci Dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
