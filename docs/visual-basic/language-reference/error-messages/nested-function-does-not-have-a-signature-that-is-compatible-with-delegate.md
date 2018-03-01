---
title: "İç içe geçmiş işlev temsilcisi &#39;ile uyumlu bir imzası yok; &lt;delegateName'in&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60cf15343023110561da3e3fcf202bd00394127a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>İç içe geçmiş işlev temsilcisi &#39;ile uyumlu bir imzası yok; &lt;delegateName'in&gt;&#39;
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
 [Gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
