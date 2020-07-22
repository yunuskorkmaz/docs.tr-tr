---
title: Özel oluşturucular-C# Programlama Kılavuzu
description: Özel Oluşturucu, bir nesnenin nasıl oluşturulabileceğini kısıtlamak için kullanılan C# içindeki özel bir örnek oluşturucudur. Bunlar, fabrika yöntemleriyle veya diğer yapım deyimleri ile kullanılabilir.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: a6b86ccb870da0262bcbc516e176e00d17724f9f
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864065"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="b68cd-104">Özel Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b68cd-104">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="b68cd-105">Özel Oluşturucu özel bir örnek oluşturucudur.</span><span class="sxs-lookup"><span data-stu-id="b68cd-105">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="b68cd-106">Genellikle yalnızca statik üyeler içeren sınıflarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b68cd-106">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="b68cd-107">Bir sınıfta bir veya daha fazla özel Oluşturucu varsa ve ortak oluşturucu yoksa, diğer sınıflar (iç içe sınıflar hariç) bu sınıfın örneklerini oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="b68cd-107">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="b68cd-108">Örnek:</span><span class="sxs-lookup"><span data-stu-id="b68cd-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="b68cd-109">Boş oluşturucunun bildirimi parametresiz bir oluşturucunun otomatik olarak oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="b68cd-109">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="b68cd-110">Oluşturucu ile bir erişim değiştiricisi kullanmıyorsanız, varsayılan olarak hala Private olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b68cd-110">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="b68cd-111">Ancak, [özel](../../language-reference/keywords/private.md) değiştirici genellikle sınıfın örneklendirilmediğini açık hale getirmek için açıkça kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b68cd-111">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="b68cd-112">Özel oluşturucular, sınıf gibi örnek alan veya yöntem olmadığında <xref:System.Math> veya bir sınıfın örneğini almak için bir yöntem çağrıldığında bir sınıfın örneklerinin oluşturulmasını engellemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b68cd-112">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="b68cd-113">Sınıftaki tüm yöntemler statikse, tüm sınıfı statik hale getirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="b68cd-113">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="b68cd-114">Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="b68cd-114">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b68cd-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="b68cd-115">Example</span></span>  
 <span data-ttu-id="b68cd-116">Aşağıda özel Oluşturucu kullanan bir sınıf örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b68cd-116">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="b68cd-117">Aşağıdaki deyimin örnek olarak açıklama eklendiğinde, koruma düzeyi nedeniyle Oluşturucu erişilemediğinden bir hata üretir:</span><span class="sxs-lookup"><span data-stu-id="b68cd-117">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="b68cd-118">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="b68cd-118">C# Language Specification</span></span>  

<span data-ttu-id="b68cd-119">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [özel oluşturucular](~/_csharplang/spec/classes.md#private-constructors) .</span><span class="sxs-lookup"><span data-stu-id="b68cd-119">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="b68cd-120">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="b68cd-120">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b68cd-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b68cd-121">See also</span></span>

- [<span data-ttu-id="b68cd-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b68cd-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b68cd-123">Sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="b68cd-123">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="b68cd-124">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="b68cd-124">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="b68cd-125">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="b68cd-125">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="b68cd-126">private</span><span class="sxs-lookup"><span data-stu-id="b68cd-126">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="b68cd-127">genel</span><span class="sxs-lookup"><span data-stu-id="b68cd-127">public</span></span>](../../language-reference/keywords/public.md)
