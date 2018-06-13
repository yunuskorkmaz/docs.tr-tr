---
title: static (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: b7e2981c8832d6ac1744c102d5bde55bbe25c256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33287273"
---
# <a name="static-c-reference"></a><span data-ttu-id="d5de0-102">static (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d5de0-102">static (C# Reference)</span></span>
<span data-ttu-id="d5de0-103">Kullanım `static` türü yerine belirli bir nesneye ait statik bir üyenin bildirmek için değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="d5de0-103">Use the `static` modifier to declare a static member, which belongs to the type itself rather than to a specific object.</span></span> <span data-ttu-id="d5de0-104">`static` Sınıfları, alanları, yöntemler, özellikler, işleçleri, olayları ve oluşturucular ile değiştiricisi kullanılabilir, ancak dizin oluşturucular, sonlandırıcılar veya türleri sınıfları dışında kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d5de0-104">The `static` modifier can be used with classes, fields, methods, properties, operators, events, and constructors, but it cannot be used with indexers, finalizers, or types other than classes.</span></span> <span data-ttu-id="d5de0-105">Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="d5de0-105">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5de0-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5de0-106">Example</span></span>  
 <span data-ttu-id="d5de0-107">Aşağıdaki sınıf olarak bildirilmiş `static` ve yalnızca içeren `static` yöntemleri:</span><span class="sxs-lookup"><span data-stu-id="d5de0-107">The following class is declared as `static` and contains only `static` methods:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 <span data-ttu-id="d5de0-108">Bir sabit veya türü örtük olarak statik bir üyenin bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="d5de0-108">A constant or type declaration is implicitly a static member.</span></span>  
  
 <span data-ttu-id="d5de0-109">Statik bir üyenin örneğinden başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="d5de0-109">A static member cannot be referenced through an instance.</span></span> <span data-ttu-id="d5de0-110">Bunun yerine, türü adı aracılığıyla başvurulur.</span><span class="sxs-lookup"><span data-stu-id="d5de0-110">Instead, it is referenced through the type name.</span></span> <span data-ttu-id="d5de0-111">Örneğin, aşağıdaki sınıf göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d5de0-111">For example, consider the following class:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 <span data-ttu-id="d5de0-112">Statik üye başvurmak için `x`, tam ad kullanın `MyBaseC.MyStruct.x`, üye aynı kapsamdan erişilebilir değilse:</span><span class="sxs-lookup"><span data-stu-id="d5de0-112">To refer to the static member `x`, use the fully qualified name, `MyBaseC.MyStruct.x`, unless the member is accessible from the same scope:</span></span>  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 <span data-ttu-id="d5de0-113">Sınıfının bir örneği sınıfın tüm örneği alanları ayrı bir kopyasını içerirken, her bir statik alan yalnızca bir kopyası yoktur.</span><span class="sxs-lookup"><span data-stu-id="d5de0-113">While an instance of a class contains a separate copy of all instance fields of the class, there is only one copy of each static field.</span></span>  
  
 <span data-ttu-id="d5de0-114">Kullanmak mümkün değil [bu](../../../csharp/language-reference/keywords/this.md) statik yöntemler veya özellik erişimcisi başvurmak için.</span><span class="sxs-lookup"><span data-stu-id="d5de0-114">It is not possible to use [this](../../../csharp/language-reference/keywords/this.md) to reference static methods or property accessors.</span></span>  
  
 <span data-ttu-id="d5de0-115">Varsa `static` anahtar sözcüğü bir sınıfa uygulandığında, sınıfın tüm üyeleri statik olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d5de0-115">If the `static` keyword is applied to a class, all the members of the class must be static.</span></span>  
  
 <span data-ttu-id="d5de0-116">Statik Oluşturucular, sınıflar ve statik sınıflar olabilir.</span><span class="sxs-lookup"><span data-stu-id="d5de0-116">Classes and static classes may have static constructors.</span></span> <span data-ttu-id="d5de0-117">Statik oluşturucular arasında belirli bir noktada program başlar ve sınıf örneğinin adı verilir.</span><span class="sxs-lookup"><span data-stu-id="d5de0-117">Static constructors are called at some point between when the program starts and the class is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5de0-118">`static` Anahtar sözcüğü C++ daha kullanır daha sınırlı.</span><span class="sxs-lookup"><span data-stu-id="d5de0-118">The `static` keyword has more limited uses than in C++.</span></span> <span data-ttu-id="d5de0-119">C++ anahtar sözcüğü ile karşılaştırmak için bkz: [depolama sınıfları (C++)](/cpp/cpp/storage-classes-cpp#static).</span><span class="sxs-lookup"><span data-stu-id="d5de0-119">To compare with the C++ keyword, see [Storage classes (C++)](/cpp/cpp/storage-classes-cpp#static).</span></span>
  
 <span data-ttu-id="d5de0-120">Statik üyeler göstermek için bir şirket çalışan temsil eden bir sınıf göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="d5de0-120">To demonstrate static members, consider a class that represents a company employee.</span></span> <span data-ttu-id="d5de0-121">Sınıfı çalışanları Say ve bir alan çalışanların sayısını depolamak için bir yöntem içerdiğini varsayar.</span><span class="sxs-lookup"><span data-stu-id="d5de0-121">Assume that the class contains a method to count employees and a field to store the number of employees.</span></span> <span data-ttu-id="d5de0-122">Yöntem ve alan için herhangi bir örnek çalışanı ait değil.</span><span class="sxs-lookup"><span data-stu-id="d5de0-122">Both the method and the field do not belong to any instance employee.</span></span> <span data-ttu-id="d5de0-123">Bunun yerine şirket sınıfına ait.</span><span class="sxs-lookup"><span data-stu-id="d5de0-123">Instead they belong to the company class.</span></span> <span data-ttu-id="d5de0-124">Bu nedenle, statik sınıf üyeleri bildirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="d5de0-124">Therefore, they should be declared as static members of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5de0-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5de0-125">Example</span></span>  
 <span data-ttu-id="d5de0-126">Bu örnekte yeni bir çalışan Kimliğini ve adını okur, çalışan sayacın bire artırır ve yeni çalışan ve yeni çalışanların sayısını bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d5de0-126">This example reads the name and ID of a new employee, increments the employee counter by one, and displays the information for the new employee and the new number of employees.</span></span> <span data-ttu-id="d5de0-127">Kolaylık olması için bu program klavyeden çalışanların geçerli sayısını okur.</span><span class="sxs-lookup"><span data-stu-id="d5de0-127">For simplicity, this program reads the current number of employees from the keyboard.</span></span> <span data-ttu-id="d5de0-128">Gerçek bir uygulamada bu bilgileri bir dosyadan okumanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d5de0-128">In a real application, this information should be read from a file.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="d5de0-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5de0-129">Example</span></span>  
 <span data-ttu-id="d5de0-130">Bu örnek, henüz bildirilen başka bir statik alan kullanarak statik bir alana başlatabilirsiniz rağmen statik alanın açıkça bir değer atayana kadar sonuçları tanımsız olacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d5de0-130">This example shows that although you can initialize a static field by using another static field not yet declared, the results will be undefined until you explicitly assign a value to the static field.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="d5de0-131">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d5de0-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d5de0-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5de0-132">See Also</span></span>  
 [<span data-ttu-id="d5de0-133">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d5de0-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d5de0-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d5de0-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d5de0-135">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d5de0-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d5de0-136">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="d5de0-136">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="d5de0-137">Statik Sınıflar ve Statik Sınıf Üyeleri</span><span class="sxs-lookup"><span data-stu-id="d5de0-137">Static Classes and Static Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
