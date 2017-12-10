---
title: AttributeUsage (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 22c45568-9a6a-4c2f-8480-f38c1caa0a99
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e9351ee10b523145ace1249bf17388da0cdba277
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="attributeusage-c"></a><span data-ttu-id="e9f98-102">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="e9f98-102">AttributeUsage (C#)</span></span>
<span data-ttu-id="e9f98-103">Özel bir öznitelik sınıfı nasıl kullanılabileceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="e9f98-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="e9f98-104">`AttributeUsage`Yeni öznitelik nasıl uygulanabilir denetlemek için özel öznitelik tanımlarını uygulanabilir bir özniteliktir.</span><span class="sxs-lookup"><span data-stu-id="e9f98-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="e9f98-105">Varsayılan ayarları açıkça uygulandığında şöyle:</span><span class="sxs-lookup"><span data-stu-id="e9f98-105">The default settings look like this when applied explicitly:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All,  
                   AllowMultiple = false,  
                   Inherited = true)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="e9f98-106">Bu örnekte, `NewAttribute` sınıfı olabilir herhangi bir öznitelik mümkün kod varlık, ancak yalnızca bir kez her varlık için uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e9f98-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="e9f98-107">Temel bir sınıfa uygulandığında türetilmiş sınıflar tarafından devralınır.</span><span class="sxs-lookup"><span data-stu-id="e9f98-107">It is inherited by derived classes when applied to a base class.</span></span>  
  
 <span data-ttu-id="e9f98-108">`AllowMultiple` Ve `Inherited` değişkenleridir isteğe bağlı, bu kodu aynı etkiye sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e9f98-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.All)]  
class NewAttribute : System.Attribute { }  
```  
  
 <span data-ttu-id="e9f98-109">İlk `AttributeUsage` bağımsız değişkeni, bir veya daha fazla öğesi olmalıdır <xref:System.AttributeTargets> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="e9f98-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="e9f98-110">Birden çok hedef türü veya işlecini şöyle birlikte bağlanabilir:</span><span class="sxs-lookup"><span data-stu-id="e9f98-110">Multiple target types can be linked together with the OR operator, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]  
class NewPropertyOrFieldAttribute : Attribute { }  
```  
  
 <span data-ttu-id="e9f98-111">Varsa `AllowMultiple` bağımsız değişkeni olarak ayarlanmış `true`, sonuçta elde edilen özniteliği bu gibi tek bir varlık için birden çok kez uygulanabilir sonra:</span><span class="sxs-lookup"><span data-stu-id="e9f98-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, AllowMultiple = true)]  
class MultiUseAttr : Attribute { }  
  
[MultiUseAttr]  
[MultiUseAttr]  
class Class1 { }  
  
[MultiUseAttr, MultiUseAttr]  
class Class2 { }  
```  
  
 <span data-ttu-id="e9f98-112">Bu durumda `MultiUseAttr` art arda çünkü uygulanabilir `AllowMultiple` ayarlanır `true`.</span><span class="sxs-lookup"><span data-stu-id="e9f98-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="e9f98-113">Birden çok öznitelik uygulamak için gösterilen iki biçimi geçerli değil.</span><span class="sxs-lookup"><span data-stu-id="e9f98-113">Both formats shown for applying multiple attributes are valid.</span></span>  
  
 <span data-ttu-id="e9f98-114">Varsa `Inherited` ayarlanır `false`, öznitelik öznitelik sınıfından türetilen sınıflar tarafından devralınır değil sonra.</span><span class="sxs-lookup"><span data-stu-id="e9f98-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="e9f98-115">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e9f98-115">For example:</span></span>  
  
```csharp  
using System;  

[AttributeUsage(AttributeTargets.Class, Inherited = false)]  
class Attr1 : Attribute { }  
  
[Attr1]  
class BClass { }  
  
class DClass : BClass { }  
```  
  
 <span data-ttu-id="e9f98-116">Bu durumda `Attr1` uygulanmaz `DClass` devralma aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="e9f98-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9f98-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e9f98-117">Remarks</span></span>  
 <span data-ttu-id="e9f98-118">`AttributeUsage` Özniteliktir tek kullanımlık özniteliği--birden çok kez aynı sınıfa uygulanamaz.</span><span class="sxs-lookup"><span data-stu-id="e9f98-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="e9f98-119">`AttributeUsage`bir diğer adı için <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e9f98-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="e9f98-120">Daha fazla bilgi için bkz: [yansıma (C#) kullanarak erişme özniteliklerle](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="e9f98-120">For more information, see [Accessing Attributes by Using Reflection (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9f98-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9f98-121">Example</span></span>  
 <span data-ttu-id="e9f98-122">Aşağıdaki örnek, etkisini gösterir `Inherited` ve `AllowMultiple` bağımsız değişkenleri `AttributeUsage` özniteliğini ve bir sınıfa uygulanan özel öznitelikler nasıl listelenebilir.</span><span class="sxs-lookup"><span data-stu-id="e9f98-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>  
  
```csharp  
using System;  

// Create some custom attributes:  
[AttributeUsage(System.AttributeTargets.Class, Inherited = false)]  
class A1 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class)]  
class A2 : System.Attribute { }  
  
[AttributeUsage(System.AttributeTargets.Class, AllowMultiple = true)]  
class A3 : System.Attribute { }  
  
// Apply custom attributes to classes:  
[A1, A2]  
class BaseClass { }  
  
[A3, A3]  
class DerivedClass : BaseClass { }  
  
public class TestAttributeUsage  
{  
    static void Main()  
    {  
        BaseClass b = new BaseClass();  
        DerivedClass d = new DerivedClass();  
  
        // Display custom attributes for each class.  
        Console.WriteLine("Attributes on Base Class:");  
        object[] attrs = b.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
  
        Console.WriteLine("Attributes on Derived Class:");  
        attrs = d.GetType().GetCustomAttributes(true);  
        foreach (Attribute attr in attrs)  
        {  
            Console.WriteLine(attr);  
        }  
    }  
}  
```  
  
## <a name="sample-output"></a><span data-ttu-id="e9f98-123">Örnek Çıktı</span><span class="sxs-lookup"><span data-stu-id="e9f98-123">Sample Output</span></span>  
  
```  
Attributes on Base Class:  
A1  
A2  
Attributes on Derived Class:  
A3  
A3  
A2  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9f98-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e9f98-124">See Also</span></span>  
 <xref:System.Attribute>  
 <xref:System.Reflection>  
 [<span data-ttu-id="e9f98-125">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e9f98-125">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e9f98-126">Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="e9f98-126">Attributes</span></span>](../../../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="e9f98-127">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="e9f98-127">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="e9f98-128">Öznitelikleri</span><span class="sxs-lookup"><span data-stu-id="e9f98-128">Attributes</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="e9f98-129">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="e9f98-129">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
 [<span data-ttu-id="e9f98-130">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="e9f98-130">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)
