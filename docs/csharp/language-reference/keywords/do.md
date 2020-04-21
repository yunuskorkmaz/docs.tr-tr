---
title: do - C# Referans
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 1d4323366e567dab4b27b07803d0c06e731611ce
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738903"
---
# <a name="do-c-reference"></a><span data-ttu-id="9d07c-102">do (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9d07c-102">do (C# Reference)</span></span>

<span data-ttu-id="9d07c-103">`do` İfade bir deyim veya ifade bloğu yürütürken, belirli bir `true`Boolean ifadesi .'ye göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9d07c-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="9d07c-104">Bu ifade döngünün her yürütülmesinden sonra `do-while` değerlendirildiği için, bir döngü bir veya daha fazla kez yürütür.</span><span class="sxs-lookup"><span data-stu-id="9d07c-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="9d07c-105">Bu, sıfır veya daha fazla kez yürüten [while](while.md) döngüsünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="9d07c-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="9d07c-106">`do` İfade bloğu içindeki herhangi bir noktada, [kesme](break.md) deyimini kullanarak döngüden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d07c-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="9d07c-107">Continue deyimini kullanarak ifadenin `while` değerlendirilmesi [continue](continue.md) için doğrudan adım atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d07c-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="9d07c-108">İfade, `true`yürütme yi değerlendirirse, döngüdeki ilk ifadede devam eder.</span><span class="sxs-lookup"><span data-stu-id="9d07c-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="9d07c-109">Aksi takdirde, yürütme döngüden sonra ilk deyimde devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="9d07c-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="9d07c-110">Ayrıca [goto](goto.md) `do-while` tarafından bir döngü çıkmak , [return](return.md), veya ifadeler [atmak.](throw.md)</span><span class="sxs-lookup"><span data-stu-id="9d07c-110">You can also exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="9d07c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="9d07c-111">Example</span></span>

<span data-ttu-id="9d07c-112">Aşağıdaki örnek, `do` deyimin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d07c-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="9d07c-113">Örnek kodu çalıştırmak için **Çalıştır'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="9d07c-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="9d07c-114">Bundan sonra kodu değiştirebilir ve yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d07c-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="9d07c-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="9d07c-115">C# language specification</span></span>

<span data-ttu-id="9d07c-116">Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [do deyimi](~/_csharplang/spec/statements.md#the-do-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9d07c-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="9d07c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d07c-117">See also</span></span>

- [<span data-ttu-id="9d07c-118">C# Referans</span><span class="sxs-lookup"><span data-stu-id="9d07c-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9d07c-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9d07c-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9d07c-120">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="9d07c-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9d07c-121">ifade ederken</span><span class="sxs-lookup"><span data-stu-id="9d07c-121">while statement</span></span>](while.md)
