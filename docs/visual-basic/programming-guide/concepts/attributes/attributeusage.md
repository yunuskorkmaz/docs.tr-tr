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
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="1e238-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e238-102">AttributeUsage (Visual Basic)</span></span>
<span data-ttu-id="1e238-103">Özel bir öznitelik sınıfı nasıl kullanılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="1e238-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="1e238-104">`AttributeUsage` Yeni öznitelik nasıl uygulanabileceğini kontrol etmek için özel öznitelik tanımlarına uygulanabilir bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="1e238-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="1e238-105">Varsayılan ayarlar, açıkça uygulandığında şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="1e238-105">The default settings look like this when applied explicitly:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All,   
                   AllowMultiple:=False,   
                   Inherited:=True)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="1e238-106">Bu örnekte, `NewAttribute` sınıfı olabilir herhangi bir öznitelik mümkün kod varlık, ancak yalnızca bir kez her varlık için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1e238-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="1e238-107">Temel bir sınıfa uygulandığında türetilmiş sınıflar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="1e238-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="1e238-108">`AllowMultiple` Ve `Inherited` bu kodu aynı etkiye sahiptir. Bu nedenle bağımsız değişken isteğe bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="1e238-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```vb  
<System.AttributeUsage(System.AttributeTargets.All)>   
Class NewAttribute  
    Inherits System.Attribute  
End Class  
```  
  
 <span data-ttu-id="1e238-109">İlk `AttributeUsage` bağımsız değişkeni olmalıdır bir veya daha fazla öğeleri <xref:System.AttributeTargets> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="1e238-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="1e238-110">Birden çok hedef türü, OR işleci, bu gibi birlikte bağlanabilir:</span><span class="sxs-lookup"><span data-stu-id="1e238-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```vb  
Imports System  
```  
  
```vb  
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>   
Class NewPropertyOrFieldAttribute  
    Inherits Attribute  
End Class  
```  
  
 <span data-ttu-id="1e238-111">Varsa `AllowMultiple` bağımsız değişkeni ayarlanır `true`, sonra elde edilen özniteliği, bu gibi tek bir varlık için birden çok kez uygulanabilir:</span><span class="sxs-lookup"><span data-stu-id="1e238-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
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
  
 <span data-ttu-id="1e238-112">Bu durumda `MultiUseAttr` art arda çünkü uygulanabilir `AllowMultiple` ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="1e238-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="1e238-113">Birden çok öznitelik uygulamak için gösterilen iki biçimi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="1e238-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="1e238-114">Varsa `Inherited` ayarlanır `false`, ardından öznitelik öznitelendirilen bir sınıftan türetilmiş sınıflar tarafından devralınır değil.</span><span class="sxs-lookup"><span data-stu-id="1e238-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="1e238-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="1e238-115">For example:</span></span>  
  
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
  
 <span data-ttu-id="1e238-116">Bu durumda `Attr1` uygulanmaz `DClass` devralma aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="1e238-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e238-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e238-117">Remarks</span></span>  
 <span data-ttu-id="1e238-118">`AttributeUsage` Özniteliği, bir tek kullanımlık özniteliğin birden çok kez aynı sınıfa uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="1e238-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="1e238-119">`AttributeUsage` için bir diğer addır <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1e238-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="1e238-120">Daha fazla bilgi için [erişme öznitelikleri kullanarak yansıma (Visual Basic) tarafından](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="1e238-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e238-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="1e238-121">Example</span></span>  
 <span data-ttu-id="1e238-122">Aşağıdaki örnek, etkisini gösterir `Inherited` ve `AllowMultiple` bağımsız değişkenleri `AttributeUsage` özniteliği ve nasıl bir sınıfa uygulanan özel öznitelikler listelenebilir.</span><span class="sxs-lookup"><span data-stu-id="1e238-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
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
  
## <a name="sample-output"></a><span data-ttu-id="1e238-123">Örnek Çıktı</span><span class="sxs-lookup"><span data-stu-id="1e238-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e238-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e238-124">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="1e238-125">Visual Basic programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1e238-125">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="1e238-126">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1e238-126">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="1e238-127">Yansıma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e238-127">Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="1e238-128">Öznitelikler (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e238-128">Attributes (Visual Basic)</span></span>](../../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="1e238-129">Özel öznitelikler (Visual Basic) oluşturma</span><span class="sxs-lookup"><span data-stu-id="1e238-129">Creating Custom Attributes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/creating-custom-attributes.md)
- [<span data-ttu-id="1e238-130">(Visual Basic) yansıma kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="1e238-130">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
