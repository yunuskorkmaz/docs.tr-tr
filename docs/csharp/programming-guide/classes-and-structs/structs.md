---
title: Yapılar - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 609169d4624802f679f9661b7aa0596403cc48e7
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261626"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="556ba-102">Yapılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="556ba-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="556ba-103">Yapılar kullanarak tanımlanmış [yapı](../../language-reference/keywords/struct.md) anahtar sözcüğü, örneğin:</span><span class="sxs-lookup"><span data-stu-id="556ba-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
<span data-ttu-id="556ba-104">Yapılar sınıflar olarak aynı sözdizimini çoğunu paylaşır.</span><span class="sxs-lookup"><span data-stu-id="556ba-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="556ba-105">Struct'ın adı geçerli C# olmalıdır [tanımlayıcı adı](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="556ba-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="556ba-106">Yapılar aşağıdaki yollarla sınıfları daha büyük/küçük harf sınırlıdır:</span><span class="sxs-lookup"><span data-stu-id="556ba-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="556ba-107">Const veya statik olarak bildirilirler sürece bir yapının bildirimi içinde alanları başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="556ba-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="556ba-108">Bir yapı varsayılan (parametresiz bir oluşturucu) bir oluşturucu ya da bir sonlandırıcı bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="556ba-108">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="556ba-109">Yapılar, atamaya bağlı kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="556ba-109">Structs are copied on assignment.</span></span> <span data-ttu-id="556ba-110">Bir yapı için yeni bir değişken atandığında, tüm verileri kopyalanır ve yeni bir kopyasını değişiklik özgün kopya verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="556ba-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="556ba-111">Bu ne zaman değerinin koleksiyonlar ile çalışma gibi türleri unutmamak önemlidir `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="556ba-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="556ba-112">Başvuru türleri sınıflar, aksine, değer türleri birimleridir.</span><span class="sxs-lookup"><span data-stu-id="556ba-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="556ba-113">Sınıflardan farklı olarak, yapılar kullanmadan oluşturulabilir bir `new` işleci.</span><span class="sxs-lookup"><span data-stu-id="556ba-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="556ba-114">Yapılar parametrelerine sahip oluşturucular bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="556ba-114">Structs can declare constructors that have parameters.</span></span> 
- <span data-ttu-id="556ba-115">Bir yapı, başka bir yapı veya sınıfından devralamaz ve temel bir sınıfı olamaz.</span><span class="sxs-lookup"><span data-stu-id="556ba-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="556ba-116">Tüm yapıları doğrudan devralan <xref:System.ValueType>, işlevinden devralan <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="556ba-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="556ba-117">Bir yapı, arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="556ba-117">A struct can implement interfaces.</span></span> 
- <span data-ttu-id="556ba-118">Bir yapı olamaz `null`, ve bir yapı değişkene atanamaz `null` boş değer atanabilir bir tür değişkenin bildirildiği sürece.</span><span class="sxs-lookup"><span data-stu-id="556ba-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable type.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="556ba-119">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="556ba-119">Related sections</span></span>  

<span data-ttu-id="556ba-120">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="556ba-120">For more information:</span></span>  
  
- [<span data-ttu-id="556ba-121">Yapıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="556ba-121">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="556ba-122">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="556ba-122">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="556ba-123">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="556ba-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="556ba-124">Nasıl yapılır: Yapı geçirme ile Metoda sınıf başvurusu geçirme arasındaki farkı bilme</span><span class="sxs-lookup"><span data-stu-id="556ba-124">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [<span data-ttu-id="556ba-125">Nasıl yapılır: Yapılar arasında kullanıcı tanımlı Dönüşümler Uygulama</span><span class="sxs-lookup"><span data-stu-id="556ba-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a><span data-ttu-id="556ba-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="556ba-126">See also</span></span>

- [<span data-ttu-id="556ba-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="556ba-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="556ba-128">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="556ba-128">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="556ba-129">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="556ba-129">Classes</span></span>](classes.md)
- [<span data-ttu-id="556ba-130">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="556ba-130">Identifier names</span></span>](../inside-a-program/identifier-names.md)
