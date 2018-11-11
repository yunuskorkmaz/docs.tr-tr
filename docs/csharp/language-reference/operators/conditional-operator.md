---
title: '?: İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 3e45ff6eaaefa5829c3ed9415abe1a12b7a1d069
ms.sourcegitcommit: 4bca8f7e172fd019ef437a4803bf5895c6bc4781
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2018
ms.locfileid: "50980628"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e95d5-102">?: İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e95d5-102">?: Operator (C# Reference)</span></span>

<span data-ttu-id="e95d5-103">Koşullu işleç (`?:`), yaygın olarak bilinen bir Üçlü koşullu işleç, bir Boolean ifadesinin değerine bağlı olarak iki değerden birini döndürür.</span><span class="sxs-lookup"><span data-stu-id="e95d5-103">The conditional operator (`?:`), commonly known as the ternary conditional operator, returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="e95d5-104">Aşağıda, koşullu işlecin sözdizimi belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e95d5-104">Following is the syntax for the conditional operator.</span></span>  

```csharp
condition ? first_expression : second_expression;  
```

<span data-ttu-id="e95d5-105">İle başlayarak C# 7.2, `first_expression` ve `second_expression` my olması [ `ref` ifadeleri](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):</span><span class="sxs-lookup"><span data-stu-id="e95d5-105">Beginning with C# 7.2, the `first_expression` and `second_expression` my be [`ref` expressions](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.2/conditional-ref.md):</span></span>

```csharp
ref condition ? ref first_expression : ref second_expression;  
```

<span data-ttu-id="e95d5-106">Sonuç atanabilir bir `ref` veya `ref readonly` değişkenine veya bir değişkene hiçbiri değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="e95d5-106">The result may be assigned to a `ref` or `ref readonly` variable, or to a variable with neither modifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="e95d5-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e95d5-107">Remarks</span></span>

<span data-ttu-id="e95d5-108">`condition` Değerlendirilmelidir `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="e95d5-108">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="e95d5-109">Varsa `condition` olduğu `true`, `first_expression` değerlendirilir ve sonuç olur.</span><span class="sxs-lookup"><span data-stu-id="e95d5-109">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="e95d5-110">Varsa `condition` olduğu `false`, `second_expression` değerlendirilir ve sonuç olur.</span><span class="sxs-lookup"><span data-stu-id="e95d5-110">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="e95d5-111">İki ifadeden yalnızca biri değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e95d5-111">Only one of the two expressions is evaluated.</span></span> <span data-ttu-id="e95d5-112">Bu sonucu olduğu ifadeler için özellikle önemlidir bir `ref`, aşağıdaki geçerli olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="e95d5-112">This is particularly important for expressions where the result is a `ref`, as the following is valid:</span></span>

```csharp
ref (storage != null) ? ref storage[3] : ref defaultValue;
```

<span data-ttu-id="e95d5-113">Başvuru `storage` olduğunda değerlendirilmez `storage` null.</span><span class="sxs-lookup"><span data-stu-id="e95d5-113">The reference to `storage` is not evaluated when `storage` is null.</span></span>

<span data-ttu-id="e95d5-114">Bir değer türü olduğunda sonucu `first_expression` ve `second_expression` aynı veya orada bir türden diğerine örtülü bir dönüştürme diğerine olmalıdır olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e95d5-114">When the result is a value, the type of `first_expression` and `second_expression` must be the same, or there must be an implicit conversion from one type to the other.</span></span> <span data-ttu-id="e95d5-115">Sonuç olduğunda bir `ref`, türü `first_expression` ve `second_expression` aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e95d5-115">When the result is a `ref`, the type of `first_expression` and `second_expression` must be the same.</span></span>

<span data-ttu-id="e95d5-116">Aksi takdirde gerektirebilecek hesaplamaları ifade edebilirsiniz bir `if-else` koşullu işleç kullanarak daha kısaca oluşturma.</span><span class="sxs-lookup"><span data-stu-id="e95d5-116">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="e95d5-117">Örneğin, aşağıdaki kod önce kullanan bir `if` deyimi ve sonra bir tamsayı artı veya eksi olarak sınıflandırmak için koşullu bir işleç.</span><span class="sxs-lookup"><span data-stu-id="e95d5-117">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>

```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```

<span data-ttu-id="e95d5-118">Koşullu işleç, sağa ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="e95d5-118">The conditional operator is right-associative.</span></span> <span data-ttu-id="e95d5-119">İfade `a ? b : c ? d : e` değerlendirmesinde `a ? b : (c ? d : e)`, olarak değil `(a ? b : c) ? d : e`.</span><span class="sxs-lookup"><span data-stu-id="e95d5-119">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
<span data-ttu-id="e95d5-120">Koşullu işleç aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="e95d5-120">The conditional operator cannot be overloaded.</span></span>
  
## <a name="example"></a><span data-ttu-id="e95d5-121">Örnek</span><span class="sxs-lookup"><span data-stu-id="e95d5-121">Example</span></span>

<span data-ttu-id="e95d5-122">Aşağıdaki örnek, koşullu işlecin sonucu olan bir değer gösterir:</span><span class="sxs-lookup"><span data-stu-id="e95d5-122">The following example shows the conditional operator whose result is a value:</span></span>

[!code-csharp[csRefOperators?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalValue)]

<span data-ttu-id="e95d5-123">Aşağıdaki alternatif koşullu işlecin sonucu başvuru olduğu gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e95d5-123">The following alternative shows the conditional operator where the result is a reference:</span></span>

[!code-csharp[csRefOperatorsRef?:](~/samples/snippets/csharp/language-reference/operators/ConditionalExamples.cs#ConditionalRef)]

## <a name="see-also"></a><span data-ttu-id="e95d5-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e95d5-124">See Also</span></span>

- [<span data-ttu-id="e95d5-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e95d5-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="e95d5-126">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e95d5-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e95d5-127">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="e95d5-127">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="e95d5-128">if-else</span><span class="sxs-lookup"><span data-stu-id="e95d5-128">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
- <span data-ttu-id="e95d5-129">[?. and ?[] İşleçleri](../../../csharp/language-reference/operators/null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="e95d5-129">[?. and ?[] Operators](../../../csharp/language-reference/operators/null-conditional-operators.md)</span></span>  
- [<span data-ttu-id="e95d5-130">?? İşleç</span><span class="sxs-lookup"><span data-stu-id="e95d5-130">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)
