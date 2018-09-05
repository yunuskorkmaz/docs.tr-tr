---
title: Özel öznitelikler (C#) oluşturma
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 5a846771eb26e3760e3f47458b862356f4da1ae6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503712"
---
# <a name="creating-custom-attributes-c"></a>Özel öznitelikler (C#) oluşturma
Bir öznitelik sınıfı doğrudan veya dolaylı olarak türetildiği bir sınıf tanımlayarak kendi özel öznitelikler oluşturabilir <xref:System.Attribute>, hızlı ve kolay meta veri özniteliği tanımlarını tanımlayan hale getirir. Etiket türlerine türü yazan Programcı adıyla istediğinizi varsayalım. Özel bir tanımlayabilir `Author` öznitelik sınıfı:  
  
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
  
 Özniteliğin adı, sınıf adıdır `Author`. Öğesinden türetilen `System.Attribute`, bir özel öznitelik sınıfı olduğu için. Özel özniteliğin konumsal parametreler oluşturucunun parametrelerdir. Bu örnekte, `name` konumsal bir parametredir. Parametreleri, tüm genel okuma-yazma alanlar ve Özellikler adlandırılır. Bu durumda, `version` tek parametre olarak adlandırılır. Kullanımına dikkat edin `AttributeUsage` yapmak için özniteliği `Author` özniteliği yalnızca sınıf geçerli ve `struct` bildirimleri.  
  
 Bu yeni bir öznitelik şu şekilde kullanabilirsiniz:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage` adlandırılmış bir parametreye sahip `AllowMultiple`, özel bir öznitelik tek kullanımlık veya multiuse yapabileceğiniz ile. Aşağıdaki kod örneğinde multiuse özniteliği oluşturulur.  
  
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
>  Öznitelik sınıfı bir özellik içeriyorsa, bu özellik salt okunur olmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Reflection>  
- [C# Programlama Kılavuzu](../../../../csharp/programming-guide/index.md)  
- [Özel Öznitelikler Yazma](../../../../standard/attributes/writing-custom-attributes.md)  
- [Yansıma (C#)](../../../../csharp/programming-guide/concepts/reflection.md)  
- [Öznitelikler (C#)](../../../../csharp/programming-guide/concepts/attributes/index.md)  
- [Yansıma (C#) kullanarak özniteliklere erişme](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
- [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
