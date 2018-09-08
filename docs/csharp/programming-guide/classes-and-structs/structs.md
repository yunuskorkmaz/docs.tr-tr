---
title: Yapılar (C# Programlama Kılavuzu)
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 27d4b0d7edf1b5e89e84ac1df5783d68ebb4efe0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186935"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="ef8e3-102">Yapılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="ef8e3-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="ef8e3-103">Yapılar kullanarak tanımlanmış [yapı](../../language-reference/keywords/struct.md) anahtar sözcüğü, örneğin:</span><span class="sxs-lookup"><span data-stu-id="ef8e3-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
[!code-csharp[csProgGuideObjects#39](./codesnippet/CSharp/structs_1.cs)]  
  
<span data-ttu-id="ef8e3-104">Yapılar sınıflar olarak aynı sözdizimini çoğunu paylaşır.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="ef8e3-105">Struct'ın adı geçerli C# olmalıdır [tanımlayıcı adı](../inside-a-program/identifier-names.md).</span><span class="sxs-lookup"><span data-stu-id="ef8e3-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="ef8e3-106">Yapılar aşağıdaki yollarla sınıfları daha büyük/küçük harf sınırlıdır:</span><span class="sxs-lookup"><span data-stu-id="ef8e3-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="ef8e3-107">Const veya statik olarak bildirilirler sürece bir yapının bildirimi içinde alanları başlatılamıyor.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="ef8e3-108">Bir yapı varsayılan (parametresiz bir oluşturucu) bir oluşturucu ya da bir sonlandırıcı bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-108">A struct cannot declare a default constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="ef8e3-109">Yapılar, atamaya bağlı kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-109">Structs are copied on assignment.</span></span> <span data-ttu-id="ef8e3-110">Bir yapı için yeni bir değişken atandığında, tüm verileri kopyalanır ve yeni bir kopyasını değişiklik özgün kopya verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="ef8e3-111">Bu ne zaman değerinin koleksiyonlar ile çalışma gibi türleri unutmamak önemlidir `Dictionary<string, myStruct>`.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="ef8e3-112">Başvuru türleri sınıflar, aksine, değer türleri birimleridir.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="ef8e3-113">Sınıflardan farklı olarak, yapılar kullanmadan oluşturulabilir bir `new` işleci.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="ef8e3-114">Yapılar parametrelerine sahip oluşturucular bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-114">Structs can declare constructors that have parameters.</span></span> 
- <span data-ttu-id="ef8e3-115">Bir yapı, başka bir yapı veya sınıfından devralamaz ve temel bir sınıfı olamaz.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="ef8e3-116">Tüm yapıları doğrudan devralan <xref:System.ValueType>, işlevinden devralan <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="ef8e3-117">Bir yapı, arabirim uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-117">A struct can implement interfaces.</span></span>  
- <span data-ttu-id="ef8e3-118">Bir yapı boş değer atanabilir bir tür kullanılan ve boş değer atanabilir.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-118">A struct can be used as a nullable type and can be assigned a null value.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ef8e3-119">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="ef8e3-119">Related sections</span></span>  

<span data-ttu-id="ef8e3-120">Daha fazla bilgi için:</span><span class="sxs-lookup"><span data-stu-id="ef8e3-120">For more information:</span></span>  
  
- [<span data-ttu-id="ef8e3-121">Yapıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="ef8e3-121">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="ef8e3-122">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="ef8e3-122">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="ef8e3-123">Boş Değer Atanabilir Tipler</span><span class="sxs-lookup"><span data-stu-id="ef8e3-123">Nullable Types</span></span>](../nullable-types/index.md)
- [<span data-ttu-id="ef8e3-124">Nasıl yapılır: Yapı Geçirme ile Yönteme Sınıf Başvurusu Geçirme Arasındaki Farkı Bilme</span><span class="sxs-lookup"><span data-stu-id="ef8e3-124">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
- [<span data-ttu-id="ef8e3-125">Nasıl yapılır: Yapılar Arasında Kullanıcı Tanımlı Dönüştürmeler Uygulama</span><span class="sxs-lookup"><span data-stu-id="ef8e3-125">How to: Implement User-Defined Conversions Between Structs</span></span>](../statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)

## <a name="see-also"></a><span data-ttu-id="ef8e3-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef8e3-126">See also</span></span>

- [<span data-ttu-id="ef8e3-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ef8e3-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ef8e3-128">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="ef8e3-128">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="ef8e3-129">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="ef8e3-129">Classes</span></span>](classes.md)
- [<span data-ttu-id="ef8e3-130">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="ef8e3-130">Identifier names</span></span>](../inside-a-program/identifier-names.md)
