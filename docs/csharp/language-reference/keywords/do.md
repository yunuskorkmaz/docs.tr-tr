---
title: do-C# başvurusu
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: d75dd816278a876fa05d133e5eb189d606300a5c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401933"
---
# <a name="do-c-reference"></a><span data-ttu-id="72e05-102">do (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="72e05-102">do (C# Reference)</span></span>

<span data-ttu-id="72e05-103">`do`Deyimi, belirtilen bir Boole ifadesi olarak değerlendirilen bir deyimi veya bir deyim bloğunu yürütür `true` .</span><span class="sxs-lookup"><span data-stu-id="72e05-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="72e05-104">Bu ifade döngünün her yürütülmesinden sonra değerlendirildiğinden bir `do-while` döngü bir veya daha fazla kez yürütülür.</span><span class="sxs-lookup"><span data-stu-id="72e05-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="72e05-105">Bu, sıfır veya daha fazla kez yürütülen [while](while.md) döngüsünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="72e05-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="72e05-106">Deyimdeki herhangi bir noktada `do` [Break](break.md) ifadesini kullanarak döngünün dışına kesebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72e05-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="72e05-107">`while` [Continue](continue.md) deyimini kullanarak doğrudan ifadenin değerlendirmesine adım adım ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72e05-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="72e05-108">İfade olarak değerlendirilirse `true` , yürütme döngüsünde ilk deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="72e05-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="72e05-109">Aksi halde, yürütme döngüden sonraki ilk ifadede devam eder.</span><span class="sxs-lookup"><span data-stu-id="72e05-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="72e05-110">Ayrıca `do-while` [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir döngüden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72e05-110">You can also exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="72e05-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="72e05-111">Example</span></span>

<span data-ttu-id="72e05-112">Aşağıdaki örnek, ifadesinin kullanımını gösterir `do` .</span><span class="sxs-lookup"><span data-stu-id="72e05-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="72e05-113">Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="72e05-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="72e05-114">Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="72e05-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](snippets/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="72e05-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="72e05-115">C# language specification</span></span>

<span data-ttu-id="72e05-116">Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [Do deyimin](~/_csharplang/spec/statements.md#the-do-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="72e05-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="72e05-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72e05-117">See also</span></span>

- [<span data-ttu-id="72e05-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="72e05-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="72e05-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="72e05-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="72e05-120">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="72e05-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="72e05-121">while deyimi</span><span class="sxs-lookup"><span data-stu-id="72e05-121">while statement</span></span>](while.md)
