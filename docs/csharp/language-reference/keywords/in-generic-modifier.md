---
title: "in (Genel Değiştirici) (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 84773fca826b5a25679f1385a11c51b590ea20f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="b3bd6-102">in (Genel Değiştirici) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b3bd6-102">in (Generic Modifier) (C# Reference)</span></span>
<span data-ttu-id="b3bd6-103">Genel tür parametreleri için `in` anahtar sözcüğü tür parametre değişken karşıtıdır olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="b3bd6-104">Kullanabileceğiniz `in` anahtar sözcüğü genel arabirimler ve temsilciler.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="b3bd6-105">Değişken karşıtı genel parametresi tarafından belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="b3bd6-106">Bu değişken arabirimleri uygulayan sınıfların örtük dönüştürme ve temsilci türleri örtük dönüştürme için sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="b3bd6-107">Kovaryans ve kontravaryans genel tür parametrelerindeki referans türleri için desteklenir, ancak değer türlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="b3bd6-108">Yalnızca bir tür yöntemi bağımsız değişken olarak kullanılan ve yöntemin dönüş türü olarak kullanılmayan bir türü karşıtı genel arabirim veya temsilci olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-108">A type can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="b3bd6-109">`Ref`ve `out` parametreleri değişken olamaz.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-109">`Ref` and `out` parameters cannot be variant.</span></span>  
  
 <span data-ttu-id="b3bd6-110">Yöntemlerinden daha az türetilmiş türler arabirimi tür parametresi tarafından belirtilen'den bağımsız değişkenleri kabul etmek karşıtı türü parametresine sahip bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="b3bd6-111">Örneğin, çünkü .NET Framework 4'te içinde <xref:System.Collections.Generic.IComparer%601> arabirimi, T türü karşıtı, bir nesnenin atayabilirsiniz `IComparer(Of Person)` bir nesne türüne `IComparer(Of Employee)` , herhangi bir özel dönüştürme yöntem kullanmadan türü `Employee` devralır `Person`.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-111">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>  
  
 <span data-ttu-id="b3bd6-112">Aynı türde, ancak daha az türetilmiş genel tür parametresi olan başka bir temsilci karşıtı temsilci atanabilir.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
 <span data-ttu-id="b3bd6-113">Daha fazla bilgi için bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="b3bd6-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3bd6-114">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3bd6-114">Example</span></span>  
 <span data-ttu-id="b3bd6-115">Aşağıdaki örnek, bildirme, genişletmek ve karşıtı genel arabirimini uygulayan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="b3bd6-116">Örtük dönüştürme bu arabirimi uygulayan sınıflar için nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="b3bd6-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="b3bd6-117">Example</span></span>  
 <span data-ttu-id="b3bd6-118">Aşağıdaki örnek, bildirme, oluşturma ve karşıtı genel temsilcisi çağırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="b3bd6-119">Ayrıca, bir temsilci türü örtük olarak nasıl dönüştürebilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-119">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="b3bd6-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="b3bd6-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b3bd6-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3bd6-121">See Also</span></span>  
 [<span data-ttu-id="b3bd6-122">çıkışı</span><span class="sxs-lookup"><span data-stu-id="b3bd6-122">out</span></span>](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [<span data-ttu-id="b3bd6-123">Kovaryans ve kontravaryans</span><span class="sxs-lookup"><span data-stu-id="b3bd6-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="b3bd6-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="b3bd6-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
