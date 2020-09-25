---
title: Özel öznitelikler oluşturma (C#)
description: Öznitelik sınıfından türetilen bir öznitelik sınıfını tanımlayarak C# ' de özel öznitelikler oluşturmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 6946b707134b2bdbc245b8786f144517a5870440
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202611"
---
# <a name="creating-custom-attributes-c"></a>Özel öznitelikler oluşturma (C#)

Doğrudan veya dolaylı olarak sınıfından türetilmiş bir sınıf olan öznitelik sınıfını tanımlayarak kendi özel öznitelerinizi oluşturabilirsiniz <xref:System.Attribute> . Bu, meta verilerde hızlı ve kolay bir şekilde öznitelik tanımları tanımlamayı sağlar. Türleri, türünü yazan programcının adıyla etiketlemek istediğinizi varsayalım. Özel bir `Author` öznitelik sınıfı tanımlayabilirsiniz:  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct)  
]  
public class AuthorAttribute : System.Attribute  
{  
    private string name;  
    public double version;  
  
    public AuthorAttribute(string name)  
    {  
        this.name = name;  
        version = 1.0;  
    }  
}  
```  
  
 Sınıf adı `AuthorAttribute` özniteliğin adı, ve `Author` `Attribute` sonektir. Öğesinden türetilir `System.Attribute` , bu nedenle özel bir öznitelik sınıfıdır. Oluşturucunun parametreleri özel özniteliğin konumsal parametreleridir. Bu örnekte, `name` bir Konumsal parametredir. Tüm genel okuma/yazma alanları veya özellikleri parametreler olarak adlandırılır. Bu durumda, `version` tek adlandırılmış parametredir. Özniteliği `AttributeUsage` `Author` yalnızca sınıf ve bildirimlerde geçerli hale getirmek için özniteliğinin kullanımını unutmayın `struct` .  
  
 Bu yeni özniteliği şu şekilde kullanabilirsiniz:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage` , `AllowMultiple` özel bir özniteliği tek kullanımı veya çok kullanımı yapabileceğiniz adlandırılmış bir parametreye sahiptir. Aşağıdaki kod örneğinde, Multiuse özniteliği oluşturulur.  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class AuthorAttribute : System.Attribute  
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
- [Yansıma kullanarak özniteliklere erişme (C#)](./accessing-attributes-by-using-reflection.md)
- [AttributeUsage (C#)](../../../language-reference/attributes/general.md)
