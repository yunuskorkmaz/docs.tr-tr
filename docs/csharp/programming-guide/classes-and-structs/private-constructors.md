---
title: "Özel Oluşturucular (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 79660cd4545fff43ac3dd6ab797fd20c0f882e05
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="0e5f7-102">Özel Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0e5f7-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="0e5f7-103">Özel Oluşturucusu bir özel örnek Oluşturucusu ' dir.</span><span class="sxs-lookup"><span data-stu-id="0e5f7-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="0e5f7-104">Bu genellikle yalnızca statik üyeleri içeren sınıfları kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0e5f7-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="0e5f7-105">Bir sınıf bir veya daha fazla özel oluşturucular ve ortak oluşturucu yok varsa, bu sınıfın örnekleri, diğer sınıflar (dışında iç içe geçmiş sınıflar) oluşturulamıyor.</span><span class="sxs-lookup"><span data-stu-id="0e5f7-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="0e5f7-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="0e5f7-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 <span data-ttu-id="0e5f7-107">Boş Oluşturucusu bildirimi varsayılan bir oluşturucu otomatik olarak oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="0e5f7-107">The declaration of the empty constructor prevents the automatic generation of a default constructor.</span></span> <span data-ttu-id="0e5f7-108">Oluşturucu bir erişim değiştiricisi kullanmazsanız, hala varsayılan olarak özel olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0e5f7-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="0e5f7-109">Ancak, [özel](../../../csharp/language-reference/keywords/private.md) değiştiricisi genellikle açıkça sağlamak için kullanılan sınıfın örneği oluşturulamıyor temizleyin.</span><span class="sxs-lookup"><span data-stu-id="0e5f7-109">However, the [private](../../../csharp/language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="0e5f7-110">Özel oluşturucular önlemek için kullanılan olduğunda hiçbir örneği alan veya yöntem, aşağıdaki gibi bir sınıf örneklerini oluşturmaya <xref:System.Math> sınıfı veya ne zaman bir yöntemi çağrıldığında bir sınıfın bir örneği elde etmek için.</span><span class="sxs-lookup"><span data-stu-id="0e5f7-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="0e5f7-111">Sınıfındaki tüm yöntemler statik varsa, tüm sınıf statik yapmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="0e5f7-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="0e5f7-112">Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="0e5f7-112">For more information see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0e5f7-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="0e5f7-113">Example</span></span>  
 <span data-ttu-id="0e5f7-114">Özel Oluşturucu kullanarak bir sınıfın bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0e5f7-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 <span data-ttu-id="0e5f7-115">Aşağıdaki deyim örneğindeki açıklamadan çıkarın, Oluşturucusu koruma düzeyi nedeniyle erişilemez durumda olduğundan, bir hata oluşturacağını dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="0e5f7-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0e5f7-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="0e5f7-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0e5f7-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0e5f7-117">See Also</span></span>  
 [<span data-ttu-id="0e5f7-118">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0e5f7-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0e5f7-119">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="0e5f7-119">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="0e5f7-120">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="0e5f7-120">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="0e5f7-121">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="0e5f7-121">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [<span data-ttu-id="0e5f7-122">Özel</span><span class="sxs-lookup"><span data-stu-id="0e5f7-122">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="0e5f7-123">Ortak</span><span class="sxs-lookup"><span data-stu-id="0e5f7-123">public</span></span>](../../../csharp/language-reference/keywords/public.md)
