---
title: AttributeUsage
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 677d49aba38801f2adf42cc745983af30b3eddc5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400738"
---
# <a name="attributeusage-visual-basic"></a>AttributeUsage (Visual Basic)

Özel bir öznitelik sınıfının nasıl kullanılabileceğini belirler. `AttributeUsage`, yeni özniteliğin nasıl uygulanabileceğini denetlemek için özel öznitelik tanımlarına uygulanabilen bir özniteliktir. Varsayılan ayarlar açıkça uygulandığında şöyle görünür:

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

Bu örnekte, `NewAttribute` sınıfı öznitelik özellikli herhangi bir kod varlığına uygulanabilir, ancak her bir varlığa yalnızca bir kez uygulanabilir. Temel sınıfa uygulandığında türetilmiş sınıflar tarafından devralınır.

`AllowMultiple`Ve `Inherited` bağımsız değişkenleri isteğe bağlıdır, bu nedenle bu kod aynı etkiye sahiptir:

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

İlk `AttributeUsage` bağımsız değişken, numaralandırmanın bir veya daha fazla öğesi olmalıdır <xref:System.AttributeTargets> . Birden çok hedef türü, OR işleciyle birlikte bağlanabilir ve şöyle olabilir:

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

`AllowMultiple`Bağımsız değişken olarak ayarlandıysa `true` , elde edilen öznitelik tek bir varlığa birden çok kez uygulanabilir, şöyle olabilir:

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

Bu durumda `MultiUseAttr` `AllowMultiple` , olarak ayarlandığı için tekrar tekrar uygulanabilir `true` . Birden çok özniteliği uygulamak için gösterilen her iki biçim de geçerlidir.

, `Inherited` Olarak ayarlanırsa `false` öznitelik, öznitelikli bir sınıftan türetilmiş sınıflar tarafından devralınmaz. Örnek:

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

Bu durumda `Attr1` `DClass` devralma aracılığıyla öğesine uygulanmaz.

## <a name="remarks"></a>Açıklamalar

`AttributeUsage`Öznitelik tek kullanım özniteliğidir; aynı sınıfa birden çok kez uygulanamaz. `AttributeUsage`, için bir diğer addır <xref:System.AttributeUsageAttribute> .

Daha fazla bilgi için bkz. [yansıma kullanarak özniteliklere erişme (Visual Basic)](accessing-attributes-by-using-reflection.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, `Inherited` ve `AllowMultiple` bağımsız değişkenlerinin `AttributeUsage` özniteliğe ve bir sınıfa uygulanan özel özniteliklerin nasıl numaralandırılacağını gösterir.

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

```console
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
- [Visual Basic Programlama Kılavuzu](../../index.md)
- [Öznitelikler](../../../../standard/attributes/index.md)
- [Yansıma (Visual Basic)](../reflection.md)
- [Öznitelikler (Visual Basic)](../../../language-reference/attributes.md)
- [Özel öznitelikler oluşturma (Visual Basic)](creating-custom-attributes.md)
- [Yansıma kullanarak özniteliklere erişme (Visual Basic)](accessing-attributes-by-using-reflection.md)
