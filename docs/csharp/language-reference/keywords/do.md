---
title: yapın - C# başvurusu
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 4bdbd1c8efac0b7ba95d4c8d16dae3101fe6bcb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661795"
---
# <a name="do-c-reference"></a><span data-ttu-id="32132-102">do (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="32132-102">do (C# Reference)</span></span>

<span data-ttu-id="32132-103">`do` Deyimi, bir deyimi veya bir deyimler bloğunu belirtilen bir Boole ifadesi değerlendirilir sırada yürütür `true`.</span><span class="sxs-lookup"><span data-stu-id="32132-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="32132-104">Bu ifade döngünün her yürütülmesi değerlendirilir çünkü bir `do-while` bir veya daha fazla kez döngü yürütür.</span><span class="sxs-lookup"><span data-stu-id="32132-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="32132-105">Bu farklıdır [sırada](while.md) döngü, sıfır veya daha fazla kez yürütülür.</span><span class="sxs-lookup"><span data-stu-id="32132-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="32132-106">Herhangi bir anda işaret içinde `do` deyim bloğunu kullanarak döngü dışında bozabilir [sonu](break.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="32132-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="32132-107">Değerlendirme için doğrudan geçebilirsiniz `while` kullanarak ifade [devam](continue.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="32132-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="32132-108">İfade değerlendirme sonucu `true`, yürütme Döngüdeki ilk deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="32132-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="32132-109">Aksi takdirde, yürütme döngüyü sonra ilk deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="32132-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="32132-110">Ayrıca çıkış bir `do-while` tarafından döngü [goto](goto.md), [dönüş](return.md), veya [throw](throw.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="32132-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="32132-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="32132-111">Example</span></span>

<span data-ttu-id="32132-112">Aşağıdaki örnek, kullanımını gösterir. `do` deyimi.</span><span class="sxs-lookup"><span data-stu-id="32132-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="32132-113">Seçin **çalıştırma** örnek kodu çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="32132-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="32132-114">Bundan sonra bu kodu Değiştir ve yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="32132-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="32132-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="32132-115">C# language specification</span></span>

<span data-ttu-id="32132-116">Daha fazla bilgi için [do deyimi](~/_csharplang/spec/statements.md#the-do-statement) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="32132-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="32132-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32132-117">See also</span></span>

- [<span data-ttu-id="32132-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="32132-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="32132-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="32132-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="32132-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="32132-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="32132-121">Yineleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="32132-121">Iteration Statements</span></span>](iteration-statements.md)
- [<span data-ttu-id="32132-122">while deyimi</span><span class="sxs-lookup"><span data-stu-id="32132-122">while statement</span></span>](while.md)
