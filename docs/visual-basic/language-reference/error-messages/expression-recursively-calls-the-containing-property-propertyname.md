---
title: İfade, içeren '<propertyname>' özelliğini tekrar tekrar çağırır
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: c05a7d9b021192d53a30e49f52abc08d9b153156
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874248"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>İfade, içeren '\<propertyname>' özelliğini tekrar tekrar çağırır

`Set`Özellik tanımı yordamındaki bir ifade, özelliğin adına bir değer depolar.  
  
 Bir özelliğin değerini tutmak için önerilen yaklaşım, `Private` özelliğin kapsayıcısında bir değişken tanımlamak ve hem hem de `Get` `Set` yordamlarında kullanmaktır. `Set`Yordamın bu değişkende gelen değeri depolaması gerekir `Private` .  
  
 `Get`Yordam, bir yordam gibi davranır `Function` , bu nedenle özellik adına bir değer atayabilir ve deyimden yararlanarak denetim getirebilirsiniz `End Get` . Ancak önerilen yaklaşım, `Private` değişkeni bir [Return ifadesine](../statements/return-statement.md)değer olarak dahil etmek için kullanılır.  
  
 `Set`Yordam `Sub` , bir değer döndürmeyen bir yordam gibi davranır. Bu nedenle, yordam veya özellik adının bir yordam içinde özel bir anlamı yoktur `Set` ve buna bir değer depolayamezsiniz.  
  
 Aşağıdaki örnekte, bu hataya neden olabilecek yaklaşım ve önerilen yaklaşım gösterilmektedir.  
  
```vb  
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
  
 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için lütfen bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata kimliği:** BC42026  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Önceki örnekte gösterildiği gibi önerilen yaklaşımı kullanmak için özellik tanımını yeniden yazın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Yordamları](../../programming-guide/language-features/procedures/property-procedures.md)
- [Property Deyimi](../statements/property-statement.md)
- [Set deyimleri](../statements/set-statement.md)
