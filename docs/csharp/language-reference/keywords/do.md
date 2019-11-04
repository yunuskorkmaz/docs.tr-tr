---
title: yapılacak C# başvuru
ms.custom: seodec18
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 08f964b1e5c78a429dc50f81398d840f58ec4b13
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422844"
---
# <a name="do-c-reference"></a><span data-ttu-id="b4676-102">do (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b4676-102">do (C# Reference)</span></span>

<span data-ttu-id="b4676-103">`do` deyimi, belirtilen bir Boole ifadesi `true`değerlendirirken bir deyimi veya bir deyim bloğunu yürütür.</span><span class="sxs-lookup"><span data-stu-id="b4676-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="b4676-104">Bu ifade döngünün her yürütülmesinden sonra değerlendirildiğinden, bir `do-while` döngüsü bir veya daha fazla kez yürütülür.</span><span class="sxs-lookup"><span data-stu-id="b4676-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="b4676-105">Bu, sıfır veya daha fazla kez yürütülen [while](while.md) döngüsünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="b4676-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="b4676-106">`do` bildiri bloğunun içindeki herhangi bir noktada [Break](break.md) ifadesini kullanarak döngünün dışına kesebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4676-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="b4676-107">[Continue](continue.md) deyimini kullanarak `while` ifadesinin değerlendirmesine doğrudan ilerleyerek.</span><span class="sxs-lookup"><span data-stu-id="b4676-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="b4676-108">İfade `true`olarak değerlendirilirse, yürütme döngüdeki ilk deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="b4676-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="b4676-109">Aksi halde, yürütme döngüden sonraki ilk ifadede devam eder.</span><span class="sxs-lookup"><span data-stu-id="b4676-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="b4676-110">Ayrıca, [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir `do-while` döngüsünden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4676-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="b4676-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="b4676-111">Example</span></span>

<span data-ttu-id="b4676-112">Aşağıdaki örnek `do` deyimin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="b4676-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="b4676-113">Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="b4676-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="b4676-114">Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b4676-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="b4676-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="b4676-115">C# language specification</span></span>

<span data-ttu-id="b4676-116">Daha fazla bilgi için, [ C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [Do deyimin](~/_csharplang/spec/statements.md#the-do-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b4676-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="b4676-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4676-117">See also</span></span>

- [<span data-ttu-id="b4676-118">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="b4676-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b4676-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b4676-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b4676-120">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="b4676-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="b4676-121">while ekstresi</span><span class="sxs-lookup"><span data-stu-id="b4676-121">while statement</span></span>](while.md)
