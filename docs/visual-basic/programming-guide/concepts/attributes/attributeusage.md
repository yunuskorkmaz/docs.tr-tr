---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: ae162c310511db160806501af895276a4a4bba5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643425"
---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)
Özel bir öznitelik sınıfı nasıl kullanılabileceğini belirler. `AttributeUsage` Yeni öznitelik nasıl uygulanabilir denetlemek için özel öznitelik tanımlarını uygulanabilir bir özniteliktir. Varsayılan ayarları açıkça uygulandığında şöyle:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 Bu örnekte, `NewAttribute` sınıfı olabilir herhangi bir öznitelik mümkün kod varlık, ancak yalnızca bir kez her varlık için uygulanır. Temel bir sınıfa uygulandığında türetilmiş sınıflar tarafından devralınır.  
  
 `AllowMultiple` Ve `Inherited` değişkenleridir isteğe bağlı, bu kodu aynı etkiye sahiptir:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 İlk `AttributeUsage` bağımsız değişkeni, bir veya daha fazla öğesi olmalıdır <xref:System.AttributeTargets> numaralandırması. Birden çok hedef türü veya işlecini şöyle birlikte bağlanabilir:  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 Varsa `AllowMultiple` bağımsız değişkeni olarak ayarlanmış `true`, sonuçta elde edilen özniteliği bu gibi tek bir varlık için birden çok kez uygulanabilir sonra:  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>   
Class MultiUseAttr  
    Inherits Attribute  
End Class  
  
<MultiUseAttr(), MultiUseAttr()>   
Class Class1  
End Class  
```  
  
 Bu durumda `MultiUseAttr` art arda çünkü uygulanabilir `AllowMultiple` ayarlanır `true`. Birden çok öznitelik uygulamak için gösterilen iki biçimi geçerli değil.  
  
 Varsa `Inherited` ayarlanır `false`, öznitelik öznitelik sınıfından türetilen sınıflar tarafından devralınır değil sonra. Örneğin:  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>   
Class Attr1  
    Inherits Attribute  
End Class  
  
<Attr1()>   
Class BClass  
  
End Class    
  
Class DClass  
    Inherits BClass  
End Class  
```  
  
 Bu durumda `Attr1` uygulanmaz `DClass` devralma aracılığıyla.  
  
## <a name="remarks"></a>Açıklamalar  
 `AttributeUsage` Özniteliktir tek kullanımlık özniteliği--birden çok kez aynı sınıfa uygulanamaz. `AttributeUsage` bir diğer adı için <xref:System.AttributeUsageAttribute>.  
  
 Daha fazla bilgi için bkz: [erişme öznitelikleri kullanarak yansıma (Visual Basic) tarafından](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, etkisini gösterir `Inherited` ve `AllowMultiple` bağımsız değişkenleri `AttributeUsage` özniteliğini ve bir sınıfa uygulanan özel öznitelikler nasıl listelenebilir.  
  
```vb  
Imports System  
```  
  
```vb  
' Create some custom attributes:  
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>   
Class A1  
    Inherits System.Attribute  
End Class  
  
<AttributeUsage(System.AttributeTargets.Class)>   
Class A2  
    Inherits System.Attribute  
End Class      
  
<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>   
Class A3  
    Inherits System.Attribute  
End Class  
  
' Apply custom attributes to classes:  
<A1(), A2()>   
Class BaseClass  
  
End Class  
  
<A3(), A3()>   
Class DerivedClass  
    Inherits BaseClass  
End Class  
  
Public Class TestAttributeUsage  
    Sub Main()  
        Dim b As New BaseClass  
        Dim d As New DerivedClass  
        ' Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:")  
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)  
  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next  
  
        Console.WriteLine("Attributes on Derived Class:")  
        attrs = d.GetType().GetCustomAttributes(True)  
        For Each attr In attrs  
            Console.WriteLine(attr)  
        Next              
    End Sub  
End Class  
```  
  
## <a name="sample-output"></a>Örnek Çıktı  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)  
 [Öznitelikler](../../../../standard/attributes/index.md)  
 [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)  
 [Öznitelikler (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)  
 [Özel öznitelikler (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [(Visual Basic) yansıma kullanarak özniteliklere erişme](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
