---
title: MustInherit (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 5d622c1cff77a45c8de7772af7efbb73586f4400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602846"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="7dd6d-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7dd6d-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="7dd6d-103">Bir sınıf yalnızca bir temel sınıf olarak kullanılabilir ve doğrudan bir nesne oluşturamazsınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dd6d-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7dd6d-104">Remarks</span></span>  
 <span data-ttu-id="7dd6d-105">Amacı bir *temel sınıfı* (olarak da bilinen bir *soyut sınıf*) ondan türetilmiş tüm sınıflar ortak işlevselliği tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="7dd6d-106">Bu türetilmiş sınıfları ortak öğeler tanımlanacak gereğini ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="7dd6d-107">Bazı durumlarda, bu ortak işlevselliği kullanılabilir bir nesne için tam değil ve eksik işlev her türetilmiş bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="7dd6d-108">Böyle bir durumda, yalnızca türetilmiş sınıflarından nesneleri oluşturmak için kullanıcı kodu istiyor.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="7dd6d-109">Kullandığınız `MustInherit` bu zorlamak için temel sınıfı.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="7dd6d-110">Başka bir kullanımını bir `MustInherit` sınıfı, bir dizi ilgili sınıflar için bir değişken kısıtlamak için.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="7dd6d-111">Bu ilgili sınıfları bu sınıftan türetilen ve bir taban sınıf tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="7dd6d-112">Türetilen sınıflar için ortak olan herhangi bir işlevsellik sağlamak temel sınıf gerekmez, ancak değişkenlere değerler atama için bir filtre olarak hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="7dd6d-113">Süren kodunuzu bir değişken temel sınıf olarak bildirirse, Visual Basic, yalnızca bir nesne türetilmiş sınıflarından biri için bu değişkeni atamanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="7dd6d-114">.NET Framework birkaç tanımlar `MustInherit` sınıfları, aralarında <xref:System.Array>, <xref:System.Enum>, ve <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="7dd6d-115"><xref:System.ValueType> bir değişken kısıtlayan bir taban sınıf örnektir.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="7dd6d-116">Tüm değer türlerini türetmek <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="7dd6d-117">Bir değişken olarak bildirirseniz <xref:System.ValueType>, bu değişken yalnızca değer türleri atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="7dd6d-118">Kurallar</span><span class="sxs-lookup"><span data-stu-id="7dd6d-118">Rules</span></span>  
  
-   <span data-ttu-id="7dd6d-119">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="7dd6d-119">**Declaration Context.**</span></span> <span data-ttu-id="7dd6d-120">Kullanabileceğiniz `MustInherit` yalnızca bir `Class` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
-   <span data-ttu-id="7dd6d-121">**Birleşik değiştirici.**</span><span class="sxs-lookup"><span data-stu-id="7dd6d-121">**Combined Modifiers.**</span></span> <span data-ttu-id="7dd6d-122">Belirtemeyeceğiniz `MustInherit` ile birlikte `NotInheritable` aynı bildirimi.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7dd6d-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="7dd6d-123">Example</span></span>  
 <span data-ttu-id="7dd6d-124">Aşağıdaki örnek, zorla devralma ve geçersiz kılma zorlanmış gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="7dd6d-125">Taban sınıfı `shape` bir değişkeni `acrossLine`.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="7dd6d-126">Sınıfları `circle` ve `square` öğesinden türetilen `shape`.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="7dd6d-127">Tanımını devral `acrossLine`, ancak işlev tanımlamalısınız `area` Bu hesaplamayı şekli her tür için farklı olduğu için.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](../../../visual-basic/language-reference/codesnippet/VisualBasic/mustinherit_1.vb)]  
  
 <span data-ttu-id="7dd6d-128">Bildirebilirsiniz `shape1` ve `shape2` türünde olması `shape`.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="7dd6d-129">Ancak, bir nesneden oluşturamazsınız `shape` işlevi işlevselliğini eksik olduğundan `area` ve işaretlenmiş `MustInherit`.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="7dd6d-130">Olarak bildirilen çünkü `shape`, değişkenleri `shape1` ve `shape2` nesnelere türetilmiş sınıflarından kısıtlanmıştır `circle` ve `square`.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="7dd6d-131">Visual Basic bu değişkenleri için herhangi bir nesneye atamak yüksek düzeyde bir tür güvenliği sağlayan izin vermez.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="7dd6d-132">Kullanım</span><span class="sxs-lookup"><span data-stu-id="7dd6d-132">Usage</span></span>  
 <span data-ttu-id="7dd6d-133">`MustInherit` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7dd6d-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="7dd6d-134">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="7dd6d-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7dd6d-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7dd6d-135">See Also</span></span>  
 [<span data-ttu-id="7dd6d-136">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="7dd6d-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="7dd6d-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="7dd6d-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)  
 [<span data-ttu-id="7dd6d-138">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="7dd6d-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)  
 [<span data-ttu-id="7dd6d-139">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="7dd6d-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
