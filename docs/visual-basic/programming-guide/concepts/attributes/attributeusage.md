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
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="21998-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21998-102">AttributeUsage (Visual Basic)</span></span>

<span data-ttu-id="21998-103">Özel bir öznitelik sınıfının nasıl kullanılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="21998-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="21998-104">`AttributeUsage`, yeni özniteliğin nasıl uygulanabileceğini denetlemek için özel öznitelik tanımlarına uygulanabilen bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="21998-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="21998-105">Varsayılan ayarlar açıkça uygulandığında şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="21998-105">The default settings look like this when applied explicitly:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="21998-106">Bu örnekte, `NewAttribute` sınıfı öznitelik özellikli herhangi bir kod varlığına uygulanabilir, ancak her bir varlığa yalnızca bir kez uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="21998-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="21998-107">Temel sınıfa uygulandığında türetilmiş sınıflar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="21998-107">It is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="21998-108">`AllowMultiple`Ve `Inherited` bağımsız değişkenleri isteğe bağlıdır, bu nedenle bu kod aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="21998-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="21998-109">İlk `AttributeUsage` bağımsız değişken, numaralandırmanın bir veya daha fazla öğesi olmalıdır <xref:System.AttributeTargets> .</span><span class="sxs-lookup"><span data-stu-id="21998-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="21998-110">Birden çok hedef türü, OR işleciyle birlikte bağlanabilir ve şöyle olabilir:</span><span class="sxs-lookup"><span data-stu-id="21998-110">Multiple target types can be linked together with the OR operator, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

<span data-ttu-id="21998-111">`AllowMultiple`Bağımsız değişken olarak ayarlandıysa `true` , elde edilen öznitelik tek bir varlığa birden çok kez uygulanabilir, şöyle olabilir:</span><span class="sxs-lookup"><span data-stu-id="21998-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

<span data-ttu-id="21998-112">Bu durumda `MultiUseAttr` `AllowMultiple` , olarak ayarlandığı için tekrar tekrar uygulanabilir `true` .</span><span class="sxs-lookup"><span data-stu-id="21998-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="21998-113">Birden çok özniteliği uygulamak için gösterilen her iki biçim de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="21998-113">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="21998-114">, `Inherited` Olarak ayarlanırsa `false` öznitelik, öznitelikli bir sınıftan türetilmiş sınıflar tarafından devralınmaz.</span><span class="sxs-lookup"><span data-stu-id="21998-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="21998-115">Örnek:</span><span class="sxs-lookup"><span data-stu-id="21998-115">For example:</span></span>

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

<span data-ttu-id="21998-116">Bu durumda `Attr1` `DClass` devralma aracılığıyla öğesine uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="21998-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="21998-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21998-117">Remarks</span></span>

<span data-ttu-id="21998-118">`AttributeUsage`Öznitelik tek kullanım özniteliğidir; aynı sınıfa birden çok kez uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="21998-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="21998-119">`AttributeUsage`, için bir diğer addır <xref:System.AttributeUsageAttribute> .</span><span class="sxs-lookup"><span data-stu-id="21998-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="21998-120">Daha fazla bilgi için bkz. [yansıma kullanarak özniteliklere erişme (Visual Basic)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="21998-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="21998-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="21998-121">Example</span></span>

<span data-ttu-id="21998-122">Aşağıdaki örnek, `Inherited` ve `AllowMultiple` bağımsız değişkenlerinin `AttributeUsage` özniteliğe ve bir sınıfa uygulanan özel özniteliklerin nasıl numaralandırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="21998-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

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

## <a name="sample-output"></a><span data-ttu-id="21998-123">Örnek Çıktı</span><span class="sxs-lookup"><span data-stu-id="21998-123">Sample Output</span></span>

```console
Attributes on Base Class:
A1
A2
Attributes on Derived Class:
A3
A3
A2
```

## <a name="see-also"></a><span data-ttu-id="21998-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21998-124">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="21998-125">Visual Basic Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="21998-125">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="21998-126">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21998-126">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="21998-127">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21998-127">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="21998-128">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21998-128">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="21998-129">Özel öznitelikler oluşturma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21998-129">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="21998-130">Yansıma kullanarak özniteliklere erişme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21998-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
