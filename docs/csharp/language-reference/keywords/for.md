---
description: for deyimleri-C# başvurusu
title: for deyimleri-C# başvurusu
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: be9ecdc08d54c9cde1c49656a16e0d85a6d7084d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126937"
---
# <a name="for-c-reference"></a><span data-ttu-id="f8a0b-103">for (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f8a0b-103">for (C# reference)</span></span>

<span data-ttu-id="f8a0b-104">`for`Deyimi, belirtilen bir Boole ifadesi olarak değerlendirilen bir deyimi veya bir deyim bloğunu yürütür `true` .</span><span class="sxs-lookup"><span data-stu-id="f8a0b-104">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="f8a0b-105">Deyimdeki herhangi bir noktada `for` , [Break](break.md) ifadesini kullanarak ya da [Continue](continue.md) ifadesini kullanarak döngünün bir sonraki yinelemesine adımla döngüyü kesebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-105">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="f8a0b-106">Ayrıca `for` [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir döngüden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-106">You can also exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="f8a0b-107">`for`Deyimin yapısı</span><span class="sxs-lookup"><span data-stu-id="f8a0b-107">Structure of the `for` statement</span></span>

<span data-ttu-id="f8a0b-108">`for`İfade *Başlatıcı*, *koşul*ve *Yineleyici* bölümlerini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="f8a0b-108">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="f8a0b-109">Üç bölüm de isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-109">All three sections are optional.</span></span> <span data-ttu-id="f8a0b-110">Döngünün gövdesi bir deyim ya da deyimler bloğu.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-110">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="f8a0b-111">Aşağıdaki örnek, `for` tanımlı tüm bölümleri içeren ifadesini gösterir:</span><span class="sxs-lookup"><span data-stu-id="f8a0b-111">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](snippets/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="f8a0b-112">*Başlatıcı* bölümü</span><span class="sxs-lookup"><span data-stu-id="f8a0b-112">The *initializer* section</span></span>

<span data-ttu-id="f8a0b-113">*Başlatıcı* bölümündeki deyimler, döngüyü girmeden önce yalnızca bir kez yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-113">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="f8a0b-114">*Başlatıcı* bölümü aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="f8a0b-114">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="f8a0b-115">Döngü dışından erişilemeyen bir yerel döngü değişkeninin bildirimi ve başlatılması.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-115">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="f8a0b-116">Aşağıdaki listeden, virgülle ayrılmış olarak sıfır veya daha fazla deyim ifadesi:</span><span class="sxs-lookup"><span data-stu-id="f8a0b-116">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="f8a0b-117">[atama](../operators/assignment-operator.md) ekstresi</span><span class="sxs-lookup"><span data-stu-id="f8a0b-117">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="f8a0b-118">bir yöntemin çağrılması</span><span class="sxs-lookup"><span data-stu-id="f8a0b-118">invocation of a method</span></span>

  - <span data-ttu-id="f8a0b-119">veya gibi ön ek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifadesi `++i``i++`</span><span class="sxs-lookup"><span data-stu-id="f8a0b-119">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="f8a0b-120">veya gibi sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifadesi `--i``i--`</span><span class="sxs-lookup"><span data-stu-id="f8a0b-120">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="f8a0b-121">[New](../operators/new-operator.md) işlecini kullanarak bir nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8a0b-121">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="f8a0b-122">[await](../operators/await.md) ifadesi</span><span class="sxs-lookup"><span data-stu-id="f8a0b-122">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="f8a0b-123">Yukarıdaki örnekteki *Başlatıcı* bölümü, yerel döngü değişkenini bildirir ve başlatır `i` :</span><span class="sxs-lookup"><span data-stu-id="f8a0b-123">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="f8a0b-124">*Koşul* bölümü</span><span class="sxs-lookup"><span data-stu-id="f8a0b-124">The *condition* section</span></span>

<span data-ttu-id="f8a0b-125">*Koşul* bölümü varsa, bir Boolean ifadesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-125">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="f8a0b-126">Bu ifade, her döngü yinelemesinden önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-126">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="f8a0b-127">*Koşul* bölümü yoksa veya Boole ifadesi olarak değerlendirilirse `true` , sonraki döngü yinelemesi yürütülür; Aksi takdirde, döngüden çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-127">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="f8a0b-128">Yukarıdaki örnekteki *koşul* bölümü, döngünün yerel döngü değişkeninin değerine göre sonlandırdığını belirler:</span><span class="sxs-lookup"><span data-stu-id="f8a0b-128">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="f8a0b-129">*Yineleyici* bölümü</span><span class="sxs-lookup"><span data-stu-id="f8a0b-129">The *iterator* section</span></span>

<span data-ttu-id="f8a0b-130">*Yineleyici* bölümü, döngü gövdesinin her yinelemesinden sonra ne olacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-130">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="f8a0b-131">*Yineleyici* bölümü, virgülle ayrılmış olarak aşağıdaki deyim ifadelerinden sıfır veya daha fazlasını içerir:</span><span class="sxs-lookup"><span data-stu-id="f8a0b-131">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="f8a0b-132">[atama](../operators/assignment-operator.md) ekstresi</span><span class="sxs-lookup"><span data-stu-id="f8a0b-132">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="f8a0b-133">bir yöntemin çağrılması</span><span class="sxs-lookup"><span data-stu-id="f8a0b-133">invocation of a method</span></span>

- <span data-ttu-id="f8a0b-134">veya gibi ön ek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifadesi `++i``i++`</span><span class="sxs-lookup"><span data-stu-id="f8a0b-134">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="f8a0b-135">veya gibi sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifadesi `--i``i--`</span><span class="sxs-lookup"><span data-stu-id="f8a0b-135">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="f8a0b-136">[New](../operators/new-operator.md) işlecini kullanarak bir nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8a0b-136">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="f8a0b-137">[await](../operators/await.md) ifadesi</span><span class="sxs-lookup"><span data-stu-id="f8a0b-137">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="f8a0b-138">Yukarıdaki örnekteki *Yineleyici* bölümü, yerel döngü değişkenini artırır:</span><span class="sxs-lookup"><span data-stu-id="f8a0b-138">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="f8a0b-139">Örnekler</span><span class="sxs-lookup"><span data-stu-id="f8a0b-139">Examples</span></span>

<span data-ttu-id="f8a0b-140">Aşağıdaki örnek, ifade bölümlerinin birkaç daha az ortak kullanımını göstermektedir `for` : *Başlatıcı* bölümünde bir dış döngü değişkenine değer atama, *Başlatıcı* ve *Yineleyici* bölümlerinde bir yöntemi çağırma ve *Yineleyici* bölümündeki iki değişkenin değerlerini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-140">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="f8a0b-141">Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-141">Select **Run** to run the example code.</span></span> <span data-ttu-id="f8a0b-142">Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-142">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](snippets/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="f8a0b-143">Aşağıdaki örnek sonsuz `for` döngüsünü tanımlar:</span><span class="sxs-lookup"><span data-stu-id="f8a0b-143">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](snippets/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="f8a0b-144">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f8a0b-144">C# language specification</span></span>

<span data-ttu-id="f8a0b-145">Daha fazla bilgi için bkz. [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [for deyimleri](~/_csharplang/spec/statements.md#the-for-statement) bölümü.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-145">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8a0b-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8a0b-146">See also</span></span>

- [<span data-ttu-id="f8a0b-147">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f8a0b-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f8a0b-148">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f8a0b-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f8a0b-149">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f8a0b-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f8a0b-150">foreach, in</span><span class="sxs-lookup"><span data-stu-id="f8a0b-150">foreach, in</span></span>](foreach-in.md)
