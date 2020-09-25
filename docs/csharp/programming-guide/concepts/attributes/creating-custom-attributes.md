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
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="ae58c-103">Özel öznitelikler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="ae58c-103">Creating Custom Attributes (C#)</span></span>

<span data-ttu-id="ae58c-104">Doğrudan veya dolaylı olarak sınıfından türetilmiş bir sınıf olan öznitelik sınıfını tanımlayarak kendi özel öznitelerinizi oluşturabilirsiniz <xref:System.Attribute> . Bu, meta verilerde hızlı ve kolay bir şekilde öznitelik tanımları tanımlamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae58c-104">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="ae58c-105">Türleri, türünü yazan programcının adıyla etiketlemek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="ae58c-105">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="ae58c-106">Özel bir `Author` öznitelik sınıfı tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ae58c-106">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="ae58c-107">Sınıf adı `AuthorAttribute` özniteliğin adı, ve `Author` `Attribute` sonektir.</span><span class="sxs-lookup"><span data-stu-id="ae58c-107">The class name `AuthorAttribute` is the attribute's name, `Author`, plus the `Attribute` suffix.</span></span> <span data-ttu-id="ae58c-108">Öğesinden türetilir `System.Attribute` , bu nedenle özel bir öznitelik sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="ae58c-108">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="ae58c-109">Oluşturucunun parametreleri özel özniteliğin konumsal parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="ae58c-109">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="ae58c-110">Bu örnekte, `name` bir Konumsal parametredir.</span><span class="sxs-lookup"><span data-stu-id="ae58c-110">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="ae58c-111">Tüm genel okuma/yazma alanları veya özellikleri parametreler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ae58c-111">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="ae58c-112">Bu durumda, `version` tek adlandırılmış parametredir.</span><span class="sxs-lookup"><span data-stu-id="ae58c-112">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="ae58c-113">Özniteliği `AttributeUsage` `Author` yalnızca sınıf ve bildirimlerde geçerli hale getirmek için özniteliğinin kullanımını unutmayın `struct` .</span><span class="sxs-lookup"><span data-stu-id="ae58c-113">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="ae58c-114">Bu yeni özniteliği şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ae58c-114">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="ae58c-115">`AttributeUsage` , `AllowMultiple` özel bir özniteliği tek kullanımı veya çok kullanımı yapabileceğiniz adlandırılmış bir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ae58c-115">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="ae58c-116">Aşağıdaki kod örneğinde, Multiuse özniteliği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ae58c-116">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class AuthorAttribute : System.Attribute  
```  
  
 <span data-ttu-id="ae58c-117">Aşağıdaki kod örneğinde, aynı türde birden çok öznitelik bir sınıfa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ae58c-117">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae58c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae58c-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="ae58c-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ae58c-119">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="ae58c-120">Özel Öznitelikler Yazma</span><span class="sxs-lookup"><span data-stu-id="ae58c-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="ae58c-121">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="ae58c-121">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="ae58c-122">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="ae58c-122">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="ae58c-123">Yansıma kullanarak özniteliklere erişme (C#)</span><span class="sxs-lookup"><span data-stu-id="ae58c-123">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="ae58c-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="ae58c-124">AttributeUsage (C#)</span></span>](../../../language-reference/attributes/general.md)
