---
title: Yansıma (C#) kullanarak Özniteliklere Erişim
ms.date: 07/20/2015
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
ms.openlocfilehash: 990b6487e50bfb2d123c3871e5f85da063711d9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595498"
---
# <a name="accessing-attributes-by-using-reflection-c"></a><span data-ttu-id="d8cd7-102">Yansıma (C#) kullanarak Özniteliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="d8cd7-102">Accessing Attributes by Using Reflection (C#)</span></span>
<span data-ttu-id="d8cd7-103">Özel öznitelikleri tanımlayabilme ve bunları kaynak kodunuza yerleştirebilmeniz, bu bilgileri almanın ve bu bilgilerüzerinde hareket etmenin bir yolu olmadan çok az değerli olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-103">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="d8cd7-104">Yansımayı kullanarak, özel özniteliklerle tanımlanan bilgileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-104">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="d8cd7-105">Anahtar `GetCustomAttributes`yöntem, kaynak kodu özniteliklerinin çalışma zamanı eşdeğerleri olan nesnelerin bir dizi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-105">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="d8cd7-106">Bu yöntemin birkaç aşırı yüklenmiş sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-106">This method has several overloaded versions.</span></span> <span data-ttu-id="d8cd7-107">Daha fazla bilgi için bkz. <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-107">For more information, see <xref:System.Attribute>.</span></span>  
  
 <span data-ttu-id="d8cd7-108">Gibi bir öznitelik belirtimi:</span><span class="sxs-lookup"><span data-stu-id="d8cd7-108">An attribute specification such as:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 <span data-ttu-id="d8cd7-109">kavramsal olarak buna eşdeğerdir:</span><span class="sxs-lookup"><span data-stu-id="d8cd7-109">is conceptually equivalent to this:</span></span>  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 <span data-ttu-id="d8cd7-110">Ancak, öznitelikler için `SampleClass` sorgulandırılana kadar kod yürütülmez.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-110">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="d8cd7-111">`GetCustomAttributes` Çağrı, `SampleClass` bir `Author` nesnenin yukarıdaki gibi oluşturulup başharfe büretilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-111">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="d8cd7-112">Sınıfın başka öznitelikleri varsa, diğer öznitelik nesneleri de benzer şekilde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-112">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="d8cd7-113">`GetCustomAttributes`sonra `Author` nesne ve bir dizideki diğer öznitelik nesneleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-113">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="d8cd7-114">Daha sonra bu dizi üzerinde yineleyebilir, her dizi öğesinin türüne göre hangi özniteliklerin uygulandığını belirleyebilir ve öznitelik nesnelerinden bilgi ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-114">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8cd7-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="d8cd7-115">Example</span></span>  
 <span data-ttu-id="d8cd7-116">İşte tam bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-116">Here is a complete example.</span></span> <span data-ttu-id="d8cd7-117">Özel bir öznitelik tanımlanır, çeşitli varlıklara uygulanır ve yansıma yoluyla alınır.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-117">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d8cd7-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8cd7-118">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="d8cd7-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d8cd7-119">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="d8cd7-120">Özniteliklerde Depolanan Bilgileri Alma</span><span class="sxs-lookup"><span data-stu-id="d8cd7-120">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [<span data-ttu-id="d8cd7-121">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="d8cd7-121">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="d8cd7-122">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="d8cd7-122">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="d8cd7-123">Özel Öznitelikler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="d8cd7-123">Creating Custom Attributes (C#)</span></span>](./creating-custom-attributes.md)
