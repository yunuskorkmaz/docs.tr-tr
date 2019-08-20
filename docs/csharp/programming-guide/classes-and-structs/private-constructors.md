---
title: Özel oluşturucular- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: faa5132845a2d463d3b7d74dc0e0cce21dca61aa
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596219"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="502e4-102">Özel Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="502e4-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="502e4-103">Özel Oluşturucu özel bir örnek oluşturucudur.</span><span class="sxs-lookup"><span data-stu-id="502e4-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="502e4-104">Genellikle yalnızca statik üyeler içeren sınıflarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="502e4-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="502e4-105">Bir sınıfta bir veya daha fazla özel Oluşturucu varsa ve ortak oluşturucu yoksa, diğer sınıflar (iç içe sınıflar hariç) bu sınıfın örneklerini oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="502e4-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="502e4-106">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="502e4-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="502e4-107">Boş oluşturucunun bildirimi parametresiz bir oluşturucunun otomatik olarak oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="502e4-107">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="502e4-108">Oluşturucu ile bir erişim değiştiricisi kullanmıyorsanız, varsayılan olarak hala Private olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="502e4-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="502e4-109">Ancak, [özel](../../language-reference/keywords/private.md) değiştirici genellikle sınıfın örneklendirilmediğini açık hale getirmek için açıkça kullanılır.</span><span class="sxs-lookup"><span data-stu-id="502e4-109">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="502e4-110">Özel oluşturucular, sınıf gibi <xref:System.Math> örnek alan veya yöntem olmadığında veya bir sınıfın örneğini almak için bir yöntem çağrıldığında bir sınıfın örneklerinin oluşturulmasını engellemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="502e4-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="502e4-111">Sınıftaki tüm yöntemler statikse, tüm sınıfı statik hale getirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="502e4-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="502e4-112">Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="502e4-112">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="502e4-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="502e4-113">Example</span></span>  
 <span data-ttu-id="502e4-114">Aşağıda özel Oluşturucu kullanan bir sınıf örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="502e4-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="502e4-115">Aşağıdaki deyimin örnek olarak açıklama eklendiğinde, koruma düzeyi nedeniyle Oluşturucu erişilemediğinden bir hata üretir:</span><span class="sxs-lookup"><span data-stu-id="502e4-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="502e4-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="502e4-116">C# Language Specification</span></span>  

<span data-ttu-id="502e4-117">Daha fazla bilgi için bkz. [ C# dil belirtiminde](../../language-reference/language-specification/index.md) [özel oluşturucular](~/_csharplang/spec/classes.md#private-constructors) .</span><span class="sxs-lookup"><span data-stu-id="502e4-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="502e4-118">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="502e4-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="502e4-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="502e4-119">See also</span></span>

- [<span data-ttu-id="502e4-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="502e4-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="502e4-121">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="502e4-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="502e4-122">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="502e4-122">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="502e4-123">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="502e4-123">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="502e4-124">private</span><span class="sxs-lookup"><span data-stu-id="502e4-124">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="502e4-125">public</span><span class="sxs-lookup"><span data-stu-id="502e4-125">public</span></span>](../../language-reference/keywords/public.md)
