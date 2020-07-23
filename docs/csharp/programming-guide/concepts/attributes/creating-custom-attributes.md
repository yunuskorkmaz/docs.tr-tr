---
title: Özel öznitelikler oluşturma (C#)
description: Öznitelik sınıfından türetilen bir öznitelik sınıfını tanımlayarak C# ' de özel öznitelikler oluşturmayı öğrenin.
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: 7d6f98620388af8715652dcbcfe78366952b853d
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925091"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="df305-103">Özel öznitelikler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="df305-103">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="df305-104">Doğrudan veya dolaylı olarak sınıfından türetilmiş bir sınıf olan öznitelik sınıfını tanımlayarak kendi özel öznitelerinizi oluşturabilirsiniz <xref:System.Attribute> . Bu, meta verilerde hızlı ve kolay bir şekilde öznitelik tanımları tanımlamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="df305-104">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="df305-105">Türleri, türünü yazan programcının adıyla etiketlemek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="df305-105">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="df305-106">Özel bir `Author` öznitelik sınıfı tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df305-106">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="df305-107">Sınıf adı `AuthorAttribute` özniteliğin adı, ve `Author` `Attribute` sonektir.</span><span class="sxs-lookup"><span data-stu-id="df305-107">The class name `AuthorAttribute` is the attribute's name, `Author`, plus the `Attribute` suffix.</span></span> <span data-ttu-id="df305-108">Öğesinden türetilir `System.Attribute` , bu nedenle özel bir öznitelik sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="df305-108">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="df305-109">Oluşturucunun parametreleri özel özniteliğin konumsal parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="df305-109">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="df305-110">Bu örnekte, `name` bir Konumsal parametredir.</span><span class="sxs-lookup"><span data-stu-id="df305-110">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="df305-111">Tüm genel okuma/yazma alanları veya özellikleri parametreler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="df305-111">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="df305-112">Bu durumda, `version` tek adlandırılmış parametredir.</span><span class="sxs-lookup"><span data-stu-id="df305-112">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="df305-113">Özniteliği `AttributeUsage` `Author` yalnızca sınıf ve bildirimlerde geçerli hale getirmek için özniteliğinin kullanımını unutmayın `struct` .</span><span class="sxs-lookup"><span data-stu-id="df305-113">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="df305-114">Bu yeni özniteliği şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="df305-114">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="df305-115">`AttributeUsage`, `AllowMultiple` özel bir özniteliği tek kullanımı veya çok kullanımı yapabileceğiniz adlandırılmış bir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="df305-115">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="df305-116">Aşağıdaki kod örneğinde, Multiuse özniteliği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="df305-116">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class AuthorAttribute : System.Attribute  
```  
  
 <span data-ttu-id="df305-117">Aşağıdaki kod örneğinde, aynı türde birden çok öznitelik bir sınıfa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="df305-117">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="df305-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df305-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="df305-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="df305-119">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="df305-120">Özel Öznitelikler Yazma</span><span class="sxs-lookup"><span data-stu-id="df305-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="df305-121">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="df305-121">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="df305-122">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="df305-122">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="df305-123">Yansıma kullanarak özniteliklere erişme (C#)</span><span class="sxs-lookup"><span data-stu-id="df305-123">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="df305-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="df305-124">AttributeUsage (C#)</span></span>](../../../language-reference/attributes/general.md)
