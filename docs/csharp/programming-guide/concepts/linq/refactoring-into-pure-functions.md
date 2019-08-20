---
title: Saf IŞLEVLERE yeniden düzenleme (C#)
ms.date: 07/20/2015
ms.assetid: 2944a0d4-fd33-4e2e-badd-abb0f9be2fcc
ms.openlocfilehash: d6e8657da0f7db06d2fdbe1231bdc48e1aa0f954
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591343"
---
# <a name="refactoring-into-pure-functions-c"></a><span data-ttu-id="63db7-102">Saf IŞLEVLERE yeniden düzenleme (C#)</span><span class="sxs-lookup"><span data-stu-id="63db7-102">Refactoring Into Pure Functions (C#)</span></span>

<span data-ttu-id="63db7-103">Saf işlevsel dönüştürmelerin önemli bir yönü, saf işlevleri kullanarak kodu yeniden düzenleme hakkında bilgi ediniyor.</span><span class="sxs-lookup"><span data-stu-id="63db7-103">An important aspect of pure functional transformations is learning how to refactor code using pure functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63db7-104">İşlevsel programlamada ortak terminoloji, programları saf işlevleri kullanarak yeniden düzenleme biçimleridir.</span><span class="sxs-lookup"><span data-stu-id="63db7-104">The common nomenclature in functional programming is that you refactor programs using pure functions.</span></span> <span data-ttu-id="63db7-105">Visual Basic ve C++' de, bu, ilgili dillerdeki işlevlerin kullanımıyla hizalanır.</span><span class="sxs-lookup"><span data-stu-id="63db7-105">In Visual Basic and C++, this aligns with the use of functions in the respective languages.</span></span> <span data-ttu-id="63db7-106">Ancak, içindeki C#işlevleri yöntemler olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="63db7-106">However, in C#, functions are called methods.</span></span> <span data-ttu-id="63db7-107">Bu tartışmanın amaçları doğrultusunda, saf bir işlev ' de C#bir yöntem olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="63db7-107">For the purposes of this discussion, a pure function is implemented as a method in C#.</span></span>  
  
 <span data-ttu-id="63db7-108">Daha önce bu bölümde belirtildiği gibi, saf bir işlev iki yararlı özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="63db7-108">As noted previously in this section, a pure function has two useful characteristics:</span></span>  
  
- <span data-ttu-id="63db7-109">Yan etkileri yoktur.</span><span class="sxs-lookup"><span data-stu-id="63db7-109">It has no side effects.</span></span> <span data-ttu-id="63db7-110">İşlev herhangi bir değişken veya işlev dışındaki herhangi bir türdeki veriyi değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="63db7-110">The function does not change any variables or the data of any type outside of the function.</span></span>  
  
- <span data-ttu-id="63db7-111">Tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="63db7-111">It is consistent.</span></span> <span data-ttu-id="63db7-112">Aynı giriş verisi kümesi verildiğinde, her zaman aynı çıkış değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="63db7-112">Given the same set of input data, it will always return the same output value.</span></span>  
  
 <span data-ttu-id="63db7-113">İşlevsel programlamaya geçiş yapmanın bir yolu, gereksiz yan etkileri ve dış bağımlılıkları ortadan kaldırmak için mevcut kodu yeniden düzenleme yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="63db7-113">One way of transitioning to functional programming is to refactor existing code to eliminate unnecessary side effects and external dependencies.</span></span> <span data-ttu-id="63db7-114">Bu şekilde, var olan kodun saf işlev sürümlerini oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63db7-114">In this way, you can create pure function versions of existing code.</span></span>  
  
 <span data-ttu-id="63db7-115">Bu konuda, saf bir işlevin ne olduğu ve ne olmadığı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="63db7-115">This topic discusses what a pure function is and what it is not.</span></span> <span data-ttu-id="63db7-116">[Öğretici: WordprocessingML belgesi (C#)](./shape-of-wordprocessingml-documents.md) öğreticisindeki içeriği işlemek bir WordprocessingML belgesinin nasıl düzenleneceğini gösterir ve saf bir işlev kullanarak yeniden düzenleme ile iki örnek içerir.</span><span class="sxs-lookup"><span data-stu-id="63db7-116">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](./shape-of-wordprocessingml-documents.md) tutorial shows how to manipulate a WordprocessingML document, and includes two examples of how to refactor using a pure function.</span></span>  
  
## <a name="eliminating-side-effects-and-external-dependencies"></a><span data-ttu-id="63db7-117">Yan etkileri ve dış bağımlılıkları ortadan kaldırma</span><span class="sxs-lookup"><span data-stu-id="63db7-117">Eliminating Side Effects and External Dependencies</span></span>  
 <span data-ttu-id="63db7-118">Aşağıdaki örneklerde, saf olmayan iki işlev ve bir saf işlev kontrast vardır.</span><span class="sxs-lookup"><span data-stu-id="63db7-118">The following examples contrast two non-pure functions and a pure function.</span></span>  
  
### <a name="non-pure-function-that-changes-a-class-member"></a><span data-ttu-id="63db7-119">Bir sınıf üyesini değiştiren saf olmayan Işlev</span><span class="sxs-lookup"><span data-stu-id="63db7-119">Non-Pure Function that Changes a Class Member</span></span>  
 <span data-ttu-id="63db7-120">Aşağıdaki kodda, `HyphenatedConcat` işlev saf bir işlev değildir, çünkü sınıfındaki `aMember` veri üyesini değiştirir:</span><span class="sxs-lookup"><span data-stu-id="63db7-120">In the following code, the `HyphenatedConcat` function is not a pure function, because it modifies the `aMember` data member in the class:</span></span>  
  
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
  
 <span data-ttu-id="63db7-121">Bu kod aşağıdaki çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="63db7-121">This code produces the following output:</span></span>  
  
```  
StringOne-StringTwo  
```  
  
 <span data-ttu-id="63db7-122">Değiştirilen `public` `static` verilerin veya bir üye ya da bir örnek üyesi olup olmadığı konusunda ilgisiz olduğunu unutmayın. `private`</span><span class="sxs-lookup"><span data-stu-id="63db7-122">Note that it is irrelevant whether the data being modified has `public` or `private` access, or is a `static` member or an instance member.</span></span> <span data-ttu-id="63db7-123">Saf bir işlev, işlevin dışındaki herhangi bir veriyi değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="63db7-123">A pure function does not change any data outside of the function.</span></span>  
  
### <a name="non-pure-function-that-changes-an-argument"></a><span data-ttu-id="63db7-124">Bir bağımsız değişkeni değiştiren saf olmayan Işlev</span><span class="sxs-lookup"><span data-stu-id="63db7-124">Non-Pure Function that Changes an Argument</span></span>  
 <span data-ttu-id="63db7-125">Ayrıca, parametresinin `sb`içeriğini değiştirdiği için aynı işlevin aşağıdaki sürümü saf değildir.</span><span class="sxs-lookup"><span data-stu-id="63db7-125">Furthermore, the following version of this same function is not pure because it modifies the contents of its parameter, `sb`.</span></span>  
  
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
  
 <span data-ttu-id="63db7-126">Programın bu sürümü ilk sürümle aynı çıktıyı üretir, çünkü `HyphenatedConcat` işlev <xref:System.Text.StringBuilder.Append%2A> üye işlevini çağırarak ilk parametresinin değerini (durum) değiştirdi.</span><span class="sxs-lookup"><span data-stu-id="63db7-126">This version of the program produces the same output as the first version, because the `HyphenatedConcat` function has changed the value (state) of its first parameter by invoking the <xref:System.Text.StringBuilder.Append%2A> member function.</span></span> <span data-ttu-id="63db7-127">Bu değişiklik, bu olguyu, çağrı- `HyphenatedConcat` değer parametresini kullanan bir olgusuna rağmen oluştuğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="63db7-127">Note that this alteration occurs despite that fact that `HyphenatedConcat` uses call-by-value parameter passing.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="63db7-128">Başvuru türleri için bir parametreyi değere göre geçirirseniz, başvurunun geçirildiği bir nesnenin kopyasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="63db7-128">For reference types, if you pass a parameter by value, it results in a copy of the reference to an object being passed.</span></span> <span data-ttu-id="63db7-129">Bu kopya, özgün başvurusuyla aynı örnek verileriyle ilişkili olmaya devam eder (başvuru değişkeni yeni bir nesneye atanana kadar).</span><span class="sxs-lookup"><span data-stu-id="63db7-129">This copy is still associated with the same instance data as the original reference (until the reference variable is assigned to a new object).</span></span> <span data-ttu-id="63db7-130">Bir parametreyi değiştirmek için bir işlev için başvuruya göre arama gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="63db7-130">Call-by-reference is not necessarily required for a function to modify a parameter.</span></span>  
  
### <a name="pure-function"></a><span data-ttu-id="63db7-131">Saf Işlev</span><span class="sxs-lookup"><span data-stu-id="63db7-131">Pure Function</span></span>  
<span data-ttu-id="63db7-132">Programın bu sonraki sürümü, `HyphenatedConcat` işlevinin saf işlev olarak nasıl uygulanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="63db7-132">This next version of the program shows how to implement the `HyphenatedConcat` function as a pure function.</span></span>  
  
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
  
 <span data-ttu-id="63db7-133">Yine, bu sürüm aynı çıkış satırını üretir: `StringOne-StringTwo`.</span><span class="sxs-lookup"><span data-stu-id="63db7-133">Again, this version produces the same line of output: `StringOne-StringTwo`.</span></span> <span data-ttu-id="63db7-134">Birleştirilmiş değeri bekletmek için, ara değişkende `s2`depolandığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="63db7-134">Note that to retain the concatenated value, it is stored in the intermediate variable `s2`.</span></span>  
  
 <span data-ttu-id="63db7-135">Çok yararlı olabilecek bir yaklaşım, yerel olarak etkileyici olan işlevleri yazmak (yani yerel değişkenleri bildirdikleri ve değiştirdiklerinde), ancak Global olarak saf bir yaklaşımdır.</span><span class="sxs-lookup"><span data-stu-id="63db7-135">One approach that can be very useful is to write functions that are locally impure (that is, they declare and modify local variables) but are globally pure.</span></span> <span data-ttu-id="63db7-136">Bu gibi işlevler, istenen ek özelliklerin çoğuna sahiptir, ancak basit bir döngü aynı şeyi gerçekleştirirken özyineleme kullanmak zorunda kalmadan, daha fazla çalışan işlevsel programlama deyimidir.</span><span class="sxs-lookup"><span data-stu-id="63db7-136">Such functions have many of the desirable composability characteristics, but avoid some of the more convoluted functional programming idioms, such as having to use recursion when a simple loop would accomplish the same thing.</span></span>  
  
## <a name="standard-query-operators"></a><span data-ttu-id="63db7-137">Standart sorgu Işleçleri</span><span class="sxs-lookup"><span data-stu-id="63db7-137">Standard Query Operators</span></span>  
 <span data-ttu-id="63db7-138">Standart sorgu işleçlerinin önemli bir özelliği, saf işlevler olarak uygulanırlar.</span><span class="sxs-lookup"><span data-stu-id="63db7-138">An important characteristic of the standard query operators is that they are implemented as pure functions.</span></span>  
  
 <span data-ttu-id="63db7-139">Daha fazla bilgi için bkz. [Standart sorgu IşleçlerineC#genel bakış ()](./standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="63db7-139">For more information, see [Standard Query Operators Overview (C#)](./standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63db7-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="63db7-140">See also</span></span>

- [<span data-ttu-id="63db7-141">Saf Işlevsel Dönüştürmelere giriş (C#)</span><span class="sxs-lookup"><span data-stu-id="63db7-141">Introduction to Pure Functional Transformations (C#)</span></span>](./introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="63db7-142">İşlevsel Programlama ve Kesinlik temelli programlamaC#()</span><span class="sxs-lookup"><span data-stu-id="63db7-142">Functional Programming vs. Imperative Programming (C#)</span></span>](./functional-programming-vs-imperative-programming.md)
