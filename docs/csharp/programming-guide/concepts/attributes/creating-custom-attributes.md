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
# <a name="creating-custom-attributes-c"></a><span data-ttu-id="85abe-102">Özel öznitelikler (C#) oluşturma</span><span class="sxs-lookup"><span data-stu-id="85abe-102">Creating Custom Attributes (C#)</span></span>
<span data-ttu-id="85abe-103">Doğrudan veya dolaylı olarak türeyen bir sınıf bir öznitelik sınıfı tanımlayarak, kendi özel öznitelikler oluşturabilirsiniz <xref:System.Attribute>, hızlı ve kolay meta verilerde özniteliği tanımlarını tanımlayan hangi yapar.</span><span class="sxs-lookup"><span data-stu-id="85abe-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="85abe-104">Etiket türleri türü yazan programcı için adıyla istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="85abe-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="85abe-105">Özel bir tanımlayabilir `Author` öznitelik sınıfı:</span><span class="sxs-lookup"><span data-stu-id="85abe-105">You might define a custom `Author` attribute class:</span></span>  
  
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
  
 <span data-ttu-id="85abe-106">Sınıf adı özniteliğin adıdır `Author`.</span><span class="sxs-lookup"><span data-stu-id="85abe-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="85abe-107">Öğesinden türetilen `System.Attribute`özel bir öznitelik sınıfı gelir.</span><span class="sxs-lookup"><span data-stu-id="85abe-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="85abe-108">Oluşturucusu ait, özel özniteliğin konumsal parametreler parametreleridir.</span><span class="sxs-lookup"><span data-stu-id="85abe-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="85abe-109">Bu örnekte, `name` konumsal bir parametredir.</span><span class="sxs-lookup"><span data-stu-id="85abe-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="85abe-110">Herhangi bir genel okuma-yazma alanlar veya özellikler parametreleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="85abe-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="85abe-111">Bu durumda, `version` tek parametresi olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="85abe-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="85abe-112">Kullanımına dikkat edin `AttributeUsage` yapmak için öznitelik `Author` özniteliği yalnızca sınıfında geçerli ve `struct` bildirimleri.</span><span class="sxs-lookup"><span data-stu-id="85abe-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `struct` declarations.</span></span>  
  
 <span data-ttu-id="85abe-113">Bu yeni öznitelik aşağıdaki gibi kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="85abe-113">You could use this new attribute as follows:</span></span>  
  
```csharp  
[Author("P. Ackerman", version = 1.1)]  
class SampleClass  
{  
    // P. Ackerman's code goes here...  
}  
```  
  
 <span data-ttu-id="85abe-114">`AttributeUsage`adlandırılmış bir parametre içeriyor `AllowMultiple`, özel bir öznitelik tek kullanımlık veya multiuse yapabileceğiniz ile.</span><span class="sxs-lookup"><span data-stu-id="85abe-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="85abe-115">Aşağıdaki kod örneğinde multiuse özniteliği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="85abe-115">In the following code example, a multiuse attribute is created.</span></span>  
  
```csharp  
[System.AttributeUsage(System.AttributeTargets.Class |  
                       System.AttributeTargets.Struct,  
                       AllowMultiple = true)  // multiuse attribute  
]  
public class Author : System.Attribute  
```  
  
 <span data-ttu-id="85abe-116">Aşağıdaki kod örneğinde aynı türde birden çok öznitelik bir sınıfa uygulanır.</span><span class="sxs-lookup"><span data-stu-id="85abe-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>  
  
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
>  <span data-ttu-id="85abe-117">Öznitelik sınıfı bir özellik varsa, bu özelliği oku-yaz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="85abe-117">If your attribute class contains a property, that property must be read-write.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85abe-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="85abe-118">See Also</span></span>  
 <xref:System.Reflection>  
 [<span data-ttu-id="85abe-119">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="85abe-119">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="85abe-120">Özel öznitelikler yazma</span><span class="sxs-lookup"><span data-stu-id="85abe-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)  
 [<span data-ttu-id="85abe-121">Yansıma (C#)</span><span class="sxs-lookup"><span data-stu-id="85abe-121">Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="85abe-122">Öznitelikler (C#)</span><span class="sxs-lookup"><span data-stu-id="85abe-122">Attributes (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="85abe-123">Yansıma (C#) kullanarak özniteliklere erişme</span><span class="sxs-lookup"><span data-stu-id="85abe-123">Accessing Attributes by Using Reflection (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
 [<span data-ttu-id="85abe-124">AttributeUsage (C#)</span><span class="sxs-lookup"><span data-stu-id="85abe-124">AttributeUsage (C#)</span></span>](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md)
