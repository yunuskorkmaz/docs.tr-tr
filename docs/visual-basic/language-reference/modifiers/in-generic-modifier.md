---
title: In (Genel Değiştirici) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: d8d503f0814a89c977cdc208eced026b2d8cb1fd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838943"
---
# <a name="in-generic-modifier-visual-basic"></a><span data-ttu-id="11984-102">In (Genel Değiştirici) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11984-102">In (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="11984-103">Genel tür parametreleri için `In` anahtar sözcüğü, tür parametresi değişken karşıtı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="11984-103">For generic type parameters, the `In` keyword specifies that the type parameter is contravariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11984-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="11984-104">Remarks</span></span>  
 <span data-ttu-id="11984-105">Kontravaryans, genel parametre olarak belirtilenden daha az türetilmiş bir tür belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="11984-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="11984-106">Bu değişken arabirimleri uygulayan sınıflar örtük dönüştürülmesi ve temsilci türlerinin örtük dönüştürme için sağlar.</span><span class="sxs-lookup"><span data-stu-id="11984-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="11984-107">Daha fazla bilgi için [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="11984-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="11984-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="11984-108">Rules</span></span>  
 <span data-ttu-id="11984-109">Kullanabileceğiniz `In` genel arabirimlerde ve temsilcilerde anahtar sözcük.</span><span class="sxs-lookup"><span data-stu-id="11984-109">You can use the `In` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="11984-110">Yalnızca bir yöntem bağımsız kullanılan türü ise ve bir yöntemin dönüş türü olarak kullanılmayan bir tür parametresi değişken karşıtı genel arabirim veya temsilci olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="11984-110">A type parameter can be declared contravariant in a generic interface or delegate if it is used only as a type of method arguments and not used as a method return type.</span></span> <span data-ttu-id="11984-111">`ByRef` parametreleri olamaz birlikte değişken veya değişken karşıtı.</span><span class="sxs-lookup"><span data-stu-id="11984-111">`ByRef` parameters cannot be covariant or contravariant.</span></span>  
  
 <span data-ttu-id="11984-112">Kovaryans ve kontravaryans başvuru türleri için desteklenir ve değer türleri için desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="11984-112">Covariance and contravariance are supported for reference types and not supported for value types.</span></span>  
  
 <span data-ttu-id="11984-113">Visual Basic'te, temsilci türü belirtmeden değişken karşıtı Arabirimlerdeki olaylar bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="11984-113">In Visual Basic, you cannot declare events in contravariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="11984-114">Ayrıca, değişken karşıtı arabirimleri sınıflar, numaralandırmalar ve yapılar iç içe geçmiş olamaz, ancak bunlar arabirimleri içe.</span><span class="sxs-lookup"><span data-stu-id="11984-114">Also, contravariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="11984-115">Davranış</span><span class="sxs-lookup"><span data-stu-id="11984-115">Behavior</span></span>  
 <span data-ttu-id="11984-116">Yöntemlerinden daha az türetilmiş türler arabirim türü parametresi ile belirtilen değerinden bağımsız değişkenleri kabul etmek bir değişken karşıtı tür parametresine sahip bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="11984-116">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="11984-117">Örneğin, çünkü .NET Framework 4'te, <xref:System.Collections.Generic.IComparer%601> arabirimi, T türü değişken karşıtı olduğundan, bir nesnenin atayabilirsiniz `IComparer(Of Person)` bir nesne türüne `IComparer(Of Employee)` özel dönüştürme yöntemleri kullanılarak olmadan türü `Person` devralır `Employee`.</span><span class="sxs-lookup"><span data-stu-id="11984-117">For example, because in .NET Framework 4, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer(Of Person)` type to an object of the `IComparer(Of Employee)` type without using any special conversion methods if `Person` inherits `Employee`.</span></span>  
  
 <span data-ttu-id="11984-118">Başka bir temsilci aynı türden, ancak daha az türetilmiş bir genel tür parametresi değişken karşıtı temsilci atanabilir.</span><span class="sxs-lookup"><span data-stu-id="11984-118">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11984-119">Örnek</span><span class="sxs-lookup"><span data-stu-id="11984-119">Example</span></span>  
 <span data-ttu-id="11984-120">Aşağıdaki örnek, bildirmek, genişletin ve değişken karşıtı genel bir arabirim uygulamak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="11984-120">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="11984-121">Ayrıca, bu arabirimi uygulayan sınıflar için örtük dönüştürme nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="11984-121">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="11984-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="11984-122">Example</span></span>  
 <span data-ttu-id="11984-123">Aşağıdaki örnek, bildirme, oluşturma ve değişken karşıtı Genel temsilci çağırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="11984-123">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="11984-124">Ayrıca, bir temsilci türü örtük olarak nasıl dönüştürebilirsiniz gösterir.</span><span class="sxs-lookup"><span data-stu-id="11984-124">It also shows how you can implicitly convert a delegate type.</span></span>  
  
 [!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="11984-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11984-125">See also</span></span>

- [<span data-ttu-id="11984-126">Genel Arabirimlerde Varyans</span><span class="sxs-lookup"><span data-stu-id="11984-126">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [<span data-ttu-id="11984-127">Çıkış</span><span class="sxs-lookup"><span data-stu-id="11984-127">Out</span></span>](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
