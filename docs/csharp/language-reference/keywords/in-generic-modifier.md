---
title: "in (Genel Değiştirici) (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2af4e27034af0067e81a52c81991edaf5a5415d8
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2018
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="5cd76-102">in (Genel Değiştirici) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5cd76-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="5cd76-103">Genel tür parametreleri için `in` anahtar sözcüğü tür parametre değişken karşıtıdır olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5cd76-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="5cd76-104">Kullanabileceğiniz `in` anahtar sözcüğü genel arabirimler ve temsilciler.</span><span class="sxs-lookup"><span data-stu-id="5cd76-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="5cd76-105">Değişken karşıtı genel parametresi tarafından belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cd76-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="5cd76-106">Bu değişken arabirimleri uygulayan sınıfların örtük dönüştürme ve temsilci türleri örtük dönüştürme için sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cd76-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="5cd76-107">Kovaryans ve kontravaryans genel tür parametrelerindeki referans türleri için desteklenir, ancak değer türlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5cd76-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="5cd76-108">Yalnızca bir yöntemin parametre ve bir yöntemin dönüş türü türü tanımlıyorsa türü karşıtı genel arabirim veya temsilci olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5cd76-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="5cd76-109">`In`, `ref`, ve `out` parametreleri ne oldukları anlamına gelir, sabit olmalıdır eşdeğişken veya karşıtı.</span><span class="sxs-lookup"><span data-stu-id="5cd76-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>
  
 <span data-ttu-id="5cd76-110">Yöntemlerinden daha az türetilmiş türler arabirimi tür parametresi tarafından belirtilen'den bağımsız değişkenleri kabul etmek karşıtı türü parametresine sahip bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5cd76-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="5cd76-111">Örneğin, <xref:System.Collections.Generic.IComparer%601> arabirimi, T türü karşıtı, bir nesnenin atayabilirsiniz `IComparer<Person>` bir nesne türüne `IComparer<Employee>` , herhangi bir özel dönüştürme yöntem kullanmadan türü `Employee` devralır `Person`.</span><span class="sxs-lookup"><span data-stu-id="5cd76-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>  
  
 <span data-ttu-id="5cd76-112">Aynı türde, ancak daha az türetilmiş genel tür parametresi olan başka bir temsilci karşıtı temsilci atanabilir.</span><span class="sxs-lookup"><span data-stu-id="5cd76-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
 <span data-ttu-id="5cd76-113">Daha fazla bilgi için bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="5cd76-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="contravariant-generic-interface"></a><span data-ttu-id="5cd76-114">Karşıtı genel arabirimi</span><span class="sxs-lookup"><span data-stu-id="5cd76-114">Contravariant generic interface</span></span>   

 <span data-ttu-id="5cd76-115">Aşağıdaki örnek, bildirme, genişletmek ve karşıtı genel arabirimini uygulayan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cd76-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="5cd76-116">Örtük dönüştürme bu arabirimi uygulayan sınıflar için nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cd76-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="contravariant-generic-delegate"></a><span data-ttu-id="5cd76-117">Karşıtı Genel temsilci</span><span class="sxs-lookup"><span data-stu-id="5cd76-117">Contravariant generic delegate</span></span>  

 <span data-ttu-id="5cd76-118">Aşağıdaki örnek, bildirme, oluşturma ve karşıtı genel temsilcisi çağırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5cd76-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="5cd76-119">Ayrıca, bir temsilci türü örtük olarak nasıl dönüştürebilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="5cd76-119">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5cd76-120">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="5cd76-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5cd76-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5cd76-121">See Also</span></span>  
 [<span data-ttu-id="5cd76-122">out</span><span class="sxs-lookup"><span data-stu-id="5cd76-122">out</span></span>](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [<span data-ttu-id="5cd76-123">Kovaryans ve Kontravaryans</span><span class="sxs-lookup"><span data-stu-id="5cd76-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [<span data-ttu-id="5cd76-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="5cd76-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
