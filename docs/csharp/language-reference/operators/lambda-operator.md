---
title: =&gt; Operator - C# başvurusu
ms.custom: seodec18
ms.date: 10/02/2017
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 8641757d9252c88cf30595cec06d27b964e4d95c
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415292"
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="3735b-102">=&gt; İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3735b-102">=&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="3735b-103">`=>` İşleci, C# dilinde iki şekilde kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="3735b-103">The `=>` operator can be used in two ways in C#:</span></span>

- <span data-ttu-id="3735b-104">Olarak [lambda işleci](#lambda-operator) içinde bir [lambda ifadesi](../../lambda-expressions.md), lambda gövdesinden girdi değişkenleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="3735b-104">As the [lambda operator](#lambda-operator) in a [lambda expression](../../lambda-expressions.md), it separates the input variables from the lambda body.</span></span>
 
- <span data-ttu-id="3735b-105">İçinde bir [ifade gövdesi tanımına](#expression-body-definition), üye uygulamasından bir üye adı ayıran.</span><span class="sxs-lookup"><span data-stu-id="3735b-105">In an [expression body definition](#expression-body-definition), it separates a member name from the member implementation.</span></span> 

## <a name="lambda-operator"></a><span data-ttu-id="3735b-106">Lambda işleci</span><span class="sxs-lookup"><span data-stu-id="3735b-106">Lambda operator</span></span>

<span data-ttu-id="3735b-107">`=>` Belirteci lambda işlecini çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3735b-107">The `=>` token is called the lambda operator.</span></span> <span data-ttu-id="3735b-108">İçinde kullanılan *lambda ifadeleri* işlecin sağ tarafındaki lambda gövdesinden sol tarafında giriş değişkenleri ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="3735b-108">It is used in *lambda expressions* to separate the input variables on the left side from the lambda body on the right side.</span></span> <span data-ttu-id="3735b-109">Lambda ifadeleri, satır içi ifadeler anonim yöntemler daha esnek ancak benzer olan; yöntem sözdizimi ifade LINQ sorgularında yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3735b-109">Lambda expressions are inline expressions similar to anonymous methods but more flexible; they are used extensively in LINQ queries that are expressed in method syntax.</span></span> <span data-ttu-id="3735b-110">Daha fazla bilgi için [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3735b-110">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="3735b-111">Aşağıdaki örnek, bulmak ve dizelerden oluşan bir dizi kısa dize uzunluğunu görüntülemek için iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3735b-111">The following example shows two ways to find and display the length of the shortest string in an array of strings.</span></span> <span data-ttu-id="3735b-112">Bir lambda ifadesi örneği ilk bölümünü uygular (`w => w.Length`) her öğesine `words` dizisi ve kullandığı <xref:System.Linq.Enumerable.Min%2A> en küçük uzunluğunu bulmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3735b-112">The first part of the example applies a lambda expression (`w => w.Length`) to each element of the `words` array and then uses the <xref:System.Linq.Enumerable.Min%2A> method to find the smallest length.</span></span> <span data-ttu-id="3735b-113">Karşılaştırma için ikinci bölümü örneğin aynı şeyi yapmak için sorgu söz dizimi kullanan daha uzun bir çözüm gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3735b-113">For comparison, the second part of the example shows a longer solution that uses query syntax to do the same thing.</span></span>  
  
```csharp  
string[] words = { "cherry", "apple", "blueberry" };  
  
// Use method syntax to apply a lambda expression to each element  
// of the words array.   
int shortestWordLength = words.Min(w => w.Length);  
Console.WriteLine(shortestWordLength);  
  
// Compare the following code that uses query syntax.  
// Get the lengths of each word in the words array.  
var query = from w in words  
            select w.Length;  
// Apply the Min method to execute the query and get the shortest length.  
int shortestWordLength2 = query.Min();  
Console.WriteLine(shortestWordLength2);  
  
// Output:   
// 5  
// 5  
```  
  
### <a name="remarks"></a><span data-ttu-id="3735b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3735b-114">Remarks</span></span>  
 <span data-ttu-id="3735b-115">`=>` İşleci atama işleci aynı önceliğe sahiptir (`=`) ve sağa ilişkilendirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3735b-115">The `=>` operator has the same precedence as the assignment operator (`=`) and is right-associative.</span></span>  
  
 <span data-ttu-id="3735b-116">Giriş değişkeninin türünü açıkça belirtmeniz veya, derleyicinin sağlar; Her iki durumda da, değişken derleme zamanında kesin olarak.</span><span class="sxs-lookup"><span data-stu-id="3735b-116">You can specify the type of the input variable explicitly or let the compiler infer it; in either case, the variable is strongly typed at compile time.</span></span> <span data-ttu-id="3735b-117">Bir türü belirttiğinizde, parantez içinde tür adı ve değişken adı aşağıdaki örnekte gösterildiği gibi almalısınız.</span><span class="sxs-lookup"><span data-stu-id="3735b-117">When you specify a type, you must enclose the type name and the variable name in parentheses, as the following example shows.</span></span>  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a><span data-ttu-id="3735b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="3735b-118">Example</span></span>  
 <span data-ttu-id="3735b-119">Aşağıdaki örnek, standart sorgu işleci aşırı yüklemesi için bir lambda ifadesinin nasıl yazılacağını gösterir <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> , iki bağımsız değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="3735b-119">The following example shows how to write a lambda expression for the overload of the standard query operator <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> that takes two arguments.</span></span> <span data-ttu-id="3735b-120">Lambda ifadesi birden fazla parametre olduğundan, parametreleri, parantez içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3735b-120">Because the lambda expression has more than one parameter, the parameters must be enclosed in parentheses.</span></span> <span data-ttu-id="3735b-121">İkinci parametre `index`, koleksiyondaki geçerli öğenin dizinini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="3735b-121">The second parameter, `index`, represents the index of the current element in the collection.</span></span> <span data-ttu-id="3735b-122">`Where` İfade, uzunlukları Dizin konumlarını dizideki değerinden küçük olan tüm dizeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3735b-122">The `Where` expression returns all the strings whose lengths are less than their index positions in the array.</span></span>  
  
```csharp  
static void Main(string[] args)  
{  
    string[] digits = { "zero", "one", "two", "three", "four", "five",   
            "six", "seven", "eight", "nine" };  
  
    Console.WriteLine("Example that uses a lambda expression:");  
    var shortDigits = digits.Where((digit, index) => digit.Length < index);  
    foreach (var sD in shortDigits)  
    {  
        Console.WriteLine(sD);  
    }  
  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
## <a name="expression-body-definition"></a><span data-ttu-id="3735b-123">İfade gövdesi tanımı</span><span class="sxs-lookup"><span data-stu-id="3735b-123">Expression body definition</span></span>

<span data-ttu-id="3735b-124">Bir ifade gövdesi tanımına, yüksek oranda sıkıştırılmış, okunabilir formda bir üyenin uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3735b-124">An expression body definition provides a member's implementation in a highly condensed, readable form.</span></span> <span data-ttu-id="3735b-125">Bu genel sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="3735b-125">It has the following general syntax:</span></span>

```csharp
member => expression;
```
<span data-ttu-id="3735b-126">Burada *ifade* geçerli bir ifadedir.</span><span class="sxs-lookup"><span data-stu-id="3735b-126">where *expression* is a valid expression.</span></span> <span data-ttu-id="3735b-127">Unutmayın *ifade* olabilir bir *deyim ifadesi* üyenin dönüş türü ise yalnızca `void`, veya üye bir oluşturucu ya da bir sonlandırıcı ise.</span><span class="sxs-lookup"><span data-stu-id="3735b-127">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor or a finalizer.</span></span>

<span data-ttu-id="3735b-128">Yöntem ve özellik get deyimleri için ifade gövdesi tanımları, C# 6 ile başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3735b-128">Expression body definitions for methods and property get statements are supported starting with C# 6.</span></span> <span data-ttu-id="3735b-129">Sonlandırıcılar, Oluşturucular için ifade gövdesi tanımları deyimleri özelliğini ayarlayın ve dizin oluşturucular, C# 7 ile başlayan desteklenir.</span><span class="sxs-lookup"><span data-stu-id="3735b-129">Expression body definitions for constructors, finalizers, property set statements, and indexers are supported starting with C# 7.</span></span>

<span data-ttu-id="3735b-130">Bir ifade gövdesi tanımı verilmiştir bir `Person.ToString` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="3735b-130">The following is an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="3735b-131">Aşağıdaki yöntem tanımının bir toplu sürümdür:</span><span class="sxs-lookup"><span data-stu-id="3735b-131">It is a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
<span data-ttu-id="3735b-132">İfade gövdesi tanımları hakkında daha ayrıntılı bilgi için bkz: [ifade gövdeli üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="3735b-132">For more detailed information on expression body definitions, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3735b-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3735b-133">See Also</span></span>

- [<span data-ttu-id="3735b-134">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3735b-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)   
- [<span data-ttu-id="3735b-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3735b-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)   
- [<span data-ttu-id="3735b-136">Lambda İfadeleri</span><span class="sxs-lookup"><span data-stu-id="3735b-136">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
- <span data-ttu-id="3735b-137">[İfade gövdeli üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="3735b-137">[Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>
