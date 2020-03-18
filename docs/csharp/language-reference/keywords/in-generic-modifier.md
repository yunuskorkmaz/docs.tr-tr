---
title: in (Genel Değiştirici) - C# Başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713481"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="b1140-102">in (Genel Değiştirici) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b1140-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="b1140-103">Genel tür parametreleri `in` için, anahtar kelime tür parametresinin karşıt olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b1140-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="b1140-104">Anahtar kelimeyi `in` genel arabirimlerde ve temsilcilerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1140-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="b1140-105">Kontravariance, genel parametre tarafından belirtilenden daha az türetilmiş bir tür kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b1140-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="b1140-106">Bu, karşıt arabirimleri uygulayan sınıfların örtük olarak dönüştürülmesine ve temsilci türlerinin örtülü olarak dönüştürülmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b1140-106">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="b1140-107">Genel tür parametrelerindeki tutarlılık ve kontravarlık başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b1140-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="b1140-108">Bir tür, genel bir arabirimde karşıtlık olarak bildirilebilir veya yalnızca yöntemin geri dönüş türünü değil, yöntemin parametrelerinin türünü tanımlıyorsa temsilci olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b1140-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="b1140-109">`In`, `ref`, `out` ve parametreler değişmez olmalıdır, yani ne eşdeğişken ne de kontrdeğişkendir.</span><span class="sxs-lookup"><span data-stu-id="b1140-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="b1140-110">Karşıt tür parametresi olan bir arabirim, yöntemlerinin arabirim türü parametresi tarafından belirtilenlerden daha az türdeki bağımsız değişkenleri kabul etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="b1140-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="b1140-111"><xref:System.Collections.Generic.IComparer%601> Örneğin, arabirimde, T türü zıttır, devralıyorsa `IComparer<Person>` `IComparer<Employee>` `Employee` `Person`herhangi bir özel dönüştürme yöntemi kullanmadan türünün bir nesnesini türün nesnesine atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1140-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="b1140-112">Karşıt bir temsilci, aynı türden, ancak daha az türetilmiş genel tür parametresi ile başka bir temsilci atanabilir.</span><span class="sxs-lookup"><span data-stu-id="b1140-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="b1140-113">Daha fazla bilgi için Bkz. [Covariance ve Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="b1140-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="b1140-114">Karşıt genel arabirim</span><span class="sxs-lookup"><span data-stu-id="b1140-114">Contravariant generic interface</span></span>

<span data-ttu-id="b1140-115">Aşağıdaki örnek, karşıt genel arabirimi nasıl beyan edeceğiz, genişletecek ve uygulayacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1140-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="b1140-116">Ayrıca, bu arabirimi uygulayan sınıflar için örtülü dönüştürmeyi nasıl kullanabileceğinizi de gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1140-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="b1140-117">Karşıt genel temsilci</span><span class="sxs-lookup"><span data-stu-id="b1140-117">Contravariant generic delegate</span></span>

<span data-ttu-id="b1140-118">Aşağıdaki örnek, karşıt bir genel temsilcinin nasıl bildirilen, anlık olarak bildirilen ve çağırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1140-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="b1140-119">Ayrıca, bir temsilci türünü dolaylı olarak nasıl dönüştürebileceğinizi de gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1140-119">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="b1140-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b1140-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="b1140-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1140-121">See also</span></span>

- [<span data-ttu-id="b1140-122">çıkış</span><span class="sxs-lookup"><span data-stu-id="b1140-122">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="b1140-123">Covariance ve Kontravariance</span><span class="sxs-lookup"><span data-stu-id="b1140-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="b1140-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="b1140-124">Modifiers</span></span>](index.md)
