---
title: "'Extension' özniteliği yalnızca 'Module', 'Sub' veya 'Function' bildirimlerine uygulanabilir"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: a4561359e4d7cb0f6ebe44a5deb09b3374556ed8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801653"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>'Extension' özniteliği yalnızca 'Module', 'Sub' veya 'Function' bildirimlerine uygulanabilir
Visual Basic'te bir veri türü genişletmek için tek bir standart modül içinde bir genişletme yöntemi tanımlamak için yoludur. Genişletme yöntemi olabilir bir `Sub` yordamı veya `Function` yordamı. Tüm uzantı yöntemleri uzantı özniteliğiyle işaretlenmelidir `<Extension()>`, gelen <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> ad alanı. İsteğe bağlı olarak, bir uzantı yöntemini içeren modül aynı şekilde işaretlenmiş olabilir. Herhangi bir kullanıma uzantısı özniteliği geçerli değil.  
  
 **Hata Kimliği:** BC36550  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Uzantı özniteliğine kaldırın.  
  
- Uzantınızı kapsayan bir modülde tanımlanmış bir yöntem olarak yeniden tasarlayın.  
  
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
