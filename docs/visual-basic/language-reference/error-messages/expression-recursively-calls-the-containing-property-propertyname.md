---
title: İfade, içeren '<propertyname>' özelliğini tekrar tekrar çağırır
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: a758d05cca5ca71943b0ef08184aef5b2c457739
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802355"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a>İfade yinelemeli olarak çağırıyor kapsayan özelliği '\<propertyname >'
Bir deyimde `Set` yordamı bir özellik tanımı, özelliğin adını bir değer depolar.  
  
 Bir özelliğin değerini tutmak için önerilen yaklaşım tanımlamaktır bir `Private` değişken özelliğin kapsayıcısındaki ve her ikisinde de kullanın `Get` ve `Set` yordamları. `Set` Yordamı ardından depolamak gelen değeri bu `Private` değişkeni.  
  
 `Get` Yordamı davranacağını gibi bir `Function` yordam, özellik adı için bir değer atamak ve dönüş denetimi ile karşılaşıldığında `End Get` deyimi. Önerilen yaklaşım, ancak dahil etmektir `Private` değeri olarak değişken bir [dönüş deyimi](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 `Set` Yordamı davranacağını gibi bir `Sub` bir değer döndürmeyen bir yordam,. Bu nedenle, içinde özel bir anlamı yordam veya özellik adına sahip bir `Set` yordam ve depolayamaz değeri içine.  
  
 Aşağıdaki örnekte, ardından tarafından önerilen yaklaşım, bu hataya neden olabilecek bir yaklaşım gösterilmektedir.  
  
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
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için lütfen bkz [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42026  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yukarıdaki örnekte gösterildiği gibi önerilen yaklaşım kullanılacak özellik tanımını yeniden yazın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Özellik Yordamları](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Property Deyimi](../../../visual-basic/language-reference/statements/property-statement.md)
- [Set Deyimi](../../../visual-basic/language-reference/statements/set-statement.md)
