---
title: "Lambda ifadeleri ilk ifadesinde geçerli olmayan bir &#39; Servis talebi &#39;seçin; deyimi"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords: BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e91401d6891d4e38014bb716a337560885cf73a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>Lambda ifadeleri ilk ifadesinde geçerli olmayan bir &#39; Servis talebi &#39;seçin; deyimi
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
 [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [If... Then... Else deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Seçin... Case deyimi](../../../visual-basic/language-reference/statements/select-case-statement.md)
