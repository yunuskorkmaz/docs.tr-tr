---
title: for (C# Başvurusu)
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: beac7727c8ce83d8ea20f0fc578f80ceef3053e7
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208420"
---
# <a name="for-c-reference"></a><span data-ttu-id="f7775-102">(için C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f7775-102">for (C# reference)</span></span>

<span data-ttu-id="f7775-103">`for` Deyimi, bir deyim veya ifadeleri bir blok için belirtilen bir Boole ifadesini değerlendirir sırada yürütür `true`.</span><span class="sxs-lookup"><span data-stu-id="f7775-103">The `for` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="f7775-104">Bir oranda noktası içinde `for` deyimi bloğu, bölün dışında döngü kullanarak [sonu](break.md) deyimi ya da kullanarak adım döngüsünde sonraki yinelemeye [devam](continue.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="f7775-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="f7775-105">Ayrıca çıkabilirsiniz bir `for` tarafından döngü [goto](goto.md), [dönmek](return.md), veya [throw](throw.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="f7775-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>
  
## <a name="structure-of-the-for-statement"></a><span data-ttu-id="f7775-106">Yapısını `for` deyimi</span><span class="sxs-lookup"><span data-stu-id="f7775-106">Structure of the `for` statement</span></span>

<span data-ttu-id="f7775-107">`for` Deyimi tanımlar *Başlatıcı*, *koşulu*, ve *yineleyici* bölümler:</span><span class="sxs-lookup"><span data-stu-id="f7775-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>
  
```csharp
for (initializer; condition; iterator)  
    body  
```

<span data-ttu-id="f7775-108">Tüm üç bölüm isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f7775-108">All three sections are optional.</span></span> <span data-ttu-id="f7775-109">Bir deyim veya deyimleri bloğu döngü gövdesidir.</span><span class="sxs-lookup"><span data-stu-id="f7775-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="f7775-110">Aşağıdaki örnekte gösterildiği `for` tüm tanımlı bölümler deyimiyle:</span><span class="sxs-lookup"><span data-stu-id="f7775-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="f7775-111">*Başlatıcı* bölümü</span><span class="sxs-lookup"><span data-stu-id="f7775-111">The *initializer* section</span></span>

<span data-ttu-id="f7775-112">İfadeler *Başlatıcı* bölüm yürütülme yalnızca bir kez döngü girmeden önce.</span><span class="sxs-lookup"><span data-stu-id="f7775-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="f7775-113">*Başlatıcı* bölümünde aşağıdakilerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="f7775-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="f7775-114">Bildirim ve başlatma gelen döngü dışında erişilemez bir yerel döngü değişkenin.</span><span class="sxs-lookup"><span data-stu-id="f7775-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="f7775-115">Sıfır veya daha fazla deyimi ifadeleri virgülle ayırarak aşağıdaki listeden:</span><span class="sxs-lookup"><span data-stu-id="f7775-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="f7775-116">[atama](../operators/assignment-operator.md) deyimi</span><span class="sxs-lookup"><span data-stu-id="f7775-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="f7775-117">bir yöntemi çağrıldı</span><span class="sxs-lookup"><span data-stu-id="f7775-117">invocation of a method</span></span>  

  - <span data-ttu-id="f7775-118">önek veya sonek [artırma](../operators/increment-operator.md) ifadesi gibi `++i` veya `i++`</span><span class="sxs-lookup"><span data-stu-id="f7775-118">prefix or postfix [increment](../operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  

  - <span data-ttu-id="f7775-119">önek veya sonek [azaltma](../operators/decrement-operator.md) ifadesi gibi `--i` veya `i--`</span><span class="sxs-lookup"><span data-stu-id="f7775-119">prefix or postfix [decrement](../operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  

  - <span data-ttu-id="f7775-120">kullanarak bir nesne oluşturulmasını [yeni](new-operator.md) anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="f7775-120">creation of an object by using [new](new-operator.md) keyword</span></span>

  - <span data-ttu-id="f7775-121">[await](await.md) ifadesi</span><span class="sxs-lookup"><span data-stu-id="f7775-121">[await](await.md) expression</span></span>

<span data-ttu-id="f7775-122">*Başlatıcı* yukarıdaki örnekte bölümünde bildirir ve yerel döngü değişkenini `i`:</span><span class="sxs-lookup"><span data-stu-id="f7775-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="f7775-123">*Koşulu* bölümü</span><span class="sxs-lookup"><span data-stu-id="f7775-123">The *condition* section</span></span>

<span data-ttu-id="f7775-124">*Koşulu* bölümünde, varsa, olmalıdır Boole ifadesi.</span><span class="sxs-lookup"><span data-stu-id="f7775-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="f7775-125">İfade, her döngü tekrarında önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f7775-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="f7775-126">Varsa *koşulu* bölüm mevcut değil ya da Boole ifadesi değerlendiren `true`sonraki döngü tekrarında yürütülen; Aksi takdirde, döngü çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="f7775-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="f7775-127">*Koşulu* yukarıdaki örnekte bölümünde döngü yerel döngü değişkeni değere göre kesilip kesilmediğini belirler:</span><span class="sxs-lookup"><span data-stu-id="f7775-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="f7775-128">*Yineleyici* bölümü</span><span class="sxs-lookup"><span data-stu-id="f7775-128">The *iterator* section</span></span>

<span data-ttu-id="f7775-129">*Yineleyici* bölümü tanımlar ne döngüden gövdesinin her yinelemeden sonra olur.</span><span class="sxs-lookup"><span data-stu-id="f7775-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="f7775-130">*Yineleyici* bölüm, sıfır veya daha fazla virgülle ayırarak aşağıdaki deyimi ifadeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="f7775-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>  

- <span data-ttu-id="f7775-131">[atama](../operators/assignment-operator.md) deyimi</span><span class="sxs-lookup"><span data-stu-id="f7775-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="f7775-132">bir yöntemi çağrıldı</span><span class="sxs-lookup"><span data-stu-id="f7775-132">invocation of a method</span></span>  

- <span data-ttu-id="f7775-133">önek veya sonek [artırma](../operators/increment-operator.md) ifadesi gibi `++i` veya `i++`</span><span class="sxs-lookup"><span data-stu-id="f7775-133">prefix or postfix [increment](../operators/increment-operator.md) expression, such as `++i` or `i++`</span></span>  

- <span data-ttu-id="f7775-134">önek veya sonek [azaltma](../operators/decrement-operator.md) ifadesi gibi `--i` veya `i--`</span><span class="sxs-lookup"><span data-stu-id="f7775-134">prefix or postfix [decrement](../operators/decrement-operator.md) expression, such as `--i` or `i--`</span></span>  

- <span data-ttu-id="f7775-135">kullanarak bir nesne oluşturulmasını [yeni](new-operator.md) anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="f7775-135">creation of an object by using [new](new-operator.md) keyword</span></span>

- <span data-ttu-id="f7775-136">[await](await.md) ifadesi</span><span class="sxs-lookup"><span data-stu-id="f7775-136">[await](await.md) expression</span></span>

<span data-ttu-id="f7775-137">*Yineleyici* yukarıdaki örnekte bölümünde artırır yerel döngü değişkeni:</span><span class="sxs-lookup"><span data-stu-id="f7775-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="f7775-138">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f7775-138">Examples</span></span>

<span data-ttu-id="f7775-139">Aşağıdaki örnek birçok yaygın kullanımları daha az gösterilmektedir `for` deyimi bölümleri: bir dış döngü değişken için bir değer atama *Başlatıcı* bölümünde, hem de bir yöntem çağırma  *Başlatıcı* ve *yineleyici* bölümler ve iki değişken değerlerini değiştirme *yineleyici* bölümü.</span><span class="sxs-lookup"><span data-stu-id="f7775-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="f7775-140">Seçin **çalıştırmak** örnek kodu çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="f7775-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="f7775-141">Bundan sonra kodu değiştirin ve yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f7775-141">After that you can modify the code and run it again.</span></span>
  
[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]
  
<span data-ttu-id="f7775-142">Aşağıdaki örnek, sonsuz tanımlar `for` döngü:</span><span class="sxs-lookup"><span data-stu-id="f7775-142">The following example defines the infinite `for` loop:</span></span>
  
[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]
  
## <a name="c-language-specification"></a><span data-ttu-id="f7775-143">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f7775-143">C# language specification</span></span>  

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
  
## <a name="see-also"></a><span data-ttu-id="f7775-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7775-144">See also</span></span>

[<span data-ttu-id="f7775-145">Deyimi (C# dil belirtimi) için</span><span class="sxs-lookup"><span data-stu-id="f7775-145">The for statement (C# language specification)</span></span>](/dotnet/csharp/language-reference/language-specification/statements#the-for-statement)  
[<span data-ttu-id="f7775-146">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f7775-146">C# Reference</span></span>](../index.md)  
[<span data-ttu-id="f7775-147">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f7775-147">C# Programming Guide</span></span>](../../programming-guide/index.md)  
[<span data-ttu-id="f7775-148">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f7775-148">C# Keywords</span></span>](index.md)  
[<span data-ttu-id="f7775-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="f7775-149">foreach, in</span></span>](foreach-in.md)  
[<span data-ttu-id="f7775-150">for Deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="f7775-150">for Statement (C++)</span></span>](/cpp/cpp/for-statement-cpp)  
[<span data-ttu-id="f7775-151">Yineleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="f7775-151">Iteration Statements</span></span>](iteration-statements.md)
