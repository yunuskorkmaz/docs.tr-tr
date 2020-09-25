---
title: Yansıma kullanarak özniteliklere erişme (C#)
description: GetCustomAttributes metodunu kullanarak C# ' deki özel özniteliklerle tanımlanan bilgileri almak için yansımayı kullanın.
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 2ed4e844d1c98bcf265572f201bce6679fd642e9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202636"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="00573-103">Yansıma kullanarak özniteliklere erişme (C#)</span><span class="sxs-lookup"><span data-stu-id="00573-103">Accessing Attributes by Using Reflection (C#)</span></span>

<span data-ttu-id="00573-104">Özel öznitelikleri tanımlayabilir ve bunları kaynak kodunuza yerleştirebilirsiniz. Bu bilgiler, bu bilgileri alma ve üzerinde işlem yapmaya gerek kalmadan çok az değer elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="00573-104">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="00573-105">Yansıma kullanarak özel özniteliklerle tanımlanan bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00573-105">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="00573-106">Anahtar yöntemi `GetCustomAttributes` , kaynak kodu özniteliklerinin çalışma zamanı eşdeğerleri olan bir nesne dizisi döndüren ' dir.</span><span class="sxs-lookup"><span data-stu-id="00573-106">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="00573-107">Bu yöntemin birkaç aşırı yüklü sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="00573-107">This method has several overloaded versions.</span></span> <span data-ttu-id="00573-108">Daha fazla bilgi için bkz. <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="00573-108">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="00573-109">Şöyle bir öznitelik belirtimi:</span><span class="sxs-lookup"><span data-stu-id="00573-109">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="00573-110">kavramsal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="00573-110">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="00573-111">Ancak, kod `SampleClass` öznitelikleri için sorgulanana kadar yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="00573-111">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="00573-112">' In çağrılması `GetCustomAttributes` `SampleClass` `Author` , bir nesnenin yukarıya oluşturulmasını ve başlatılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="00573-112">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="00573-113">Sınıfın başka öznitelikleri varsa, diğer öznitelik nesneleri benzer şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="00573-113">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="00573-114">`GetCustomAttributes` sonra `Author` nesneyi ve dizideki diğer öznitelik nesnelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="00573-114">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="00573-115">Daha sonra bu dizinin üzerinde yineleyebilir, her bir dizi öğesinin türüne göre hangi özniteliklerin uygulandığını belirleyebilir ve öznitelik nesnelerinden bilgi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="00573-115">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00573-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="00573-116">Example</span></span>  

 <span data-ttu-id="00573-117">Aşağıda bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="00573-117">Here is a complete example.</span></span> <span data-ttu-id="00573-118">Özel bir öznitelik tanımlanır, birkaç varlığa uygulanır ve yansıma aracılığıyla alınır.</span><span class="sxs-lookup"><span data-stu-id="00573-118">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="00573-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00573-119">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="00573-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="00573-120">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="00573-121">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="00573-121">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="00573-122">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="00573-122">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="00573-123">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="00573-123">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="00573-124">Özel öznitelikler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="00573-124">Creating Custom Attributes (C#)</span></span>](./creating-custom-attributes.md)
