---
title: "İfade yinelemeli olarak içeren özellik &#39;çağırır; &lt;propertyname&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47de3c2d25336962168f01a4c8717274de7c9aad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a>İfade yinelemeli olarak içeren özellik &#39;çağırır; &lt;propertyname&gt;&#39;
Bir deyimde `Set` yordamı özelliği tanımı bir değer özelliğinin adı depolar.  
  
 Bir özelliğin değerini tutan önerilen yaklaşım tanımlamaktır bir `Private` özelliğin kapsayıcısında değişken ve ikisi de kullanmak `Get` ve `Set` yordamları. `Set` Yordamı sonra depolamak gelen değeri bu `Private` değişkeni.  
  
 `Get` Yordamı davranır gibi bir `Function` yordamı, özellik adı için bir değer atamak ve dönüş denetim karşılaşmadan tarafından `End Get` deyimi. Önerilen yaklaşım ancak eklemektir `Private` değişken değer olarak bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Set` Yordamı davranır gibi bir `Sub` bir değer döndürmüyor yordamı. Bu nedenle, içinde özel bir anlamı yordamı veya özellik adına sahip bir `Set` yordam ve depolayamaz bir değer içine.  
  
 Aşağıdaki örnek tarafından önerilen yaklaşım ve ardından bu hataya neden olabilir bir yaklaşım gösterilmektedir.  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için lütfen bkz [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42026  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Önceki örnekte gösterildiği gibi önerilen yaklaşımı kullanmak için özellik tanımını yeniden yazın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellik yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Property deyimi](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Set deyimi](../../../visual-basic/language-reference/statements/set-statement.md)
