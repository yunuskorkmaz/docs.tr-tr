---
title: Yapılar (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: ffb5b8da6c72056620cf890f38af4e7a8116ab3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322994"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="f708f-102">Yapılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="f708f-102">Structs (C# Programming Guide)</span></span>
<span data-ttu-id="f708f-103">Yapılar kullanılarak tanımlanmış [yapısı](../../../csharp/language-reference/keywords/struct.md) anahtar sözcüğü, örneğin:</span><span class="sxs-lookup"><span data-stu-id="f708f-103">Structs are defined by using the [struct](../../../csharp/language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 <span data-ttu-id="f708f-104">Yapılar sınıfları'den daha kısıtlı olsa yapılar sınıfları, aynı söz dizimini çoğunu paylaşır:</span><span class="sxs-lookup"><span data-stu-id="f708f-104">Structs share most of the same syntax as classes, although structs are more limited than classes:</span></span>  
  
-   <span data-ttu-id="f708f-105">Const veya statik olarak bildirilir sürece yapısı bildirimi içinde alanları başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="f708f-105">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
  
-   <span data-ttu-id="f708f-106">Yapı, varsayılan bir oluşturucu (parametresiz bir oluşturucu) veya bir sonlandırıcı bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="f708f-106">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
  
-   <span data-ttu-id="f708f-107">Yapılar atamada kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="f708f-107">Structs are copied on assignment.</span></span> <span data-ttu-id="f708f-108">Yapı için yeni bir değişken atandığında, tüm verileri kopyalanır ve yeni bir kopyasını kendilerine herhangi bir değişiklik özgün kopya verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="f708f-108">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="f708f-109">Bu değer türleri sözlük gibi koleksiyonları ile çalışırken unutulmaması önemlidir;\<dize, myStruct >.</span><span class="sxs-lookup"><span data-stu-id="f708f-109">This is important to remember when working with collections of value types such as Dictionary\<string, myStruct>.</span></span>  
  
-   <span data-ttu-id="f708f-110">Yapılar değer türleri ve sınıfları başvuru türleri.</span><span class="sxs-lookup"><span data-stu-id="f708f-110">Structs are value types and classes are reference types.</span></span>  
  
-   <span data-ttu-id="f708f-111">Sınıfları kullanmadan yapılar oluşturulabilir bir `new` işleci.</span><span class="sxs-lookup"><span data-stu-id="f708f-111">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
  
-   <span data-ttu-id="f708f-112">Yapılar parametrelere sahip oluşturucular bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f708f-112">Structs can declare constructors that have parameters.</span></span>  
  
-   <span data-ttu-id="f708f-113">Yapı başka bir yapı veya sınıfından devralan ve bir sınıfın temel olamaz.</span><span class="sxs-lookup"><span data-stu-id="f708f-113">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="f708f-114">Tüm yapıları doğrudan devralınmalıdır `System.ValueType`, devralan `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="f708f-114">All structs inherit directly from `System.ValueType`, which inherits from `System.Object`.</span></span>  
  
-   <span data-ttu-id="f708f-115">Yapı arabirimleri uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="f708f-115">A struct can implement interfaces.</span></span>  
  
-   <span data-ttu-id="f708f-116">Yapı boş değer atanabilir bir tür olarak kullanılan ve boş değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="f708f-116">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f708f-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="f708f-117">Related Sections</span></span>  
 <span data-ttu-id="f708f-118">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="f708f-118">For more information:</span></span>  
  
-   [<span data-ttu-id="f708f-119">Yapıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="f708f-119">Using Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [<span data-ttu-id="f708f-120">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="f708f-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="f708f-121">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="f708f-121">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [<span data-ttu-id="f708f-122">Nasıl yapılır: Yapı Geçirme ile Yönteme Sınıf Başvurusu Geçirme Arasındaki Farkı Bilme</span><span class="sxs-lookup"><span data-stu-id="f708f-122">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [<span data-ttu-id="f708f-123">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama</span><span class="sxs-lookup"><span data-stu-id="f708f-123">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a><span data-ttu-id="f708f-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f708f-124">See Also</span></span>  
 [<span data-ttu-id="f708f-125">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f708f-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f708f-126">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="f708f-126">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="f708f-127">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="f708f-127">Classes</span></span>](../../../csharp/programming-guide/classes-and-structs/classes.md)
