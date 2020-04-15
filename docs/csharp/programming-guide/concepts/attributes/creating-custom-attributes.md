---
title: Özel Öznitelikler oluşturma (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: ec959723c339a13a40fd62388421ceacb736dfca
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389553"
---
# <a name="creating-custom-attributes-c"></a>Özel Öznitelikler oluşturma (C#)
Doğrudan veya dolaylı <xref:System.Attribute>olarak türetilen ve meta verilerdeki öznitelik tanımlarını tanımlamayı hızlı ve kolay hale getiren bir öznitelik sınıfı tanımlayarak kendi özel özniteliklerinizi oluşturabilirsiniz. Türleri türü yazan programcının adıyla etiketlemek istediğinizi varsayalım. Özel `Author` bir öznitelik sınıfı tanımlayabilirsiniz:  
  
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
  
 Sınıf adı özniteliğin adıdır. `Author` Bu türetilmiştir `System.Attribute`, bu yüzden özel bir öznitelik sınıfıdır. Oluşturucunun parametreleri özel özniteliğin konumsal parametreleridir. Bu örnekte, `name` bir konumsal parametredir. Tüm ortak okuma-yazma alanları veya özellikleri parametreleri adlandırılır. Bu durumda, `version` yalnızca adlandırılmış parametredir. Özniteliği yalnızca `AttributeUsage` sınıf ve `Author` `struct` bildirimlerüzerinde geçerli kılmak için özniteliğin kullanımına dikkat edin.  
  
 Bu yeni özniteliği aşağıdaki gibi kullanabilirsiniz:  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 `AttributeUsage`özel bir öznitelik `AllowMultiple`tek kullanımlık veya çok kullanımlı yapabilirsiniz adlı bir parametre vardır. Aşağıdaki kod örneğinde, çok kullanımlı bir öznitelik oluşturulur.  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 Aşağıdaki kod örneğinde, aynı türden birden çok öznitelik bir sınıfa uygulanır.  
  
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
- [Yansıma (C#) kullanarak Özniteliklere Erişim](./accessing-attributes-by-using-reflection.md)
- [ÖznitelikKullanım (C#)](../../../language-reference/attributes/general.md)
