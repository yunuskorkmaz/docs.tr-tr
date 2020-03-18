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
# <a name="accessing-attributes-by-using-reflection-c"></a>Yansıma (C#) kullanarak Özniteliklere Erişim
Özel öznitelikleri tanımlayabilme ve bunları kaynak kodunuza yerleştirebilmeniz, bu bilgileri almanın ve bu bilgilerüzerinde hareket etmenin bir yolu olmadan çok az değerli olacaktır. Yansımayı kullanarak, özel özniteliklerle tanımlanan bilgileri alabilirsiniz. Anahtar `GetCustomAttributes`yöntem, kaynak kodu özniteliklerinin çalışma zamanı eşdeğerleri olan nesnelerin bir dizi döndürür. Bu yöntemin birkaç aşırı yüklenmiş sürümü vardır. Daha fazla bilgi için bkz. <xref:System.Attribute>.  
  
 Gibi bir öznitelik belirtimi:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 kavramsal olarak buna eşdeğerdir:  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 Ancak, öznitelikler için `SampleClass` sorgulandırılana kadar kod yürütülmez. `GetCustomAttributes` Çağrı, `SampleClass` bir `Author` nesnenin yukarıdaki gibi oluşturulup başharfe büretilmesine neden olur. Sınıfın başka öznitelikleri varsa, diğer öznitelik nesneleri de benzer şekilde oluşturulur. `GetCustomAttributes`sonra `Author` nesne ve bir dizideki diğer öznitelik nesneleri döndürür. Daha sonra bu dizi üzerinde yineleyebilir, her dizi öğesinin türüne göre hangi özniteliklerin uygulandığını belirleyebilir ve öznitelik nesnelerinden bilgi ayıklayabilirsiniz.  
  
## <a name="example"></a>Örnek  
 İşte tam bir örnektir. Özel bir öznitelik tanımlanır, çeşitli varlıklara uygulanır ve yansıma yoluyla alınır.  
  
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
- [Özel Öznitelikler oluşturma (C#)](./creating-custom-attributes.md)
