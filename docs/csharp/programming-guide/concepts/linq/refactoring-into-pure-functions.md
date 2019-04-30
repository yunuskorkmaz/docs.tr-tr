---
title: Saf işlevler halinde (C#) yeniden düzenleme
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 3e856c1e32d4b0dc16291e1b913e9a5cc19717c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680447"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="6f4a7-102">Saf işlevler halinde (C#) yeniden düzenleme</span><span class="sxs-lookup"><span data-stu-id="6f4a7-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="6f4a7-103">Saf işlevsel dönüşümlere önemli bir yönüdür saf işlevler kullanarak kodunuzu yeniden değiştirmenin nasıl öğrenmeye devam ettiği.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f4a7-104">Saf işlevler kullanan programlar yeniden düzenleyin, işlevsel programlama, ortak terminoloji olur.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="6f4a7-105">Visual Basic ve C++ dillerinde, kendi dillerde işlevleri kullanarak bu hizalar.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="6f4a7-106">Ancak, C# dilinde işlevler yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="6f4a7-107">Bu tartışma amacı doğrultusunda, saf işlev C# dilinde bir yöntem olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="6f4a7-108">Bu bölümde daha önce belirtildiği gibi saf işlev iki yararlı özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="6f4a7-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
- <span data-ttu-id="6f4a7-109">Bu, yan etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-109">It has no side effects.</span></span> <span data-ttu-id="6f4a7-110">İşlevi, tüm değişkenler veya işlev dışında herhangi bir türde verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
- <span data-ttu-id="6f4a7-111">Tutarlı olur.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-111">It is consistent.</span></span> <span data-ttu-id="6f4a7-112">Aynı giriş veri kümesi düşünüldüğünde, bu her zaman aynı çıkış değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="6f4a7-113">Yollarından fonksiyonel programlama için geçiş, gereksiz yan etkileri ve dış bağımlılıkları ortadan kaldırmak için mevcut kodu yeniden düzenleyin sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="6f4a7-114">Bu şekilde, varolan kod sürümlerini saf işlev oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="6f4a7-115">Bu konuda ele alınmıştır saf işlev ne olduğunu ve ne değildir.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="6f4a7-116">[Öğreticisi: WordprocessingML belgesindeki içeriği düzenleme (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) öğretici WordprocessingML belgesinin işlemek nasıl gösterir ve nasıl saf işlev kullanarak yeniden düzenleme için iki örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="6f4a7-117">Yan etkiler ve dış bağımlılıkları ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="6f4a7-118">Aşağıdaki örnekler, iki saf olmayan işlevler ve saf işlev karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="6f4a7-119">Sınıf üyesi değişiklikleri saf olmayan işlevi</span><span class="sxs-lookup"><span data-stu-id="6f4a7-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="6f4a7-120">Aşağıdaki kodda, `HyphenatedConcat` işlevi değil, saf işlev değiştirdiği çünkü `aMember` sınıftaki veri üyesi:</span><span class="sxs-lookup"><span data-stu-id="6f4a7-120">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
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
  
 <span data-ttu-id="6f4a7-121">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6f4a7-121">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="6f4a7-122">Bu verilerin değiştirilmesi olup ilgisiz olduğuna dikkat edin `public` veya `private` erişim ya da bir `static` veya bir örnek üyesi.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="6f4a7-123">Saf işlev, işlev dışındaki tüm verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="6f4a7-124">Bağımsız değişken değişiklikleri saf olmayan işlevi</span><span class="sxs-lookup"><span data-stu-id="6f4a7-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="6f4a7-125">Kendi parametre içeriğini değiştirir ayrıca, aynı işlevi aşağıdaki sürümü saf olmadığından `sb`.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
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
  
 <span data-ttu-id="6f4a7-126">Çünkü programın bu sürümünü aynı ilk sürümde çıktı üretir `HyphenatedConcat` işlevi, birinci parametresinin değerini (durum) çağırarak değişti <xref:System.Text.StringBuilder.Append%2A> üye işlevi.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="6f4a7-127">Bu değişikliği rağmen bu durumu kendi lehine oluştuğunu unutmayın, `HyphenatedConcat` çağrı değerli parametre geçirme kullanır.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-127">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6f4a7-128">Değere göre bir parametre geçirirseniz başvuru türleri için geçirilen bir nesneye başvuru bir kopyasını sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="6f4a7-129">(Yeni bir nesneye başvuru değişkenini atanıncaya kadar) Bu hala özgün başvuru aynı örnek verileri ile ilişkili bir kopyasıdır.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="6f4a7-130">Başvuru ile çağrı parametreyi değiştirmek bir işlev için mutlaka gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="6f4a7-131">Saf işlev</span><span class="sxs-lookup"><span data-stu-id="6f4a7-131">Pure Function</span></span>  
<span data-ttu-id="6f4a7-132">Bu program'ın sonraki sürümü nasıl uygulayacağınızı gösteren `HyphenatedConcat` işlevi saf işlev.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="6f4a7-133">Bu sürümü çıktı satırını yeniden üretir: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="6f4a7-134">Birleştirilmiş değer korumak için bu Ara değişkende depolandığını unutmayın `s2`.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="6f4a7-135">Yerel olarak Hanuka işlevleri yazmak için kullanışlı bir yaklaşım olan (diğer bir deyişle, bunlar bildirme ve yerel değişkenleri değiştirin), ancak genel olarak saf.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="6f4a7-136">Bu tür işlevleri birçok arzu composability özelliklere sahip, ancak bazı basit döngüyü aynı şeyi yaptığınız zaman, özyineleme kullanmak zorunda gibi daha karışık işlevsel programlama deyimlerini, kaçının.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="6f4a7-137">Standart sorgu işleçleri</span><span class="sxs-lookup"><span data-stu-id="6f4a7-137">Standard Query Operators</span></span>  
 <span data-ttu-id="6f4a7-138">Standart sorgu işleçlerinin önemli bir özelliği, saf işlevler uygulanan ' dir.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="6f4a7-139">Daha fazla bilgi için [standart sorgu işleçlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6f4a7-139">For more information, see [Standard Query Operators Overview (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f4a7-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f4a7-140">See also</span></span>

- [<span data-ttu-id="6f4a7-141">Giriş saf işlevsel dönüşümlere (C#)</span><span class="sxs-lookup"><span data-stu-id="6f4a7-141">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="6f4a7-142">İşlevsel Programlama ve Kesin programlama karşılaştırması (C#)</span><span class="sxs-lookup"><span data-stu-id="6f4a7-142">Functional Programming vs. Imperative Programming (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)
