---
title: while - C# Referans
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: 481d3f7b87dbe874de010825c3c7f052e4bc33c0
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738750"
---
# <a name="while-c-reference"></a><span data-ttu-id="b431d-102">while (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b431d-102">while (C# Reference)</span></span>

<span data-ttu-id="b431d-103">`while` İfade bir deyim veya ifade bloğu yürütürken, belirli bir `true`Boolean ifadesi .'ye göre değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b431d-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="b431d-104">Bu ifade döngünün her yürütülmesinden önce `while` değerlendirildiği için, bir döngü sıfır veya daha fazla kez yürütür.</span><span class="sxs-lookup"><span data-stu-id="b431d-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="b431d-105">Bu, bir veya daha fazla kez yürüten [do](do.md) döngüsünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="b431d-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="b431d-106">`while` İfade bloğu içindeki herhangi bir noktada, [kesme](break.md) deyimini kullanarak döngüden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b431d-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="b431d-107">Continue deyimini kullanarak ifadenin `while` değerlendirilmesi [continue](continue.md) için doğrudan adım atabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b431d-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="b431d-108">İfade, `true`yürütme yi değerlendirirse, döngüdeki ilk ifadede devam eder.</span><span class="sxs-lookup"><span data-stu-id="b431d-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="b431d-109">Aksi takdirde, yürütme döngüden sonra ilk deyimde devam ediyor.</span><span class="sxs-lookup"><span data-stu-id="b431d-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="b431d-110">Ayrıca [goto](goto.md) `while` tarafından bir döngü çıkmak , [return](return.md), veya ifadeler [atmak.](throw.md)</span><span class="sxs-lookup"><span data-stu-id="b431d-110">You can also exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="b431d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b431d-111">Example</span></span>

<span data-ttu-id="b431d-112">Aşağıdaki örnek, `while` deyimin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b431d-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="b431d-113">Örnek kodu çalıştırmak için **Çalıştır'ı** seçin.</span><span class="sxs-lookup"><span data-stu-id="b431d-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="b431d-114">Bundan sonra kodu değiştirebilir ve yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b431d-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="b431d-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b431d-115">C# language specification</span></span>

<span data-ttu-id="b431d-116">Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [while deyimi](~/_csharplang/spec/statements.md#the-while-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b431d-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="b431d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b431d-117">See also</span></span>

- [<span data-ttu-id="b431d-118">C# Referans</span><span class="sxs-lookup"><span data-stu-id="b431d-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b431d-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b431d-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b431d-120">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="b431d-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b431d-121">deyimi yapmak</span><span class="sxs-lookup"><span data-stu-id="b431d-121">do statement</span></span>](do.md)
