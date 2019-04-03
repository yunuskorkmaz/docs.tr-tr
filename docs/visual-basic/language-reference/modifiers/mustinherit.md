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
ms.openlocfilehash: 0bda03d3c01356317fbcc56d44199ff4f9484b5b
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816570"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="b5116-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5116-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="b5116-103">Bir sınıf yalnızca temel sınıf olarak kullanılabilir ve doğrudan bir nesne oluşturamazsınız belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5116-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5116-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b5116-104">Remarks</span></span>  
 <span data-ttu-id="b5116-105">Amacı, bir *temel sınıfı* (olarak da bilinen bir *soyut sınıf*) bundan türetilmiş tüm sınıflara ortak işlevselliği tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="b5116-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="b5116-106">Bu, türetilmiş sınıfları ortak öğeleri yeniden tanımlamak zorunda kalmaktan kurtarır.</span><span class="sxs-lookup"><span data-stu-id="b5116-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="b5116-107">Bazı durumlarda, bu ortak işlevselliği kullanışlı bir nesne haline getirmek için eksiksiz değildir ve eksik işlevselliğe her türetilmiş bir sınıf tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b5116-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="b5116-108">Böyle bir durumda, tüketici kod yalnızca türetilmiş sınıflardan nesneleri oluşturmak için istediğiniz.</span><span class="sxs-lookup"><span data-stu-id="b5116-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="b5116-109">Kullandığınız `MustInherit` bunu zorunlu kılmak için taban sınıfta.</span><span class="sxs-lookup"><span data-stu-id="b5116-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="b5116-110">Başka bir kullanımını bir `MustInherit` sınıfı, bir dizi ilgili sınıflar için bir değişken kısıtlamak için.</span><span class="sxs-lookup"><span data-stu-id="b5116-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="b5116-111">Bir temel sınıf tanımlayabilir ve tüm ilgili sınıflar bundan türetir.</span><span class="sxs-lookup"><span data-stu-id="b5116-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="b5116-112">Temel sınıfın türetilmiş sınıfların tümü için ortak olan herhangi bir işlevsellik sağlayan gerekmez, ancak değerleri değişkenlere atamak için bir filtre olarak hizmet verebilir.</span><span class="sxs-lookup"><span data-stu-id="b5116-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="b5116-113">Visual Basic kullanan kod temel sınıf olarak bir değişken bildiriyorsa, yalnızca bir nesne türetilmiş sınıflarının birinden bu değişkene atamanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="b5116-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="b5116-114">.NET Framework birkaç tanımlar `MustInherit` sınıfları, aralarında <xref:System.Array>, <xref:System.Enum>, ve <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="b5116-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="b5116-115"><xref:System.ValueType> bir değişken kısıtlayan bir taban sınıfın bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="b5116-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="b5116-116">Tüm değer türleri türetin <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="b5116-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="b5116-117">Bir değişken olarak bildirirseniz <xref:System.ValueType>, değer türleri yalnızca bu değişkene atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5116-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b5116-118">Kurallar</span><span class="sxs-lookup"><span data-stu-id="b5116-118">Rules</span></span>  
  
-   <span data-ttu-id="b5116-119">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="b5116-119">**Declaration Context.**</span></span> <span data-ttu-id="b5116-120">Kullanabileceğiniz `MustInherit` yalnızca bir `Class` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b5116-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
-   <span data-ttu-id="b5116-121">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="b5116-121">**Combined Modifiers.**</span></span> <span data-ttu-id="b5116-122">Belirtemezsiniz `MustInherit` ile birlikte `NotInheritable` aynı bildirimde.</span><span class="sxs-lookup"><span data-stu-id="b5116-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5116-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="b5116-123">Example</span></span>  
 <span data-ttu-id="b5116-124">Aşağıdaki örnek, zorla devralma ve geçersiz kılma zorlanmış gösterir.</span><span class="sxs-lookup"><span data-stu-id="b5116-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="b5116-125">Temel sınıf `shape` bir değişkeni tanımlar `acrossLine`.</span><span class="sxs-lookup"><span data-stu-id="b5116-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="b5116-126">Sınıfları `circle` ve `square` öğesinden türetilen `shape`.</span><span class="sxs-lookup"><span data-stu-id="b5116-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="b5116-127">Bunlar tanımını devral `acrossLine`, ancak işlev tanımlamanız gerekir `area` Bu hesaplamayı şekli her tür için farklı olduğu için.</span><span class="sxs-lookup"><span data-stu-id="b5116-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="b5116-128">Bildirebilirsiniz `shape1` ve `shape2` türünde olmasını `shape`.</span><span class="sxs-lookup"><span data-stu-id="b5116-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="b5116-129">Ancak, bir nesneden oluşturamazsınız `shape` işlevinin işlevselliğine eksik olduğundan `area` ve işaretlenmiş `MustInherit`.</span><span class="sxs-lookup"><span data-stu-id="b5116-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="b5116-130">Olarak bildirilen çünkü `shape`, değişkenleri `shape1` ve `shape2` nesnelere türetilmiş sınıflardan kısıtlanmıştır `circle` ve `square`.</span><span class="sxs-lookup"><span data-stu-id="b5116-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="b5116-131">Visual Basic, bu değişkenler için herhangi bir nesneye atamak yüksek düzeyde bir tür güvenliği sağlayan izin vermez.</span><span class="sxs-lookup"><span data-stu-id="b5116-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="b5116-132">Kullanım</span><span class="sxs-lookup"><span data-stu-id="b5116-132">Usage</span></span>  
 <span data-ttu-id="b5116-133">`MustInherit` Bu bağlamda değiştirici kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="b5116-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="b5116-134">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="b5116-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b5116-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5116-135">See also</span></span>

- [<span data-ttu-id="b5116-136">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="b5116-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="b5116-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="b5116-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="b5116-138">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="b5116-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="b5116-139">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="b5116-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
