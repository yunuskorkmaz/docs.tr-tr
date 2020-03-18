---
title: while - C# Referans
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: eb9aa2ea8d6b1c96e0be7d377f7c047194b598de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712799"
---
# <a name="while-c-reference"></a><span data-ttu-id="ad47b-102">while (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="ad47b-102">while (C# Reference)</span></span>

<span data-ttu-id="ad47b-103">`while` İfade bir deyim veya ifade bloğu yürütürken, belirli bir `true`Boolean ifadesi .'ye göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ad47b-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="ad47b-104">Bu ifade döngünün her yürütülmesinden önce `while` değerlendirildiği için, bir döngü sıfır veya daha fazla kez yürütür.</span><span class="sxs-lookup"><span data-stu-id="ad47b-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="ad47b-105">Bu, bir veya daha fazla kez yürüten [do](do.md) döngüsünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="ad47b-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="ad47b-106">`while` İfade bloğu içindeki herhangi bir noktada, [kesme](break.md) deyimini kullanarak döngüden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad47b-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="ad47b-107">Continue deyimini kullanarak ifadenin `while` değerlendirilmesi [continue](continue.md) için doğrudan adım atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad47b-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="ad47b-108">İfade, `true`yürütme yi değerlendirirse, döngüdeki ilk ifadede devam eder.</span><span class="sxs-lookup"><span data-stu-id="ad47b-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="ad47b-109">Aksi takdirde, yürütme döngüden sonra ilk deyimde devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="ad47b-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="ad47b-110">Ayrıca `while` [goto,](goto.md) [return](return.md)veya [atmak](throw.md) ifadeleri tarafından bir döngü çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad47b-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="ad47b-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="ad47b-111">Example</span></span>

<span data-ttu-id="ad47b-112">Aşağıdaki örnek, `while` deyimin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ad47b-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="ad47b-113">Örnek kodu çalıştırmak için **Çalıştır'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="ad47b-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="ad47b-114">Bundan sonra kodu değiştirebilir ve yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ad47b-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="ad47b-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="ad47b-115">C# language specification</span></span>

<span data-ttu-id="ad47b-116">Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [while deyimi](~/_csharplang/spec/statements.md#the-while-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="ad47b-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad47b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ad47b-117">See also</span></span>

- [<span data-ttu-id="ad47b-118">C# Referans</span><span class="sxs-lookup"><span data-stu-id="ad47b-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ad47b-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ad47b-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ad47b-120">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="ad47b-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ad47b-121">deyimi yapmak</span><span class="sxs-lookup"><span data-stu-id="ad47b-121">do statement</span></span>](do.md)
