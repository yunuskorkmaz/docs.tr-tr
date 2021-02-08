---
description: 'Hakkında daha fazla bilgi edinin: ın (genel değiştirici) (Visual Basic)'
title: In (genel değiştirici)-Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: e6ac95a77253b28e45a4be8a29623bdd76a231f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774544"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="1555b-103">In (Genel Değiştirici) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1555b-103">In (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="1555b-104">Genel tür parametreleri için, `In` anahtar sözcüğü tür parametresinin değişken karşıtı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1555b-104">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="1555b-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1555b-105">Remarks</span></span>

<span data-ttu-id="1555b-106">Değişken Varyans, genel parametre ile belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="1555b-106">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="1555b-107">Bu, değişken arabirimleri uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="1555b-107">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="1555b-108">Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="1555b-108">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="1555b-109">Kurallar</span><span class="sxs-lookup"><span data-stu-id="1555b-109">Rules</span></span>

<span data-ttu-id="1555b-110">`In`Genel arabirimlerde ve temsilcilerde anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1555b-110">You can use the `In` keyword in generic interfaces and delegates.</span></span>
  
<span data-ttu-id="1555b-111">Bir tür parametresi, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılırsa ve yöntem dönüş türü olarak kullanılmazsa genel bir arabirimde veya temsilcisinde değişken karşıtı olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="1555b-111">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="1555b-112">`ByRef` parametreler birlikte değişken veya değişken karşıtı olamaz.</span><span class="sxs-lookup"><span data-stu-id="1555b-112">`ByRef` parameters cannot be covariant or contravariant.</span></span>

<span data-ttu-id="1555b-113">Kovaryans ve değişken Varyans, başvuru türleri için desteklenir ve değer türleri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="1555b-113">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>

<span data-ttu-id="1555b-114">Visual Basic, temsilci türünü belirtmeden olayları değişken olmayan arabirimlerde bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="1555b-114">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="1555b-115">Ayrıca, değişken karşıtı arabirimlerde iç içe sınıflar, numaralandırmalar veya yapılar bulunamaz, ancak iç içe arabirimler olabilir.</span><span class="sxs-lookup"><span data-stu-id="1555b-115">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="1555b-116">Davranış</span><span class="sxs-lookup"><span data-stu-id="1555b-116">Behavior</span></span>

<span data-ttu-id="1555b-117">Değişken karşıtı tür parametresine sahip bir arabirim, yöntemlerinin, arabirim türü parametresi tarafından belirtilenden daha az türetilmiş türlerin bağımsız değişkenlerini kabul etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="1555b-117">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="1555b-118">Örneğin, .NET Framework 4 ' te, <xref:System.Collections.Generic.IComparer%601> arabiriminde, T türü değişken değişken ise, ' `IComparer(Of Person)` `IComparer(Of Employee)` den devralırsa herhangi bir özel dönüştürme yöntemini kullanmadan, türün bir nesnesine türünün bir nesnesine atayabilirsiniz `Employee` `Person` .</span><span class="sxs-lookup"><span data-stu-id="1555b-118">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits from `Person`.</span></span>

<span data-ttu-id="1555b-119">Değişken karşıtı bir temsilciye aynı türde başka bir temsilci atanabilir, ancak daha az türetilmiş bir genel tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="1555b-119">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

## <a name="example---contravariant-generic-interface"></a><span data-ttu-id="1555b-120">Örnek değişken karşıtı genel arabirim</span><span class="sxs-lookup"><span data-stu-id="1555b-120">Example - contravariant generic interface</span></span>

<span data-ttu-id="1555b-121">Aşağıdaki örnek, bir değişken karşıtı genel arabirimin nasıl bildirileceği, genişletileceği ve uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1555b-121">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="1555b-122">Ayrıca, bu arabirimi uygulayan sınıflar için örtük dönüştürmeyi nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="1555b-122">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]

## <a name="example---contravariant-generic-delegate"></a><span data-ttu-id="1555b-123">Örnek değişken karşıtı genel temsilci</span><span class="sxs-lookup"><span data-stu-id="1555b-123">Example - contravariant generic delegate</span></span>

<span data-ttu-id="1555b-124">Aşağıdaki örnek, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini, örneklendirilemeyeceğini ve çağıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1555b-124">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="1555b-125">Ayrıca, bir temsilci türünü örtülü olarak nasıl dönüştürebileceğiniz de gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1555b-125">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="1555b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1555b-126">See also</span></span>

- [<span data-ttu-id="1555b-127">Genel Arabirimlerde Varyans</span><span class="sxs-lookup"><span data-stu-id="1555b-127">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="1555b-128">Dışı</span><span class="sxs-lookup"><span data-stu-id="1555b-128">Out</span></span>](out-generic-modifier.md)
