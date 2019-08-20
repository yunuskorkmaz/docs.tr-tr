---
title: Özel öznitelikler (C#) oluşturma
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: c0f25adf0d562b659edaa8f36e72332fd0c1ee7e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595411"
---
# <a name="creating-custom-attributes-c"></a>Özel öznitelikler (C#) oluşturma
Doğrudan veya dolaylı <xref:System.Attribute>olarak sınıfından türetilmiş bir sınıf olan öznitelik sınıfını tanımlayarak kendi özel öznitelerinizi oluşturabilirsiniz. Bu, meta verilerde hızlı ve kolay bir şekilde öznitelik tanımları tanımlamayı sağlar. Türleri, türünü yazan programcının adıyla etiketlemek istediğinizi varsayalım. Özel `Author` bir öznitelik sınıfı tanımlayabilirsiniz:  
  
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
  
 Sınıf adı özniteliğin adıdır, `Author`. Öğesinden `System.Attribute`türetilir, bu nedenle özel bir öznitelik sınıfıdır. Oluşturucunun parametreleri özel özniteliğin konumsal parametreleridir. Bu örnekte, `name` bir Konumsal parametredir. Tüm genel okuma/yazma alanları veya özellikleri parametreler olarak adlandırılır. Bu durumda, `version` tek adlandırılmış parametredir. Özniteliği yalnızca sınıf ve `AttributeUsage` `struct` bildirimlerde geçerli `Author` hale getirmek için özniteliğinin kullanımını unutmayın.  
  
 Bu yeni özniteliği şu şekilde kullanabilirsiniz:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage`, özel bir özniteliği tek `AllowMultiple`kullanımı veya çok kullanımı yapabileceğiniz adlandırılmış bir parametreye sahiptir. Aşağıdaki kod örneğinde, Multiuse özniteliği oluşturulur.  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 Aşağıdaki kod örneğinde, aynı türde birden çok öznitelik bir sınıfa uygulanır.  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection>
- [C# Programlama Kılavuzu](../../index.md)
- [Özel Öznitelikler Yazma](../../../../standard/attributes/writing-custom-attributes.md)
- [Yansıma (C#)](../reflection.md)
- [Öznitelikler (C#)](./index.md)
- [Yansıma (C#) kullanarak özniteliklere erişme](./accessing-attributes-by-using-reflection.md)
- [AttributeUsage (C#)](./attributeusage.md)
