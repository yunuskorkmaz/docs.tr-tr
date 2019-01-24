---
title: Yansıma (C#) kullanarak özniteliklere erişme
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: f7c7b89be13022471f4e17bcb6ed9a90bcbc1c54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660417"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="2a12f-102">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="2a12f-102">Accessing Attributes by Using Reflection (C#)</span></span>
<span data-ttu-id="2a12f-103">Özel öznitelikler tanımlamak ve bunları kaynak kodunuzu getirin olgu üzerinde çalışan ve bu bilgileri alınırken bir şekilde olmadan küçük değer olacaktır.</span><span class="sxs-lookup"><span data-stu-id="2a12f-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="2a12f-104">Yansıma kullanarak özel öznitelik tanımlandı bilgi alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a12f-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="2a12f-105">Anahtar yöntemi `GetCustomAttributes`, kaynak kod özniteliklerini çalışma zamanı eşdeğerleri olan nesneler dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="2a12f-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="2a12f-106">Bu yöntem, birden fazla aşırı yüklenmiş sürümleri vardır.</span><span class="sxs-lookup"><span data-stu-id="2a12f-106">This method has several overloaded versions.</span></span> <span data-ttu-id="2a12f-107">Daha fazla bilgi için bkz. <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="2a12f-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="2a12f-108">Bir öznitelik belirtimi gibi:</span><span class="sxs-lookup"><span data-stu-id="2a12f-108">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="2a12f-109">Bunun için kavramsal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="2a12f-109">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="2a12f-110">Ancak, kod kadar yürütülmez `SampleClass` öznitelikleri için sorgulanır.</span><span class="sxs-lookup"><span data-stu-id="2a12f-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="2a12f-111">Çağırma `GetCustomAttributes` üzerinde `SampleClass` neden olan bir `Author` nesne oluşturulur ve yukarıdaki gibi başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="2a12f-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="2a12f-112">Sınıfın diğer öznitelikleri varsa, diğer öznitelik nesneleri benzer şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2a12f-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="2a12f-113">`GetCustomAttributes` ardından döndürür `Author` ve diğer öznitelik nesneleri bir dizideki nesne.</span><span class="sxs-lookup"><span data-stu-id="2a12f-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="2a12f-114">Bu dizi yineleme hangi özniteliklerin her dizi öğesi türüne bağlı olarak uygulanan belirlemek ve öznitelik nesnelerden bilgiler ayıklayın.</span><span class="sxs-lookup"><span data-stu-id="2a12f-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a12f-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a12f-115">Example</span></span>  
 <span data-ttu-id="2a12f-116">Tam bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2a12f-116">Here is a complete example.</span></span> <span data-ttu-id="2a12f-117">Özel bir öznitelik tanımlı, birden fazla varlıklarına uygulanan ve yansıma alınır.</span><span class="sxs-lookup"><span data-stu-id="2a12f-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
```csharp  
// Multiuse attribute.  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // Multiuse attribute.  
]  
public class Author : System.Attribute  
{  
    string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
  
        // Default value.  
        version = 1.0;  
    }  
  
    public string GetName()  
    {  
        return name;  
    }  
}  
  
// Class with the Author attribute.  
[Author("P. Ackerman")]  
public class FirstClass  
{  
    // ...  
}  
  
// Class without the Author attribute.  
public class SecondClass  
{  
    // ...  
}  
  
// Class with multiple Author attributes.  
[Author("P. Ackerman"), Author("R. Koch", version = 2.0)]  
public class ThirdClass  
{  
    // ...  
}  
  
class TestAuthorAttribute  
{  
    static void Test()  
    {  
        PrintAuthorInfo(typeof(FirstClass));  
        PrintAuthorInfo(typeof(SecondClass));  
        PrintAuthorInfo(typeof(ThirdClass));  
    }  
  
    private static void PrintAuthorInfo(System.Type t)  
    {  
        System.Console.WriteLine("Author information for {0}", t);  
  
        // Using reflection.  
        System.Attribute[] attrs = System.Attribute.GetCustomAttributes(t);  // Reflection.  
  
        // Displaying output.  
        foreach (System.Attribute attr in attrs)  
        {  
            if (attr is Author)  
            {  
                Author a = (Author)attr;  
                System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version);  
            }  
        }  
    }  
}  
/* Output:  
    Author information for FirstClass  
       P. Ackerman, version 1.00  
    Author information for SecondClass  
    Author information for ThirdClass  
       R. Koch, version 2.00  
       P. Ackerman, version 1.00  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a12f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a12f-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="2a12f-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2a12f-119">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2a12f-120">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="2a12f-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="2a12f-121">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="2a12f-121">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)
- [<span data-ttu-id="2a12f-122">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="2a12f-122">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="2a12f-123">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="2a12f-123">Creating Custom Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)
