---
title: "Saf işlevlerini (C#) yeniden düzenleme"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4fe9a9250e0a87ecaa02258526b7cc796de8e387
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2018
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="83fc7-102">Saf işlevlerini (C#) yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="83fc7-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="83fc7-103">Saf işlevsel Dönüşümlerin önemli bir durum kodu saf işlevler kullanılarak yeniden nasıl öğrenme.</span><span class="sxs-lookup"><span data-stu-id="83fc7-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83fc7-104">İşlevsel programlama içinde ortak terminolojisi saf işlevleri kullanarak programları yeniden Düzenle ' dir.</span><span class="sxs-lookup"><span data-stu-id="83fc7-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="83fc7-105">Visual Basic ve C++'de, bu işlevler ilgili dillerde kullanımı ile hizalar.</span><span class="sxs-lookup"><span data-stu-id="83fc7-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="83fc7-106">Ancak, C# ' ta işlevleri yöntemleri olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="83fc7-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="83fc7-107">Bu tartışma amaçları doğrultusunda, C# yöntemi olarak saf işlevi uygulanır.</span><span class="sxs-lookup"><span data-stu-id="83fc7-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="83fc7-108">Bu bölümde daha önce belirtildiği gibi saf işlevi iki yararlı özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="83fc7-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
-   <span data-ttu-id="83fc7-109">Hiçbir yan etkisi vardır.</span><span class="sxs-lookup"><span data-stu-id="83fc7-109">It has no side effects.</span></span> <span data-ttu-id="83fc7-110">İşlev hiçbir değişken veya işlev dışında herhangi bir türde verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="83fc7-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
-   <span data-ttu-id="83fc7-111">Tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="83fc7-111">It is consistent.</span></span> <span data-ttu-id="83fc7-112">Aynı dizi girdi verisi verildiğinde, her zaman aynı çıkış değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="83fc7-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="83fc7-113">İşlevsel programlama koddan bir gereksiz yan etkiler ve dış bağımlılıkları ortadan kaldırmak için var olan kodu yeniden düzenlemeniz için yoludur.</span><span class="sxs-lookup"><span data-stu-id="83fc7-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="83fc7-114">Bu şekilde, var olan kodu saf işlevi sürümlerini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83fc7-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="83fc7-115">Bu konuda ele alınmıştır saf işlevi ne olduğu ve ne değildir.</span><span class="sxs-lookup"><span data-stu-id="83fc7-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="83fc7-116">[Öğreticisi: WordprocessingML belgede (C#) içerik düzenleme](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğretici WordprocessingML belgeyi işlemek nasıl gösterir ve nasıl saf işlevi kullanarak düzenleme için iki örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="83fc7-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="83fc7-117">Yan etkiler ve dış bağımlılıkları ortadan</span><span class="sxs-lookup"><span data-stu-id="83fc7-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="83fc7-118">Aşağıdaki örnekler, iki saf olmayan işlevler ve saf işlevi karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="83fc7-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="83fc7-119">Sınıf üyesine değişiklikleri saf olmayan işlevi</span><span class="sxs-lookup"><span data-stu-id="83fc7-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="83fc7-120">Aşağıdaki kodda, `HyphenatedConcat` işlevi değil saf işlevi değiştirdiği çünkü `aMember` sınıfı veri üyesi:</span><span class="sxs-lookup"><span data-stu-id="83fc7-120">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
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
  
 <span data-ttu-id="83fc7-121">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="83fc7-121">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="83fc7-122">Değiştirilen verileri olup ilgisiz olup olmadığını Not `public` veya `private` erişim ya da bir `static` üyesi veya bir örnek üyesine.</span><span class="sxs-lookup"><span data-stu-id="83fc7-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="83fc7-123">Saf işlevi işlevi dışında herhangi bir veri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="83fc7-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="83fc7-124">Bağımsız değişken değişiklikleri saf olmayan işlevi</span><span class="sxs-lookup"><span data-stu-id="83fc7-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="83fc7-125">Kendi parametresinin içeriğini değiştirdiği Ayrıca, aynı bu işlevi aşağıdaki sürümü saf olmadığından `sb`.</span><span class="sxs-lookup"><span data-stu-id="83fc7-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
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
  
 <span data-ttu-id="83fc7-126">Çünkü programın bu sürümü aynı ilk sürüm olarak çıktı üretir `HyphenatedConcat` işlevini çağırarak, ilk parametresinin değeri (durum) değişti <xref:System.Text.StringBuilder.Append%2A> üye işlevi.</span><span class="sxs-lookup"><span data-stu-id="83fc7-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="83fc7-127">Bu değişiklikle rağmen bu olgu oluştuğunu unutmayın, `HyphenatedConcat` çağrısı değerli parametre geçirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="83fc7-127">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="83fc7-128">Bir parametre değeri tarafından geçirirseniz başvuru türleri için geçirilen bir nesneye başvuru kopyasını sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="83fc7-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="83fc7-129">(Yeni bir nesneye başvuru değişkeni atanıncaya kadar) Bu hala özgün başvuru olarak aynı örnek verilerle ilişkili bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="83fc7-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="83fc7-130">Çağrı tarafından başvuru mutlaka bir işlev parametre değiştirmek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="83fc7-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="83fc7-131">Saf işlevi</span><span class="sxs-lookup"><span data-stu-id="83fc7-131">Pure Function</span></span>  
<span data-ttu-id="83fc7-132">Bu program sonraki sürümü nasıl uygulandığını gösterir `HyphenatedConcat` işlev saf işlevi.</span><span class="sxs-lookup"><span data-stu-id="83fc7-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="83fc7-133">Yeniden, bu sürümü aynı satır çıktı üretir: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="83fc7-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="83fc7-134">Birleştirilmiş değer korumak için onu Ara değişkeninde depolandığını unutmayın `s2`.</span><span class="sxs-lookup"><span data-stu-id="83fc7-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="83fc7-135">Çok kullanışlı olabilir bir yaklaşım ise yerel olarak Hanuka işlevlerinin (diğer bir deyişle, bunlar bildirme ve yerel değişkenleri değiştirin), ancak genel olarak saf.</span><span class="sxs-lookup"><span data-stu-id="83fc7-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="83fc7-136">Bu tür işlevler birçok arzu composability özelliklere sahip, ancak bazı basit bir döngüsü aynı şeyi başarmak zaman özyineleme kullanmak zorunda gibi daha karışık işlevsel programlama deyimleri, kaçının.</span><span class="sxs-lookup"><span data-stu-id="83fc7-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="83fc7-137">Standart sorgu işleçleri</span><span class="sxs-lookup"><span data-stu-id="83fc7-137">Standard Query Operators</span></span>  
 <span data-ttu-id="83fc7-138">Bir önemli standart sorgu işleçleri saf işlevleri olarak uygulanan özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="83fc7-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="83fc7-139">Daha fazla bilgi için bkz: [standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="83fc7-139">For more information, see [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83fc7-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="83fc7-140">See Also</span></span>  
 [<span data-ttu-id="83fc7-141">Giriş saf işlevsel Dönüşümleri (C#)</span><span class="sxs-lookup"><span data-stu-id="83fc7-141">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [<span data-ttu-id="83fc7-142">İşlevsel Programlama ve Kesinlik temelli programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="83fc7-142">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
