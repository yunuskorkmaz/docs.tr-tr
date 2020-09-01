---
description: out anahtar sözcüğü (genel değiştirici)-C# başvurusu
title: out anahtar sözcüğü (genel değiştirici)-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 84f3647309c0772f6ae61d3614f8649fe277f153
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142342"
---
# <a name="out-generic-modifier-c-reference"></a><span data-ttu-id="eb7d3-103">Out (genel değiştirici) (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="eb7d3-103">out (generic modifier) (C# Reference)</span></span>

<span data-ttu-id="eb7d3-104">Genel tür parametreleri için, `out` anahtar sözcüğü tür parametresinin birlikte değişken olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-104">For generic type parameters, the `out` keyword specifies that the type parameter is covariant.</span></span> <span data-ttu-id="eb7d3-105">`out`Genel arabirimlerde ve temsilcilerde anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-105">You can use the `out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="eb7d3-106">Kovaryans, genel parametre ile belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-106">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="eb7d3-107">Bu, covaryant arabirimlerini uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-107">This allows for implicit conversion of classes that implement covariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="eb7d3-108">Kovaryans ve değişken Varyans, başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-108">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="eb7d3-109">Covaryant türü parametresine sahip bir arabirim, yöntemlerinin tür parametresiyle belirtenlerden daha fazla türetilmiş tür döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-109">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="eb7d3-110">Örneğin, içinde .NET Framework 4 ' te, <xref:System.Collections.Generic.IEnumerable%601> T türü de birlikte değişken ise, `IEnumerable(Of String)` herhangi bir özel dönüştürme yöntemi kullanmadan türdeki bir nesneye türünün bir nesnesine atayabilirsiniz `IEnumerable(Of Object)` .</span><span class="sxs-lookup"><span data-stu-id="eb7d3-110">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="eb7d3-111">Birlikte değişken temsilcisine aynı türde başka bir temsilci atanabilir, ancak daha türetilmiş bir genel tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-111">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

<span data-ttu-id="eb7d3-112">Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="eb7d3-112">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="example---covariant-generic-interface"></a><span data-ttu-id="eb7d3-113">Örnek-birlikte değişken genel arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb7d3-113">Example - covariant generic interface</span></span>

<span data-ttu-id="eb7d3-114">Aşağıdaki örnek, bir covaryant genel arabiriminin nasıl bildirileceği, genişletileceği ve uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-114">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="eb7d3-115">Ayrıca, birlikte değişken arabirimi uygulayan sınıflar için örtük dönüştürmeyi nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-115">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

<span data-ttu-id="eb7d3-116">Bir genel arabirimde, bir tür parametresi aşağıdaki koşullara uygunsa birlikte değişken olarak bildirilemez:</span><span class="sxs-lookup"><span data-stu-id="eb7d3-116">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="eb7d3-117">Tür parametresi yalnızca Arabirim yöntemlerinin dönüş türü olarak kullanılır ve Yöntem bağımsız değişkenlerinin türü olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-117">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="eb7d3-118">Bu kural için bir özel durum var.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-118">There is one exception to this rule.</span></span> <span data-ttu-id="eb7d3-119">Bir covaryant arayüzünde bir yöntem parametresi olarak bir değişken karşıtı genel temsilciniz varsa, bu temsilci için ortak tür parametresi olarak covaryant türü ' ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-119">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="eb7d3-120">Covaryant ve değişken karşıtı genel Temsilciler hakkında daha fazla bilgi için bkz. [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Func ve eylem genel temsilcileri için varyans kullanma](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="eb7d3-120">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="eb7d3-121">Tür parametresi, arabirim yöntemleri için genel kısıtlama olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-121">The type parameter is not used as a generic constraint for the interface methods.</span></span>

## <a name="example---covariant-generic-delegate"></a><span data-ttu-id="eb7d3-122">Örnek-birlikte değişken genel temsilcisi</span><span class="sxs-lookup"><span data-stu-id="eb7d3-122">Example - covariant generic delegate</span></span>

<span data-ttu-id="eb7d3-123">Aşağıdaki örnek, bir covaryant genel temsilcisinin nasıl bildirilemeyeceğini, örneklendirilemeyeceğini ve çağıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-123">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="eb7d3-124">Ayrıca, temsilci türlerini örtük olarak nasıl dönüştürebileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-124">It also shows how to implicitly convert delegate types.</span></span>

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

<span data-ttu-id="eb7d3-125">Genel bir temsilcisinde, bir tür yalnızca bir yöntem dönüş türü olarak kullanılıyorsa ve Yöntem bağımsız değişkenleri için kullanılmazsa, birlikte değişken olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-125">In a generic delegate, a type can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eb7d3-126">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="eb7d3-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="eb7d3-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb7d3-127">See also</span></span>

- [<span data-ttu-id="eb7d3-128">Genel Arabirimlerde Varyans</span><span class="sxs-lookup"><span data-stu-id="eb7d3-128">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="eb7d3-129">'ndaki</span><span class="sxs-lookup"><span data-stu-id="eb7d3-129">in</span></span>](in-generic-modifier.md)
- [<span data-ttu-id="eb7d3-130">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="eb7d3-130">Modifiers</span></span>](index.md)
