---
title: "Özel öznitelikler (C#) oluşturma"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 38bdedb352cc79f7a4cc3d08eb6138e7d994514b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-custom-attributes-c"></a>Özel öznitelikler (C#) oluşturma
Doğrudan veya dolaylı olarak türeyen bir sınıf bir öznitelik sınıfı tanımlayarak, kendi özel öznitelikler oluşturabilirsiniz <xref:System.Attribute>, hızlı ve kolay meta verilerde özniteliği tanımlarını tanımlayan hangi yapar. Etiket türleri türü yazan programcı için adıyla istediğinizi varsayalım. Özel bir tanımlayabilir `Author` öznitelik sınıfı:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class Author : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public Author(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 Sınıf adı özniteliğin adıdır `Author`. Öğesinden türetilen `System.Attribute`özel bir öznitelik sınıfı gelir. Oluşturucusu ait, özel özniteliğin konumsal parametreler parametreleridir. Bu örnekte, `name` konumsal bir parametredir. Herhangi bir genel okuma-yazma alanlar veya özellikler parametreleri olarak adlandırılır. Bu durumda, `version` tek parametresi olarak adlandırılır. Kullanımına dikkat edin `AttributeUsage` yapmak için öznitelik `Author` özniteliği yalnızca sınıfında geçerli ve `struct` bildirimleri.  
  
 Bu yeni öznitelik aşağıdaki gibi kullanabilirsiniz:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage`adlandırılmış bir parametre içeriyor `AllowMultiple`, özel bir öznitelik tek kullanımlık veya multiuse yapabileceğiniz ile. Aşağıdaki kod örneğinde multiuse özniteliği oluşturulur.  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 Aşağıdaki kod örneğinde aynı türde birden çok öznitelik bir sınıfa uygulanır.  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
> [!NOTE]
>  Öznitelik sınıfı bir özellik varsa, bu özelliği oku-yaz olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection>  
 [C# programlama kılavuzu](../../../../csharp/programming-guide/index.md)  
 [Özel öznitelikler yazma](../../../../standard/attributes/writing-custom-attributes.md)  
 [Yansıma (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
 [Öznitelikler (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [Yansıma (C#) kullanarak özniteliklere erişme](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
