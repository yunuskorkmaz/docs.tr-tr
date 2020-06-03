---
title: Özel öznitelikler oluşturma (C#)
ms.date: 07/20/2015
ms.assetid: 500e1977-c6de-462d-abce-78a0eb1eda22
ms.openlocfilehash: ec959723c339a13a40fd62388421ceacb736dfca
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389553"
---
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="27a75-102">Özel öznitelikler oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="27a75-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="27a75-103">Doğrudan veya dolaylı olarak sınıfından türetilmiş bir sınıf olan öznitelik sınıfını tanımlayarak kendi özel öznitelerinizi oluşturabilirsiniz <xref:System.Attribute> . Bu, meta verilerde hızlı ve kolay bir şekilde öznitelik tanımları tanımlamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="27a75-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="27a75-104">Türleri, türünü yazan programcının adıyla etiketlemek istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="27a75-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="27a75-105">Özel bir `Author` öznitelik sınıfı tanımlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="27a75-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="27a75-106">Sınıf adı özniteliğin adıdır, `Author` .</span><span class="sxs-lookup"><span data-stu-id="27a75-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="27a75-107">Öğesinden türetilir `System.Attribute` , bu nedenle özel bir öznitelik sınıfıdır.</span><span class="sxs-lookup"><span data-stu-id="27a75-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="27a75-108">Oluşturucunun parametreleri özel özniteliğin konumsal parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="27a75-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="27a75-109">Bu örnekte, `name` bir Konumsal parametredir.</span><span class="sxs-lookup"><span data-stu-id="27a75-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="27a75-110">Tüm genel okuma/yazma alanları veya özellikleri parametreler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="27a75-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="27a75-111">Bu durumda, `version` tek adlandırılmış parametredir.</span><span class="sxs-lookup"><span data-stu-id="27a75-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="27a75-112">Özniteliği `AttributeUsage` `Author` yalnızca sınıf ve bildirimlerde geçerli hale getirmek için özniteliğinin kullanımını unutmayın `struct` .</span><span class="sxs-lookup"><span data-stu-id="27a75-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="27a75-113">Bu yeni özniteliği şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="27a75-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="27a75-114">`AttributeUsage`, `AllowMultiple` özel bir özniteliği tek kullanımı veya çok kullanımı yapabileceğiniz adlandırılmış bir parametreye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="27a75-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="27a75-115">Aşağıdaki kod örneğinde, Multiuse özniteliği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="27a75-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="27a75-116">Aşağıdaki kod örneğinde, aynı türde birden çok öznitelik bir sınıfa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="27a75-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
[Author("R. Koch", version = 1.2)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
    // R. Koch's code goes here...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="27a75-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27a75-117">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="27a75-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="27a75-118">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="27a75-119">Özel Öznitelikler Yazma</span><span class="sxs-lookup"><span data-stu-id="27a75-119">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="27a75-120">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="27a75-120">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="27a75-121">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="27a75-121">Attributes (C#)</span></span>](./index.md)
- [<span data-ttu-id="27a75-122">Yansıma kullanarak özniteliklere erişme (C#)</span><span class="sxs-lookup"><span data-stu-id="27a75-122">Accessing Attributes by Using Reflection (C#)</span></span>](./accessing-attributes-by-using-reflection.md)
- [<span data-ttu-id="27a75-123">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="27a75-123">AttributeUsage (C#)</span></span>](../../../language-reference/attributes/general.md)
