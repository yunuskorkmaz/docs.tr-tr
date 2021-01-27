---
title: Özel oluşturucular-C# Programlama Kılavuzu
description: Özel Oluşturucu, bir nesnenin nasıl oluşturulabileceğini kısıtlamak için kullanılan C# içindeki özel bir örnek oluşturucudur. Bunlar, fabrika yöntemleriyle veya diğer yapım deyimleri ile kullanılabilir.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 980a638fbe6250b3d47a3effc7cbad5ec57fbcad
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899418"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="13083-104">Özel Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="13083-104">Private Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="13083-105">Özel Oluşturucu özel bir örnek oluşturucudur.</span><span class="sxs-lookup"><span data-stu-id="13083-105">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="13083-106">Genellikle yalnızca statik üyeler içeren sınıflarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13083-106">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="13083-107">Bir sınıfta bir veya daha fazla özel Oluşturucu varsa ve ortak oluşturucu yoksa, diğer sınıflar (iç içe sınıflar hariç) bu sınıfın örneklerini oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="13083-107">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="13083-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="13083-108">For example:</span></span>  
  
 [!code-csharp[ClassWithPrivateConstructorExample#1](snippets/private-constructors/Program.cs#1)]
  
 <span data-ttu-id="13083-109">Boş oluşturucunun bildirimi parametresiz bir oluşturucunun otomatik olarak oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="13083-109">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="13083-110">Oluşturucu ile bir erişim değiştiricisi kullanmıyorsanız, varsayılan olarak hala Private olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="13083-110">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="13083-111">Ancak, [özel](../../language-reference/keywords/private.md) değiştirici genellikle sınıfın örneklendirilmediğini açık hale getirmek için açıkça kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13083-111">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="13083-112">Özel oluşturucular, sınıf gibi örnek alan veya yöntem olmadığında <xref:System.Math> veya bir sınıfın örneğini almak için bir yöntem çağrıldığında bir sınıfın örneklerinin oluşturulmasını engellemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="13083-112">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="13083-113">Sınıftaki tüm yöntemler statikse, tüm sınıfı statik hale getirmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="13083-113">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="13083-114">Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="13083-114">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="13083-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="13083-115">Example</span></span>  

 <span data-ttu-id="13083-116">Aşağıda özel Oluşturucu kullanan bir sınıf örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="13083-116">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[CounterClassWithPrivateConstructor#2](snippets/private-constructors/Program.cs#2)]
  
 <span data-ttu-id="13083-117">Aşağıdaki deyimin örnek olarak açıklama eklendiğinde, koruma düzeyi nedeniyle Oluşturucu erişilemediğinden bir hata üretir:</span><span class="sxs-lookup"><span data-stu-id="13083-117">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[ErrorInstantiatingUsingPrivateConstructor#13](snippets/private-constructors/Program.cs#3)]
  
## <a name="c-language-specification"></a><span data-ttu-id="13083-118">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="13083-118">C# Language Specification</span></span>  

<span data-ttu-id="13083-119">Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [özel oluşturucular](~/_csharplang/spec/classes.md#private-constructors) .</span><span class="sxs-lookup"><span data-stu-id="13083-119">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="13083-120">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="13083-120">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="13083-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13083-121">See also</span></span>

- [<span data-ttu-id="13083-122">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="13083-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="13083-123">Sınıflar ve Yapılar</span><span class="sxs-lookup"><span data-stu-id="13083-123">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="13083-124">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="13083-124">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="13083-125">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="13083-125">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="13083-126">özelleştirme</span><span class="sxs-lookup"><span data-stu-id="13083-126">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="13083-127">genel</span><span class="sxs-lookup"><span data-stu-id="13083-127">public</span></span>](../../language-reference/keywords/public.md)
