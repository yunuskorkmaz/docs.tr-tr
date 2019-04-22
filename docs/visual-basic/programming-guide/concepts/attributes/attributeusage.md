---
title: AttributeUsage (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 1841171f2f3fc26ba9244c72c69960b765d39807
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827516"
---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)
Özel bir öznitelik sınıfı nasıl kullanılabileceğini belirler. `AttributeUsage` Yeni öznitelik nasıl uygulanabileceğini kontrol etmek için özel öznitelik tanımlarına uygulanabilir bir özniteliktir. Varsayılan ayarlar, açıkça uygulandığında şöyle görünür:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 Bu örnekte, `NewAttribute` sınıfı olabilir herhangi bir öznitelik mümkün kod varlık, ancak yalnızca bir kez her varlık için uygulanır. Temel bir sınıfa uygulandığında türetilmiş sınıflar tarafından devralınır.  
  
 `AllowMultiple` Ve `Inherited` bu kodu aynı etkiye sahiptir. Bu nedenle bağımsız değişken isteğe bağlıdır:  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 İlk `AttributeUsage` bağımsız değişkeni olmalıdır bir veya daha fazla öğeleri <xref:System.AttributeTargets> sabit listesi. Birden çok hedef türü, OR işleci, bu gibi birlikte bağlanabilir:  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 Varsa `AllowMultiple` bağımsız değişkeni ayarlanır `true`, sonra elde edilen özniteliği, bu gibi tek bir varlık için birden çok kez uygulanabilir:  
  
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
  
 Varsa `Inherited` ayarlanır `false`, ardından öznitelik öznitelendirilen bir sınıftan türetilmiş sınıflar tarafından devralınır değil. Örneğin:  
  
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
 `AttributeUsage` Özniteliği, bir tek kullanımlık özniteliğin birden çok kez aynı sınıfa uygulanamaz. `AttributeUsage` için bir diğer addır <xref:System.AttributeUsageAttribute>.  
  
 Daha fazla bilgi için [erişme öznitelikleri kullanarak yansıma (Visual Basic) tarafından](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, etkisini gösterir `Inherited` ve `AllowMultiple` bağımsız değişkenleri `AttributeUsage` özniteliği ve nasıl bir sınıfa uygulanan özel öznitelikler listelenebilir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Attribute>
- <xref:System.Reflection>
- [Visual Basic programlama kılavuzu](../../../../visual-basic/programming-guide/index.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Yansıma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [Öznitelikler (Visual Basic)](../../../../visual-basic/language-reference/attributes.md)
- [Özel öznitelikler (Visual Basic) oluşturma](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [(Visual Basic) yansıma kullanarak özniteliklere erişme](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
