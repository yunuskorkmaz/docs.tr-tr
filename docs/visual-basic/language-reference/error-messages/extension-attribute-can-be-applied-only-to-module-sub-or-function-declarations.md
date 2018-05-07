---
title: '&#39;Uzantı&#39; özniteliği yalnızca uygulanabilir &#39;Modülü&#39;, &#39;alt&#39;, veya &#39;işlevi&#39; bildirimleri'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: d7f8829cb879d612711ac6bcc6bf4aa065fbe323
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>&#39;Uzantı&#39; özniteliği yalnızca uygulanabilir &#39;Modülü&#39;, &#39;alt&#39;, veya &#39;işlevi&#39; bildirimleri
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
 [Genişletme Yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)
