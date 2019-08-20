---
title: Yansıma (C#) kullanarak özniteliklere erişme
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 990b6487e50bfb2d123c3871e5f85da063711d9e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595498"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="6f920-102">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="6f920-102">Accessing Attributes by Using Reflection (C#)</span></span>
<span data-ttu-id="6f920-103">Özel öznitelikleri tanımlayabilir ve bunları kaynak kodunuza yerleştirebilirsiniz. Bu bilgiler, bu bilgileri alma ve üzerinde işlem yapmaya gerek kalmadan çok az değer elde edebilir.</span><span class="sxs-lookup"><span data-stu-id="6f920-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="6f920-104">Yansıma kullanarak özel özniteliklerle tanımlanan bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f920-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="6f920-105">Anahtar yöntemi, kaynak `GetCustomAttributes`kodu özniteliklerinin çalışma zamanı eşdeğerleri olan bir nesne dizisi döndüren ' dir.</span><span class="sxs-lookup"><span data-stu-id="6f920-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="6f920-106">Bu yöntemin birkaç aşırı yüklü sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="6f920-106">This method has several overloaded versions.</span></span> <span data-ttu-id="6f920-107">Daha fazla bilgi için bkz. <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="6f920-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="6f920-108">Şöyle bir öznitelik belirtimi:</span><span class="sxs-lookup"><span data-stu-id="6f920-108">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="6f920-109">kavramsal olarak eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="6f920-109">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="6f920-110">Ancak, kod öznitelikleri için sorgulanana kadar `SampleClass` yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="6f920-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="6f920-111">`Author` ' `GetCustomAttributes` Inçağrılması,birnesneninyukarıyaoluşturulmasınıvebaşlatılmasınısağlar.`SampleClass`</span><span class="sxs-lookup"><span data-stu-id="6f920-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="6f920-112">Sınıfın başka öznitelikleri varsa, diğer öznitelik nesneleri benzer şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6f920-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="6f920-113">`GetCustomAttributes`sonra `Author` nesneyi ve dizideki diğer öznitelik nesnelerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f920-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="6f920-114">Daha sonra bu dizinin üzerinde yineleyebilir, her bir dizi öğesinin türüne göre hangi özniteliklerin uygulandığını belirleyebilir ve öznitelik nesnelerinden bilgi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f920-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f920-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="6f920-115">Example</span></span>  
 <span data-ttu-id="6f920-116">Aşağıda bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f920-116">Here is a complete example.</span></span> <span data-ttu-id="6f920-117">Özel bir öznitelik tanımlanır, birkaç varlığa uygulanır ve yansıma aracılığıyla alınır.</span><span class="sxs-lookup"><span data-stu-id="6f920-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f920-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f920-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="6f920-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6f920-119">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="6f920-120">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="6f920-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="6f920-121">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="6f920-121">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="6f920-122">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="6f920-122">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="6f920-123">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="6f920-123">Creating Custom Attributes (C#)</span></span>](./creating-custom-attributes.md)
