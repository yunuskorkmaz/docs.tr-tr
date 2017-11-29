---
title: "if-else (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a0ecc915af00caffeba92a8308a60bc24198d477
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="if-else-c-reference"></a><span data-ttu-id="81bdd-102">if-else (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="81bdd-102">if-else (C# Reference)</span></span>
<span data-ttu-id="81bdd-103">Bir `if` deyimi tanımlayan çalıştırmak için hangi deyimi değeri temel alınarak bir `Boolean` ifade.</span><span class="sxs-lookup"><span data-stu-id="81bdd-103">An `if` statement identifies which statement to run based on the value of a `Boolean` expression.</span></span> <span data-ttu-id="81bdd-104">Aşağıdaki örnekte, `Boolean` değişkeni `result` ayarlanır `true` ve ardından iade `if` deyimi.</span><span class="sxs-lookup"><span data-stu-id="81bdd-104">In the following example, the `Boolean` variable `result` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="81bdd-105">Çıktı `The condition is true`.</span><span class="sxs-lookup"><span data-stu-id="81bdd-105">The output is `The condition is true`.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]  
  
 <span data-ttu-id="81bdd-106">Bunları yerleştirerek bu konudaki örnekler çalıştırabilirsiniz `Main` bir konsol uygulaması yöntemi.</span><span class="sxs-lookup"><span data-stu-id="81bdd-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>  
  
 <span data-ttu-id="81bdd-107">Bir `if` C# deyimi, aşağıdaki örnekte gösterildiği gibi iki form alabilir.</span><span class="sxs-lookup"><span data-stu-id="81bdd-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>  
  
```csharp  
// if-else statement  
if (condition)  
{  
    then-statement;  
}  
else  
{  
    else-statement;  
}  
// Next statement in the program.  
  
// if statement without an else  
if (condition)  
{  
    then-statement;  
}  
// Next statement in the program.  
```  
  
 <span data-ttu-id="81bdd-108">İçinde bir `if-else` deyimi, varsa `condition` doğru olarak değerlendirir `then-statement` çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="81bdd-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="81bdd-109">Varsa `condition` false, `else-statement` çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="81bdd-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="81bdd-110">Çünkü `condition` aynı anda true ve false olamaz `then-statement` ve `else-statement` , bir `if-else` deyimi hiçbir zaman hem de çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81bdd-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="81bdd-111">Sonra `then-statement` veya `else-statement` çalıştığında, Denetim sonra next deyimi için aktarılır `if` deyimi.</span><span class="sxs-lookup"><span data-stu-id="81bdd-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>  
  
 <span data-ttu-id="81bdd-112">İçinde bir `if` içermeyen deyimi bir `else` deyimi, varsa `condition` doğrudur `then-statement` çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="81bdd-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="81bdd-113">Varsa `condition` denetim sonra next deyimi için aktarılır yanlış `if` deyimi.</span><span class="sxs-lookup"><span data-stu-id="81bdd-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>  
  
 <span data-ttu-id="81bdd-114">Hem `then-statement` ve `else-statement` tek bir deyimde veya ayraç içine birden çok deyime oluşabilir (`{}`).</span><span class="sxs-lookup"><span data-stu-id="81bdd-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="81bdd-115">Tek bir deyimde için Küme ayraçları isteğe bağlıdır ancak önerilir.</span><span class="sxs-lookup"><span data-stu-id="81bdd-115">For a single statement, the braces are optional but recommended.</span></span>  
  
 <span data-ttu-id="81bdd-116">Deyimin veya deyimlerinde `then-statement` ve `else-statement` başka dahil olmak üzere her türlü olabilir `if` deyimi, özgün içinde iç içe geçmiş `if` deyimi.</span><span class="sxs-lookup"><span data-stu-id="81bdd-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="81bdd-117">İçinde iç içe geçmiş `if` deyimleri, her `else` yan tümcesi ait son `if` karşılık gelen yok `else`.</span><span class="sxs-lookup"><span data-stu-id="81bdd-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="81bdd-118">Aşağıdaki örnekte, `Result1` her iki görünür `m > 10` ve `n > 20` true olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="81bdd-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="81bdd-119">Varsa `m > 10` geçerlidir, ancak `n > 20` false, `Result2` görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="81bdd-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]  
  
 <span data-ttu-id="81bdd-120">Bunun yerine, isterseniz, `Result2` ne zaman görünmesi `(m > 10)` başlangıcı ve sonu iç içe oluşturmak için Küme ayraçları kullanarak bu ilişkiyi belirtebilirsiniz yanlış `if` deyimi, aşağıdaki örnekte gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="81bdd-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]  
  
 <span data-ttu-id="81bdd-121">`Result2`görünür koşul `(m > 10)` yanlış olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="81bdd-121">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81bdd-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="81bdd-122">Example</span></span>  
 <span data-ttu-id="81bdd-123">Aşağıdaki örnekte, klavyeden bir karakter girin ve programı bir iç içe kullanır `if` giriş karakter alfasayısal bir karakter olup olmadığını belirlemek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="81bdd-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="81bdd-124">Giriş karakter alfasayısal bir karakter ise, program giriş karakteri küçük harfler veya büyük olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="81bdd-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="81bdd-125">Her örneği için bir ileti görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="81bdd-125">A message appears for each case.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="81bdd-126">Örnek</span><span class="sxs-lookup"><span data-stu-id="81bdd-126">Example</span></span>  
 <span data-ttu-id="81bdd-127">Ayrıca geçirebilmenize bir `if` başka bir blok ifadeye aşağıdaki gösterildiği gibi kısmi kodu.</span><span class="sxs-lookup"><span data-stu-id="81bdd-127">You also can nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="81bdd-128">Örnek Yuvalar `if` ifadeleri iki başka blokları ve sonra bloğu içinde.</span><span class="sxs-lookup"><span data-stu-id="81bdd-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="81bdd-129">True veya false her bloğundaki hangi koşullar açıklamaları belirtin.</span><span class="sxs-lookup"><span data-stu-id="81bdd-129">The comments specify which conditions are true or false in each block.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="81bdd-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="81bdd-130">Example</span></span>  
 <span data-ttu-id="81bdd-131">Aşağıdaki örnek, bir giriş karakteri küçük harf, büyük harf veya sayı olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="81bdd-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="81bdd-132">Tüm üç koşul yanlış ise, karakter alfasayısal bir karakter değil.</span><span class="sxs-lookup"><span data-stu-id="81bdd-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="81bdd-133">Örneğin, her örneği için bir ileti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="81bdd-133">The example displays a message for each case.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]  
  
 <span data-ttu-id="81bdd-134">Herhangi bir geçerli ifadesi başka blok veya sonra blok deyiminde yalnızca olabildiği kadar koşul için geçerli bir Boolean ifadesini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="81bdd-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="81bdd-135">Mantıksal işleçler gibi kullanabilir [ && ](../../../csharp/language-reference/operators/conditional-and-operator.md), [ & ](../../../csharp/language-reference/operators/and-operator.md), [&#124; &#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) ve [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="81bdd-135">You can use logical operators such as [&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) and [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span></span> <span data-ttu-id="81bdd-136">Bileşik koşullar yapma.</span><span class="sxs-lookup"><span data-stu-id="81bdd-136">to make compound conditions.</span></span> <span data-ttu-id="81bdd-137">Aşağıdaki kod örnekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="81bdd-137">The following code shows examples.</span></span>  
  
```csharp  
// NOT  
bool result = true;  
if (!result)  
{  
    Console.WriteLine("The condition is true (result is false).");  
}  
else  
{  
    Console.WriteLine("The condition is false (result is true).");  
}  
  
// Short-circuit AND  
int m = 9;  
int n = 7;  
int p = 5;  
if (m >= n && m >= p)  
{  
    Console.WriteLine("Nothing is larger than m.");  
}  
  
// AND and NOT  
if (m >= n && !(p > m))  
{  
    Console.WriteLine("Nothing is larger than m.");  
}  
  
// Short-circuit OR  
if (m > n || m > p)  
{  
    Console.WriteLine("m isn't the smallest.");  
}  
  
// NOT and OR  
m = 4;  
if (!(m >= n || m >= p))  
{  
    Console.WriteLine("Now m is the smallest.");  
}  
// Output:  
// The condition is false (result is true).  
// Nothing is larger than m.  
// Nothing is larger than m.  
// m isn't the smallest.  
// Now m is the smallest.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="81bdd-138">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="81bdd-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="81bdd-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="81bdd-139">See Also</span></span>  
 [<span data-ttu-id="81bdd-140">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="81bdd-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="81bdd-141">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="81bdd-141">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="81bdd-142">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="81bdd-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="81bdd-143">?: İşleci</span><span class="sxs-lookup"><span data-stu-id="81bdd-143">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
 [<span data-ttu-id="81bdd-144">if-else deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="81bdd-144">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)  
 [<span data-ttu-id="81bdd-145">geçiş</span><span class="sxs-lookup"><span data-stu-id="81bdd-145">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)
