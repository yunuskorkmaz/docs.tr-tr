---
title: İfade, içeren '<propertyname>' özelliğini tekrar tekrar çağırır
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 42177f22e632e4a05b1f0b4d934f3e56ab9ff0f2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698574"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>İfade, içeren ' \<propertyname > ' özelliğini yinelemeli olarak çağırıyor
Özellik tanımının `Set` yordamındaki bir ifade, özelliğin adına bir değer depolar.  
  
 Bir özelliğin değerini tutmak için önerilen yaklaşım, özelliğin kapsayıcısında `Private` değişkeni tanımlamak ve hem `Get` hem de `Set` yordamlarında kullanmaktır. @No__t-0 yordamının bu `Private` değişkeninde gelen değeri depolaması gerekir.  
  
 @No__t-0 yordamı, bir `Function` yordamı gibi davranır, böylece özellik adına bir değer atayabilir ve `End Get` ifadesiyle karşılaşarak denetim getirebilirsiniz. Ancak önerilen yaklaşım, [dönüş deyimindeki](../../../visual-basic/language-reference/statements/return-statement.md)değer olarak `Private` değişkenini dahil etmek için kullanılır.  
  
 @No__t-0 yordamı, bir değer döndürmeyen bir `Sub` yordamı gibi davranır. Bu nedenle, yordam veya özellik adının `Set` yordamında özel bir anlamı yoktur ve buna bir değer depolayamezsiniz.  
  
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

- [Özellik Yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Set Deyimi](../../../visual-basic/language-reference/statements/set-statement.md)
