---
title: "Out (Genel Değiştirici) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e54504cd65b78846af41692f39899140a6d99b5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2017
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="fa4fb-102">Out (Genel Değiştirici) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa4fb-102">Out (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="fa4fb-103">Genel tür parametreleri için `Out` anahtar sözcük türü eşdeğişken olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa4fb-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa4fb-104">Remarks</span></span>  
 <span data-ttu-id="fa4fb-105">Kovaryans genel parametresi tarafından belirtilenden daha fazla türetilmiş bir tür kullanmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="fa4fb-106">Bu değişken arabirimleri uygulayan sınıfların örtük dönüştürme ve temsilci türleri örtük dönüştürme için sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="fa4fb-107">Daha fazla bilgi için bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="fa4fb-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="fa4fb-108">Kurallar</span><span class="sxs-lookup"><span data-stu-id="fa4fb-108">Rules</span></span>  
 <span data-ttu-id="fa4fb-109">Kullanabileceğiniz `Out` anahtar sözcüğü genel arabirimler ve temsilciler.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="fa4fb-110">Bir genel arabiriminde bir tür parametresi aşağıdaki koşullar uymazsa eşdeğişken bildirilebilir:</span><span class="sxs-lookup"><span data-stu-id="fa4fb-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="fa4fb-111">Tür parametresi yalnızca bir dönüş türü arabirim yöntemleri olarak kullanılan ve yöntem bağımsız değişkenleri bir tür olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fa4fb-112">Bu kural için bir istisna vardır.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-112">There is one exception to this rule.</span></span> <span data-ttu-id="fa4fb-113">Eşdeğişken arabiriminde karşıtı Genel temsilci bir yöntem parametresi olarak varsa, bu temsilci için genel tür parametresi olarak eşdeğişken türü kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="fa4fb-114">Eşdeğişken hakkında daha fazla bilgi ve karşıtı genel temsilciler [Temsilcilerde varyans](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri için varyans kullanma](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="fa4fb-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) and [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).</span></span>  
  
-   <span data-ttu-id="fa4fb-115">Tür parametresi, arabirim yöntemleri için genel bir kısıtlama olarak kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
 <span data-ttu-id="fa4fb-116">Yalnızca bir yöntemin dönüş türü olarak kullanılır ve yöntem bağımsız değişkenleri için kullanılmaz, genel bir temsilci türü parametresi eşdeğişken olarak bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
 <span data-ttu-id="fa4fb-117">Kovaryans ve kontravaryans referans türleri için desteklenir, ancak değer türlerinde desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="fa4fb-118">Visual Basic'te temsilci türü belirtmeden eşdeğişken Arabirimlerdeki olaylar bildiremezsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="fa4fb-119">Ayrıca, eşdeğişken arabirimleri sınıfları, numaralandırmaları ve yapıları işleminde içe olamaz, ancak bunlar arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="fa4fb-120">Davranış</span><span class="sxs-lookup"><span data-stu-id="fa4fb-120">Behavior</span></span>  
 <span data-ttu-id="fa4fb-121">Tür parametresi tarafından belirtilen daha fazla türetilmiş türler döndürülecek yöntemlerinden eşdeğişken türü parametresine sahip bir arabirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="fa4fb-122">Örneğin, çünkü .NET Framework 4'te içinde <xref:System.Collections.Generic.IEnumerable%601>T türü eşdeğişken, bir nesnenin atayabilirsiniz `IEnumerabe(Of String)` bir nesne türüne `IEnumerable(Of Object)` herhangi bir özel dönüştürme yöntem kullanmadan türü.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="fa4fb-123">Aynı türde, ancak daha fazla türetilmiş genel tür parametresi olan başka bir temsilci eşdeğişken temsilci atanabilir.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa4fb-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa4fb-124">Example</span></span>  
 <span data-ttu-id="fa4fb-125">Aşağıdaki örnek, bildirme, genişletmek ve eşdeğişken genel arabirimini uygulayan gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="fa4fb-126">Ayrıca, eşdeğişken arabirimini uygulayan sınıflar için örtük dönüşüm kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="fa4fb-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa4fb-127">Example</span></span>  
 <span data-ttu-id="fa4fb-128">Aşağıdaki örnek, bildirme, oluşturma ve eşdeğişken genel temsilcisi çağırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="fa4fb-129">Örtük dönüştürme temsilci türleri için nasıl kullanabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-129">It also shows how you can use implicit conversion for delegate types.</span></span>  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fa4fb-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fa4fb-130">See Also</span></span>  
 [<span data-ttu-id="fa4fb-131">Genel Arabirimlerde Varyans</span><span class="sxs-lookup"><span data-stu-id="fa4fb-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="fa4fb-132">İçinde</span><span class="sxs-lookup"><span data-stu-id="fa4fb-132">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
