---
title: "Nasıl yapılır: foreach ile Koleksiyon Sınıfına Erişme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: collection classes [C#], foreach statement
ms.assetid: a6b9cf5c-6c8d-4223-b12c-288949434493
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0cf827e958d4dc3b951d17b53effd155356c0ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-collection-class-with-foreach-c-programming-guide"></a><span data-ttu-id="b9bdc-102">Nasıl yapılır: foreach ile Koleksiyon Sınıfına Erişme (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="b9bdc-102">How to: Access a Collection Class with foreach (C# Programming Guide)</span></span>
<span data-ttu-id="b9bdc-103">Aşağıdaki kod örneğinde nasıl ile kullanılan genel olmayan koleksiyon sınıfı yazılacağını gösterir [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="b9bdc-103">The following code example illustrates how to write a non-generic collection class that can be used with [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span></span> <span data-ttu-id="b9bdc-104">Örnek bir dizeyi simgeleştirici sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-104">The example defines a string tokenizer class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9bdc-105">Bu örnekte, yalnızca bir genel koleksiyon sınıfı kullanamadığında önerilen uygulama temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-105">This example represents recommended practice only when you cannot use a generic collection class.</span></span> <span data-ttu-id="b9bdc-106">Destekleyen bir genel tür kullanımı uyumlu koleksiyon sınıfın nasıl uygulanacağını ilişkin bir örnek <xref:System.Collections.Generic.IEnumerable%601>, bkz: [yineleyiciler](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="b9bdc-106">For an example of how to implement a type-safe generic collection class that supports <xref:System.Collections.Generic.IEnumerable%601>, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="b9bdc-107">Örnekte, aşağıdaki kod kesimi kullanır `Tokens` "Örnek cümle budur." cümlesi bölüneceği sınıfı</span><span class="sxs-lookup"><span data-stu-id="b9bdc-107">In the example, the following code segment uses the `Tokens` class to break the sentence "This is a sample sentence."</span></span> <span data-ttu-id="b9bdc-108">kullanarak belirteçler içine ' ' ve '-' ayırıcı olarak.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-108">into tokens by using ' ' and '-' as separators.</span></span> <span data-ttu-id="b9bdc-109">Kod daha sonra bu belirteçleri kullanarak görüntüler bir `foreach` deyimi.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-109">The code then displays those tokens by using a `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideCollections#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="b9bdc-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9bdc-110">Example</span></span>  
 <span data-ttu-id="b9bdc-111">Dahili olarak, `Tokens` sınıfı belirteçleri depolamak için bir dizi kullanır.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-111">Internally, the `Tokens` class uses an array to store the tokens.</span></span> <span data-ttu-id="b9bdc-112">Diziler uyguladığınız için <xref:System.Collections.IEnumerator> ve <xref:System.Collections.IEnumerable>, kod örneğinde dizinin numaralandırma yöntemlerini kullanabilirdik (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, ve <xref:System.Collections.IEnumerator.Current%2A>) bunları tanımlama yerine `Tokens` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-112">Because arrays implement <xref:System.Collections.IEnumerator> and <xref:System.Collections.IEnumerable>, the code example could have used the array's enumeration methods (<xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A>) instead of defining them in the `Tokens` class.</span></span> <span data-ttu-id="b9bdc-113">Yöntem tanımlarını nasıl tanımlanır ve ne açıklamak için örnekte bulunan her yapar.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-113">The method definitions are included in the example to clarify how they are defined and what each does.</span></span>  
  
 [!code-csharp[csProgGuideCollections#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-access-a-collection-class-with-foreach_2.cs)]  
  
 <span data-ttu-id="b9bdc-114">C# ' ta uygulamak koleksiyon sınıfı için ise gerekli değildir <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> ile uyumlu olacak şekilde `foreach`.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-114">In C#, it is not necessary for a collection class to implement <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> to be compatible with `foreach`.</span></span> <span data-ttu-id="b9bdc-115">Sınıfı gerekli olup olmadığını <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, ve <xref:System.Collections.IEnumerator.Current%2A> üyeleri, onu ile çalışır `foreach`.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-115">If the class has the required <xref:System.Collections.IEnumerable.GetEnumerator%2A>, <xref:System.Collections.IEnumerator.MoveNext%2A>, <xref:System.Collections.IEnumerator.Reset%2A>, and <xref:System.Collections.IEnumerator.Current%2A> members, it will work with `foreach`.</span></span> <span data-ttu-id="b9bdc-116">Arabirimler atlama sahip bir dönüş türü için tanımlamanızı etkinleştirme avantajı `Current` daha belirgin olan <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-116">Omitting the interfaces has the advantage of enabling you to define a return type for `Current` that is more specific than <xref:System.Object>.</span></span> <span data-ttu-id="b9bdc-117">Bu tür güvenliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-117">This provides type safety.</span></span>  
  
 <span data-ttu-id="b9bdc-118">Örneğin, önceki örnekte aşağıdaki satırları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-118">For example, change the following lines in the previous example.</span></span>  
  
```csharp  
// Change the Tokens class so that it no longer implements IEnumerable.  
public class Tokens  
{  
    // . . .  
  
    // Change the return type for the GetEnumerator method.  
    public TokenEnumerator GetEnumerator()  
    {   }  
  
    // Change TokenEnumerator so that it no longer implements IEnumerator.  
    public class TokenEnumerator  
    {  
        // . . .  
  
        // Change the return type of method Current to string.  
        public string Current  
        {   }  
    }  
 }  
```  
  
 <span data-ttu-id="b9bdc-119">Çünkü `Current` dizesi döndürür, derleyicinin türü uyumsuz kullanıldığında algılayabilir bir `foreach` aşağıdaki kodda gösterildiği gibi deyimi.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-119">Because `Current` returns a string, the compiler can detect when an incompatible type is used in a `foreach` statement, as shown in the following code.</span></span>  
  
```csharp  
// Error: Cannot convert type string to int.  
foreach (int item in f)    
```  
  
 <span data-ttu-id="b9bdc-120">Atlama dezavantajı <xref:System.Collections.IEnumerable> ve <xref:System.Collections.IEnumerator> koleksiyona sınıfında artık birlikte çalışabilir olmasıdır `foreach` deyimleri ya da diğer ortak dil çalışma zamanı dillerin eşdeğer deyimleri.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-120">The disadvantage of omitting <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> is that the collection class is no longer interoperable with the `foreach` statements, or equivalent statements, of other common language runtime languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9bdc-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b9bdc-121">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="b9bdc-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="b9bdc-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b9bdc-123">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b9bdc-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b9bdc-124">Diziler</span><span class="sxs-lookup"><span data-stu-id="b9bdc-124">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="b9bdc-125">Koleksiyonları</span><span class="sxs-lookup"><span data-stu-id="b9bdc-125">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)
