---
title: for ifadesinin C# başvurusu
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: fc6a23cabd93323cacc33dfc4388116881c1fc84
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552263"
---
# <a name="for-c-reference"></a><span data-ttu-id="aab9c-102">(C# başvuru) için</span><span class="sxs-lookup"><span data-stu-id="aab9c-102">for (C# reference)</span></span>

<span data-ttu-id="aab9c-103">`for` deyimi, belirtilen bir Boole ifadesi `true`değerlendirirken bir deyimi veya bir deyim bloğunu yürütür.</span><span class="sxs-lookup"><span data-stu-id="aab9c-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="aab9c-104">`for` bildiri bloğunun içindeki herhangi bir noktada, [Break](break.md) ifadesini kullanarak döngünün dışına bölebilir veya [Continue](continue.md) ifadesini kullanarak döngünün bir sonraki yinelemesine adım aktarabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aab9c-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="aab9c-105">Ayrıca, [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir `for` döngüsünden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aab9c-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="aab9c-106">`for` deyimin yapısı</span><span class="sxs-lookup"><span data-stu-id="aab9c-106">Structure of the `for` statement</span></span>

<span data-ttu-id="aab9c-107">`for` bildiri *Başlatıcı*, *koşul*ve *Yineleyici* bölümlerini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="aab9c-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="aab9c-108">Üç bölüm de isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="aab9c-108">All three sections are optional.</span></span> <span data-ttu-id="aab9c-109">Döngünün gövdesi bir deyim ya da deyimler bloğu.</span><span class="sxs-lookup"><span data-stu-id="aab9c-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="aab9c-110">Aşağıdaki örnekte, tanımlı tüm bölümler ile `for` deyimleri gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="aab9c-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="aab9c-111">*Başlatıcı* bölümü</span><span class="sxs-lookup"><span data-stu-id="aab9c-111">The *initializer* section</span></span>

<span data-ttu-id="aab9c-112">*Başlatıcı* bölümündeki deyimler, döngüyü girmeden önce yalnızca bir kez yürütülür.</span><span class="sxs-lookup"><span data-stu-id="aab9c-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="aab9c-113">*Başlatıcı* bölümü aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="aab9c-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="aab9c-114">Döngü dışından erişilemeyen bir yerel döngü değişkeninin bildirimi ve başlatılması.</span><span class="sxs-lookup"><span data-stu-id="aab9c-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="aab9c-115">Aşağıdaki listeden, virgülle ayrılmış olarak sıfır veya daha fazla deyim ifadesi:</span><span class="sxs-lookup"><span data-stu-id="aab9c-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="aab9c-116">[atama](../operators/assignment-operator.md) ekstresi</span><span class="sxs-lookup"><span data-stu-id="aab9c-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="aab9c-117">bir yöntemin çağrılması</span><span class="sxs-lookup"><span data-stu-id="aab9c-117">invocation of a method</span></span>

  - <span data-ttu-id="aab9c-118">`++i` veya `i++` gibi önek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifadesi</span><span class="sxs-lookup"><span data-stu-id="aab9c-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="aab9c-119">`--i` veya `i--` gibi ön ek veya sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifadesi</span><span class="sxs-lookup"><span data-stu-id="aab9c-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="aab9c-120">[New](../operators/new-operator.md) işlecini kullanarak bir nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="aab9c-120">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

  - <span data-ttu-id="aab9c-121">[await](../operators/await.md) ifadesi</span><span class="sxs-lookup"><span data-stu-id="aab9c-121">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="aab9c-122">Yukarıdaki örnekteki *Başlatıcı* bölümü, `i`yerel döngü değişkenini bildirir ve başlatır:</span><span class="sxs-lookup"><span data-stu-id="aab9c-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="aab9c-123">*Koşul* bölümü</span><span class="sxs-lookup"><span data-stu-id="aab9c-123">The *condition* section</span></span>

<span data-ttu-id="aab9c-124">*Koşul* bölümü varsa, bir Boolean ifadesi olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aab9c-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="aab9c-125">Bu ifade, her döngü yinelemesinden önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="aab9c-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="aab9c-126">*Koşul* bölümü yoksa veya boole ifadesi `true`olarak değerlendirilirse, sonraki döngü yinelemesi yürütülür; Aksi takdirde, döngüden çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="aab9c-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="aab9c-127">Yukarıdaki örnekteki *koşul* bölümü, döngünün yerel döngü değişkeninin değerine göre sonlandırdığını belirler:</span><span class="sxs-lookup"><span data-stu-id="aab9c-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="aab9c-128">*Yineleyici* bölümü</span><span class="sxs-lookup"><span data-stu-id="aab9c-128">The *iterator* section</span></span>

<span data-ttu-id="aab9c-129">*Yineleyici* bölümü, döngü gövdesinin her yinelemesinden sonra ne olacağını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aab9c-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="aab9c-130">*Yineleyici* bölümü, virgülle ayrılmış olarak aşağıdaki deyim ifadelerinden sıfır veya daha fazlasını içerir:</span><span class="sxs-lookup"><span data-stu-id="aab9c-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="aab9c-131">[atama](../operators/assignment-operator.md) ekstresi</span><span class="sxs-lookup"><span data-stu-id="aab9c-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="aab9c-132">bir yöntemin çağrılması</span><span class="sxs-lookup"><span data-stu-id="aab9c-132">invocation of a method</span></span>

- <span data-ttu-id="aab9c-133">`++i` veya `i++` gibi önek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifadesi</span><span class="sxs-lookup"><span data-stu-id="aab9c-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="aab9c-134">`--i` veya `i--` gibi ön ek veya sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifadesi</span><span class="sxs-lookup"><span data-stu-id="aab9c-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="aab9c-135">[New](../operators/new-operator.md) işlecini kullanarak bir nesne oluşturma</span><span class="sxs-lookup"><span data-stu-id="aab9c-135">creation of an object by using the [new](../operators/new-operator.md) operator</span></span>

- <span data-ttu-id="aab9c-136">[await](../operators/await.md) ifadesi</span><span class="sxs-lookup"><span data-stu-id="aab9c-136">[await](../operators/await.md) expression</span></span>

<span data-ttu-id="aab9c-137">Yukarıdaki örnekteki *Yineleyici* bölümü, yerel döngü değişkenini artırır:</span><span class="sxs-lookup"><span data-stu-id="aab9c-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="aab9c-138">Örnekler</span><span class="sxs-lookup"><span data-stu-id="aab9c-138">Examples</span></span>

<span data-ttu-id="aab9c-139">Aşağıdaki örnek, `for` deyimin bölümlerinin birkaç daha az ortak kullanımını göstermektedir: *Başlatıcı* bölümünde bir dış döngü değişkenine değer atama, hem *Başlatıcı* hem de *Yineleyici* içinde bir yöntemi çağırma bölümler ve *Yineleyici* bölümünde iki değişkenin değerlerini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="aab9c-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="aab9c-140">Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="aab9c-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="aab9c-141">Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aab9c-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="aab9c-142">Aşağıdaki örnek sonsuz `for` döngüsünü tanımlar:</span><span class="sxs-lookup"><span data-stu-id="aab9c-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="aab9c-143">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="aab9c-143">C# language specification</span></span>

<span data-ttu-id="aab9c-144">Daha fazla bilgi için bkz. [ C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [for deyimleri](~/_csharplang/spec/statements.md#the-for-statement) bölümü.</span><span class="sxs-lookup"><span data-stu-id="aab9c-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="aab9c-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aab9c-145">See also</span></span>

- [<span data-ttu-id="aab9c-146">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="aab9c-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aab9c-147">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="aab9c-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aab9c-148">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="aab9c-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="aab9c-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="aab9c-149">foreach, in</span></span>](foreach-in.md)
