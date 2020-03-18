---
title: Özel Yapıcılar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 2f8b93fbeb7c2996f3e2683fe86f159fbfa61a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705450"
---
# <a name="private-constructors-c-programming-guide"></a><span data-ttu-id="49bf3-102">Özel Oluşturucular (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="49bf3-102">Private Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="49bf3-103">Özel bir yapıcı özel bir örnek oluşturucudur.</span><span class="sxs-lookup"><span data-stu-id="49bf3-103">A private constructor is a special instance constructor.</span></span> <span data-ttu-id="49bf3-104">Genellikle yalnızca statik üye içeren sınıflarda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="49bf3-104">It is generally used in classes that contain static members only.</span></span> <span data-ttu-id="49bf3-105">Bir sınıfın bir veya daha fazla özel oluşturucusu varsa ve ortak oluşturucu yoksa, diğer sınıflar (iç içe geçen sınıflar hariç) bu sınıfın örneklerini oluşturamaz.</span><span class="sxs-lookup"><span data-stu-id="49bf3-105">If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.</span></span> <span data-ttu-id="49bf3-106">Örnek:</span><span class="sxs-lookup"><span data-stu-id="49bf3-106">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 <span data-ttu-id="49bf3-107">Boş oluşturucubesi, parametresiz bir oluşturucunun otomatik olarak oluşturulmasını engeller.</span><span class="sxs-lookup"><span data-stu-id="49bf3-107">The declaration of the empty constructor prevents the automatic generation of a parameterless constructor.</span></span> <span data-ttu-id="49bf3-108">Oluşturucuile bir erişim değiştirici kullanmazsanız varsayılan olarak yine de özel olacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="49bf3-108">Note that if you do not use an access modifier with the constructor it will still be private by default.</span></span> <span data-ttu-id="49bf3-109">Ancak, [özel](../../language-reference/keywords/private.md) değiştirici genellikle açıkça sınıf anlık olamaz açık hale getirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="49bf3-109">However, the [private](../../language-reference/keywords/private.md) modifier is usually used explicitly to make it clear that the class cannot be instantiated.</span></span>  
  
 <span data-ttu-id="49bf3-110">Özel oluşturucular, sınıf gibi örnek alanlar veya yöntemler olmadığında veya bir yöntem <xref:System.Math> bir sınıfın örneğini elde etmek için çağrıldığında bir sınıfın örneklerini oluşturmayı önlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="49bf3-110">Private constructors are used to prevent creating instances of a class when there are no instance fields or methods, such as the <xref:System.Math> class, or when a method is called to obtain an instance of a class.</span></span> <span data-ttu-id="49bf3-111">Sınıftaki tüm yöntemler statikse, sınıfın tamamını statik yapmayı düşünün.</span><span class="sxs-lookup"><span data-stu-id="49bf3-111">If all the methods in the class are static, consider making the complete class static.</span></span> <span data-ttu-id="49bf3-112">Daha fazla bilgi için statik [sınıflar ve Statik Sınıf Üyeleri](./static-classes-and-static-class-members.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="49bf3-112">For more information see [Static Classes and Static Class Members](./static-classes-and-static-class-members.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="49bf3-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="49bf3-113">Example</span></span>  
 <span data-ttu-id="49bf3-114">Aşağıda, özel bir oluşturucu kullanan bir sınıfın bir örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="49bf3-114">The following is an example of a class using a private constructor.</span></span>  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 <span data-ttu-id="49bf3-115">Örnekteki aşağıdaki ifadeyi açıklamazsanız, koruma düzeyi nedeniyle oluşturucuya erişilememektedir, çünkü bir hata oluşturacağını unutmayın:</span><span class="sxs-lookup"><span data-stu-id="49bf3-115">Notice that if you uncomment the following statement from the example, it will generate an error because the constructor is inaccessible because of its protection level:</span></span>  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="49bf3-116">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="49bf3-116">C# Language Specification</span></span>  

<span data-ttu-id="49bf3-117">Daha fazla bilgi için [C# Language Specification'daki](/dotnet/csharp/language-reference/language-specification/introduction) [Özel yapıcılar'a](~/_csharplang/spec/classes.md#private-constructors) bakın.</span><span class="sxs-lookup"><span data-stu-id="49bf3-117">For more information, see [Private constructors](~/_csharplang/spec/classes.md#private-constructors) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="49bf3-118">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="49bf3-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="49bf3-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49bf3-119">See also</span></span>

- [<span data-ttu-id="49bf3-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="49bf3-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="49bf3-121">Sınıflar ve Structs</span><span class="sxs-lookup"><span data-stu-id="49bf3-121">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="49bf3-122">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="49bf3-122">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="49bf3-123">Sonlandırıcılar</span><span class="sxs-lookup"><span data-stu-id="49bf3-123">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="49bf3-124">Özel</span><span class="sxs-lookup"><span data-stu-id="49bf3-124">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="49bf3-125">Kamu</span><span class="sxs-lookup"><span data-stu-id="49bf3-125">public</span></span>](../../language-reference/keywords/public.md)
