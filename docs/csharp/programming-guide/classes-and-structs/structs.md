---
title: Yapılar - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 063d7e3b68fbe6c01ff0df4ae935fec5af6f6891
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743842"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="0e0bc-102">Yapılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0e0bc-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="0e0bc-103">Yapılar kullanarak tanımlanmış [yapı](../../language-reference/keywords/struct.md) anahtar sözcüğü, örneğin:</span><span class="sxs-lookup"><span data-stu-id="0e0bc-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
<span data-ttu-id="0e0bc-104">Yapılar sınıflar olarak aynı sözdizimini çoğunu paylaşır.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="0e0bc-105">Struct'ın adı geçerli C# olmalıdır [tanımlayıcı adı](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="0e0bc-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="0e0bc-106">Yapılar aşağıdaki yollarla sınıfları daha büyük/küçük harf sınırlıdır:</span><span class="sxs-lookup"><span data-stu-id="0e0bc-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="0e0bc-107">Const veya statik olarak bildirilirler sürece bir yapının bildirimi içinde alanları başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="0e0bc-108">Bir yapı, parametresiz bir oluşturucu (parametresiz bir oluşturucu) veya bir sonlandırıcı bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-108">A struct cannot declare a parameterless constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="0e0bc-109">Yapılar, atamaya bağlı kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-109">Structs are copied on assignment.</span></span> <span data-ttu-id="0e0bc-110">Bir yapı için yeni bir değişken atandığında, tüm verileri kopyalanır ve yeni bir kopyasını değişiklik özgün kopya verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="0e0bc-111">Bu ne zaman değerinin koleksiyonlar ile çalışma gibi türleri unutmamak önemlidir `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="0e0bc-112">Başvuru türleri sınıflar, aksine, değer türleri birimleridir.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="0e0bc-113">Sınıflardan farklı olarak, yapılar kullanmadan oluşturulabilir bir `new` işleci.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="0e0bc-114">Yapılar parametrelerine sahip oluşturucular bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-114">Structs can declare constructors that have parameters.</span></span>
- <span data-ttu-id="0e0bc-115">Bir yapı, başka bir yapı veya sınıfından devralamaz ve temel bir sınıfı olamaz.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="0e0bc-116">Tüm yapıları doğrudan devralan <xref:System.ValueType>, işlevinden devralan <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="0e0bc-117">Bir yapı, arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-117">A struct can implement interfaces.</span></span>
- <span data-ttu-id="0e0bc-118">Bir yapı olamaz `null`, ve bir yapı değişkene atanamaz `null` boş değer atanabilir bir tür değişkenin bildirildiği sürece.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable type.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0e0bc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e0bc-119">See also</span></span>

- [<span data-ttu-id="0e0bc-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0e0bc-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="0e0bc-121">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="0e0bc-121">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="0e0bc-122">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="0e0bc-122">Classes</span></span>](classes.md)
- [<span data-ttu-id="0e0bc-123">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="0e0bc-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="0e0bc-124">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="0e0bc-124">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="0e0bc-125">Yapıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="0e0bc-125">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="0e0bc-126">Nasıl yapılır: Yapı geçirme ile Metoda sınıf başvurusu geçirme arasındaki farkı bilme</span><span class="sxs-lookup"><span data-stu-id="0e0bc-126">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
