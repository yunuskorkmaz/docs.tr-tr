---
title: C#for deyimleri
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 61315a04ca8d5a619a3dcaf43b15a309919d3c42
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2019
ms.locfileid: "70167877"
---
# <a name="for-c-reference"></a><span data-ttu-id="2c2f3-102">(C# başvuru) için</span><span class="sxs-lookup"><span data-stu-id="2c2f3-102">for (C# reference)</span></span>

<span data-ttu-id="2c2f3-103">Deyimi `for` , belirtilen bir Boole ifadesi olarak `true`değerlendirilen bir deyimi veya bir deyim bloğunu yürütür.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="2c2f3-104">`for` Deyimdeki herhangi bir noktada, [Break](break.md) ifadesini kullanarak ya da [Continue](continue.md) ifadesini kullanarak döngünün bir sonraki yinelemesine adımla döngüyü kesebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="2c2f3-105">Ayrıca [goto](goto.md), [Return](return.md)veya `for` [throw](throw.md) deyimleriyle bir döngüden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="2c2f3-106">`for` Deyimin yapısı</span><span class="sxs-lookup"><span data-stu-id="2c2f3-106">Structure of the `for` statement</span></span>

<span data-ttu-id="2c2f3-107">İfade Başlatıcı, *koşul*ve *Yineleyici* bölümlerini tanımlar: `for`</span><span class="sxs-lookup"><span data-stu-id="2c2f3-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="2c2f3-108">Üç bölüm de isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-108">All three sections are optional.</span></span> <span data-ttu-id="2c2f3-109">Döngünün gövdesi bir deyim ya da deyimler bloğu.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="2c2f3-110">Aşağıdaki örnek, tanımlı tüm `for` bölümleri içeren ifadesini gösterir:</span><span class="sxs-lookup"><span data-stu-id="2c2f3-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="2c2f3-111">*Başlatıcı* bölümü</span><span class="sxs-lookup"><span data-stu-id="2c2f3-111">The *initializer* section</span></span>

<span data-ttu-id="2c2f3-112">*Başlatıcı* bölümündeki deyimler, döngüyü girmeden önce yalnızca bir kez yürütülür.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="2c2f3-113">*Başlatıcı* bölümü aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="2c2f3-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="2c2f3-114">Döngü dışından erişilemeyen bir yerel döngü değişkeninin bildirimi ve başlatılması.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="2c2f3-115">Aşağıdaki listeden, virgülle ayrılmış olarak sıfır veya daha fazla deyim ifadesi:</span><span class="sxs-lookup"><span data-stu-id="2c2f3-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="2c2f3-116">[atama](../operators/assignment-operator.md) ekstresi</span><span class="sxs-lookup"><span data-stu-id="2c2f3-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="2c2f3-117">bir yöntemin çağrılması</span><span class="sxs-lookup"><span data-stu-id="2c2f3-117">invocation of a method</span></span>

  - <span data-ttu-id="2c2f3-118">veya gibi `++i` ön ek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifadesi`i++`</span><span class="sxs-lookup"><span data-stu-id="2c2f3-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="2c2f3-119">veya gibi `--i` sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifadesi`i--`</span><span class="sxs-lookup"><span data-stu-id="2c2f3-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="2c2f3-120">[New](../operators/new-operator.md) işlecini kullanarak bir nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="2c2f3-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="2c2f3-121">[await](../operators/await.md) ifadesi</span><span class="sxs-lookup"><span data-stu-id="2c2f3-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="2c2f3-122">Yukarıdaki örnekteki *Başlatıcı* bölümü, yerel döngü değişkenini `i`bildirir ve başlatır:</span><span class="sxs-lookup"><span data-stu-id="2c2f3-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="2c2f3-123">*Koşul* bölümü</span><span class="sxs-lookup"><span data-stu-id="2c2f3-123">The *condition* section</span></span>

<span data-ttu-id="2c2f3-124">*Koşul* bölümü varsa, bir Boolean ifadesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="2c2f3-125">Bu ifade, her döngü yinelemesinden önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="2c2f3-126">*Koşul* bölümü yoksa veya Boole ifadesi olarak `true`değerlendirilirse, sonraki döngü yinelemesi yürütülür; Aksi takdirde, döngüden çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="2c2f3-127">Yukarıdaki örnekteki *koşul* bölümü, döngünün yerel döngü değişkeninin değerine göre sonlandırdığını belirler:</span><span class="sxs-lookup"><span data-stu-id="2c2f3-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="2c2f3-128">*Yineleyici* bölümü</span><span class="sxs-lookup"><span data-stu-id="2c2f3-128">The *iterator* section</span></span>

<span data-ttu-id="2c2f3-129">*Yineleyici* bölümü, döngü gövdesinin her yinelemesinden sonra ne olacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="2c2f3-130">*Yineleyici* bölümü, virgülle ayrılmış olarak aşağıdaki deyim ifadelerinden sıfır veya daha fazlasını içerir:</span><span class="sxs-lookup"><span data-stu-id="2c2f3-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="2c2f3-131">[atama](../operators/assignment-operator.md) ekstresi</span><span class="sxs-lookup"><span data-stu-id="2c2f3-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="2c2f3-132">bir yöntemin çağrılması</span><span class="sxs-lookup"><span data-stu-id="2c2f3-132">invocation of a method</span></span>

- <span data-ttu-id="2c2f3-133">veya gibi `++i` ön ek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifadesi`i++`</span><span class="sxs-lookup"><span data-stu-id="2c2f3-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="2c2f3-134">veya gibi `--i` sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifadesi`i--`</span><span class="sxs-lookup"><span data-stu-id="2c2f3-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="2c2f3-135">[New](../operators/new-operator.md) işlecini kullanarak bir nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="2c2f3-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="2c2f3-136">[await](../operators/await.md) ifadesi</span><span class="sxs-lookup"><span data-stu-id="2c2f3-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="2c2f3-137">Yukarıdaki örnekteki *Yineleyici* bölümü, yerel döngü değişkenini artırır:</span><span class="sxs-lookup"><span data-stu-id="2c2f3-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="2c2f3-138">Örnekler</span><span class="sxs-lookup"><span data-stu-id="2c2f3-138">Examples</span></span>

<span data-ttu-id="2c2f3-139">Aşağıdaki örnek, `for` ifade bölümlerinin birkaç daha az ortak kullanımını göstermektedir: *Başlatıcı* bölümünde bir dış döngü değişkenine değer atama, hem *Başlatıcı* hem de Yineleyici içinde bir yöntemi çağırmabölümler ve *Yineleyici* bölümünde iki değişkenin değerlerini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="2c2f3-140">Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="2c2f3-141">Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="2c2f3-142">Aşağıdaki örnek sonsuz `for` döngüsünü tanımlar:</span><span class="sxs-lookup"><span data-stu-id="2c2f3-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="2c2f3-143">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="2c2f3-143">C# language specification</span></span>

<span data-ttu-id="2c2f3-144">Daha fazla bilgi için bkz. [ C# dil belirtiminin](../language-specification/index.md) [for deyimleri](~/_csharplang/spec/statements.md#the-for-statement) bölümü.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2c2f3-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c2f3-145">See also</span></span>

- [<span data-ttu-id="2c2f3-146">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="2c2f3-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2c2f3-147">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2c2f3-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2c2f3-148">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="2c2f3-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2c2f3-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="2c2f3-149">foreach, in</span></span>](foreach-in.md)
