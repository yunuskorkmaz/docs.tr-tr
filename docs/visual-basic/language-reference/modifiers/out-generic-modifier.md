---
description: 'Daha fazla bilgi edinin: Out (genel değiştirici) (Visual Basic)'
title: Out (Genel Değiştirici)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: cdf80439fbae0d2411eecff1c7e8438534fcfdc1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99730544"
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="839fe-103">Out (Genel Değiştirici) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="839fe-103">Out (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="839fe-104">Genel tür parametreleri için `Out` anahtar sözcüğü, türün birlikte değişken olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="839fe-104">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="839fe-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="839fe-105">Remarks</span></span>

<span data-ttu-id="839fe-106">Kovaryans, genel parametre ile belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="839fe-106">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="839fe-107">Bu, değişken arabirimleri uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="839fe-107">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="839fe-108">Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="839fe-108">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="839fe-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="839fe-109">Rules</span></span>

<span data-ttu-id="839fe-110">`Out`Genel arabirimlerde ve temsilcilerde anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="839fe-110">You can use the `Out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="839fe-111">Bir genel arabirimde, bir tür parametresi aşağıdaki koşullara uygunsa birlikte değişken olarak bildirilemez:</span><span class="sxs-lookup"><span data-stu-id="839fe-111">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="839fe-112">Tür parametresi yalnızca Arabirim yöntemlerinin dönüş türü olarak kullanılır ve Yöntem bağımsız değişkenlerinin türü olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="839fe-112">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="839fe-113">Bu kural için bir özel durum var.</span><span class="sxs-lookup"><span data-stu-id="839fe-113">There is one exception to this rule.</span></span> <span data-ttu-id="839fe-114">Bir covaryant arayüzünde bir yöntem parametresi olarak bir değişken karşıtı genel temsilciniz varsa, bu temsilci için ortak tür parametresi olarak covaryant türü ' ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="839fe-114">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="839fe-115">Covaryant ve değişken karşıtı genel Temsilciler hakkında daha fazla bilgi için bkz. [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [Func ve eylem genel temsilcileri için varyans kullanma](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="839fe-115">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="839fe-116">Tür parametresi, arabirim yöntemleri için genel kısıtlama olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="839fe-116">The type parameter is not used as a generic constraint for the interface methods.</span></span>

<span data-ttu-id="839fe-117">Genel bir temsilcisinde, bir tür parametresi yalnızca yöntem dönüş türü olarak kullanılırsa ve Yöntem bağımsız değişkenleri için kullanılmazsa birlikte değişken olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="839fe-117">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

<span data-ttu-id="839fe-118">Kovaryans ve değişken Varyans, başvuru türleri için desteklenir, ancak değer türleri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="839fe-118">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="839fe-119">Visual Basic, temsilci türünü belirtmeden birlikte değişken arabirimlerde olayları bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="839fe-119">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="839fe-120">Ayrıca, birlikte değişken arabirimlerin iç içe sınıfları, numaralandırmalar veya yapıları olamaz, ancak iç içe arabirimler olabilir.</span><span class="sxs-lookup"><span data-stu-id="839fe-120">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="839fe-121">Davranış</span><span class="sxs-lookup"><span data-stu-id="839fe-121">Behavior</span></span>

<span data-ttu-id="839fe-122">Covaryant türü parametresine sahip bir arabirim, yöntemlerinin tür parametresiyle belirtenlerden daha fazla türetilmiş tür döndürmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="839fe-122">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="839fe-123">Örneğin, içinde .NET Framework 4 ' te, <xref:System.Collections.Generic.IEnumerable%601> T türü de birlikte değişken ise, `IEnumerable(Of String)` herhangi bir özel dönüştürme yöntemi kullanmadan türdeki bir nesneye türünün bir nesnesine atayabilirsiniz `IEnumerable(Of Object)` .</span><span class="sxs-lookup"><span data-stu-id="839fe-123">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="839fe-124">Birlikte değişken temsilcisine aynı türde başka bir temsilci atanabilir, ancak daha türetilmiş bir genel tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="839fe-124">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="839fe-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="839fe-125">Example</span></span>

<span data-ttu-id="839fe-126">Aşağıdaki örnek, bir covaryant genel arabiriminin nasıl bildirileceği, genişletileceği ve uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="839fe-126">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="839fe-127">Ayrıca, birlikte değişken arabirimi uygulayan sınıflar için örtük dönüştürmeyi nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="839fe-127">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="839fe-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="839fe-128">Example</span></span>

<span data-ttu-id="839fe-129">Aşağıdaki örnek, bir covaryant genel temsilcisinin nasıl bildirilemeyeceğini, örneklendirilemeyeceğini ve çağıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="839fe-129">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="839fe-130">Ayrıca, temsilci türleri için örtük dönüştürmeyi nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="839fe-130">It also shows how you can use implicit conversion for delegate types.</span></span>

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="839fe-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="839fe-131">See also</span></span>

- [<span data-ttu-id="839fe-132">Genel Arabirimlerde Varyans</span><span class="sxs-lookup"><span data-stu-id="839fe-132">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="839fe-133">İçinde</span><span class="sxs-lookup"><span data-stu-id="839fe-133">In</span></span>](in-generic-modifier.md)
