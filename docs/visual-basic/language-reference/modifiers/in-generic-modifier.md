---
title: In (genel değiştirici)-Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 9c0f7d454767112e1e309af81407b5fdef22eee9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004874"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="8d6c2-102">In (Genel Değiştirici) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d6c2-102">In (Generic Modifier) (Visual Basic)</span></span>

<span data-ttu-id="8d6c2-103">Genel tür parametreleri için `In` anahtar sözcüğü tür parametresinin değişken karşıtı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d6c2-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8d6c2-104">Remarks</span></span>

<span data-ttu-id="8d6c2-105">Değişken Varyans, genel parametre ile belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="8d6c2-106">Bu, değişken arabirimleri uygulayan sınıfların örtük dönüştürülmesini ve temsilci türlerinin örtük dönüştürülmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>

<span data-ttu-id="8d6c2-107">Daha fazla bilgi için bkz. [Kovaryans ve değişken varyans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="8d6c2-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="rules"></a><span data-ttu-id="8d6c2-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="8d6c2-108">Rules</span></span>

<span data-ttu-id="8d6c2-109">Genel arabirimlerde ve temsilcilerde `In` anahtar sözcüğünü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>
  
<span data-ttu-id="8d6c2-110">Bir tür parametresi, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılırsa ve yöntem dönüş türü olarak kullanılmazsa genel bir arabirimde veya temsilcisinde değişken karşıtı olarak bildirilemez.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="8d6c2-111">`ByRef` parametreleri birlikte değişken veya değişken karşıtı olamaz.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>

<span data-ttu-id="8d6c2-112">Kovaryans ve değişken Varyans, başvuru türleri için desteklenir ve değer türleri için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>

<span data-ttu-id="8d6c2-113">Visual Basic, temsilci türünü belirtmeden olayları değişken olmayan arabirimlerde bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="8d6c2-114">Ayrıca, değişken karşıtı arabirimlerde iç içe sınıflar, numaralandırmalar veya yapılar bulunamaz, ancak iç içe arabirimler olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>

## <a name="behavior"></a><span data-ttu-id="8d6c2-115">Davranış</span><span class="sxs-lookup"><span data-stu-id="8d6c2-115">Behavior</span></span>

<span data-ttu-id="8d6c2-116">Değişken karşıtı tür parametresine sahip bir arabirim, yöntemlerinin, arabirim türü parametresi tarafından belirtilenden daha az türetilmiş türlerin bağımsız değişkenlerini kabul etmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="8d6c2-117">Örneğin, .NET Framework 4 ' te, <xref:System.Collections.Generic.IComparer%601> arabiriminde T yazın ve `Employee` `Person` ' ten devralırsa herhangi bir özel dönüştürme yöntemini kullanmadan `IComparer(Of Person)` türünün bir nesnesine `IComparer(Of Employee)` türünde bir nesne atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Employee` inherits from `Person`.</span></span>

<span data-ttu-id="8d6c2-118">Değişken karşıtı bir temsilciye aynı türde başka bir temsilci atanabilir, ancak daha az türetilmiş bir genel tür parametresi olabilir.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

## <a name="example---contravariant-generic-interface"></a><span data-ttu-id="8d6c2-119">Örnek değişken karşıtı genel arabirim</span><span class="sxs-lookup"><span data-stu-id="8d6c2-119">Example - contravariant generic interface</span></span>

<span data-ttu-id="8d6c2-120">Aşağıdaki örnek, bir değişken karşıtı genel arabirimin nasıl bildirileceği, genişletileceği ve uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="8d6c2-121">Ayrıca, bu arabirimi uygulayan sınıflar için örtük dönüştürmeyi nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]

## <a name="example---contravariant-generic-delegate"></a><span data-ttu-id="8d6c2-122">Örnek değişken karşıtı genel temsilci</span><span class="sxs-lookup"><span data-stu-id="8d6c2-122">Example - contravariant generic delegate</span></span>

<span data-ttu-id="8d6c2-123">Aşağıdaki örnek, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini, örneklendirilemeyeceğini ve çağıralınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="8d6c2-124">Ayrıca, bir temsilci türünü örtülü olarak nasıl dönüştürebileceğiniz de gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-124">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="8d6c2-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d6c2-125">See also</span></span>

- [<span data-ttu-id="8d6c2-126">Genel Arabirimlerde Varyans</span><span class="sxs-lookup"><span data-stu-id="8d6c2-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="8d6c2-127">Dışı</span><span class="sxs-lookup"><span data-stu-id="8d6c2-127">Out</span></span>](out-generic-modifier.md)
