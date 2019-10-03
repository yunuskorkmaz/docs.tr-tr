---
title: Saf IŞLEVLERE yeniden düzenleme (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: e951b3e9108f26a9c861eb49c44bb0a510131819
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834911"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="8ae2d-102">Saf IŞLEVLERE yeniden düzenleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ae2d-102">Refactoring Into Pure Functions (Visual Basic)</span></span>

<span data-ttu-id="8ae2d-103">Saf işlevsel dönüştürmelerin önemli bir yönü, saf işlevleri kullanarak kodu yeniden düzenleme hakkında bilgi ediniyor.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

<span data-ttu-id="8ae2d-104">Daha önce bu bölümde belirtildiği gibi, saf bir işlev iki yararlı özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="8ae2d-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="8ae2d-105">Yan etkileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-105">It has no side effects.</span></span> <span data-ttu-id="8ae2d-106">İşlev herhangi bir değişken veya işlev dışındaki herhangi bir türdeki veriyi değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-106">The function does not change any variables or the data of any type outside of the function.</span></span>

- <span data-ttu-id="8ae2d-107">Tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-107">It is consistent.</span></span> <span data-ttu-id="8ae2d-108">Aynı giriş verisi kümesi verildiğinde, her zaman aynı çıkış değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-108">Given the same set of input data, it will always return the same output value.</span></span>

 <span data-ttu-id="8ae2d-109">İşlevsel programlamaya geçiş yapmanın bir yolu, gereksiz yan etkileri ve dış bağımlılıkları ortadan kaldırmak için mevcut kodu yeniden düzenleme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="8ae2d-110">Bu şekilde, var olan kodun saf işlev sürümlerini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-110">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="8ae2d-111">Bu konuda, saf bir işlevin ne olduğu ve ne olmadığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="8ae2d-112">[Öğretici: bir WordprocessingML belgesi (Visual Basic) öğreticisindeki Içeriği düzenleme](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) bir WordprocessingML belgesinin nasıl düzenleneceğini gösterir ve saf bir işlev kullanarak yeniden düzenleme ile iki örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="8ae2d-113">Yan etkileri ve dış bağımlılıkları ortadan kaldırma</span><span class="sxs-lookup"><span data-stu-id="8ae2d-113">Eliminating Side Effects and External Dependencies</span></span>

<span data-ttu-id="8ae2d-114">Aşağıdaki örneklerde, saf olmayan iki işlev ve bir saf işlev kontrast vardır.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-114">The following examples contrast two non-pure functions and a pure function.</span></span>

### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="8ae2d-115">Bir sınıf üyesini değiştiren saf olmayan Işlev</span><span class="sxs-lookup"><span data-stu-id="8ae2d-115">Non-Pure Function that Changes a Class Member</span></span>

<span data-ttu-id="8ae2d-116">Aşağıdaki kodda `HyphenatedConcat` işlevi saf bir işlev değildir, çünkü sınıfta `aMember` veri üyesini değiştirir:</span><span class="sxs-lookup"><span data-stu-id="8ae2d-116">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>

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

<span data-ttu-id="8ae2d-117">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="8ae2d-117">This code produces the following output:</span></span>

```console
StringOne-StringTwo
```

<span data-ttu-id="8ae2d-118">Değiştirilen verilerin `public` veya `private` erişimine sahip olup olmadığını veya `shared` üyesi mi yoksa örnek üyesini mi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="8ae2d-119">Saf bir işlev, işlevin dışındaki herhangi bir veriyi değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-119">A pure function does not change any data outside of the function.</span></span>

### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="8ae2d-120">Bir bağımsız değişkeni değiştiren saf olmayan Işlev</span><span class="sxs-lookup"><span data-stu-id="8ae2d-120">Non-Pure Function that Changes an Argument</span></span>

<span data-ttu-id="8ae2d-121">Ayrıca, aynı işlevin aşağıdaki sürümü saf değildir çünkü parametresinin içeriğini değiştirir, `sb`.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>

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

<span data-ttu-id="8ae2d-122">Programın bu sürümü ilk sürümle aynı çıktıyı üretir, çünkü `HyphenatedConcat` işlevi, <xref:System.Text.StringBuilder.Append%2A> üye işlevini çağırarak ilk parametresinin değerini (durum) değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-122">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="8ae2d-123">Bu değişiklik, `HyphenatedConcat` ' ın değer olarak çağırma parametresi geçirdiğine rağmen meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-123">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8ae2d-124">Başvuru türleri için bir parametreyi değere göre geçirirseniz, başvurunun geçirildiği bir nesnenin kopyasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="8ae2d-125">Bu kopya, özgün başvurusuyla aynı örnek verileriyle ilişkili olmaya devam eder (başvuru değişkeni yeni bir nesneye atanana kadar).</span><span class="sxs-lookup"><span data-stu-id="8ae2d-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="8ae2d-126">Bir parametreyi değiştirmek için bir işlev için başvuruya göre arama gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>

### <a name="pure-function"></a><span data-ttu-id="8ae2d-127">Saf Işlev</span><span class="sxs-lookup"><span data-stu-id="8ae2d-127">Pure Function</span></span>

<span data-ttu-id="8ae2d-128">Programın bu sonraki sürümü, `HyphenatedConcat` işlevini saf işlev olarak nasıl uygulayacağınızı barındırdı.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-128">This next version of the program hows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

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

<span data-ttu-id="8ae2d-129">Yine, bu sürüm aynı çıkış satırını üretir: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="8ae2d-130">Art arda gelen değeri bekletmek için `s2` ara değişkeninde depolandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="8ae2d-131">Çok yararlı olabilecek bir yaklaşım, yerel olarak etkileyici olan işlevleri yazmak (yani yerel değişkenleri bildirdikleri ve değiştirdiklerinde), ancak Global olarak saf bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="8ae2d-132">Bu gibi işlevler, istenen ek özelliklerin çoğuna sahiptir, ancak basit bir döngü aynı şeyi gerçekleştirirken özyineleme kullanmak zorunda kalmadan, daha fazla çalışan işlevsel programlama deyimidir.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="8ae2d-133">Standart sorgu Işleçleri</span><span class="sxs-lookup"><span data-stu-id="8ae2d-133">Standard Query Operators</span></span>

<span data-ttu-id="8ae2d-134">Standart sorgu işleçlerinin önemli bir özelliği, saf işlevler olarak uygulanırlar.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>

<span data-ttu-id="8ae2d-135">Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8ae2d-135">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8ae2d-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ae2d-136">See also</span></span>

- [<span data-ttu-id="8ae2d-137">Saf Işlevsel dönüşümlere giriş (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ae2d-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="8ae2d-138">Fonksiyonel programlama ile kesinlik temelli programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ae2d-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
