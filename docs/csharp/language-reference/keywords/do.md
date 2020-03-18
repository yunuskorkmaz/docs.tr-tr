---
title: do - C# Referans
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 38224ce70c19ff67ad80b99d3da52155849f1341
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713595"
---
# <a name="do-c-reference"></a><span data-ttu-id="d10a8-102">do (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d10a8-102">do (C# Reference)</span></span>

<span data-ttu-id="d10a8-103">`do` İfade bir deyim veya ifade bloğu yürütürken, belirli bir `true`Boolean ifadesi .'ye göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="d10a8-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="d10a8-104">Bu ifade döngünün her yürütülmesinden sonra `do-while` değerlendirildiği için, bir döngü bir veya daha fazla kez yürütür.</span><span class="sxs-lookup"><span data-stu-id="d10a8-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="d10a8-105">Bu, sıfır veya daha fazla kez yürüten [while](while.md) döngüsünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="d10a8-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="d10a8-106">`do` İfade bloğu içindeki herhangi bir noktada, [kesme](break.md) deyimini kullanarak döngüden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d10a8-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="d10a8-107">Continue deyimini kullanarak ifadenin `while` değerlendirilmesi [continue](continue.md) için doğrudan adım atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d10a8-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="d10a8-108">İfade, `true`yürütme yi değerlendirirse, döngüdeki ilk ifadede devam eder.</span><span class="sxs-lookup"><span data-stu-id="d10a8-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="d10a8-109">Aksi takdirde, yürütme döngüden sonra ilk deyimde devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="d10a8-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="d10a8-110">Ayrıca `do-while` [goto,](goto.md) [return](return.md)veya [atmak](throw.md) ifadeleri tarafından bir döngü çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d10a8-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="d10a8-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="d10a8-111">Example</span></span>

<span data-ttu-id="d10a8-112">Aşağıdaki örnek, `do` deyimin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d10a8-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="d10a8-113">Örnek kodu çalıştırmak için **Çalıştır'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="d10a8-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="d10a8-114">Bundan sonra kodu değiştirebilir ve yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d10a8-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="d10a8-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="d10a8-115">C# language specification</span></span>

<span data-ttu-id="d10a8-116">Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [do deyimi](~/_csharplang/spec/statements.md#the-do-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d10a8-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="d10a8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d10a8-117">See also</span></span>

- [<span data-ttu-id="d10a8-118">C# Referans</span><span class="sxs-lookup"><span data-stu-id="d10a8-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d10a8-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d10a8-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d10a8-120">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="d10a8-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d10a8-121">ifade ederken</span><span class="sxs-lookup"><span data-stu-id="d10a8-121">while statement</span></span>](while.md)
