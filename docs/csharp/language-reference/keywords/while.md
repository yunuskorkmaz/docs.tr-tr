---
title: while - C# başvurusu
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 486936ae29552891c6a58913b6d5cf9a0d725a69
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422487"
---
# <a name="while-c-reference"></a><span data-ttu-id="4c69d-102">while (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="4c69d-102">while (C# Reference)</span></span>

<span data-ttu-id="4c69d-103">`while` Deyimi, bir deyimi veya bir deyimler bloğunu belirtilen bir Boole ifadesi değerlendirilir sırada yürütür `true`.</span><span class="sxs-lookup"><span data-stu-id="4c69d-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="4c69d-104">Bu ifade döngünün her yürütmesinden önce değerlendirilir çünkü bir `while` sıfır veya daha fazla kez döngü yürütür.</span><span class="sxs-lookup"><span data-stu-id="4c69d-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="4c69d-105">Bu farklıdır [yapmak](do.md) yürüten bir veya daha fazla kez döngü.</span><span class="sxs-lookup"><span data-stu-id="4c69d-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="4c69d-106">Herhangi bir anda işaret içinde `while` deyim bloğunu kullanarak döngü dışında bozabilir [sonu](break.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="4c69d-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="4c69d-107">Değerlendirme için doğrudan geçebilirsiniz `while` kullanarak ifade [devam](continue.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="4c69d-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="4c69d-108">İfade değerlendirme sonucu `true`, yürütme Döngüdeki ilk deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="4c69d-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="4c69d-109">Aksi takdirde, yürütme döngüyü sonra ilk deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="4c69d-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="4c69d-110">Ayrıca çıkış bir `while` tarafından döngü [goto](goto.md), [dönüş](return.md), veya [throw](throw.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="4c69d-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="4c69d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c69d-111">Example</span></span>

<span data-ttu-id="4c69d-112">Aşağıdaki örnek, kullanımını gösterir. `while` deyimi.</span><span class="sxs-lookup"><span data-stu-id="4c69d-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="4c69d-113">Seçin **çalıştırma** örnek kodu çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="4c69d-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="4c69d-114">Bundan sonra bu kodu Değiştir ve yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c69d-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="4c69d-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="4c69d-115">C# language specification</span></span>

<span data-ttu-id="4c69d-116">Daha fazla bilgi için [while ifadesi](~/_csharplang/spec/statements.md#the-while-statement) bölümünü [ C# dil belirtimi](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4c69d-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c69d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c69d-117">See also</span></span>

- [<span data-ttu-id="4c69d-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="4c69d-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4c69d-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4c69d-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4c69d-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="4c69d-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4c69d-121">do deyimi</span><span class="sxs-lookup"><span data-stu-id="4c69d-121">do statement</span></span>](do.md)
