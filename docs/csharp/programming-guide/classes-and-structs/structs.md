---
title: "Yapılar (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 475d9b96e078270faf6c841a62e6031556e8e539
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="2acf8-102">Yapılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2acf8-102">Structs (C# Programming Guide)</span></span>
<span data-ttu-id="2acf8-103">Yapılar kullanılarak tanımlanmış [yapısı](../../../csharp/language-reference/keywords/struct.md) anahtar sözcüğü, örneğin:</span><span class="sxs-lookup"><span data-stu-id="2acf8-103">Structs are defined by using the [struct](../../../csharp/language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 <span data-ttu-id="2acf8-104">Yapılar sınıfları'den daha kısıtlı olsa yapılar sınıfları, aynı söz dizimini çoğunu paylaşır:</span><span class="sxs-lookup"><span data-stu-id="2acf8-104">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="2acf8-105">Const veya statik olarak bildirilir sürece yapısı bildirimi içinde alanları başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="2acf8-105">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
  
-   <span data-ttu-id="2acf8-106">Yapı, varsayılan bir oluşturucu (parametresiz bir oluşturucu) veya bir sonlandırıcı bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acf8-106">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="2acf8-107">Yapılar atamada kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="2acf8-107">Structs are copied on assignment.</span></span> <span data-ttu-id="2acf8-108">Yapı için yeni bir değişken atandığında, tüm verileri kopyalanır ve yeni bir kopyasını kendilerine herhangi bir değişiklik özgün kopya verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="2acf8-108">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="2acf8-109">Bu değer türleri sözlük gibi koleksiyonları ile çalışırken unutulmaması önemlidir;\<dize, myStruct >.</span><span class="sxs-lookup"><span data-stu-id="2acf8-109">This is important to remember when working with collections of value types such as Dictionary\<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="2acf8-110">Yapılar değer türleri ve sınıfları başvuru türleri.</span><span class="sxs-lookup"><span data-stu-id="2acf8-110">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="2acf8-111">Sınıfları kullanmadan yapılar oluşturulabilir bir `new` işleci.</span><span class="sxs-lookup"><span data-stu-id="2acf8-111">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="2acf8-112">Yapılar parametrelere sahip oluşturucular bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2acf8-112">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="2acf8-113">Yapı başka bir yapı veya sınıfından devralan ve bir sınıfın temel olamaz.</span><span class="sxs-lookup"><span data-stu-id="2acf8-113">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="2acf8-114">Tüm yapıları doğrudan devralınmalıdır `System.ValueType`, devralan `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="2acf8-114">All structs inherit directly from `System.ValueType`, which inherits from `System.Object`.</span></span>  
  
-   <span data-ttu-id="2acf8-115">Yapı arabirimleri uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="2acf8-115">A struct can implement interfaces.</span></span>  
  
-   <span data-ttu-id="2acf8-116">Yapı boş değer atanabilir bir tür olarak kullanılan ve boş değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="2acf8-116">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2acf8-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2acf8-117">Related Sections</span></span>  
 <span data-ttu-id="2acf8-118">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="2acf8-118">For more information:</span></span>  
  
-   [<span data-ttu-id="2acf8-119">Yapıları kullanma</span><span class="sxs-lookup"><span data-stu-id="2acf8-119">Using Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [<span data-ttu-id="2acf8-120">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="2acf8-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="2acf8-121">Boş değer atanabilir türler</span><span class="sxs-lookup"><span data-stu-id="2acf8-121">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [<span data-ttu-id="2acf8-122">Nasıl yapılır: Yapı geçirme ile yönteme sınıf başvurusu geçirme arasındaki farkı bilme</span><span class="sxs-lookup"><span data-stu-id="2acf8-122">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [<span data-ttu-id="2acf8-123">Nasıl yapılır: yapılar arasında kullanıcı tanımlı dönüşümler</span><span class="sxs-lookup"><span data-stu-id="2acf8-123">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a><span data-ttu-id="2acf8-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2acf8-124">See Also</span></span>  
 [<span data-ttu-id="2acf8-125">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2acf8-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2acf8-126">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="2acf8-126">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="2acf8-127">Sınıfları</span><span class="sxs-lookup"><span data-stu-id="2acf8-127">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
