---
title: Saf işlevlerde yeniden düzenleme-LINQ to XML
description: Saf işlevler ve kodu yeniden düzenleme için nasıl kullanılacağı hakkında bilgi edinin.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 18418a1fc39bee9f08cbe92d42c842e3fc9e148a
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553916"
---
# <a name="refactor-into-pure-functions-linq-to-xml"></a><span data-ttu-id="96926-103">Saf işlevlere yeniden düzenleme (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="96926-103">Refactor into pure functions (LINQ to XML)</span></span>

<span data-ttu-id="96926-104">Saf işlevsel dönüştürmelerin önemli bir yönü, saf işlevleri kullanarak kodu yeniden düzenleme hakkında bilgi ediniyor.</span><span class="sxs-lookup"><span data-stu-id="96926-104">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>

> [!NOTE]
> <span data-ttu-id="96926-105">İşlevsel programlamada ortak terminoloji, programları saf işlevleri kullanarak yeniden düzenleme biçimleridir.</span><span class="sxs-lookup"><span data-stu-id="96926-105">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="96926-106">Visual Basic ve C++ ' da bu, ilgili dillerdeki işlevlerin kullanımıyla hizalanır.</span><span class="sxs-lookup"><span data-stu-id="96926-106">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="96926-107">Ancak C# ' de işlevleri yöntemler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="96926-107">However, in C#, functions are called methods.</span></span> <span data-ttu-id="96926-108">Bu tartışmanın amaçları doğrultusunda, saf bir işlev C# dilinde bir yöntem olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="96926-108">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>

<span data-ttu-id="96926-109">Daha önce bu bölümde belirtildiği gibi, saf bir işlev iki yararlı özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="96926-109">As noted previously in this section, a pure function has two useful characteristics:</span></span>

- <span data-ttu-id="96926-110">Yan etkileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="96926-110">It has no side effects.</span></span> <span data-ttu-id="96926-111">İşlev herhangi bir değişken veya işlev dışındaki herhangi bir türdeki verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="96926-111">The function doesn't change any variables or the data of any type outside of the function.</span></span>
- <span data-ttu-id="96926-112">Tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="96926-112">It's consistent.</span></span> <span data-ttu-id="96926-113">Aynı giriş verisi kümesi verildiğinde, her zaman aynı çıkış değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="96926-113">Given the same set of input data, it will always return the same output value.</span></span>

<span data-ttu-id="96926-114">İşlevsel programlamaya geçiş yapmanın bir yolu, gereksiz yan etkileri ve dış bağımlılıkları ortadan kaldırmak için mevcut kodu yeniden düzenleme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="96926-114">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="96926-115">Bu şekilde, var olan kodun saf işlev sürümlerini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96926-115">In this way, you can create pure function versions of existing code.</span></span>

<span data-ttu-id="96926-116">Bu makalede, saf bir işlevin ne olduğu ve ne olmadığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="96926-116">This article discusses what a pure function is and what it's not.</span></span> <span data-ttu-id="96926-117">[Öğretici: bir WordprocessingML belgesi öğreticisindeki Içeriği değiştirme](xml-shape-wordprocessingml-documents.md) bir WordprocessingML belgesinin nasıl düzenleneceğini gösterir ve saf bir işlev kullanarak yeniden düzenleme ile iki örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="96926-117">The [Tutorial: Manipulate content in a WordprocessingML document](xml-shape-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>

<span data-ttu-id="96926-118">Aşağıdaki örneklerde, saf olmayan iki işlev ve bir saf işlev kontrast vardır.</span><span class="sxs-lookup"><span data-stu-id="96926-118">The following examples contrast two non-pure functions and a pure function.</span></span>

## <a name="example-implement-a-non-pure-function-that-changes-a-static-class-member"></a><span data-ttu-id="96926-119">Örnek: statik sınıf üyesini değiştiren saf olmayan bir işlev uygulama</span><span class="sxs-lookup"><span data-stu-id="96926-119">Example: Implement a non-pure function that changes a static class member</span></span>

<span data-ttu-id="96926-120">Aşağıdaki kodda, `HyphenatedConcat` statik sınıf üyesini değiştirdiği için işlev saf bir işlev değildir `aMember` :</span><span class="sxs-lookup"><span data-stu-id="96926-120">In the following code, the `HyphenatedConcat` function isn't a pure function, because it modifies the `aMember` static class member:</span></span>

```csharp
public class Program
{
    private static string aMember = "StringOne";

    public static void HyphenatedConcat(string appendStr)
    {
        aMember += '-' + appendStr;
    }

    public static void Main()
    {
        HyphenatedConcat("StringTwo");
        Console.WriteLine(aMember);
    }
}
```

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

<span data-ttu-id="96926-121">Bu örnek aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="96926-121">This example produces the following output:</span></span>

```output
StringOne-StringTwo
```

<span data-ttu-id="96926-122">Değiştirilen verilerin, veya erişimi olduğunu ya da `public` `private` `static` üye, `shared` üye veya örnek üyesi olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="96926-122">Note that it's irrelevant whether the data being modified has `public` or `private` access, or is a `static` member, `shared` member, or instance member.</span></span> <span data-ttu-id="96926-123">Saf işlev, işlevin dışındaki verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="96926-123">A pure function doesn't change any data outside of the function.</span></span>

## <a name="example-implement-a-non-pure-function-that-changes-a-parameter"></a><span data-ttu-id="96926-124">Örnek: bir parametreyi değiştiren saf olmayan bir işlev uygulama</span><span class="sxs-lookup"><span data-stu-id="96926-124">Example: Implement a non-pure function that changes a parameter</span></span>

<span data-ttu-id="96926-125">Ayrıca, parametresinin içeriğini değiştirdiği için aynı işlevin aşağıdaki sürümü saf değildir `sb` .</span><span class="sxs-lookup"><span data-stu-id="96926-125">Furthermore, the following version of this same function isn't pure because it modifies the contents of its parameter, `sb`.</span></span>

```csharp
public class Program
{
    public static void HyphenatedConcat(StringBuilder sb, String appendStr)
    {
        sb.Append('-' + appendStr);
    }

    public static void Main()
    {
        StringBuilder sb1 = new StringBuilder("StringOne");
        HyphenatedConcat(sb1, "StringTwo");
        Console.WriteLine(sb1);
    }
}
```

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

<span data-ttu-id="96926-126">Programın bu sürümü ilk sürümle aynı çıktıyı üretir, çünkü `HyphenatedConcat` işlev üye işlevini çağırarak ilk parametresinin değerini (durum) değiştirdi <xref:System.Text.StringBuilder.Append%2A> .</span><span class="sxs-lookup"><span data-stu-id="96926-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="96926-127">Bu değişiklik, `HyphenatedConcat` değer çağırma parametresi geçen olgusuna rağmen oluşur.</span><span class="sxs-lookup"><span data-stu-id="96926-127">Note that this alteration occurs despite the fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96926-128">Başvuru türleri için bir parametreyi değere göre geçirirseniz, başvurunun geçirildiği bir nesnenin kopyasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="96926-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="96926-129">Bu kopya, özgün başvurusuyla aynı örnek verileriyle ilişkili olmaya devam eder (başvuru değişkeni yeni bir nesneye atanana kadar).</span><span class="sxs-lookup"><span data-stu-id="96926-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="96926-130">Bir parametreyi değiştirmek için bir işlev için başvuruya göre arama gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="96926-130">Call-by-reference isn't necessarily required for a function to modify a parameter.</span></span>

## <a name="example-implement-a-pure-function"></a><span data-ttu-id="96926-131">Örnek: saf bir işlev uygulama</span><span class="sxs-lookup"><span data-stu-id="96926-131">Example: Implement a pure function</span></span>

<span data-ttu-id="96926-132">Programın bu sonraki sürümü, `HyphenatedConcat` işlevinin saf işlev olarak nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="96926-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>

```csharp
class Program
{
    public static string HyphenatedConcat(string s, string appendStr)
    {
        return (s + '-' + appendStr);
    }

    public static void Main(string[] args)
    {
        string s1 = "StringOne";
        string s2 = HyphenatedConcat(s1, "StringTwo");
        Console.WriteLine(s2);
    }
}
```

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

<span data-ttu-id="96926-133">Yine, bu sürüm aynı çıkış satırını üretir: `StringOne-StringTwo` .</span><span class="sxs-lookup"><span data-stu-id="96926-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="96926-134">Birleştirilmiş değeri bekletmek için, ara değişkende depolandığını unutmayın `s2` .</span><span class="sxs-lookup"><span data-stu-id="96926-134">Note that to retain the concatenated value, it's stored in the intermediate variable `s2`.</span></span>

<span data-ttu-id="96926-135">Çok yararlı olabilecek bir yaklaşım, yerel olarak etkileyici olan işlevleri yazmak (yani yerel değişkenleri bildirdikleri ve değiştirdiklerinde), ancak Global olarak saf bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="96926-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="96926-136">Bu gibi işlevler, istenen ek özelliklerin çoğuna sahiptir, ancak basit bir döngü aynı şeyi gerçekleştirirken özyineleme kullanmak zorunda kalmadan, daha fazla çalışan işlevsel programlama deyimidir.</span><span class="sxs-lookup"><span data-stu-id="96926-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>

## <a name="standard-query-operators"></a><span data-ttu-id="96926-137">Standart sorgu işleçleri</span><span class="sxs-lookup"><span data-stu-id="96926-137">Standard query operators</span></span>

<span data-ttu-id="96926-138">Standart sorgu işleçlerinin önemli bir özelliği, saf işlevler olarak uygulanırlar.</span><span class="sxs-lookup"><span data-stu-id="96926-138">An important characteristic of the standard query operators is that they're implemented as pure functions.</span></span>

<span data-ttu-id="96926-139">Daha fazla bilgi için bkz. [Standart sorgu Işleçlerine genel bakış (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) ve [Standart sorgu işleçlerine genel bakış (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="96926-139">For more information, see [Standard Query Operators Overview (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) and [Standard Query Operators Overview (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="96926-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96926-140">See also</span></span>

- [<span data-ttu-id="96926-141">Saf işlevsel dönüşümlere giriş</span><span class="sxs-lookup"><span data-stu-id="96926-141">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)
- [<span data-ttu-id="96926-142">Fonksiyonel programlama ve kesinlik temelli programlama karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="96926-142">Functional programming vs. imperative programming</span></span>](functional-vs-imperative-programming.md)
