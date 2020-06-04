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
ms.openlocfilehash: 84df7a5cfdad3b5bc6764675725a5d0cb402b0b7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396213"
---
# <a name="mustinherit-visual-basic"></a><span data-ttu-id="3cca7-102">MustInherit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3cca7-102">MustInherit (Visual Basic)</span></span>
<span data-ttu-id="3cca7-103">Bir sınıfın sadece temel sınıf olarak kullanılabileceğini ve doğrudan bundan bir nesne oluşturkullanılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3cca7-103">Specifies that a class can be used only as a base class and that you cannot create an object directly from it.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cca7-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3cca7-104">Remarks</span></span>  
 <span data-ttu-id="3cca7-105">*Temel sınıfın* amacı ( *soyut sınıf*olarak da bilinir), bundan türetilmiş tüm sınıflar için ortak olan işlevleri tanımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="3cca7-105">The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it.</span></span> <span data-ttu-id="3cca7-106">Bu, türetilmiş sınıfları ortak öğeleri yeniden tanımlamak zorunda kalmadan kaydeder.</span><span class="sxs-lookup"><span data-stu-id="3cca7-106">This saves the derived classes from having to redefine the common elements.</span></span> <span data-ttu-id="3cca7-107">Bazı durumlarda, bu ortak işlevsellik kullanılabilir bir nesne oluşturmak için yeterli değildir ve her türetilmiş sınıf eksik işlevselliği tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3cca7-107">In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality.</span></span> <span data-ttu-id="3cca7-108">Böyle bir durumda, tüketen kodun yalnızca türetilmiş sınıflardan nesneler oluşturmasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="3cca7-108">In such a case, you want the consuming code to create objects only from the derived classes.</span></span> <span data-ttu-id="3cca7-109">`MustInherit`Bunu zorlamak için temel sınıfta kullanın.</span><span class="sxs-lookup"><span data-stu-id="3cca7-109">You use `MustInherit` on the base class to enforce this.</span></span>  
  
 <span data-ttu-id="3cca7-110">Bir sınıfının başka bir kullanımı `MustInherit` , bir değişkeni ilgili sınıflar kümesiyle kısıtlamadır.</span><span class="sxs-lookup"><span data-stu-id="3cca7-110">Another use of a `MustInherit` class is to restrict a variable to a set of related classes.</span></span> <span data-ttu-id="3cca7-111">Bir temel sınıf tanımlayabilir ve bu ilgili sınıfları bundan türetebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cca7-111">You can define a base class and derive all these related classes from it.</span></span> <span data-ttu-id="3cca7-112">Temel sınıfın tüm türetilmiş sınıflarda ortak bir işlev sağlaması gerekmez, ancak değişkenlere değer atamak için bir filtre işlevi görebilir.</span><span class="sxs-lookup"><span data-stu-id="3cca7-112">The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables.</span></span> <span data-ttu-id="3cca7-113">Tüketim kodunuz temel sınıf olarak bir değişken bildirirse Visual Basic, yalnızca türetilmiş sınıflardan birindeki bir nesneyi bu değişkene atamanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="3cca7-113">If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.</span></span>  
  
 <span data-ttu-id="3cca7-114">.NET Framework, `MustInherit` ve arasında birkaç sınıfı tanımlar <xref:System.Array> <xref:System.Enum> <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="3cca7-114">The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>.</span></span> <span data-ttu-id="3cca7-115"><xref:System.ValueType>, bir değişkeni kısıtlayan temel sınıfa bir örnektir.</span><span class="sxs-lookup"><span data-stu-id="3cca7-115"><xref:System.ValueType> is an example of a base class that restricts a variable.</span></span> <span data-ttu-id="3cca7-116">Tüm değer türleri öğesinden türetilir <xref:System.ValueType> .</span><span class="sxs-lookup"><span data-stu-id="3cca7-116">All value types derive from <xref:System.ValueType>.</span></span> <span data-ttu-id="3cca7-117">Bir değişkeni olarak bildirirseniz <xref:System.ValueType> , bu değişkene yalnızca değer türlerini atayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cca7-117">If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3cca7-118">Kurallar</span><span class="sxs-lookup"><span data-stu-id="3cca7-118">Rules</span></span>  
  
- <span data-ttu-id="3cca7-119">**Bildirim bağlamı.**</span><span class="sxs-lookup"><span data-stu-id="3cca7-119">**Declaration Context.**</span></span> <span data-ttu-id="3cca7-120">`MustInherit`Yalnızca bir `Class` ifadede kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3cca7-120">You can use `MustInherit` only in a `Class` statement.</span></span>  
  
- <span data-ttu-id="3cca7-121">**Birleşik değiştiriciler.**</span><span class="sxs-lookup"><span data-stu-id="3cca7-121">**Combined Modifiers.**</span></span> <span data-ttu-id="3cca7-122">`MustInherit`Aynı bildirimde ile birlikte belirtemezsiniz `NotInheritable` .</span><span class="sxs-lookup"><span data-stu-id="3cca7-122">You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cca7-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="3cca7-123">Example</span></span>  
 <span data-ttu-id="3cca7-124">Aşağıdaki örnek, hem zorunlu devralmayı hem de geçersiz kılmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="3cca7-124">The following example illustrates both forced inheritance and forced overriding.</span></span> <span data-ttu-id="3cca7-125">Temel sınıf `shape` bir değişkeni tanımlar `acrossLine` .</span><span class="sxs-lookup"><span data-stu-id="3cca7-125">The base class `shape` defines a variable `acrossLine`.</span></span> <span data-ttu-id="3cca7-126">Sınıflar `circle` ve `square` türetilir `shape` .</span><span class="sxs-lookup"><span data-stu-id="3cca7-126">The classes `circle` and `square` derive from `shape`.</span></span> <span data-ttu-id="3cca7-127">Tanımları devralınır `acrossLine` , ancak `area` Bu hesaplama her bir şekil türü için farklı olduğu için işlevi tanımlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3cca7-127">They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.</span></span>  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 <span data-ttu-id="3cca7-128">`shape1`' İ ve `shape2` türünü belirtebilirsiniz `shape` .</span><span class="sxs-lookup"><span data-stu-id="3cca7-128">You can declare `shape1` and `shape2` to be of type `shape`.</span></span> <span data-ttu-id="3cca7-129">Ancak, `shape` işlevin işlevselliğine sahip olmadığı ve işaretlendiği için bir nesnesi oluşturamazsınız `area` `MustInherit` .</span><span class="sxs-lookup"><span data-stu-id="3cca7-129">However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.</span></span>  
  
 <span data-ttu-id="3cca7-130">`shape`, Değişkenleri olarak bildirildiği `shape1` için, ve `shape2` türetilmiş sınıflardaki nesnelerle kısıtlıdır `circle` `square` .</span><span class="sxs-lookup"><span data-stu-id="3cca7-130">Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`.</span></span> <span data-ttu-id="3cca7-131">Visual Basic, bu değişkenlere başka herhangi bir nesne atamanıza izin vermez, bu da size yüksek düzeyde güvenlik düzeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3cca7-131">Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="3cca7-132">Kullanım</span><span class="sxs-lookup"><span data-stu-id="3cca7-132">Usage</span></span>  
 <span data-ttu-id="3cca7-133">`MustInherit`Değiştirici Bu bağlamda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="3cca7-133">The `MustInherit` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="3cca7-134">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="3cca7-134">Class Statement</span></span>](../statements/class-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3cca7-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cca7-135">See also</span></span>

- [<span data-ttu-id="3cca7-136">Inherits Deyimi</span><span class="sxs-lookup"><span data-stu-id="3cca7-136">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="3cca7-137">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="3cca7-137">NotInheritable</span></span>](notinheritable.md)
- [<span data-ttu-id="3cca7-138">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="3cca7-138">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="3cca7-139">Devralma Temelleri</span><span class="sxs-lookup"><span data-stu-id="3cca7-139">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
