---
title: =&gt;İşleci (C# Başvurusu)
ms.date: 10/02/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44cb0485aefa8b0ab10a00ae0525180020ce436d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="gt-operator-c-reference"></a><span data-ttu-id="7ffda-102">=&gt;İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7ffda-102">=&gt; Operator (C# Reference)</span></span>

<span data-ttu-id="7ffda-103">`=>` İşleci, C# iki yolla kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="7ffda-103">The `=>` operator can be used in two ways in C#:</span></span>

- <span data-ttu-id="7ffda-104">Olarak [lambda işleci](#lamba-operator) içinde bir [lambda ifadesi](../../lambda-expressions.md), girdi değişkenleri lambda gövdesinden ayırır.</span><span class="sxs-lookup"><span data-stu-id="7ffda-104">As the [lambda operator](#lamba-operator) in a [lambda expression](../../lambda-expressions.md), it separates the input variables from the lambda body.</span></span>
 
- <span data-ttu-id="7ffda-105">İçinde bir [ifade gövdesi tanımı](#expression-body-definition), üye uygulamasından bir üye adı ayırır.</span><span class="sxs-lookup"><span data-stu-id="7ffda-105">In an [expression body definition](#expression-body-definition), it separates a member name from the member implementation.</span></span> 

## <a name="lambda-operator"></a><span data-ttu-id="7ffda-106">Lambda işleci</span><span class="sxs-lookup"><span data-stu-id="7ffda-106">Lambda operator</span></span>

<span data-ttu-id="7ffda-107">`=>` Belirteci lambda işleci çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7ffda-107">The `=>` token is called the lambda operator.</span></span> <span data-ttu-id="7ffda-108">İçinde kullanılan *lambda ifadeleri* girdi değişkenleri sol taraftaki sağ tarafında lambda gövde ayırmak için.</span><span class="sxs-lookup"><span data-stu-id="7ffda-108">It is used in *lambda expressions* to separate the input variables on the left side from the lambda body on the right side.</span></span> <span data-ttu-id="7ffda-109">Lambda ifadeleri satır içi ifadeler daha esnek ancak anonim yöntemler benzer; yine de uygun istiyor musunuz? yöntem sözdiziminde ifade LINQ sorgularında yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ffda-109">Lambda expressions are inline expressions similar to anonymous methods but more flexible; they are used extensively in LINQ queries that are expressed in method syntax.</span></span> <span data-ttu-id="7ffda-110">Daha fazla bilgi için bkz: [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="7ffda-110">For more information, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="7ffda-111">Aşağıdaki örnek bulmak ve bir dizeler dizisi kısa dize uzunluğu görüntülemek için iki yolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="7ffda-111">The following example shows two ways to find and display the length of the shortest string in an array of strings.</span></span> <span data-ttu-id="7ffda-112">Lambda ifadesi örnek ilk bölümünü uygular (`w => w.Length`) her öğesine `words` dizi ve kullandığı <xref:System.Linq.Enumerable.Min%2A> en küçük uzunluk bulmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="7ffda-112">The first part of the example applies a lambda expression (`w => w.Length`) to each element of the `words` array and then uses the <xref:System.Linq.Enumerable.Min%2A> method to find the smallest length.</span></span> <span data-ttu-id="7ffda-113">Karşılaştırma için ikinci bölümü örneğin aynı şeyi yapmak için sorgu sözdizimini kullanır daha uzun bir çözüm gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7ffda-113">For comparison, the second part of the example shows a longer solution that uses query syntax to do the same thing.</span></span>  
  
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
  
### <a name="remarks"></a><span data-ttu-id="7ffda-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ffda-114">Remarks</span></span>  
 <span data-ttu-id="7ffda-115">`=>` Atama işleci olarak aynı önceliğe sahip (`=`) ve sağa ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7ffda-115">The `=>` operator has the same precedence as the assignment operator (`=`) and is right-associative.</span></span>  
  
 <span data-ttu-id="7ffda-116">Giriş değişkeninin türü açıkça belirtin veya bunu Infer derleyici sağlar; Her iki durumda da değişkeni kesinlikle derleme zamanında tür belirtilmiş.</span><span class="sxs-lookup"><span data-stu-id="7ffda-116">You can specify the type of the input variable explicitly or let the compiler infer it; in either case, the variable is strongly typed at compile time.</span></span> <span data-ttu-id="7ffda-117">Bir türü belirttiğinizde, parantez içine tür adı ve değişken adı aşağıdaki örnekte gösterildiği gibi almalısınız.</span><span class="sxs-lookup"><span data-stu-id="7ffda-117">When you specify a type, you must enclose the type name and the variable name in parentheses, as the following example shows.</span></span>  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a><span data-ttu-id="7ffda-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ffda-118">Example</span></span>  
 <span data-ttu-id="7ffda-119">Aşağıdaki örnekte bir lambda ifadesi standart sorgu işleci aşırı için yazma gösterilmektedir <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> iki bağımsız değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="7ffda-119">The following example shows how to write a lambda expression for the overload of the standard query operator <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> that takes two arguments.</span></span> <span data-ttu-id="7ffda-120">Lambda ifadesi birden fazla parametre içerdiğinden parametreleri parantez içine alınmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7ffda-120">Because the lambda expression has more than one parameter, the parameters must be enclosed in parentheses.</span></span> <span data-ttu-id="7ffda-121">İkinci parametre `index`, koleksiyondaki geçerli öğenin dizinini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7ffda-121">The second parameter, `index`, represents the index of the current element in the collection.</span></span> <span data-ttu-id="7ffda-122">`Where` İfade olan uzunlukta olan dizin konumlarına dizideki değerinden tüm dizeleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="7ffda-122">The `Where` expression returns all the strings whose lengths are less than their index positions in the array.</span></span>  
  
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
## <a name="expression-body-definition"></a><span data-ttu-id="7ffda-123">İfade gövdesi tanımı</span><span class="sxs-lookup"><span data-stu-id="7ffda-123">Expression body definition</span></span>

<span data-ttu-id="7ffda-124">Bir ifade gövdesi tanımı yüksek oranda sıkıştırılmış, okunabilir bir biçimde bir üyenin uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7ffda-124">An expression body definition provides a member's implementation in a highly condensed, readable form.</span></span> <span data-ttu-id="7ffda-125">Genel sözdizimi aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7ffda-125">It has the following general syntax:</span></span>

```csharp
member => expression;
```
<span data-ttu-id="7ffda-126">Burada *ifade* geçerli bir ifade değil.</span><span class="sxs-lookup"><span data-stu-id="7ffda-126">where *expression* is a valid expression.</span></span> <span data-ttu-id="7ffda-127">Unutmayın *ifade* olabilir bir *deyimi ifade* üyenin dönüş türü ise yalnızca `void`, veya bir oluşturucu veya bir sonlandırıcı üyesiyse.</span><span class="sxs-lookup"><span data-stu-id="7ffda-127">Note that *expression* can be a *statement expression* only if the member's return type is `void`, or if the member is a constructor or a finalizer.</span></span>

<span data-ttu-id="7ffda-128">İfade gövdesi tanımları yöntem ve özellik get deyimleri için C# 6 ile başlayarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7ffda-128">Expression body definitions for methods and property get statements are supported starting with C# 6.</span></span> <span data-ttu-id="7ffda-129">Dizin oluşturucular C# 7 ile başlayan desteklenir ve ifade gövdesi Oluşturucular, sonlandırıcılar, tanımlarında deyimleri özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ffda-129">Expression body definitions for constructors, finalizers, property set statements, and indexers are supported starting with C# 7.</span></span>

<span data-ttu-id="7ffda-130">İçin bir ifade gövdesi tanımı aşağıda verilmiştir bir `Person.ToString` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="7ffda-130">The following is an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="7ffda-131">Aşağıdaki yöntem tanımını kestirme sürümü şöyledir:</span><span class="sxs-lookup"><span data-stu-id="7ffda-131">It is a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
<span data-ttu-id="7ffda-132">İfade gövdesi tanımları hakkında daha ayrıntılı bilgi için bkz: [ifade bodied üyeleri](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="7ffda-132">For more detailed information on expression body definitions, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ffda-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ffda-133">See Also</span></span>  
<span data-ttu-id="7ffda-134">[C# başvurusu](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="7ffda-134">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="7ffda-135">[C# programlama kılavuzu](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="7ffda-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="7ffda-136">[Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="7ffda-136">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
<span data-ttu-id="7ffda-137">[İfade bodied üyeleri](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="7ffda-137">[Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>