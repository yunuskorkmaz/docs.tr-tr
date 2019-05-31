---
title: C# deyimi
ms.date: 06/13/2018
f1_keywords:
- for
- for_CSharpKeyword
helpviewer_keywords:
- for keyword [C#]
ms.assetid: 34041a40-2c87-467a-9ffb-a0417d8f67a8
ms.openlocfilehash: 166f8a99a3556664f5f3701c94aa8593ac7ebe32
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422085"
---
# <a name="for-c-reference"></a><span data-ttu-id="193b0-102">(için C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="193b0-102">for (C# reference)</span></span>

<span data-ttu-id="193b0-103">`for` Deyimi, bir deyimi veya bir deyimler bloğunu belirtilen bir Boole ifadesi değerlendirilir sırada yürütür `true`.</span><span class="sxs-lookup"><span data-stu-id="193b0-103">The `for` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span>

<span data-ttu-id="193b0-104">Herhangi bir anda işaret içinde `for` deyim bloğunu kullanarak döngü dışında bozabilir [sonu](break.md) deyimi veya bir sonraki yinelemesine kullanarak adım [devam](continue.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="193b0-104">At any point within the `for` statement block, you can break out of the loop by using the [break](break.md) statement, or step to the next iteration in the loop by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="193b0-105">Ayrıca çıkış bir `for` tarafından döngü [goto](goto.md), [dönüş](return.md), veya [throw](throw.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="193b0-105">You also can exit a `for` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="structure-of-the-for-statement"></a><span data-ttu-id="193b0-106">Yapısını `for` deyimi</span><span class="sxs-lookup"><span data-stu-id="193b0-106">Structure of the `for` statement</span></span>

<span data-ttu-id="193b0-107">`for` Tanımlar *Başlatıcı*, *koşul*, ve *yineleyici* bölümler:</span><span class="sxs-lookup"><span data-stu-id="193b0-107">The `for` statement defines *initializer*, *condition*, and *iterator* sections:</span></span>

```csharp
for (initializer; condition; iterator)
    body
```

<span data-ttu-id="193b0-108">Tüm üç bölüm isteğe bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="193b0-108">All three sections are optional.</span></span> <span data-ttu-id="193b0-109">Döngü gövdesi bir deyimi veya bir deyimler bloğunu ' dir.</span><span class="sxs-lookup"><span data-stu-id="193b0-109">The body of the loop is either a statement or a block of statements.</span></span>

<span data-ttu-id="193b0-110">Aşağıdaki örnekte gösterildiği `for` deyimiyle tüm tanımlı bölümler:</span><span class="sxs-lookup"><span data-stu-id="193b0-110">The following example shows the `for` statement with all of the sections defined:</span></span>

[!code-csharp-interactive[for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#5)]

### <a name="the-initializer-section"></a><span data-ttu-id="193b0-111">*Başlatıcı* bölümü</span><span class="sxs-lookup"><span data-stu-id="193b0-111">The *initializer* section</span></span>

<span data-ttu-id="193b0-112">İfadeler *Başlatıcı* bölüm yürütülür yalnızca bir kez döngü girmeden önce.</span><span class="sxs-lookup"><span data-stu-id="193b0-112">The statements in the *initializer* section are executed only once, before entering the loop.</span></span> <span data-ttu-id="193b0-113">*Başlatıcı* bölümünde aşağıdakilerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="193b0-113">The *initializer* section is either of the following:</span></span>

- <span data-ttu-id="193b0-114">Döngü dışında erişilemez bir yerel Döngü değişkeninin başlatma ve bildirimi.</span><span class="sxs-lookup"><span data-stu-id="193b0-114">The declaration and initialization of a local loop variable, which can't be accessed from outside the loop.</span></span>

- <span data-ttu-id="193b0-115">Virgülle ayırarak aşağıdaki listeden sıfır veya daha fazla deyim ifadeleri:</span><span class="sxs-lookup"><span data-stu-id="193b0-115">Zero or more statement expressions from the following list, separated by commas:</span></span>

  - <span data-ttu-id="193b0-116">[atama](../operators/assignment-operator.md) deyimi</span><span class="sxs-lookup"><span data-stu-id="193b0-116">[assignment](../operators/assignment-operator.md) statement</span></span>

  - <span data-ttu-id="193b0-117">bir yöntemi çağrıldı</span><span class="sxs-lookup"><span data-stu-id="193b0-117">invocation of a method</span></span>

  - <span data-ttu-id="193b0-118">ön ek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifade gibi `++i` veya `i++`</span><span class="sxs-lookup"><span data-stu-id="193b0-118">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

  - <span data-ttu-id="193b0-119">ön ek veya sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifade gibi `--i` veya `i--`</span><span class="sxs-lookup"><span data-stu-id="193b0-119">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

  - <span data-ttu-id="193b0-120">kullanarak bir nesne oluşturulması [yeni](new-operator.md) anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="193b0-120">creation of an object by using [new](new-operator.md) keyword</span></span>

  - <span data-ttu-id="193b0-121">[await](await.md) ifadesi</span><span class="sxs-lookup"><span data-stu-id="193b0-121">[await](await.md) expression</span></span>

<span data-ttu-id="193b0-122">*Başlatıcı* Yukarıdaki örnek bölümünde bildirir ve yerel Döngü değişkeninin başlatır `i`:</span><span class="sxs-lookup"><span data-stu-id="193b0-122">The *initializer* section in the example above declares and initializes the local loop variable `i`:</span></span>

```csharp
int i = 0
```

### <a name="the-condition-section"></a><span data-ttu-id="193b0-123">*Koşul* bölümü</span><span class="sxs-lookup"><span data-stu-id="193b0-123">The *condition* section</span></span>

<span data-ttu-id="193b0-124">*Koşul* bölümünde varsa olmalıdır bir boolean ifadesi.</span><span class="sxs-lookup"><span data-stu-id="193b0-124">The *condition* section, if present, must be a boolean expression.</span></span> <span data-ttu-id="193b0-125">Bu ifade, her döngü yinelemesinden önce değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="193b0-125">That expression is evaluated before every loop iteration.</span></span> <span data-ttu-id="193b0-126">Varsa *koşul* bölümü mevcut değil ya da Boole ifadenin değerlendirdiği `true`sonraki döngü yinelemesi yürütülen; Aksi takdirde, döngü çıkıldı.</span><span class="sxs-lookup"><span data-stu-id="193b0-126">If the *condition* section is not present or the boolean expression evaluates to `true`, the next loop iteration is executed; otherwise, the loop is exited.</span></span>

<span data-ttu-id="193b0-127">*Koşul* Yukarıdaki örnek bölümünde döngü yerel Döngü değişkeninin değerine göre kesilip kesilmediğini belirler:</span><span class="sxs-lookup"><span data-stu-id="193b0-127">The *condition* section in the example above determines if the loop terminates based on the value of the local loop variable:</span></span>

```csharp
i < 5
```

### <a name="the-iterator-section"></a><span data-ttu-id="193b0-128">*Yineleyici* bölümü</span><span class="sxs-lookup"><span data-stu-id="193b0-128">The *iterator* section</span></span>

<span data-ttu-id="193b0-129">*Yineleyici* bölüm tanımlar döngü gövdesinin her yinelemeden sonra ne olur.</span><span class="sxs-lookup"><span data-stu-id="193b0-129">The *iterator* section defines what happens after each iteration of the body of the loop.</span></span> <span data-ttu-id="193b0-130">*Yineleyici* sıfır veya daha fazla virgülle ayırarak aşağıdaki deyim ifadeleri bölüm içerir:</span><span class="sxs-lookup"><span data-stu-id="193b0-130">The *iterator* section contains zero or more of the following statement expressions, separated by commas:</span></span>

- <span data-ttu-id="193b0-131">[atama](../operators/assignment-operator.md) deyimi</span><span class="sxs-lookup"><span data-stu-id="193b0-131">[assignment](../operators/assignment-operator.md) statement</span></span>

- <span data-ttu-id="193b0-132">bir yöntemi çağrıldı</span><span class="sxs-lookup"><span data-stu-id="193b0-132">invocation of a method</span></span>

- <span data-ttu-id="193b0-133">ön ek veya sonek [artışı](../operators/arithmetic-operators.md#increment-operator-) ifade gibi `++i` veya `i++`</span><span class="sxs-lookup"><span data-stu-id="193b0-133">prefix or postfix [increment](../operators/arithmetic-operators.md#increment-operator-) expression, such as `++i` or `i++`</span></span>

- <span data-ttu-id="193b0-134">ön ek veya sonek [azaltma](../operators/arithmetic-operators.md#decrement-operator---) ifade gibi `--i` veya `i--`</span><span class="sxs-lookup"><span data-stu-id="193b0-134">prefix or postfix [decrement](../operators/arithmetic-operators.md#decrement-operator---) expression, such as `--i` or `i--`</span></span>

- <span data-ttu-id="193b0-135">kullanarak bir nesne oluşturulması [yeni](new-operator.md) anahtar sözcüğü</span><span class="sxs-lookup"><span data-stu-id="193b0-135">creation of an object by using [new](new-operator.md) keyword</span></span>

- <span data-ttu-id="193b0-136">[await](await.md) ifadesi</span><span class="sxs-lookup"><span data-stu-id="193b0-136">[await](await.md) expression</span></span>

<span data-ttu-id="193b0-137">*Yineleyici* Yukarıdaki örnek bölümünde yerel Döngü değişkeninin artırır:</span><span class="sxs-lookup"><span data-stu-id="193b0-137">The *iterator* section in the example above increments the local loop variable:</span></span>

```csharp
i++
```

## <a name="examples"></a><span data-ttu-id="193b0-138">Örnekler</span><span class="sxs-lookup"><span data-stu-id="193b0-138">Examples</span></span>

<span data-ttu-id="193b0-139">Aşağıdaki örnekte, birkaç yaygın kullanımları daha az gösterilmektedir `for` deyimi bölümler: bir dış Döngü değişkeninin içinde bir değer atamak *Başlatıcı* bölümü, hem de bir yöntem çağırma  *Başlatıcı* ve *yineleyici* bölümler ve iki değişkenin değiştirerek *yineleyici* bölümü.</span><span class="sxs-lookup"><span data-stu-id="193b0-139">The following example illustrates several less common usages of the `for` statement sections: assigning a value to an external loop variable in the *initializer* section, invoking a method in both the *initializer* and the *iterator* sections, and changing the values of two variables in the *iterator* section.</span></span> <span data-ttu-id="193b0-140">Seçin **çalıştırma** örnek kodu çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="193b0-140">Select **Run** to run the example code.</span></span> <span data-ttu-id="193b0-141">Bundan sonra bu kodu Değiştir ve yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="193b0-141">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[not typical for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#6)]

<span data-ttu-id="193b0-142">Aşağıdaki örnek, sınırsız tanımlar `for` döngü:</span><span class="sxs-lookup"><span data-stu-id="193b0-142">The following example defines the infinite `for` loop:</span></span>

[!code-csharp[infinite for loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#7)]

## <a name="c-language-specification"></a><span data-ttu-id="193b0-143">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="193b0-143">C# language specification</span></span>

<span data-ttu-id="193b0-144">Daha fazla bilgi için [deyimi için](~/_csharplang/spec/statements.md#the-for-statement) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="193b0-144">For more information, see [The for statement](~/_csharplang/spec/statements.md#the-for-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="193b0-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="193b0-145">See also</span></span>

- [<span data-ttu-id="193b0-146">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="193b0-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="193b0-147">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="193b0-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="193b0-148">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="193b0-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="193b0-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="193b0-149">foreach, in</span></span>](foreach-in.md)
