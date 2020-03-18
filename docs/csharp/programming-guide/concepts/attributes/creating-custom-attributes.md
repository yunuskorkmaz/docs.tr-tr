---
title: Özel Öznitelikler oluşturma (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: c0f25adf0d562b659edaa8f36e72332fd0c1ee7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69595411"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="ba8d6-102">Özel Öznitelikler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="ba8d6-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="ba8d6-103">Doğrudan veya dolaylı <xref:System.Attribute>olarak türetilen ve meta verilerdeki öznitelik tanımlarını tanımlamayı hızlı ve kolay hale getiren bir öznitelik sınıfı tanımlayarak kendi özel özniteliklerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ba8d6-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="ba8d6-104">Türleri türü yazan programcının adıyla etiketlemek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="ba8d6-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="ba8d6-105">Özel `Author` bir öznitelik sınıfı tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba8d6-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="ba8d6-106">Sınıf adı özniteliğin adıdır. `Author`</span><span class="sxs-lookup"><span data-stu-id="ba8d6-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="ba8d6-107">Bu türetilmiştir `System.Attribute`, bu yüzden özel bir öznitelik sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="ba8d6-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="ba8d6-108">Oluşturucunun parametreleri özel özniteliğin konumsal parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="ba8d6-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="ba8d6-109">Bu örnekte, `name` bir konumsal parametredir.</span><span class="sxs-lookup"><span data-stu-id="ba8d6-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="ba8d6-110">Tüm ortak okuma-yazma alanları veya özellikleri parametreleri adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ba8d6-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="ba8d6-111">Bu durumda, `version` yalnızca adlandırılmış parametredir.</span><span class="sxs-lookup"><span data-stu-id="ba8d6-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="ba8d6-112">Özniteliği yalnızca `AttributeUsage` sınıf ve `Author` `struct` bildirimlerüzerinde geçerli kılmak için özniteliğin kullanımına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="ba8d6-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="ba8d6-113">Bu yeni özniteliği aşağıdaki gibi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ba8d6-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="ba8d6-114">`AttributeUsage`özel bir öznitelik `AllowMultiple`tek kullanımlık veya çok kullanımlı yapabilirsiniz adlı bir parametre vardır.</span><span class="sxs-lookup"><span data-stu-id="ba8d6-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="ba8d6-115">Aşağıdaki kod örneğinde, çok kullanımlı bir öznitelik oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ba8d6-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="ba8d6-116">Aşağıdaki kod örneğinde, aynı türden birden çok öznitelik bir sınıfa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ba8d6-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba8d6-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba8d6-117">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="ba8d6-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ba8d6-118">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="ba8d6-119">Özel Öznitelikler Yazma</span><span class="sxs-lookup"><span data-stu-id="ba8d6-119">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="ba8d6-120">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="ba8d6-120">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="ba8d6-121">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="ba8d6-121">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="ba8d6-122">Yansıma (C#) kullanarak Özniteliklere Erişim</span><span class="sxs-lookup"><span data-stu-id="ba8d6-122">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="ba8d6-123">ÖznitelikKullanım (C#)</span><span class="sxs-lookup"><span data-stu-id="ba8d6-123">AttributeUsage (C#)</span></span>](./attributeusage.md)
