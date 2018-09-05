---
title: Yapılar (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: abe39b336aa8e9aa7a8a8ee96ed6848804644ddd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518709"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="c218f-102">Yapılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="c218f-102">Structs (C# Programming Guide)</span></span>
<span data-ttu-id="c218f-103">Yapılar kullanarak tanımlanmış [yapı](../../../csharp/language-reference/keywords/struct.md) anahtar sözcüğü, örneğin:</span><span class="sxs-lookup"><span data-stu-id="c218f-103">Structs are defined by using the [struct](../../../csharp/language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 <span data-ttu-id="c218f-104">Yapılar sınıfları daha sınırlı olmasına karşın yapılar sınıfları, aynı söz dizimini çoğunu paylaşır:</span><span class="sxs-lookup"><span data-stu-id="c218f-104">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="c218f-105">Const veya statik olarak bildirilirler sürece bir yapının bildirimi içinde alanları başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="c218f-105">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
  
-   <span data-ttu-id="c218f-106">Bir yapı varsayılan (parametresiz bir oluşturucu) bir oluşturucu ya da bir sonlandırıcı bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="c218f-106">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="c218f-107">Yapılar, atamaya bağlı kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="c218f-107">Structs are copied on assignment.</span></span> <span data-ttu-id="c218f-108">Bir yapı için yeni bir değişken atandığında, tüm verileri kopyalanır ve yeni bir kopyasını değişiklik özgün kopya verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="c218f-108">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="c218f-109">Bu sözlük gibi değer türlerinin koleksiyonları ile çalışırken unutmamak önemlidir\<string, myStruct >.</span><span class="sxs-lookup"><span data-stu-id="c218f-109">This is important to remember when working with collections of value types such as Dictionary\<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="c218f-110">Yapılar değer türüdür ve sınıflar, başvuru türleridir.</span><span class="sxs-lookup"><span data-stu-id="c218f-110">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="c218f-111">Sınıflardan farklı olarak, yapılar kullanmadan oluşturulabilir bir `new` işleci.</span><span class="sxs-lookup"><span data-stu-id="c218f-111">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="c218f-112">Yapılar parametrelerine sahip oluşturucular bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c218f-112">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="c218f-113">Bir yapı, başka bir yapı veya sınıfından devralamaz ve temel bir sınıfı olamaz.</span><span class="sxs-lookup"><span data-stu-id="c218f-113">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="c218f-114">Tüm yapıları doğrudan devralan `System.ValueType`, işlevinden devralan `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="c218f-114">All structs inherit directly from `System.ValueType`, which inherits from `System.Object`.</span></span>  
  
-   <span data-ttu-id="c218f-115">Bir yapı, arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="c218f-115">A struct can implement interfaces.</span></span>  
  
-   <span data-ttu-id="c218f-116">Bir yapı boş değer atanabilir bir tür kullanılan ve boş değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="c218f-116">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c218f-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c218f-117">Related Sections</span></span>  
 <span data-ttu-id="c218f-118">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="c218f-118">For more information:</span></span>  
  
-   [<span data-ttu-id="c218f-119">Yapıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="c218f-119">Using Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [<span data-ttu-id="c218f-120">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="c218f-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="c218f-121">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="c218f-121">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [<span data-ttu-id="c218f-122">Nasıl yapılır: Yapı Geçirme ile Yönteme Sınıf Başvurusu Geçirme Arasındaki Farkı Bilme</span><span class="sxs-lookup"><span data-stu-id="c218f-122">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [<span data-ttu-id="c218f-123">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama</span><span class="sxs-lookup"><span data-stu-id="c218f-123">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a><span data-ttu-id="c218f-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c218f-124">See Also</span></span>

- [<span data-ttu-id="c218f-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c218f-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c218f-126">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="c218f-126">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="c218f-127">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="c218f-127">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
