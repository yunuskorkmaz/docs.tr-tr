---
title: "Yansıma (C#) kullanarak özniteliklere erişme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: dce3a696-4ceb-489a-b5e4-322a83052f18
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 162bdd6b968def391a2f3413596ee8c2a8b01cc3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-attributes-by-using-reflection-c"></a>Yansıma (C#) kullanarak özniteliklere erişme
Özel öznitelikler tanımlayın ve bunları kaynak kodunda yerleştirmek olgu ve bu bilgileri alma üzerinde çalışan herhangi bir şekilde olmadan az değerinin olacaktır. Yansıma kullanarak özel öznitelikler içeren tanımlandı bilgi alabilirsiniz. Anahtar yöntemi `GetCustomAttributes`, kaynak kodu özniteliklerinin çalışma zamanı eşdeğerleri olan nesneler dizisi döndürür. Bu yöntem, birden fazla aşırı yüklenmiş sürümlerini içerir. Daha fazla bilgi için bkz. <xref:System.Attribute>.  
  
 Öznitelik belirtimi gibi:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
```  
  
 Bunun için kavramsal olarak eşdeğerdir:  
  
```csharp  
Author anonymousAuthorObject = new Author("P. Ackerman");  
anonymousAuthorObject.version = 1.1;  
```  
  
 Bununla birlikte, kod kadar yürütülmez `SampleClass` öznitelikler için sorgulanır. Çağırma `GetCustomAttributes` üzerinde `SampleClass` neden olan bir `Author` nesnesi oluşturulur ve yukarıdaki olarak başlatıldı. Sınıfın diğer öznitelikleri varsa, diğer öznitelik nesneleri benzer şekilde oluşturulur. `GetCustomAttributes`ardından döndürür `Author` nesne ve bir dizi diğer öznitelik nesneleri. Bu dizi yineleme öznitelikleri her dizi öğesi türüne bağlı olarak uygulanan belirlemek ve öznitelik nesnelerden bilgi ayıklamak.  
  
## <a name="example"></a>Örnek  
 Burada, tam bir örnek verilmiştir. Özel bir öznitelik tanımlı, birkaç varlıklara uygulanan ve yansıma alınır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection>  
 <xref:System.Attribute>  
 [C# programlama kılavuzu](../../../../csharp/programming-guide/index.md)  
 [Özniteliklerde depolanan bilgileri alma](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)  
 [Yansıma (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Öznitelikler (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Özel öznitelikler (C#) oluşturma](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)
