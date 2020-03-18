---
title: anahtar kelime (genel değiştirici) - C# Başvuru
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 97ddae2efe55be89840f7a483c18d61259020283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713283"
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="91b70-102">out (genel değiştirici) (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="91b70-102">out (generic modifier) (C# Reference)</span></span>

<span data-ttu-id="91b70-103">Genel tür parametreleri `out` için, anahtar kelime tür parametresinin ortak olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="91b70-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="91b70-104">Anahtar kelimeyi `out` genel arabirimlerde ve temsilcilerde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91b70-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="91b70-105">Covariance, genel parametre tarafından belirtilenden daha türemiş bir tür kullanmanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="91b70-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="91b70-106">Bu, ortak değişken arabirimleri uygulayan sınıfların örtülü olarak dönüştürülmesine ve temsilci türlerinin örtülü olarak dönüştürülmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="91b70-106">This allows for implicit conversion of classes that implement covariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="91b70-107">Tutarlılık ve kontravariance başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="91b70-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="91b70-108">Eşdeğişken türü parametresi olan bir arabirim, yöntemlerinin tür parametresi tarafından belirtilenlerden daha fazla tür döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="91b70-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="91b70-109">Örneğin, .NET Framework 4'te, <xref:System.Collections.Generic.IEnumerable%601>T türü nde ortak olduğundan, özel `IEnumerable(Of String)` dönüştürme yöntemleri kullanmadan `IEnumerable(Of Object)` türün bir nesnesini türün nesnesine atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91b70-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="91b70-110">Ortak değişken temsilcisine aynı türden, ancak daha türetilmiş genel tür parametresi olan başka bir temsilci atanabilir.</span><span class="sxs-lookup"><span data-stu-id="91b70-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

<span data-ttu-id="91b70-111">Daha fazla bilgi için Bkz. [Covariance ve Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="91b70-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="example---covariant-generic-interface"></a><span data-ttu-id="91b70-112">Örnek - ortak genel arabirim</span><span class="sxs-lookup"><span data-stu-id="91b70-112">Example - covariant generic interface</span></span>

<span data-ttu-id="91b70-113">Aşağıdaki örnek, bir birlikte varyant genel arabirimi nasıl bildirecek, genişletecek ve uygulayacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="91b70-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="91b70-114">Ayrıca, bir birlikte varyant arabirimi uygulayan sınıflar için örtülü dönüştürmenin nasıl kullanılacağını da gösterir.</span><span class="sxs-lookup"><span data-stu-id="91b70-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

<span data-ttu-id="91b70-115">Genel bir arabirimde, bir tür parametresi aşağıdaki koşulları karşılarsa eş değişken olarak bildirilebilir:</span><span class="sxs-lookup"><span data-stu-id="91b70-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="91b70-116">Tür parametresi yalnızca arabirim yöntemlerinin dönüş türü olarak kullanılır ve yöntem bağımsız değişkenleri türü olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="91b70-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="91b70-117">Bu kuralın bir istisnası vardır.</span><span class="sxs-lookup"><span data-stu-id="91b70-117">There is one exception to this rule.</span></span> <span data-ttu-id="91b70-118">Bir eşvaryant arabiriminde yöntem parametresi olarak karşıt bir genel temsilciniz varsa, bu temsilci için genel tür parametresi olarak ortak değişken türünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91b70-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="91b70-119">Ortak ve karşıt genel temsilciler hakkında daha fazla bilgi için, [Temsilcilerde Varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Func ve Action Generic Delegates için Varyans kullanma'ya](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="91b70-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="91b70-120">Tür parametresi arabirim yöntemleri için genel bir kısıtlama olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="91b70-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>

## <a name="example---covariant-generic-delegate"></a><span data-ttu-id="91b70-121">Örnek - ortak varyant genel temsilci</span><span class="sxs-lookup"><span data-stu-id="91b70-121">Example - covariant generic delegate</span></span>

<span data-ttu-id="91b70-122">Aşağıdaki örnek, ortak değişken bir genel temsilcinin nasıl bildirilen, anlık olarak bildirilen ve çağırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="91b70-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="91b70-123">Ayrıca, temsilci türlerinin nasıl dönüştürüldüğünü de gösterir.</span><span class="sxs-lookup"><span data-stu-id="91b70-123">It also shows how to implicitly convert delegate types.</span></span>

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

<span data-ttu-id="91b70-124">Genel bir temsilcide, yalnızca yöntem dönüş türü olarak kullanılırsa ve yöntem bağımsız değişkenleri için kullanılmazsa, bir tür ortak değişken olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="91b70-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="91b70-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="91b70-125">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="91b70-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91b70-126">See also</span></span>

- [<span data-ttu-id="91b70-127">Genel Arabirimlerde Varyans</span><span class="sxs-lookup"><span data-stu-id="91b70-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="91b70-128">Inç</span><span class="sxs-lookup"><span data-stu-id="91b70-128">in</span></span>](in-generic-modifier.md)
- [<span data-ttu-id="91b70-129">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="91b70-129">Modifiers</span></span>](index.md)
