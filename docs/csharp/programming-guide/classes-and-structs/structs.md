---
title: Yapılar- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 08/21/2018
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: 945d4b060dd9d08f6f16013b27980f66e804ad45
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739234"
---
# <a name="structs-c-programming-guide"></a><span data-ttu-id="3194a-102">Yapılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3194a-102">Structs (C# Programming Guide)</span></span>

<span data-ttu-id="3194a-103">Yapılar [struct](../../language-reference/keywords/struct.md) anahtar sözcüğü kullanılarak tanımlanır, örneğin:</span><span class="sxs-lookup"><span data-stu-id="3194a-103">Structs are defined by using the [struct](../../language-reference/keywords/struct.md) keyword, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#39)]  
  
<span data-ttu-id="3194a-104">Yapılar, aynı sözdiziminin büyük bir kısmını sınıflarla paylaşır.</span><span class="sxs-lookup"><span data-stu-id="3194a-104">Structs share most of the same syntax as classes.</span></span> <span data-ttu-id="3194a-105">Yapının adı geçerli C# bir [tanımlayıcı adı](../inside-a-program/identifier-names.md)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3194a-105">The name of the struct must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="3194a-106">Yapılar aşağıdaki yollarla sınıflardan daha sınırlıdır:</span><span class="sxs-lookup"><span data-stu-id="3194a-106">Structs are more limited than classes in the following ways:</span></span>  
  
- <span data-ttu-id="3194a-107">Bir struct bildiriminde, alanlar const veya static olarak bildirilmeyen sürece başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="3194a-107">Within a struct declaration, fields cannot be initialized unless they are declared as const or static.</span></span>  
- <span data-ttu-id="3194a-108">Struct parametresiz bir Oluşturucu (parametresiz bir Oluşturucu) veya sonlandırıcısı bildiremez.</span><span class="sxs-lookup"><span data-stu-id="3194a-108">A struct cannot declare a parameterless constructor (a constructor without parameters) or a finalizer.</span></span>  
- <span data-ttu-id="3194a-109">Yapılar atamaya kopyalanır.</span><span class="sxs-lookup"><span data-stu-id="3194a-109">Structs are copied on assignment.</span></span> <span data-ttu-id="3194a-110">Bir yapı yeni bir değişkene atandığında, tüm veriler kopyalanır ve yeni kopyada yapılan değişiklikler özgün kopyanın verilerini değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="3194a-110">When a struct is assigned to a new variable, all the data is copied, and any modification to the new copy does not change the data for the original copy.</span></span> <span data-ttu-id="3194a-111">Bu, `Dictionary<string, myStruct>`gibi değer türlerinin koleksiyonlarıyla çalışırken unutmamak önemlidir.</span><span class="sxs-lookup"><span data-stu-id="3194a-111">This is important to remember when working with collections of value types such as `Dictionary<string, myStruct>`.</span></span>  
- <span data-ttu-id="3194a-112">Yapılar, başvuru türleri olan sınıfların aksine değer türlerdir.</span><span class="sxs-lookup"><span data-stu-id="3194a-112">Structs are value types, unlike classes, which are reference types.</span></span>  
- <span data-ttu-id="3194a-113">Sınıfların aksine, yapılar `new` işleci kullanılmadan oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="3194a-113">Unlike classes, structs can be instantiated without using a `new` operator.</span></span>  
- <span data-ttu-id="3194a-114">Yapılar, parametreleri olan oluşturucular bildirebilir.</span><span class="sxs-lookup"><span data-stu-id="3194a-114">Structs can declare constructors that have parameters.</span></span>
- <span data-ttu-id="3194a-115">Yapı, başka bir struct veya sınıftan devralınabilir ve bir sınıfın temeli olamaz.</span><span class="sxs-lookup"><span data-stu-id="3194a-115">A struct cannot inherit from another struct or class, and it cannot be the base of a class.</span></span> <span data-ttu-id="3194a-116">Tüm yapılar, <xref:System.Object>devralan <xref:System.ValueType>doğrudan devralır.</span><span class="sxs-lookup"><span data-stu-id="3194a-116">All structs inherit directly from <xref:System.ValueType>, which inherits from <xref:System.Object>.</span></span>  
- <span data-ttu-id="3194a-117">Bir struct, arabirimler uygulayabilir.</span><span class="sxs-lookup"><span data-stu-id="3194a-117">A struct can implement interfaces.</span></span>
- <span data-ttu-id="3194a-118">Bir struct `null`olamaz ve değişken null değer türü olarak bildirildiği sürece bir struct değişkeni `null` atanamaz.</span><span class="sxs-lookup"><span data-stu-id="3194a-118">A struct cannot be `null`, and a struct variable cannot be assigned `null` unless the variable is declared as a nullable value type.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3194a-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3194a-119">See also</span></span>

- [<span data-ttu-id="3194a-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3194a-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3194a-121">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="3194a-121">Classes and Structs</span></span>](index.md)
- [<span data-ttu-id="3194a-122">Sınıflar</span><span class="sxs-lookup"><span data-stu-id="3194a-122">Classes</span></span>](classes.md)
- [<span data-ttu-id="3194a-123">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="3194a-123">Nullable value types</span></span>](../../language-reference/builtin-types/nullable-value-types.md)
- [<span data-ttu-id="3194a-124">Tanımlayıcı adları</span><span class="sxs-lookup"><span data-stu-id="3194a-124">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="3194a-125">Yapıları Kullanma</span><span class="sxs-lookup"><span data-stu-id="3194a-125">Using Structs</span></span>](using-structs.md)
- [<span data-ttu-id="3194a-126">Nasıl yapılır: Yapı Geçirme ile Yönteme Sınıf Başvurusu Geçirme Arasındaki Farkı Bilme</span><span class="sxs-lookup"><span data-stu-id="3194a-126">How to: Know the Difference Between Passing a Struct and Passing a Class Reference to a Method</span></span>](how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)
