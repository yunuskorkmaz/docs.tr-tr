---
title: Özel Oluşturucular (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 5b387447046e4755287fc9f6a8813a19752799c2
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "50980722"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="6e82e-102">Özel Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6e82e-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="6e82e-103">Bir özel örnek oluşturucusu bir özel oluşturucudur.</span><span class="sxs-lookup"><span data-stu-id="6e82e-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="6e82e-104">Ayrıca, yalnızca statik üyeleri içeren sınıflar genel olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e82e-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="6e82e-105">Bir sınıf, bir veya daha fazla özel oluşturucular ve genel Oluşturucusu varsa, diğer sınıflar (iç içe geçmiş sınıflar dışında) bu sınıfın örnekleri oluşturulamaz.</span><span class="sxs-lookup"><span data-stu-id="6e82e-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="6e82e-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6e82e-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 <span data-ttu-id="6e82e-107">Boş Oluşturucu bildirimi bir varsayılan oluşturucu otomatik olarak oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="6e82e-107">The declaration of the empty constructor prevents the automatic generation of a default constructor.</span></span> <span data-ttu-id="6e82e-108">Bir erişim değiştiricisidir oluşturucuyla kullanmazsanız, yine de varsayılan olarak özel olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6e82e-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="6e82e-109">Ancak, [özel](../../../csharp/language-reference/keywords/private.md) değiştiricisi genellikle açıkça sağlamak için kullanılan sınıfın oluşturulamadığını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="6e82e-109">However, the [private](../../../csharp/language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="6e82e-110">Özel oluşturucular önlemek için kullanılan olduğunda hiçbir örneği alanlar veya yöntemler, aşağıdaki gibi bir sınıfın örnekleri oluşturma <xref:System.Math> sınıfı veya ne zaman bir yöntemi çağrıldığında bir sınıfın bir örneği elde etmek için.</span><span class="sxs-lookup"><span data-stu-id="6e82e-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="6e82e-111">Sınıfındaki tüm yöntemler statik ise tam sınıf statik yapma göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="6e82e-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="6e82e-112">Daha fazla bilgi için [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="6e82e-112">For more information see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e82e-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="6e82e-113">Example</span></span>  
 <span data-ttu-id="6e82e-114">Aşağıdaki özel bir oluşturucu kullanılarak sınıfının bir örneğidir.</span><span class="sxs-lookup"><span data-stu-id="6e82e-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 <span data-ttu-id="6e82e-115">Aşağıdaki örnek ifade açıklamasını kaldırın, koruma düzeyi nedeniyle oluşturucusuna erişilemediğinden, bir hata oluşturacağına dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="6e82e-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6e82e-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="6e82e-116">C# Language Specification</span></span>  

<span data-ttu-id="6e82e-117">Daha fazla bilgi için [özel oluşturucular](~/_csharplang/spec/classes.md#private-constructors) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6e82e-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="6e82e-118">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="6e82e-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6e82e-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e82e-119">See Also</span></span>

- [<span data-ttu-id="6e82e-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6e82e-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6e82e-121">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="6e82e-121">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="6e82e-122">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="6e82e-122">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
- [<span data-ttu-id="6e82e-123">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="6e82e-123">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
- [<span data-ttu-id="6e82e-124">private</span><span class="sxs-lookup"><span data-stu-id="6e82e-124">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="6e82e-125">public</span><span class="sxs-lookup"><span data-stu-id="6e82e-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)
