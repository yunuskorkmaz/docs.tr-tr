---
title: Saf işlevleri (Visual Basic) yeniden düzenleme
ms.date: 07/20/2015
ms.assetid: 99e7d27b-a3ff-4577-bdb2-5a8278d6d7af
ms.openlocfilehash: 207b77ff50cd2aaeede758db69b48c8f29a16ab1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654267"
---
# <a name="refactoring-into-pure-functions-visual-basic"></a><span data-ttu-id="f03b2-102">Saf işlevleri (Visual Basic) yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="f03b2-102">Refactoring Into Pure Functions (Visual Basic)</span></span>
<span data-ttu-id="f03b2-103">Saf işlevsel Dönüşümlerin önemli bir durum kodu saf işlevler kullanılarak yeniden nasıl öğrenme.</span><span class="sxs-lookup"><span data-stu-id="f03b2-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
 <span data-ttu-id="f03b2-104">Bu bölümde daha önce belirtildiği gibi saf işlevi iki yararlı özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="f03b2-104">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
-   <span data-ttu-id="f03b2-105">Hiçbir yan etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="f03b2-105">It has no side effects.</span></span> <span data-ttu-id="f03b2-106">İşlev hiçbir değişken veya işlev dışında herhangi bir türde verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="f03b2-106">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
-   <span data-ttu-id="f03b2-107">Tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="f03b2-107">It is consistent.</span></span> <span data-ttu-id="f03b2-108">Aynı dizi girdi verisi verildiğinde, her zaman aynı çıkış değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f03b2-108">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="f03b2-109">İşlevsel programlama koddan bir gereksiz yan etkiler ve dış bağımlılıkları ortadan kaldırmak için var olan kodu yeniden düzenlemeniz için yoludur.</span><span class="sxs-lookup"><span data-stu-id="f03b2-109">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="f03b2-110">Bu şekilde, var olan kodu saf işlevi sürümlerini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f03b2-110">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="f03b2-111">Bu konuda ele alınmıştır saf işlevi ne olduğu ve ne değildir.</span><span class="sxs-lookup"><span data-stu-id="f03b2-111">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="f03b2-112">[Öğreticisi: düzenleme içerik WordprocessingML belgedeki (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğretici WordprocessingML belgeyi işlemek nasıl gösterir ve nasıl saf işlevi kullanarak düzenleme için iki örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f03b2-112">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="f03b2-113">Yan etkiler ve dış bağımlılıkları ortadan</span><span class="sxs-lookup"><span data-stu-id="f03b2-113">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="f03b2-114">Aşağıdaki örnekler, iki saf olmayan işlevler ve saf işlevi karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="f03b2-114">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="f03b2-115">Sınıf üyesine değişiklikleri saf olmayan işlevi</span><span class="sxs-lookup"><span data-stu-id="f03b2-115">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="f03b2-116">Aşağıdaki kodda, `HypenatedConcat` işlevi değil saf işlevi değiştirdiği çünkü `aMember` sınıfı veri üyesi:</span><span class="sxs-lookup"><span data-stu-id="f03b2-116">In the following code, the `HypenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
```vb  
Module Module1  
    Dim aMember As String = "StringOne"  
  
    Public Sub HypenatedConcat(ByVal appendStr As String)  
        aMember = aMember & "-" & appendStr  
    End Sub  
  
    Sub Main()  
        HypenatedConcat("StringTwo")  
        Console.WriteLine(aMember)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="f03b2-117">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="f03b2-117">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="f03b2-118">Değiştirilen verileri olup ilgisiz olup olmadığını Not `public` veya `private` erişim ya da bir `shared` üyesi veya bir örnek üyesine.</span><span class="sxs-lookup"><span data-stu-id="f03b2-118">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a  `shared` member or an instance member.</span></span> <span data-ttu-id="f03b2-119">Saf işlevi işlevi dışında herhangi bir veri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="f03b2-119">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="f03b2-120">Bağımsız değişken değişiklikleri saf olmayan işlevi</span><span class="sxs-lookup"><span data-stu-id="f03b2-120">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="f03b2-121">Kendi parametresinin içeriğini değiştirdiği Ayrıca, aynı bu işlevi aşağıdaki sürümü saf olmadığından `sb`.</span><span class="sxs-lookup"><span data-stu-id="f03b2-121">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
```vb  
Module Module1  
    Public Sub HypenatedConcat(ByVal sb As StringBuilder, ByVal appendStr As String)  
        sb.Append("-" & appendStr)  
    End Sub  
  
    Sub Main()  
        Dim sb1 As StringBuilder = New StringBuilder("StringOne")  
        HypenatedConcat(sb1, "StringTwo")  
        Console.WriteLine(sb1)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="f03b2-122">Çünkü programın bu sürümü aynı ilk sürüm olarak çıktı üretir `HypenatedConcat` işlevini çağırarak, ilk parametresinin değeri (durum) değişti <xref:System.Text.StringBuilder.Append%2A> üye işlevi.</span><span class="sxs-lookup"><span data-stu-id="f03b2-122">This version of the program produces the same output as the first version, because the `HypenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="f03b2-123">Bu değişiklikle rağmen bu olgu oluştuğunu unutmayın, `HypenatedConcat` çağrısı değerli parametre geçirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="f03b2-123">Note that this alteration occurs despite that fact that `HypenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f03b2-124">Bir parametre değeri tarafından geçirirseniz başvuru türleri için geçirilen bir nesneye başvuru kopyasını sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="f03b2-124">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="f03b2-125">(Yeni bir nesneye başvuru değişkeni atanıncaya kadar) Bu hala özgün başvuru olarak aynı örnek verilerle ilişkili bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="f03b2-125">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="f03b2-126">Çağrı tarafından başvuru mutlaka bir işlev parametre değiştirmek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="f03b2-126">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="f03b2-127">Saf işlevi</span><span class="sxs-lookup"><span data-stu-id="f03b2-127">Pure Function</span></span>  
 <span data-ttu-id="f03b2-128">Bu program sonraki sürümü hows nasıl uygulanacağını `HypenatedConcat` işlev saf işlevi.</span><span class="sxs-lookup"><span data-stu-id="f03b2-128">This next version of the program hows how to implement the `HypenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="f03b2-129">Yeniden, bu sürümü aynı satır çıktı üretir: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="f03b2-129">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="f03b2-130">Birleştirilmiş değer korumak için onu Ara değişkeninde depolandığını unutmayın `s2`.</span><span class="sxs-lookup"><span data-stu-id="f03b2-130">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="f03b2-131">Çok kullanışlı olabilir bir yaklaşım ise yerel olarak Hanuka işlevlerinin (diğer bir deyişle, bunlar bildirme ve yerel değişkenleri değiştirin), ancak genel olarak saf.</span><span class="sxs-lookup"><span data-stu-id="f03b2-131">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="f03b2-132">Bu tür işlevler birçok arzu composability özelliklere sahip, ancak bazı basit bir döngüsü aynı şeyi başarmak zaman özyineleme kullanmak zorunda gibi daha karışık işlevsel programlama deyimleri, kaçının.</span><span class="sxs-lookup"><span data-stu-id="f03b2-132">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="f03b2-133">Standart sorgu işleçleri</span><span class="sxs-lookup"><span data-stu-id="f03b2-133">Standard Query Operators</span></span>  
 <span data-ttu-id="f03b2-134">Bir önemli standart sorgu işleçleri saf işlevleri olarak uygulanan özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="f03b2-134">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="f03b2-135">Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f03b2-135">For more information, see [Standard Query Operators Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f03b2-136">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f03b2-136">See Also</span></span>  
 [<span data-ttu-id="f03b2-137">Giriş saf işlevsel Dönüşümleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f03b2-137">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [<span data-ttu-id="f03b2-138">İşlevsel Programlama ve Kesinlik temelli programlama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f03b2-138">Functional Programming vs. Imperative Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
