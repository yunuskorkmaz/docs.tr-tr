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
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="155e4-102">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="155e4-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="155e4-103">Bir öznitelik sınıfı doğrudan veya dolaylı olarak türetildiği bir sınıf tanımlayarak kendi özel öznitelikler oluşturabilir <xref:System.Attribute>, hızlı ve kolay meta veri özniteliği tanımlarını tanımlayan hale getirir.</span><span class="sxs-lookup"><span data-stu-id="155e4-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="155e4-104">Etiket türlerine türü yazan Programcı adıyla istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="155e4-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="155e4-105">Özel bir tanımlayabilir `Author` öznitelik sınıfı:</span><span class="sxs-lookup"><span data-stu-id="155e4-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="155e4-106">Özniteliğin adı, sınıf adıdır `Author`.</span><span class="sxs-lookup"><span data-stu-id="155e4-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="155e4-107">Öğesinden türetilen `System.Attribute`, bir özel öznitelik sınıfı olduğu için.</span><span class="sxs-lookup"><span data-stu-id="155e4-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="155e4-108">Özel özniteliğin konumsal parametreler oluşturucunun parametrelerdir.</span><span class="sxs-lookup"><span data-stu-id="155e4-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="155e4-109">Bu örnekte, `name` konumsal bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="155e4-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="155e4-110">Parametreleri, tüm genel okuma-yazma alanlar ve Özellikler adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="155e4-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="155e4-111">Bu durumda, `version` tek parametre olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="155e4-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="155e4-112">Kullanımına dikkat edin `AttributeUsage` yapmak için özniteliği `Author` özniteliği yalnızca sınıf geçerli ve `struct` bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="155e4-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="155e4-113">Bu yeni bir öznitelik şu şekilde kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="155e4-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="155e4-114">`AttributeUsage` adlandırılmış bir parametreye sahip `AllowMultiple`, özel bir öznitelik tek kullanımlık veya multiuse yapabileceğiniz ile.</span><span class="sxs-lookup"><span data-stu-id="155e4-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="155e4-115">Aşağıdaki kod örneğinde multiuse özniteliği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="155e4-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="155e4-116">Aşağıdaki kod örneğinde aynı türde birden çok öznitelik bir sınıfa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="155e4-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
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
>  <span data-ttu-id="155e4-117">Öznitelik sınıfı bir özellik içeriyorsa, bu özellik salt okunur olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="155e4-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="155e4-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="155e4-118">See Also</span></span>

- <xref:System.Reflection>  
- [<span data-ttu-id="155e4-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="155e4-119">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="155e4-120">Özel Öznitelikler Yazma</span><span class="sxs-lookup"><span data-stu-id="155e4-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)  
- [<span data-ttu-id="155e4-121">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="155e4-121">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
- [<span data-ttu-id="155e4-122">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="155e4-122">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
- [<span data-ttu-id="155e4-123">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="155e4-123">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="155e4-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="155e4-124">AttributeUsage (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
