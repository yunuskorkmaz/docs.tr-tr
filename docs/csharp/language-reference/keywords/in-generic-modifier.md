---
description: ın (genel değiştirici)-C# başvurusu
title: ın (genel değiştirici)-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: feae17be7bdf29f6bc90e8c85b3878d4714699f4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118462"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="5d56d-103">in (Genel Değiştirici) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5d56d-103">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="5d56d-104">Genel tür parametreleri için, `in` anahtar sözcüğü tür parametresinin değişken karşıtı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5d56d-104">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="5d56d-105">`in`Genel arabirimlerde ve temsilcilerde anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d56d-105">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="5d56d-106">Değişken Varyans, genel parametre ile belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d56d-106">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="5d56d-107">Bu, değişken karşıtı arabirimler uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d56d-107">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="5d56d-108">Genel tür parametrelerindeki Kovaryans ve değişken Varyans, başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5d56d-108">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="5d56d-109">Bir tür, genel bir arabirimde veya bir yöntemin dönüş türü değil, bir yöntemin parametrelerinin türünü tanımlıyorsa yalnızca bir veya temsilcisinde değişken karşıtı olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="5d56d-109">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="5d56d-110">`In`, `ref` , ve `out` parametrelerinin sabit olması gerekir, yani bunlar birlikte değişken veya değişken karşıtı değildir.</span><span class="sxs-lookup"><span data-stu-id="5d56d-110">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="5d56d-111">Değişken karşıtı tür parametresine sahip bir arabirim, yöntemlerinin, arabirim türü parametresi tarafından belirtilenden daha az türetilmiş türlerin bağımsız değişkenlerini kabul etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5d56d-111">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="5d56d-112">Örneğin, <xref:System.Collections.Generic.IComparer%601> arabiriminde T yazın, tür bir nesnesini, `IComparer<Person>` `IComparer<Employee>` devralırsa özel bir dönüştürme yöntemini kullanmadan, türün bir nesnesine atayabilirsiniz `Employee` `Person` .</span><span class="sxs-lookup"><span data-stu-id="5d56d-112">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="5d56d-113">Değişken karşıtı bir temsilciye aynı türde başka bir temsilci atanabilir, ancak daha az türetilmiş bir genel tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="5d56d-113">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="5d56d-114">Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="5d56d-114">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="5d56d-115">Değişken karşıtı genel arabirim</span><span class="sxs-lookup"><span data-stu-id="5d56d-115">Contravariant generic interface</span></span>

<span data-ttu-id="5d56d-116">Aşağıdaki örnek, bir değişken karşıtı genel arabirimin nasıl bildirileceği, genişletileceği ve uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d56d-116">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="5d56d-117">Ayrıca, bu arabirimi uygulayan sınıflar için örtük dönüştürmeyi nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d56d-117">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="5d56d-118">Değişken karşıtı genel temsilci</span><span class="sxs-lookup"><span data-stu-id="5d56d-118">Contravariant generic delegate</span></span>

<span data-ttu-id="5d56d-119">Aşağıdaki örnek, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini, örneklendirilemeyeceğini ve çağıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5d56d-119">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="5d56d-120">Ayrıca, bir temsilci türünü örtülü olarak nasıl dönüştürebileceğiniz de gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5d56d-120">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="5d56d-121">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5d56d-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5d56d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d56d-122">See also</span></span>

- [<span data-ttu-id="5d56d-123">dışı</span><span class="sxs-lookup"><span data-stu-id="5d56d-123">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="5d56d-124">Kovaryans ve değişken sapması</span><span class="sxs-lookup"><span data-stu-id="5d56d-124">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="5d56d-125">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="5d56d-125">Modifiers</span></span>](index.md)
