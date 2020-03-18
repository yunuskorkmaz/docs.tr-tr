---
title: deyim için - C# referans
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: fc6a23cabd93323cacc33dfc4388116881c1fc84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74552263"
---
# <a name="for-c-reference"></a><span data-ttu-id="b0dfb-102">for (C# referansı)</span><span class="sxs-lookup"><span data-stu-id="b0dfb-102">for (C# reference)</span></span>

<span data-ttu-id="b0dfb-103">`for` İfade bir deyim veya ifade bloğu yürütürken, belirli bir `true`Boolean ifadesi .'ye göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="b0dfb-104">İfade bloğu içindeki herhangi bir noktada, [kesme](break.md) deyimini kullanarak döngüden çıkabilir veya continue deyimini kullanarak döngüdeki bir sonraki yinelemeye adım atabilirsiniz. [continue](continue.md) `for`</span><span class="sxs-lookup"><span data-stu-id="b0dfb-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="b0dfb-105">Ayrıca `for` [goto,](goto.md) [return](return.md)veya [atmak](throw.md) ifadeleri tarafından bir döngü çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="b0dfb-106">İfadenin `for` yapısı</span><span class="sxs-lookup"><span data-stu-id="b0dfb-106">Structure of the `for` statement</span></span>

<span data-ttu-id="b0dfb-107">Deyim, *başharf*, *durum*ve *yineleyici* bölümleri tanımlar: `for`</span><span class="sxs-lookup"><span data-stu-id="b0dfb-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="b0dfb-108">Her üç bölüm isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-108">All three sections are optional.</span></span> <span data-ttu-id="b0dfb-109">Döngügövdesi bir deyim veya ifadeler bloğudur.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="b0dfb-110">Aşağıdaki örnek, `for` tanımlanan tüm bölümlerle ifadeyi gösterir:</span><span class="sxs-lookup"><span data-stu-id="b0dfb-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="b0dfb-111">*Baş harf* bölümü</span><span class="sxs-lookup"><span data-stu-id="b0dfb-111">The *initializer* section</span></span>

<span data-ttu-id="b0dfb-112">*Başharf* bölümündeki ifadeler döngüye girmeden önce yalnızca bir kez yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="b0dfb-113">*Baş harfi* alan bölüm aşağıdakilerden biridir:</span><span class="sxs-lookup"><span data-stu-id="b0dfb-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="b0dfb-114">Döngü dışından erişilmeden yerel bir döngü değişkeninin bildirimi ve başlatılması.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="b0dfb-115">Aşağıdaki listeden virgülle ayrılmış sıfır veya daha fazla ifade ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="b0dfb-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="b0dfb-116">[atama](../operators/assignment-operator.md) deyimi</span><span class="sxs-lookup"><span data-stu-id="b0dfb-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="b0dfb-117">bir yöntemin çağrılması</span><span class="sxs-lookup"><span data-stu-id="b0dfb-117">invocation of a method</span></span>

  - <span data-ttu-id="b0dfb-118">önek veya postfix [artış](../operators/arithmetic-operators.md#increment-operator-) ifade, `++i` gibi veya`i++`</span><span class="sxs-lookup"><span data-stu-id="b0dfb-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="b0dfb-119">önek veya postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) `--i` ifadesi gibi veya`i--`</span><span class="sxs-lookup"><span data-stu-id="b0dfb-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="b0dfb-120">[yeni](../operators/new-operator.md) işleç kullanarak bir nesnenin oluşturulması</span><span class="sxs-lookup"><span data-stu-id="b0dfb-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="b0dfb-121">ifade [bekliyor](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="b0dfb-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="b0dfb-122">Yukarıdaki örnekteki *başharf* bölümü yerel döngü değişkenini `i`bildirir ve başharfe bildirir:</span><span class="sxs-lookup"><span data-stu-id="b0dfb-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="b0dfb-123">*Koşul* bölümü</span><span class="sxs-lookup"><span data-stu-id="b0dfb-123">The *condition* section</span></span>

<span data-ttu-id="b0dfb-124">*Durum* bölümü, varsa, bir boolean ifade olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="b0dfb-125">Bu ifade her döngü yinelemesinden önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="b0dfb-126">*Koşul* bölümü yoksa veya boolean ifadesi ,bir `true`sonraki döngü yinelemesi yürütülür; aksi takdirde, döngü çıkar.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="b0dfb-127">Yukarıdaki örnekteki *koşul* bölümü, döngünün yerel döngü değişkeninin değerine göre sonunun dolup dolmadığını belirler:</span><span class="sxs-lookup"><span data-stu-id="b0dfb-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="b0dfb-128">*Yineleyici* bölümü</span><span class="sxs-lookup"><span data-stu-id="b0dfb-128">The *iterator* section</span></span>

<span data-ttu-id="b0dfb-129">*Yineleme* bölümü, döngü gövdesinin her yinelemeden sonra ne olacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="b0dfb-130">*Yineleyici* bölümü, virgülle ayrılmış aşağıdaki deyim ifadelerinden sıfır veya daha fazlasını içerir:</span><span class="sxs-lookup"><span data-stu-id="b0dfb-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="b0dfb-131">[atama](../operators/assignment-operator.md) deyimi</span><span class="sxs-lookup"><span data-stu-id="b0dfb-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="b0dfb-132">bir yöntemin çağrılması</span><span class="sxs-lookup"><span data-stu-id="b0dfb-132">invocation of a method</span></span>

- <span data-ttu-id="b0dfb-133">önek veya postfix [artış](../operators/arithmetic-operators.md#increment-operator-) ifade, `++i` gibi veya`i++`</span><span class="sxs-lookup"><span data-stu-id="b0dfb-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="b0dfb-134">önek veya postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) `--i` ifadesi gibi veya`i--`</span><span class="sxs-lookup"><span data-stu-id="b0dfb-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="b0dfb-135">[yeni](../operators/new-operator.md) işleç kullanarak bir nesnenin oluşturulması</span><span class="sxs-lookup"><span data-stu-id="b0dfb-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="b0dfb-136">ifade [bekliyor](../operators/await.md)</span><span class="sxs-lookup"><span data-stu-id="b0dfb-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="b0dfb-137">Yukarıdaki örnekteki *yineleyici* bölümü yerel döngü değişkenini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b0dfb-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="b0dfb-138">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b0dfb-138">Examples</span></span>

<span data-ttu-id="b0dfb-139">Aşağıdaki örnek, deyim `for` bölümlerinin daha az yaygın birkaç kullanımını göstermektedir: *başharf* bölümünde bir dış döngü değişkenine değer atamak, hem *başharf* hem de *yineleyici* bölümlerinde bir yöntem çağırmak ve *yineleyici* bölümündeki iki değişkenin değerlerini değiştirmek.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="b0dfb-140">Örnek kodu çalıştırmak için **Çalıştır'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="b0dfb-141">Bundan sonra kodu değiştirebilir ve yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="b0dfb-142">Aşağıdaki örnekte sonsuz `for` döngü tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="b0dfb-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="b0dfb-143">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b0dfb-143">C# language specification</span></span>

<span data-ttu-id="b0dfb-144">Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [ekstre](~/_csharplang/spec/statements.md#the-for-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0dfb-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-145">See also</span></span>

- [<span data-ttu-id="b0dfb-146">C# Referans</span><span class="sxs-lookup"><span data-stu-id="b0dfb-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b0dfb-147">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b0dfb-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b0dfb-148">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="b0dfb-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b0dfb-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="b0dfb-149">foreach, in</span></span>](foreach-in.md)
