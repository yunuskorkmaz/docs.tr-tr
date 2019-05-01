---
title: (Visual Basic) saf işlevler halinde yeniden düzenleme
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 0a37b30278c850256355612cec09a4c017c7adc2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787172"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="73554-102">(Visual Basic) saf işlevler halinde yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="73554-102">Refactoring Into Pure Functions (Visual Basic)</span></span>

<span data-ttu-id="73554-103">Saf işlevsel dönüşümlere önemli bir yönüdür saf işlevler kullanarak kodunuzu yeniden değiştirmenin nasıl öğrenmeye devam ettiği.</span><span class="sxs-lookup"><span data-stu-id="73554-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

<span data-ttu-id="73554-104">Bu bölümde daha önce belirtildiği gibi saf işlev iki yararlı özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="73554-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="73554-105">Bu, yan etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="73554-105">It has no side effects.</span></span> <span data-ttu-id="73554-106">İşlevi, tüm değişkenler veya işlev dışında herhangi bir türde verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="73554-106">The function does not change any variables or the data of any type outside of the function.</span></span>

- <span data-ttu-id="73554-107">Tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="73554-107">It is consistent.</span></span> <span data-ttu-id="73554-108">Aynı giriş veri kümesi düşünüldüğünde, bu her zaman aynı çıkış değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="73554-108">Given the same set of input data, it will always return the same output value.</span></span>

 <span data-ttu-id="73554-109">Yollarından fonksiyonel programlama için geçiş, gereksiz yan etkileri ve dış bağımlılıkları ortadan kaldırmak için mevcut kodu yeniden düzenleyin sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="73554-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="73554-110">Bu şekilde, varolan kod sürümlerini saf işlev oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="73554-110">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="73554-111">Bu konuda ele alınmıştır saf işlev ne olduğunu ve ne değildir.</span><span class="sxs-lookup"><span data-stu-id="73554-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="73554-112">[Öğreticisi: (Visual Basic) WordprocessingML belgesindeki içeriği düzenleme](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğretici WordprocessingML belgesinin işlemek nasıl gösterir ve nasıl saf işlev kullanarak yeniden düzenleme için iki örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="73554-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="73554-113">Yan etkiler ve dış bağımlılıkları ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="73554-113">Eliminating Side Effects and External Dependencies</span></span>

<span data-ttu-id="73554-114">Aşağıdaki örnekler, iki saf olmayan işlevler ve saf işlev karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="73554-114">The following examples contrast two non-pure functions and a pure function.</span></span>

### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="73554-115">Sınıf üyesi değişiklikleri saf olmayan işlevi</span><span class="sxs-lookup"><span data-stu-id="73554-115">Non-Pure Function that Changes a Class Member</span></span>

<span data-ttu-id="73554-116">Aşağıdaki kodda, `HyphenatedConcat` işlevi değil, saf işlev değiştirdiği çünkü `aMember` sınıftaki veri üyesi:</span><span class="sxs-lookup"><span data-stu-id="73554-116">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>

```vb
Module Module1
    Dim aMember As String = "StringOne"

    Public Sub HyphenatedConcat(ByVal appendStr As String)
        aMember = aMember & "-" & appendStr
    End Sub

    Sub Main()
        HyphenatedConcat("StringTwo")
        Console.WriteLine(aMember)
    End Sub
End Module
```

<span data-ttu-id="73554-117">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="73554-117">This code produces the following output:</span></span>

```
StringOne-StringTwo
```

<span data-ttu-id="73554-118">Bu verilerin değiştirilmesi olup ilgisiz olduğuna dikkat edin `public` veya `private` erişim ya da bir `shared` veya bir örnek üyesi.</span><span class="sxs-lookup"><span data-stu-id="73554-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="73554-119">Saf işlev, işlev dışındaki tüm verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="73554-119">A pure function does not change any data outside of the function.</span></span>

### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="73554-120">Bağımsız değişken değişiklikleri saf olmayan işlevi</span><span class="sxs-lookup"><span data-stu-id="73554-120">Non-Pure Function that Changes an Argument</span></span>

<span data-ttu-id="73554-121">Kendi parametre içeriğini değiştirir ayrıca, aynı işlevi aşağıdaki sürümü saf olmadığından `sb`.</span><span class="sxs-lookup"><span data-stu-id="73554-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>

```vb
Module Module1
    Public Sub HyphenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)
        sb.Append("-" & appendStr)
    End Sub

    Sub Main()
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")
        HyphenatedConcat(sb1, "StringTwo")
        Console.WriteLine(sb1)
    End Sub
End Module
```

<span data-ttu-id="73554-122">Çünkü programın bu sürümünü aynı ilk sürümde çıktı üretir `HyphenatedConcat` işlevi, birinci parametresinin değerini (durum) çağırarak değişti <xref:System.Text.StringBuilder.Append%2A> üye işlevi.</span><span class="sxs-lookup"><span data-stu-id="73554-122">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="73554-123">Bu değişikliği rağmen bu durumu kendi lehine oluştuğunu unutmayın, `HyphenatedConcat` çağrı değerli parametre geçirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="73554-123">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="73554-124">Değere göre bir parametre geçirirseniz başvuru türleri için geçirilen bir nesneye başvuru bir kopyasını sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="73554-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="73554-125">(Yeni bir nesneye başvuru değişkenini atanıncaya kadar) Bu hala özgün başvuru aynı örnek verileri ile ilişkili bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="73554-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="73554-126">Başvuru ile çağrı parametreyi değiştirmek bir işlev için mutlaka gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="73554-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>

### <a name="pure-function"></a><span data-ttu-id="73554-127">Saf işlev</span><span class="sxs-lookup"><span data-stu-id="73554-127">Pure Function</span></span>

<span data-ttu-id="73554-128">Bu program'ın sonraki sürümü sorularının yanıtlarını nasıl uygulanacağı `HyphenatedConcat` işlevi saf işlev.</span><span class="sxs-lookup"><span data-stu-id="73554-128">This next version of the program hows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

```vb
Module Module1
    Public Function HyphenatedConcat(ByVal s As String, ByVal appendStr As String) As String
        Return (s & "-" & appendStr)
    End Function

    Sub Main()
        Dim s1 As String = "StringOne"
        Dim s2 As String = HyphenatedConcat(s1, "StringTwo")
        Console.WriteLine(s2)
    End Sub
End Module
```

<span data-ttu-id="73554-129">Bu sürümü çıktı satırını yeniden üretir: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="73554-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="73554-130">Birleştirilmiş değer korumak için bu Ara değişkende depolandığını unutmayın `s2`.</span><span class="sxs-lookup"><span data-stu-id="73554-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="73554-131">Yerel olarak Hanuka işlevleri yazmak için kullanışlı bir yaklaşım olan (diğer bir deyişle, bunlar bildirme ve yerel değişkenleri değiştirin), ancak genel olarak saf.</span><span class="sxs-lookup"><span data-stu-id="73554-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="73554-132">Bu tür işlevleri birçok arzu composability özelliklere sahip, ancak bazı basit döngüyü aynı şeyi yaptığınız zaman, özyineleme kullanmak zorunda gibi daha karışık işlevsel programlama deyimlerini, kaçının.</span><span class="sxs-lookup"><span data-stu-id="73554-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="73554-133">Standart sorgu işleçleri</span><span class="sxs-lookup"><span data-stu-id="73554-133">Standard Query Operators</span></span>

<span data-ttu-id="73554-134">Standart sorgu işleçlerinin önemli bir özelliği, saf işlevler uygulanan ' dir.</span><span class="sxs-lookup"><span data-stu-id="73554-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>

<span data-ttu-id="73554-135">Daha fazla bilgi için [standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="73554-135">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73554-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="73554-136">See also</span></span>

- [<span data-ttu-id="73554-137">Saf işlevsel dönüşümlere (Visual Basic) giriş</span><span class="sxs-lookup"><span data-stu-id="73554-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="73554-138">İşlevsel Programlama ve Kesin programlama karşılaştırması (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73554-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
