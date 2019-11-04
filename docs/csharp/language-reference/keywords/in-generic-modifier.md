---
title: ın (genel değiştirici)- C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 0806169b9b1c3521dcf89f5ea0fa5aec188030c2
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422782"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="5b188-102">in (Genel Değiştirici) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5b188-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="5b188-103">Genel tür parametreleri için `in` anahtar sözcüğü tür parametresinin değişken karşıtı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5b188-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="5b188-104">Genel arabirimlerde ve temsilcilerde `in` anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b188-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="5b188-105">Değişken Varyans, genel parametre ile belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b188-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="5b188-106">Bu, değişken karşıtı arabirimler uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5b188-106">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="5b188-107">Genel tür parametrelerindeki Kovaryans ve değişken Varyans, başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5b188-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="5b188-108">Bir tür, genel bir arabirimde veya bir yöntemin dönüş türü değil, bir yöntemin parametrelerinin türünü tanımlıyorsa yalnızca bir veya temsilcisinde değişken karşıtı olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="5b188-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="5b188-109">`In`, `ref`ve `out` parametreleri sabit olmalıdır, yani bunlar birlikte değişken veya değişken karşıtı değil.</span><span class="sxs-lookup"><span data-stu-id="5b188-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="5b188-110">Değişken karşıtı tür parametresine sahip bir arabirim, yöntemlerinin, arabirim türü parametresi tarafından belirtilenden daha az türetilmiş türlerin bağımsız değişkenlerini kabul etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5b188-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="5b188-111">Örneğin, <xref:System.Collections.Generic.IComparer%601> arabiriminde T yazın, `IComparer<Person>` türünün bir nesnesini `IComparer<Employee>` türünün bir nesnesine `Employee` devr`Person`alırsa herhangi bir özel dönüştürme yöntemini kullanmadan atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b188-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="5b188-112">Değişken karşıtı bir temsilciye aynı türde başka bir temsilci atanabilir, ancak daha az türetilmiş bir genel tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="5b188-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="5b188-113">Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="5b188-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="5b188-114">Değişken karşıtı genel arabirim</span><span class="sxs-lookup"><span data-stu-id="5b188-114">Contravariant generic interface</span></span>

<span data-ttu-id="5b188-115">Aşağıdaki örnek, bir değişken karşıtı genel arabirimin nasıl bildirileceği, genişletileceği ve uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b188-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="5b188-116">Ayrıca, bu arabirimi uygulayan sınıflar için örtük dönüştürmeyi nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b188-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="5b188-117">Değişken karşıtı genel temsilci</span><span class="sxs-lookup"><span data-stu-id="5b188-117">Contravariant generic delegate</span></span>

<span data-ttu-id="5b188-118">Aşağıdaki örnek, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini, örneklendirilemeyeceğini ve çağıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5b188-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="5b188-119">Ayrıca, bir temsilci türünü örtülü olarak nasıl dönüştürebileceğiniz de gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5b188-119">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="5b188-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5b188-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5b188-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b188-121">See also</span></span>

- [<span data-ttu-id="5b188-122">out</span><span class="sxs-lookup"><span data-stu-id="5b188-122">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="5b188-123">Kovaryans ve Kontravaryans</span><span class="sxs-lookup"><span data-stu-id="5b188-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="5b188-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="5b188-124">Modifiers</span></span>](index.md)
