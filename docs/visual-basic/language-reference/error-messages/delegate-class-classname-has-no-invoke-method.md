---
title: "Temsilci sınıfı &#39; &lt;classname&gt;&#39; hiçbir Invoke yöntemi sahiptir, bu nedenle bu tür bir ifade bir yöntem çağrısı hedefi olamaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords: BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 55d0e2442807e25737d90ac4b45a59b9d3e73037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="delegate-class-39ltclassnamegt39-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Temsilci sınıfı &#39; &lt;classname&gt;&#39; hiçbir Invoke yöntemi sahiptir, bu nedenle bu tür bir ifade bir yöntem çağrısı hedefi olamaz
Çağrı `Invoke` bir temsilci başarısız oldu `Invoke` temsilci sınıf üzerinde uygulanmadı.  
  
 **Hata Kimliği:** BC30220  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Temsilci sınıfının bir örneği ile oluşturulan olun bir `Dim` deyimi ve bir yordam temsilci örneğine atanan `AddressOf` işleci.  
  
2.  Temsilci sınıfı uygulayan kodu bulun ve bunu uygulayan emin olun `Invoke` yordamı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temsilciler](../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Delegate deyimi](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [AddressOf işleci](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)
