---
title: MustInherit
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
ms.openlocfilehash: 30befaaf194d78d26a57f29c59bf0a603e9f07a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351504"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="4f0e6-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f0e6-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="4f0e6-103">Bir sınıfın sadece temel sınıf olarak kullanılabileceğini ve doğrudan bundan bir nesne oluşturkullanılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f0e6-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4f0e6-104">Remarks</span></span>  
 <span data-ttu-id="4f0e6-105">*Temel sınıfın* amacı ( *soyut sınıf*olarak da bilinir), bundan türetilmiş tüm sınıflar için ortak olan işlevleri tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="4f0e6-106">Bu, türetilmiş sınıfları ortak öğeleri yeniden tanımlamak zorunda kalmadan kaydeder.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="4f0e6-107">Bazı durumlarda, bu ortak işlevsellik kullanılabilir bir nesne oluşturmak için yeterli değildir ve her türetilmiş sınıf eksik işlevselliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="4f0e6-108">Böyle bir durumda, tüketen kodun yalnızca türetilmiş sınıflardan nesneler oluşturmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="4f0e6-109">Bunu zorlamak için temel sınıfta `MustInherit` kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="4f0e6-110">`MustInherit` sınıfının başka bir kullanımı, bir değişkeni ilgili sınıflar kümesiyle kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="4f0e6-111">Bir temel sınıf tanımlayabilir ve bu ilgili sınıfları bundan türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="4f0e6-112">Temel sınıfın tüm türetilmiş sınıflarda ortak bir işlev sağlaması gerekmez, ancak değişkenlere değer atamak için bir filtre işlevi görebilir.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="4f0e6-113">Tüketim kodunuz temel sınıf olarak bir değişken bildirirse Visual Basic, yalnızca türetilmiş sınıflardan birindeki bir nesneyi bu değişkene atamanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="4f0e6-114">.NET Framework, <xref:System.Array>, <xref:System.Enum>ve <xref:System.ValueType>arasında çeşitli `MustInherit` sınıfları tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="4f0e6-115"><xref:System.ValueType>, bir değişkeni kısıtlayan temel sınıfa bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="4f0e6-116">Tüm değer türleri <xref:System.ValueType>türetilir.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="4f0e6-117">Bir değişkeni <xref:System.ValueType>olarak bildirirseniz, bu değişkene yalnızca değer türlerini atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4f0e6-118">Kurallar</span><span class="sxs-lookup"><span data-stu-id="4f0e6-118">Rules</span></span>  
  
- <span data-ttu-id="4f0e6-119">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="4f0e6-119">**Declaration Context.**</span></span> <span data-ttu-id="4f0e6-120">Yalnızca bir `Class` bildiriminde `MustInherit` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
- <span data-ttu-id="4f0e6-121">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="4f0e6-121">**Combined Modifiers.**</span></span> <span data-ttu-id="4f0e6-122">Aynı bildirimde `NotInheritable` birlikte `MustInherit` belirtemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f0e6-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="4f0e6-123">Example</span></span>  
 <span data-ttu-id="4f0e6-124">Aşağıdaki örnek, hem zorunlu devralmayı hem de geçersiz kılmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="4f0e6-125">Temel sınıf `shape` bir değişken `acrossLine`tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="4f0e6-126">Sınıflar `circle` ve `square` `shape`türetilir.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="4f0e6-127">`acrossLine`tanımını alırlar, ancak bu hesaplama her bir şekil türü için farklı olduğundan, bu, işlevi `area` tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="4f0e6-128">`shape1` ve `shape2` `shape`türünde olacak şekilde bildirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="4f0e6-129">Ancak, `shape` bir nesne oluşturamazsınız çünkü bu, işlev `area` işlevselliğine sahip ve `MustInherit`olarak işaretlenmiş.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="4f0e6-130">`shape`olarak bildirildiği için, `shape1` ve `shape2` değişkenleri türetilmiş sınıflardaki nesnelerle kısıtlıdır `circle` ve `square`.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="4f0e6-131">Visual Basic, bu değişkenlere başka herhangi bir nesne atamanıza izin vermez, bu da size yüksek düzeyde güvenlik düzeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="4f0e6-132">Kullanım</span><span class="sxs-lookup"><span data-stu-id="4f0e6-132">Usage</span></span>  
 <span data-ttu-id="4f0e6-133">`MustInherit` değiştiricisi Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="4f0e6-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="4f0e6-134">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f0e6-134">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="4f0e6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f0e6-135">See also</span></span>

- [<span data-ttu-id="4f0e6-136">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="4f0e6-136">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="4f0e6-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="4f0e6-137">NotInheritable</span></span>](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="4f0e6-138">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="4f0e6-138">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="4f0e6-139">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="4f0e6-139">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
