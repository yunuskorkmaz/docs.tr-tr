---
title: Operators - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 60e7f7c25b525c6db856731bd16c1c0e60efe6d6
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422931"
---
# <a name="operators-c-programming-guide"></a><span data-ttu-id="58701-102">İşleçler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="58701-102">Operators (C# Programming Guide)</span></span>

<span data-ttu-id="58701-103">C# ' ta, bir *işleci* uygulanan bir program öğesi için bir veya daha fazla olan *işlenenler* bir deyim veya ifade.</span><span class="sxs-lookup"><span data-stu-id="58701-103">In C#, an *operator* is a program element that is applied to one or more *operands* in an expression or statement.</span></span> <span data-ttu-id="58701-104">Artırım işleci gibi tek bir işlenen alan işleçler (`++`) veya `new`, denir *birli* işleçleri.</span><span class="sxs-lookup"><span data-stu-id="58701-104">Operators that take one operand, such as the increment operator (`++`) or `new`, are referred to as *unary* operators.</span></span> <span data-ttu-id="58701-105">Aritmetik işleçleri gibi iki işlene alan işleçler (`+`,`-`,`*`,`/`), denir *ikili* işleçleri.</span><span class="sxs-lookup"><span data-stu-id="58701-105">Operators that take two operands, such as arithmetic operators (`+`,`-`,`*`,`/`), are referred to as *binary* operators.</span></span> <span data-ttu-id="58701-106">Bir işleç, koşullu işleç (`?:`) üç işlenen alır ve C# ' deki tek Üçlü işleç.</span><span class="sxs-lookup"><span data-stu-id="58701-106">One operator, the conditional operator (`?:`), takes three operands and is the sole ternary operator in C#.</span></span>  
  
 <span data-ttu-id="58701-107">Aşağıdaki C# deyimi tek bir birli işleç ve tek bir işlenen içerir.</span><span class="sxs-lookup"><span data-stu-id="58701-107">The following C# statement contains a single unary operator and a single operand.</span></span> <span data-ttu-id="58701-108">Artırım işleci `++`, işleneninin değerini değiştirir `y`.</span><span class="sxs-lookup"><span data-stu-id="58701-108">The increment operator, `++`, modifies the value of the operand `y`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 <span data-ttu-id="58701-109">Aşağıdaki C# deyimi, her biri iki işlenenli iki ikili işleç alır.</span><span class="sxs-lookup"><span data-stu-id="58701-109">The following C# statement contains two binary operators, each with two operands.</span></span> <span data-ttu-id="58701-110">Atama işleci `=`, tamsayı değişkeni sahip `y` ve ifade `2 + 3` işlenen olarak.</span><span class="sxs-lookup"><span data-stu-id="58701-110">The assignment operator, `=`, has the integer variable `y` and the expression `2 + 3` as operands.</span></span> <span data-ttu-id="58701-111">İfade `2 + 3` kendisi, toplama işleci ve iki işlenenden oluşur `2` ve `3`.</span><span class="sxs-lookup"><span data-stu-id="58701-111">The expression `2 + 3` itself consists of the addition operator and two operands, `2` and `3`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
<span data-ttu-id="58701-112">Bir işlenen, herhangi bir uzunlukta koddan oluşan geçerli bir ifade olabilir ve herhangi bir sayıda alt ifade içerebilir.</span><span class="sxs-lookup"><span data-stu-id="58701-112">An operand can be a valid expression that is composed of any length of code, and it can comprise any number of sub expressions.</span></span> <span data-ttu-id="58701-113">Birden çok işleç içeren bir ifadede, işleçlerin uygulanma sırası tarafından belirlenir *İşleç önceliği*, *ilişkilendirilebilirliği*ve parantezler.</span><span class="sxs-lookup"><span data-stu-id="58701-113">In an expression that contains multiple operators, the order in which the operators are applied is determined by *operator precedence*, *associativity*, and parentheses.</span></span>  

## <a name="operator-precedence"></a><span data-ttu-id="58701-114">İşleç önceliği</span><span class="sxs-lookup"><span data-stu-id="58701-114">Operator precedence</span></span>
  
<span data-ttu-id="58701-115">Her işleç tanımlanmış bir önceliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="58701-115">Each operator has a defined precedence.</span></span> <span data-ttu-id="58701-116">Farklı öncelik düzeyleri olan birden çok işleç içeren bir ifadede, işleçlerin önceliği, işleçlerin değerlendirilme sırasını belirler.</span><span class="sxs-lookup"><span data-stu-id="58701-116">In an expression that contains multiple operators that have different precedence levels, the precedence of the operators determines the order in which the operators are evaluated.</span></span> <span data-ttu-id="58701-117">Örneğin, aşağıdaki deyim 3 atar `n1`:</span><span class="sxs-lookup"><span data-stu-id="58701-117">For example, the following statement assigns 3 to `n1`:</span></span>

```csharp
n1 = 11 - 2 * 4;
```

<span data-ttu-id="58701-118">Çarpma çıkarmaya göre öncelikli olduğundan, önce çarpma yürütülür.</span><span class="sxs-lookup"><span data-stu-id="58701-118">The multiplication is executed first because multiplication takes precedence over subtraction.</span></span>

<span data-ttu-id="58701-119">Tam listesi için C# işleçler, öncelik düzeyine göre sıralanmış bkz [ C# işleçleri](../../language-reference/operators/index.md).</span><span class="sxs-lookup"><span data-stu-id="58701-119">For the complete list of C# operators ordered by precedence level, see [C# operators](../../language-reference/operators/index.md).</span></span>
  
## <a name="associativity"></a><span data-ttu-id="58701-120">İlişkilendirilebilirlik</span><span class="sxs-lookup"><span data-stu-id="58701-120">Associativity</span></span>

 <span data-ttu-id="58701-121">Aynı önceliğe sahip iki veya daha fazla işleç bir ifadede yer aldığında, ilişkilendirilebilirliğe dayalı olarak değerlendirilirler.</span><span class="sxs-lookup"><span data-stu-id="58701-121">When two or more operators that have the same precedence are present in an expression, they are evaluated based on associativity.</span></span> <span data-ttu-id="58701-122">Solla ilişkilendirilebilir işleçler, soldan sağa doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="58701-122">Left-associative operators are evaluated in order from left to right.</span></span> <span data-ttu-id="58701-123">Örneğin, `x * y / z` değerlendirmesinde `(x * y) / z`.</span><span class="sxs-lookup"><span data-stu-id="58701-123">For example, `x * y / z` is evaluated as `(x * y) / z`.</span></span> <span data-ttu-id="58701-124">Sağla ilişkilendirilebilir işleçler, sağdan sola doğru değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="58701-124">Right-associative operators are evaluated in order from right to left.</span></span> <span data-ttu-id="58701-125">Örneğin, atama işleci sağla ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="58701-125">For example, the assignment operator is right associative.</span></span> <span data-ttu-id="58701-126">Öyle olmasaydı, aşağıdaki kod bir hataya neden olurdu.</span><span class="sxs-lookup"><span data-stu-id="58701-126">If it were not, the following code would result in an error.</span></span>  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 <span data-ttu-id="58701-127">Başka bir örnek Üçlü işleç ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) sağla ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="58701-127">As another example the ternary operator ([?:](../../../csharp/language-reference/operators/conditional-operator.md)) is right associative.</span></span> <span data-ttu-id="58701-128">Çoğu ikili işleçler solla ilişkilendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="58701-128">Most binary operators are left associative.</span></span>  
  
 <span data-ttu-id="58701-129">Bir ifadedeki işleçler ister solla isterse sağla ilişkilendirilebilir olsun, her bir ifadenin işlenenleri ilk olarak, soldan sağa doğru ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="58701-129">Whether the operators in an expression are left associative or right associative, the operands of each expression are evaluated first, from left to right.</span></span> <span data-ttu-id="58701-130">Aşağıdaki örnekler, işleçlerin ve işlenenleri değerlendirilme sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="58701-130">The following examples illustrate the order of evaluation of operators and operands.</span></span>  
  
|<span data-ttu-id="58701-131">Deyim</span><span class="sxs-lookup"><span data-stu-id="58701-131">Statement</span></span>|<span data-ttu-id="58701-132">Değerlendirme sırası</span><span class="sxs-lookup"><span data-stu-id="58701-132">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = b`|<span data-ttu-id="58701-133">a, b, =</span><span class="sxs-lookup"><span data-stu-id="58701-133">a, b, =</span></span>|  
|`a = b + c`|<span data-ttu-id="58701-134">a, b, c, +, =</span><span class="sxs-lookup"><span data-stu-id="58701-134">a, b, c, +, =</span></span>|  
|`a = b + c * d`|<span data-ttu-id="58701-135">a, b, c, d, \*, +, =</span><span class="sxs-lookup"><span data-stu-id="58701-135">a, b, c, d, \*, +, =</span></span>|  
|`a = b * c + d`|<span data-ttu-id="58701-136">a, b, c, \*, d, +, =</span><span class="sxs-lookup"><span data-stu-id="58701-136">a, b, c, \*, d, +, =</span></span>|  
|`a = b - c + d`|<span data-ttu-id="58701-137">a, b, c, -, d, +, =</span><span class="sxs-lookup"><span data-stu-id="58701-137">a, b, c, -, d, +, =</span></span>|  
|`a += b -= c`|<span data-ttu-id="58701-138">a, b, c, -=, +=</span><span class="sxs-lookup"><span data-stu-id="58701-138">a, b, c, -=, +=</span></span>|  
  
## <a name="adding-parentheses"></a><span data-ttu-id="58701-139">Ayraç ekleme</span><span class="sxs-lookup"><span data-stu-id="58701-139">Adding parentheses</span></span>

 <span data-ttu-id="58701-140">Parantezler kullanarak işleç önceliği ve ilişkilendirilebilirlik tarafından dayatılan sırayı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58701-140">You can change the order imposed by operator precedence and associativity by using parentheses.</span></span> <span data-ttu-id="58701-141">Örneğin, `2 + 3 * 2` çarpma işleçleri toplama işleçlerine göre öncelikli olduğundan, normalde 8 olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="58701-141">For example, `2 + 3 * 2` ordinarily evaluates to 8, because multiplicative operators take precedence over additive operators.</span></span> <span data-ttu-id="58701-142">Ancak, bir ifade olarak yazarsanız `(2 + 3) * 2`eklenmesi çarpımdan önce değerlendirilir ve sonucu 10'dur.</span><span class="sxs-lookup"><span data-stu-id="58701-142">However, if you write the expression as `(2 + 3) * 2`, the addition is evaluated before the multiplication, and the result is 10.</span></span> <span data-ttu-id="58701-143">Aşağıdaki örnekler, parantezli ifadelerdeki değerlendirme sırasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="58701-143">The following examples illustrate the order of evaluation in parenthesized expressions.</span></span> <span data-ttu-id="58701-144">Önceki örneklerde olduğu gibi, işlenenler işleç uygulanmadan önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="58701-144">As in previous examples, the operands are evaluated before the operator is applied.</span></span>  
  
|<span data-ttu-id="58701-145">Deyim</span><span class="sxs-lookup"><span data-stu-id="58701-145">Statement</span></span>|<span data-ttu-id="58701-146">Değerlendirme sırası</span><span class="sxs-lookup"><span data-stu-id="58701-146">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = (b + c) * d`|<span data-ttu-id="58701-147">a, b, c, +, d, \*, =</span><span class="sxs-lookup"><span data-stu-id="58701-147">a, b, c, +, d, \*, =</span></span>|  
|`a = b - (c + d)`|<span data-ttu-id="58701-148">a, b, c, d, +, -, =</span><span class="sxs-lookup"><span data-stu-id="58701-148">a, b, c, d, +, -, =</span></span>|  
|`a = (b + c) * (d - e)`|<span data-ttu-id="58701-149">a, b, c, +, d, e, -, \*, =</span><span class="sxs-lookup"><span data-stu-id="58701-149">a, b, c, +, d, e, -, \*, =</span></span>|  
  
## <a name="operator-overloading"></a><span data-ttu-id="58701-150">İşleç aşırı yüklemesi</span><span class="sxs-lookup"><span data-stu-id="58701-150">Operator overloading</span></span>

<span data-ttu-id="58701-151">Özel sınıflar ve yapılar için belirli işleçlerin davranışını tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="58701-151">You can define the behavior of certain operators for custom classes and structs.</span></span> <span data-ttu-id="58701-152">Bu işlem olarak adlandırılır *İşleç aşırı yüklemesi*.</span><span class="sxs-lookup"><span data-stu-id="58701-152">This process is referred to as *operator overloading*.</span></span> <span data-ttu-id="58701-153">Daha fazla bilgi için [fazla yüklenebilir işleçler](overloadable-operators.md) ve [işleci](../../language-reference/keywords/operator.md) anahtar sözcüğü makalesi.</span><span class="sxs-lookup"><span data-stu-id="58701-153">For more information, see [Overloadable operators](overloadable-operators.md) and the [operator](../../language-reference/keywords/operator.md) keyword article.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="58701-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="58701-154">See also</span></span>

- [<span data-ttu-id="58701-155">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="58701-155">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="58701-156">Deyimler, İfadeler ve İşleçler</span><span class="sxs-lookup"><span data-stu-id="58701-156">Statements, Expressions, and Operators</span></span>](index.md)
- [<span data-ttu-id="58701-157">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="58701-157">C# Operators</span></span>](../../language-reference/operators/index.md)
