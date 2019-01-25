---
title: '&#39;Uzantı&#39; özniteliği yalnızca uygulanabilir &#39;Modülü&#39;, &#39;alt&#39;, veya &#39;işlevi&#39; bildirimleri'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: fabd602f31a362fe33954253d565e86a065e0a83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718240"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a>&#39;Uzantı&#39; özniteliği yalnızca uygulanabilir &#39;Modülü&#39;, &#39;alt&#39;, veya &#39;işlevi&#39; bildirimleri
Visual Basic'te bir veri türü genişletmek için tek bir standart modül içinde bir genişletme yöntemi tanımlamak için yoludur. Genişletme yöntemi olabilir bir `Sub` yordamı veya `Function` yordamı. Tüm uzantı yöntemleri uzantı özniteliğiyle işaretlenmelidir `<Extension()>`, gelen <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı. İsteğe bağlı olarak, bir uzantı yöntemini içeren modül aynı şekilde işaretlenmiş olabilir. Herhangi bir kullanıma uzantısı özniteliği geçerli değil.  
  
 **Hata Kimliği:** BC36550  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Uzantı özniteliğine kaldırın.  
  
-   Uzantınızı kapsayan bir modülde tanımlanmış bir yöntem olarak yeniden tasarlayın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte tanımlayan bir `Print` yöntemi `String` veri türü.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- [Öznitelikler genel bakış](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [Genişletme Yöntemleri](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Module Deyimi](../../../visual-basic/language-reference/statements/module-statement.md)
