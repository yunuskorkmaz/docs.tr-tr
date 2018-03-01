---
title: "&#39; Uzantı &#39; öznitelik yalnızca uygulanabilir &#39; Modül &#39; &#39; Alt &#39; veya &#39; İşlev &#39; bildirimleri"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d77933c52484eb934501107d1ddad15f0eca826
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>&#39; Uzantı &#39; öznitelik yalnızca uygulanabilir &#39; Modül &#39; &#39; Alt &#39; veya &#39; İşlev &#39; bildirimleri
Visual Basic'te bir veri türü genişletmek için tek bir standart modül içinde bir genişletme yöntemi tanımlamak için yoludur. Genişletme yöntemi olabilir bir `Sub` yordamı veya `Function` yordamı. Tüm uzantı yöntemleri uzantısı özniteliği ile işaretlenmiş olmalıdır `<Extension()>`, gelen <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı. İsteğe bağlı olarak, bir genişletme yöntemi içeren bir modül aynı şekilde işaretlenmiş olabilir. Herhangi bir uzantı özniteliğinin kullanımını geçerli değil.  
  
 **Hata Kimliği:** BC36550  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Uzantı özniteliğini kaldırın.  
  
-   Uzantınızı yeniden tasarlamanız kapsayan bir modülde tanımlanmış bir yöntem olarak.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek tanımlayan bir `Print` yöntemi `String` veri türü.  
  
```  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [Genişletme yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md)
