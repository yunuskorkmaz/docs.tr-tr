---
title: Saf Fonksiyonlara Yeniden Düzenleme (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: 4cf91ff078bd1c4582daa05475a91c4a4ecaba3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253105"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="6c4ae-102">Saf Fonksiyonlara Yeniden Düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="6c4ae-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="6c4ae-103">Saf işlevsel dönüşümlerin önemli bir yönü, saf işlevleri kullanarak kodu nasıl yeniden düzenlemeyi öğrenmektir.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6c4ae-104">İşlevsel programlamada yaygın olarak kullanılan adlandırma, programları saf işlevleri kullanarak yeniden düzenlemenizdir.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="6c4ae-105">Visual Basic ve C++'da bu, ilgili dillerdeki işlevlerin kullanımıyla uyumludur.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="6c4ae-106">Ancak, C#'da işlevler yöntem olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="6c4ae-107">Bu tartışmanın amaçları için C#'da bir yöntem olarak saf bir işlev uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="6c4ae-108">Bu bölümde daha önce belirtildiği gibi, saf bir işlevin iki yararlı özelliği vardır:</span><span class="sxs-lookup"><span data-stu-id="6c4ae-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
- <span data-ttu-id="6c4ae-109">Hiçbir yan etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-109">It has no side effects.</span></span> <span data-ttu-id="6c4ae-110">İşlev, herhangi bir değişkeni veya işlev dışında herhangi bir türdeki verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
- <span data-ttu-id="6c4ae-111">Tutarlı.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-111">It is consistent.</span></span> <span data-ttu-id="6c4ae-112">Aynı giriş veri kümesi göz önüne alındığında, her zaman aynı çıktı değerini döndürecektir.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="6c4ae-113">İşlevsel programlamaya geçişin bir yolu, gereksiz yan etkileri ve dışa bağımlılıkları ortadan kaldırmak için varolan kodu yeniden duruma getirmektir.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="6c4ae-114">Bu şekilde, varolan kodun saf işlev sürümlerini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="6c4ae-115">Bu konu, saf bir işlevin ne olduğunu ve ne olmadığını tartışır.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="6c4ae-116">[Öğretici: WordprocessingML Belgesinde (C#) öğreticide İçeriği niçin değiştirilir,](./shape-of-wordprocessingml-documents.md) WordprocessingML belgesinin nasıl değiştirilebildiğini gösterir ve saf bir işlev kullanarak nasıl yeniden kusturun iki örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](./shape-of-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="6c4ae-117">Yan Etkileri ve Dış Bağımlılıkları Ortadan Kaldırma</span><span class="sxs-lookup"><span data-stu-id="6c4ae-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="6c4ae-118">Aşağıdaki örnekler, saf olmayan iki işlev ve saf bir işlevle tezat atretmektedir.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="6c4ae-119">Sınıf Üyesini Değiştiren Saf Olmayan İşlev</span><span class="sxs-lookup"><span data-stu-id="6c4ae-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="6c4ae-120">Aşağıdaki kodda, `HyphenatedConcat` işlev saf bir işlev değildir, çünkü `aMember` sınıftaki veri üyesini değiştirir:</span><span class="sxs-lookup"><span data-stu-id="6c4ae-120">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
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
  
 <span data-ttu-id="6c4ae-121">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="6c4ae-121">This code produces the following output:</span></span>  
  
```output  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="6c4ae-122">Değiştirilen verilerin sahip `public` olup olmadığının veya `private` erişip erişmediğinin veya üye `static` veya örnek üye olup olmadığının önemsiz olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="6c4ae-123">Saf bir işlev, işlev in dışındaki verileri değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="6c4ae-124">Bağımsız Değişkeni Değiştiren Saf Olmayan İşlev</span><span class="sxs-lookup"><span data-stu-id="6c4ae-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="6c4ae-125">Ayrıca, aynı işlevin aşağıdaki sürümü, parametresinin içeriğini değiştirir, çünkü saf `sb`değildir.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
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
  
 <span data-ttu-id="6c4ae-126">`HyphenatedConcat` Programın bu sürümü, <xref:System.Text.StringBuilder.Append%2A> üye işlevi çağırarak ilk parametresinin değerini (durumunu) değiştirdiğinden, ilk sürümle aynı çıktıyı üretir.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="6c4ae-127">Bu değişikliğin, çağrı değeri parametre geçişi nin kullanımı gerçeğine `HyphenatedConcat` rağmen oluştuğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-127">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6c4ae-128">Başvuru türleri için, bir parametreyi değere göre geçerseniz, geçirilen bir nesneye başvurunun bir kopyasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="6c4ae-129">Bu kopya hala özgün başvuruyla aynı örnek verilerle ilişkilidir (başvuru değişkeni yeni bir nesneye atanana kadar).</span><span class="sxs-lookup"><span data-stu-id="6c4ae-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="6c4ae-130">Bir işlevin bir parametreyi değiştirmesi için çağrı-by-reference mutlaka gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="6c4ae-131">Saf Fonksiyon</span><span class="sxs-lookup"><span data-stu-id="6c4ae-131">Pure Function</span></span>  
<span data-ttu-id="6c4ae-132">Programın bir sonraki sürümü, işlevin `HyphenatedConcat` saf bir işlev olarak nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="6c4ae-133">Yine, bu sürüm çıkış aynı `StringOne-StringTwo`satırı üretir: .</span><span class="sxs-lookup"><span data-stu-id="6c4ae-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="6c4ae-134">Concatenated değerini korumak için, ara değişkende `s2`depolanır unutmayın.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="6c4ae-135">Çok yararlı olabilecek bir yaklaşım, yerel olarak saf olmayan (diğer bir şekilde yerel değişkenleri beyan edip değiştirebilen) ancak genel olarak saf olan işlevleri yazmaktır.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="6c4ae-136">Bu tür işlevler arzu edilen kullanılabilirlik özelliklerinin çoğuna sahiptir, ancak basit bir döngü aynı şeyi gerçekleştireceği zaman özyineleme kullanmak zorunda kalmak gibi daha karmaşık işlevsel programlama deyimlerinden bazılarını önler.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="6c4ae-137">Standart Sorgu Operatörleri</span><span class="sxs-lookup"><span data-stu-id="6c4ae-137">Standard Query Operators</span></span>  
 <span data-ttu-id="6c4ae-138">Standart sorgu işleçlerinin önemli bir özelliği, bunların saf işlevler olarak uygulanmasıdır.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="6c4ae-139">Daha fazla bilgi için, [Bkz. Standart Sorgu Operatörleri Genel Bakış (C#)](./standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6c4ae-139">For more information, see [Standard Query Operators Overview (C#)](./standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c4ae-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c4ae-140">See also</span></span>

- [<span data-ttu-id="6c4ae-141">Saf İşlevsel Dönüşümlere Giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="6c4ae-141">Introduction to Pure Functional Transformations (C#)</span></span>](./introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="6c4ae-142">Fonksiyonel Programlama ve Zorunlu Programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="6c4ae-142">Functional Programming vs. Imperative Programming (C#)</span></span>](./functional-programming-vs-imperative-programming.md)
