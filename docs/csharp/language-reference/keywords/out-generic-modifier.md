---
title: out anahtar sözcüğü (genel değiştirici) C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 121faf46f1c5ba50f132dc180e9d4f802ac91696
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422655"
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="d8797-102">Out (genel değiştirici) (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="d8797-102">out (generic modifier) (C# Reference)</span></span>

<span data-ttu-id="d8797-103">Genel tür parametreleri için `out` anahtar sözcüğü, tür parametresinin birlikte değişken olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d8797-103">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="d8797-104">Genel arabirimlerde ve temsilcilerde `out` anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8797-104">You can use the `out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="d8797-105">Kovaryans, genel parametre ile belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8797-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="d8797-106">Bu, covaryant arabirimlerini uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8797-106">This allows for implicit conversion of classes that implement covariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="d8797-107">Kovaryans ve değişken Varyans, başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d8797-107">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="d8797-108">Covaryant türü parametresine sahip bir arabirim, yöntemlerinin tür parametresiyle belirtenlerden daha fazla türetilmiş tür döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d8797-108">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="d8797-109">Örneğin, .NET Framework 4 ' te, <xref:System.Collections.Generic.IEnumerable%601>' de T yazın ve bir özel dönüştürme yöntemi kullanmadan `IEnumerable(Of String)` türünün bir nesnesini `IEnumerable(Of Object)` türünün bir nesnesine atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8797-109">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="d8797-110">Birlikte değişken temsilcisine aynı türde başka bir temsilci atanabilir, ancak daha türetilmiş bir genel tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="d8797-110">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

<span data-ttu-id="d8797-111">Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="d8797-111">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="example---covariant-generic-interface"></a><span data-ttu-id="d8797-112">Örnek-birlikte değişken genel arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8797-112">Example - covariant generic interface</span></span>

<span data-ttu-id="d8797-113">Aşağıdaki örnek, bir covaryant genel arabiriminin nasıl bildirileceği, genişletileceği ve uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8797-113">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="d8797-114">Ayrıca, birlikte değişken arabirimi uygulayan sınıflar için örtük dönüştürmeyi nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8797-114">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

<span data-ttu-id="d8797-115">Bir genel arabirimde, bir tür parametresi aşağıdaki koşullara uygunsa birlikte değişken olarak bildirilemez:</span><span class="sxs-lookup"><span data-stu-id="d8797-115">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="d8797-116">Tür parametresi yalnızca Arabirim yöntemlerinin dönüş türü olarak kullanılır ve Yöntem bağımsız değişkenlerinin türü olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="d8797-116">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d8797-117">Bu kural için bir özel durum var.</span><span class="sxs-lookup"><span data-stu-id="d8797-117">There is one exception to this rule.</span></span> <span data-ttu-id="d8797-118">Bir covaryant arayüzünde bir yöntem parametresi olarak bir değişken karşıtı genel temsilciniz varsa, bu temsilci için ortak tür parametresi olarak covaryant türü ' ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8797-118">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="d8797-119">Covaryant ve değişken karşıtı genel Temsilciler hakkında daha fazla bilgi için bkz. [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Func ve eylem genel temsilcileri için varyans kullanma](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="d8797-119">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="d8797-120">Tür parametresi, arabirim yöntemleri için genel kısıtlama olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="d8797-120">The type parameter is not used as a generic constraint for the interface methods.</span></span>

## <a name="example---covariant-generic-delegate"></a><span data-ttu-id="d8797-121">Örnek-birlikte değişken genel temsilcisi</span><span class="sxs-lookup"><span data-stu-id="d8797-121">Example - covariant generic delegate</span></span>

<span data-ttu-id="d8797-122">Aşağıdaki örnek, bir covaryant genel temsilcisinin nasıl bildirilemeyeceğini, örneklendirilemeyeceğini ve çağıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8797-122">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="d8797-123">Ayrıca, temsilci türlerini örtük olarak nasıl dönüştürebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d8797-123">It also shows how to implicitly convert delegate types.</span></span>

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

<span data-ttu-id="d8797-124">Genel bir temsilcisinde, bir tür yalnızca bir yöntem dönüş türü olarak kullanılıyorsa ve Yöntem bağımsız değişkenleri için kullanılmazsa, birlikte değişken olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="d8797-124">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d8797-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d8797-125">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d8797-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8797-126">See also</span></span>

- [<span data-ttu-id="d8797-127">Genel Arabirimlerde Varyans</span><span class="sxs-lookup"><span data-stu-id="d8797-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="d8797-128">in</span><span class="sxs-lookup"><span data-stu-id="d8797-128">in</span></span>](in-generic-modifier.md)
- [<span data-ttu-id="d8797-129">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="d8797-129">Modifiers</span></span>](index.md)
