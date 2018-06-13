---
title: In (Genel Değiştirici) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: d1d9209cd583ac96ece59660ad29c76a66d3395a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597438"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="d3391-102">In (Genel Değiştirici) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3391-102">In (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="d3391-103">Genel tür parametreleri için `In` anahtar sözcüğü tür parametre değişken karşıtıdır olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d3391-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3391-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d3391-104">Remarks</span></span>  
 <span data-ttu-id="d3391-105">Değişken karşıtı genel parametresi tarafından belirtilenden daha az türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3391-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="d3391-106">Bu değişken arabirimleri uygulayan sınıfların örtük dönüştürme ve temsilci türleri örtük dönüştürme için sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3391-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="d3391-107">Daha fazla bilgi için bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="d3391-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d3391-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="d3391-108">Rules</span></span>  
 <span data-ttu-id="d3391-109">Kullanabileceğiniz `In` anahtar sözcüğü genel arabirimler ve temsilciler.</span><span class="sxs-lookup"><span data-stu-id="d3391-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="d3391-110">Yalnızca bir tür yöntemi bağımsız değişken olarak kullanılan ve yöntemin dönüş türü olarak kullanılmayan bir tür parametresi bir genel arabirim ya da temsilci karşıtı bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d3391-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="d3391-111">`ByRef` parametreleri eşdeğişken olamaz veya karşıtı.</span><span class="sxs-lookup"><span data-stu-id="d3391-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>  
  
 <span data-ttu-id="d3391-112">Kovaryans ve kontravaryans başvuru türleri için desteklenir ve değer türleri için desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="d3391-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>  
  
 <span data-ttu-id="d3391-113">Visual Basic'te temsilci türü belirtmeden karşıtı Arabirimlerdeki olaylar bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="d3391-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="d3391-114">Ayrıca karşıtı arabirimleri sınıfları, numaralandırmaları ve yapıları işleminde içe olamaz, ancak bunlar arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="d3391-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="d3391-115">Davranış</span><span class="sxs-lookup"><span data-stu-id="d3391-115">Behavior</span></span>  
 <span data-ttu-id="d3391-116">Yöntemlerinden daha az türetilmiş türler arabirimi tür parametresi tarafından belirtilen'den bağımsız değişkenleri kabul etmek karşıtı türü parametresine sahip bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3391-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="d3391-117">Örneğin, çünkü .NET Framework 4'te içinde <xref:System.Collections.Generic.IComparer%601> arabirimi, T türü karşıtı, bir nesnenin atayabilirsiniz `IComparer(Of Person)` bir nesne türüne `IComparer(Of Employee)` , herhangi bir özel dönüştürme yöntem kullanmadan türü `Person` devralır `Employee`.</span><span class="sxs-lookup"><span data-stu-id="d3391-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Person` inherits `Employee`.</span></span>  
  
 <span data-ttu-id="d3391-118">Aynı türde, ancak daha az türetilmiş genel tür parametresi olan başka bir temsilci karşıtı temsilci atanabilir.</span><span class="sxs-lookup"><span data-stu-id="d3391-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3391-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3391-119">Example</span></span>  
 <span data-ttu-id="d3391-120">Aşağıdaki örnek, bildirme, genişletmek ve karşıtı genel arabirimini uygulayan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d3391-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="d3391-121">Örtük dönüştürme bu arabirimi uygulayan sınıflar için nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3391-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="d3391-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="d3391-122">Example</span></span>  
 <span data-ttu-id="d3391-123">Aşağıdaki örnek, bildirme, oluşturma ve karşıtı genel temsilcisi çağırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d3391-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="d3391-124">Ayrıca, bir temsilci türü örtük olarak nasıl dönüştürebilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="d3391-124">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d3391-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3391-125">See Also</span></span>  
 [<span data-ttu-id="d3391-126">Genel Arabirimlerde Varyans</span><span class="sxs-lookup"><span data-stu-id="d3391-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="d3391-127">Çıkışı</span><span class="sxs-lookup"><span data-stu-id="d3391-127">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
