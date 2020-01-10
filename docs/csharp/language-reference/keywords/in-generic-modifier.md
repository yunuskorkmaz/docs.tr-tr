---
title: ın (genel değiştirici)- C# başvuru
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713481"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="29792-102">in (Genel Değiştirici) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="29792-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="29792-103">Genel tür parametreleri için `in` anahtar sözcüğü tür parametresinin değişken karşıtı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="29792-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="29792-104">Genel arabirimlerde ve temsilcilerde `in` anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29792-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="29792-105">Değişken Varyans, genel parametre ile belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="29792-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="29792-106">Bu, değişken karşıtı arabirimler uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="29792-106">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="29792-107">Genel tür parametrelerindeki Kovaryans ve değişken Varyans, başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="29792-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="29792-108">Bir tür, genel bir arabirimde veya bir yöntemin dönüş türü değil, bir yöntemin parametrelerinin türünü tanımlıyorsa yalnızca bir veya temsilcisinde değişken karşıtı olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="29792-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="29792-109">`In`, `ref`ve `out` parametreleri sabit olmalıdır, yani bunlar birlikte değişken veya değişken karşıtı değil.</span><span class="sxs-lookup"><span data-stu-id="29792-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="29792-110">Değişken karşıtı tür parametresine sahip bir arabirim, yöntemlerinin, arabirim türü parametresi tarafından belirtilenden daha az türetilmiş türlerin bağımsız değişkenlerini kabul etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="29792-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="29792-111">Örneğin, <xref:System.Collections.Generic.IComparer%601> arabiriminde T yazın, `IComparer<Person>` türünün bir nesnesini `IComparer<Employee>` türünün bir nesnesine `Employee` devr`Person`alırsa herhangi bir özel dönüştürme yöntemini kullanmadan atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29792-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="29792-112">Değişken karşıtı bir temsilciye aynı türde başka bir temsilci atanabilir, ancak daha az türetilmiş bir genel tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="29792-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="29792-113">Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="29792-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="29792-114">Değişken karşıtı genel arabirim</span><span class="sxs-lookup"><span data-stu-id="29792-114">Contravariant generic interface</span></span>

<span data-ttu-id="29792-115">Aşağıdaki örnek, bir değişken karşıtı genel arabirimin nasıl bildirileceği, genişletileceği ve uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29792-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="29792-116">Ayrıca, bu arabirimi uygulayan sınıflar için örtük dönüştürmeyi nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="29792-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="29792-117">Değişken karşıtı genel temsilci</span><span class="sxs-lookup"><span data-stu-id="29792-117">Contravariant generic delegate</span></span>

<span data-ttu-id="29792-118">Aşağıdaki örnek, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini, örneklendirilemeyeceğini ve çağıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29792-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="29792-119">Ayrıca, bir temsilci türünü örtülü olarak nasıl dönüştürebileceğiniz de gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="29792-119">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="29792-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="29792-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="29792-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29792-121">See also</span></span>

- [<span data-ttu-id="29792-122">out</span><span class="sxs-lookup"><span data-stu-id="29792-122">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="29792-123">Kovaryans ve Kontravaryans</span><span class="sxs-lookup"><span data-stu-id="29792-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="29792-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="29792-124">Modifiers</span></span>](index.md)
