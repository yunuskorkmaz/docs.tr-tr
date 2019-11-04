---
title: while- C# Reference
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: ab0a8ba0b724757b4f239daf1d3319b989c4531a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73421912"
---
# <a name="while-c-reference"></a><span data-ttu-id="c3691-102">while (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c3691-102">while (C# Reference)</span></span>

<span data-ttu-id="c3691-103">`while` deyimi, belirtilen bir Boole ifadesi `true`değerlendirirken bir deyimi veya bir deyim bloğunu yürütür.</span><span class="sxs-lookup"><span data-stu-id="c3691-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="c3691-104">Bu ifade döngünün her yürütmeden önce değerlendirildiğinden `while` döngüsü sıfır veya daha fazla kez yürütülür.</span><span class="sxs-lookup"><span data-stu-id="c3691-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="c3691-105">Bu, bir veya daha fazla kez yürütülen [Do](do.md) döngüsünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="c3691-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="c3691-106">`while` bildiri bloğunun içindeki herhangi bir noktada [Break](break.md) ifadesini kullanarak döngünün dışına kesebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3691-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="c3691-107">[Continue](continue.md) deyimini kullanarak `while` ifadesinin değerlendirmesine doğrudan ilerleyerek.</span><span class="sxs-lookup"><span data-stu-id="c3691-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="c3691-108">İfade `true`olarak değerlendirilirse, yürütme döngüdeki ilk deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="c3691-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="c3691-109">Aksi halde, yürütme döngüden sonraki ilk ifadede devam eder.</span><span class="sxs-lookup"><span data-stu-id="c3691-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="c3691-110">Ayrıca, [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir `while` döngüsünden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3691-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="c3691-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="c3691-111">Example</span></span>

<span data-ttu-id="c3691-112">Aşağıdaki örnek `while` deyimin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c3691-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="c3691-113">Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="c3691-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="c3691-114">Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c3691-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="c3691-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="c3691-115">C# language specification</span></span>

<span data-ttu-id="c3691-116">Daha fazla bilgi için, [ C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [while ifadesinin](~/_csharplang/spec/statements.md#the-while-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="c3691-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3691-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3691-117">See also</span></span>

- [<span data-ttu-id="c3691-118">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="c3691-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c3691-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c3691-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c3691-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c3691-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c3691-121">do ekstresi</span><span class="sxs-lookup"><span data-stu-id="c3691-121">do statement</span></span>](do.md)
