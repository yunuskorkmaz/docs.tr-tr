---
title: Out (Genel Değiştirici) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: fa14e83af16cd30a72ca1c165596fa9320842fce
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379230"
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="94341-102">Out (Genel Değiştirici) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94341-102">Out (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="94341-103">Genel tür parametreleri için `Out` anahtar sözcük türü birlikte değişken olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="94341-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="94341-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94341-104">Remarks</span></span>

<span data-ttu-id="94341-105">Kovaryans genel parametre olarak belirtilenden daha türetilmiş bir tür belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="94341-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="94341-106">Bu değişken arabirimleri uygulayan sınıflar örtük dönüştürülmesi ve temsilci türlerinin örtük dönüştürme için sağlar.</span><span class="sxs-lookup"><span data-stu-id="94341-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="94341-107">Daha fazla bilgi için [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="94341-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="94341-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="94341-108">Rules</span></span>

<span data-ttu-id="94341-109">Kullanabileceğiniz `Out` genel arabirimlerde ve temsilcilerde anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="94341-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="94341-110">Genel arabiriminin tür parametresi aşağıdaki koşulları karşılıyorsa, birlikte değişken bildirilebilir:</span><span class="sxs-lookup"><span data-stu-id="94341-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>

- <span data-ttu-id="94341-111">Tür parametresi yalnızca bir dönüş türü arabirim yöntemleri olarak kullanılan ve yöntem bağımsız bir türü olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="94341-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>

    > [!NOTE]
    > <span data-ttu-id="94341-112">Bu kuralın tek istisnası yoktur.</span><span class="sxs-lookup"><span data-stu-id="94341-112">There is one exception to this rule.</span></span> <span data-ttu-id="94341-113">Birlikte değişen bir arabirimde bir yöntem parametresi olarak bir değişken karşıtı Genel temsilci varsa, birlikte değişken türünde genel tür parametre olarak bu metot temsilcisi için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94341-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="94341-114">Birlikte değişken hakkında daha fazla bilgi ve değişken karşıtı genel temsilciler [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri için varyans kullanma](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="94341-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>

- <span data-ttu-id="94341-115">Tür parametresi, arabirim yöntemleri için genel bir kısıtlama kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="94341-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>

<span data-ttu-id="94341-116">Yalnızca bir yöntem dönüş türü kullanılan ve kullanılmayan yöntem bağımsız değişkenleri için genel bir temsilci, bir tür parametresi birlikte değişken olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="94341-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>

<span data-ttu-id="94341-117">Kovaryans ve kontravaryans başvuru türleri için desteklenir ancak değer türleri için desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="94341-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="94341-118">Visual Basic'te, temsilci türü belirtmeden birlikte değişken Arabirimlerdeki olaylar bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="94341-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="94341-119">Ayrıca, birlikte değişken arabirimleri sınıflar, numaralandırmalar ve yapılar iç içe geçmiş olamaz, ancak bunlar arabirimleri içe.</span><span class="sxs-lookup"><span data-stu-id="94341-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="94341-120">Davranış</span><span class="sxs-lookup"><span data-stu-id="94341-120">Behavior</span></span>

<span data-ttu-id="94341-121">Dönüş türü parametresi tarafından belirtilenlerden daha türetilmiş türleri metotlarını bir birlikte değişen türde parametresi olan bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="94341-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="94341-122">Örneğin, çünkü .NET Framework 4 içinde <xref:System.Collections.Generic.IEnumerable%601>T türü birlikte değişken, bir nesnenin atayabilirsiniz `IEnumerable(Of String)` bir nesne türüne `IEnumerable(Of Object)` herhangi bir özel dönüştürme yöntemini kullanmadan türü.</span><span class="sxs-lookup"><span data-stu-id="94341-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerable(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>

<span data-ttu-id="94341-123">Birlikte değişen bir temsilci, aynı türden, ancak daha fazla türetilmiş bir genel tür parametresi ile başka bir temsilci atanabilir.</span><span class="sxs-lookup"><span data-stu-id="94341-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>

## <a name="example"></a><span data-ttu-id="94341-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="94341-124">Example</span></span>

<span data-ttu-id="94341-125">Aşağıdaki örnek, bildirmek, genişletin ve bir değişken genel arabirim uygulamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="94341-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="94341-126">Ayrıca, birlikte değişen bir arabirimi uygulayan sınıflar için örtük dönüştürme kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="94341-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="94341-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="94341-127">Example</span></span>

<span data-ttu-id="94341-128">Aşağıdaki örnek, bildirme, oluşturma ve birlikte değişken temsilci çağırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="94341-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="94341-129">Ayrıca, temsilci türleri için örtük dönüştürme nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="94341-129">It also shows how you can use implicit conversion for delegate types.</span></span>

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="94341-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94341-130">See also</span></span>

- [<span data-ttu-id="94341-131">Genel Arabirimlerde Varyans</span><span class="sxs-lookup"><span data-stu-id="94341-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="94341-132">İçinde</span><span class="sxs-lookup"><span data-stu-id="94341-132">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
