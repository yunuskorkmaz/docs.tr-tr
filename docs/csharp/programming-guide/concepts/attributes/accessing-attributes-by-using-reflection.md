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
# <a name="accessing-attributes-by-using-reflection-c"></a>Yansıma (C#) kullanarak özniteliklere erişme
Özel öznitelikleri tanımlayabilir ve bunları kaynak kodunuza yerleştirebilirsiniz. Bu bilgiler, bu bilgileri alma ve üzerinde işlem yapmaya gerek kalmadan çok az değer elde edebilir. Yansıma kullanarak özel özniteliklerle tanımlanan bilgileri alabilirsiniz. Anahtar yöntemi, kaynak `GetCustomAttributes`kodu özniteliklerinin çalışma zamanı eşdeğerleri olan bir nesne dizisi döndüren ' dir. Bu yöntemin birkaç aşırı yüklü sürümü vardır. Daha fazla bilgi için bkz. <xref:System.Attribute>.  
  
 Şöyle bir öznitelik belirtimi:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 kavramsal olarak eşdeğerdir:  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 Ancak, kod öznitelikleri için sorgulanana kadar `SampleClass` yürütülmez. `Author` ' `GetCustomAttributes` Inçağrılması,birnesneninyukarıyaoluşturulmasınıvebaşlatılmasınısağlar.`SampleClass` Sınıfın başka öznitelikleri varsa, diğer öznitelik nesneleri benzer şekilde oluşturulur. `GetCustomAttributes`sonra `Author` nesneyi ve dizideki diğer öznitelik nesnelerini döndürür. Daha sonra bu dizinin üzerinde yineleyebilir, her bir dizi öğesinin türüne göre hangi özniteliklerin uygulandığını belirleyebilir ve öznitelik nesnelerinden bilgi ayıklayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıda bir örnek verilmiştir. Özel bir öznitelik tanımlanır, birkaç varlığa uygulanır ve yansıma aracılığıyla alınır.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- <xref:System.Attribute>
- [C# Programlama Kılavuzu](../../index.md)
- [Özniteliklerde Depolanan Bilgileri Alma](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- [Yansıma (C#)](../reflection.md)
- [Öznitelikler (C#)](./index.md)
- [Özel öznitelikler (C#) oluşturma](./creating-custom-attributes.md)
