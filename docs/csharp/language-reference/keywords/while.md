---
title: while-C# başvurusu
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: af616c2381b993f86296cbfa43a01ba2f9e000c2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401868"
---
# <a name="while-c-reference"></a><span data-ttu-id="f9b23-102">while (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f9b23-102">while (C# Reference)</span></span>

<span data-ttu-id="f9b23-103">`while`Deyimi, belirtilen bir Boole ifadesi olarak değerlendirilen bir deyimi veya bir deyim bloğunu yürütür `true` .</span><span class="sxs-lookup"><span data-stu-id="f9b23-103">The `while` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="f9b23-104">Bu ifade döngünün her yürütmeden önce değerlendirildiğinden, bir `while` döngü sıfır veya daha fazla kez yürütülür.</span><span class="sxs-lookup"><span data-stu-id="f9b23-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="f9b23-105">Bu, bir veya daha fazla kez yürütülen [Do](do.md) döngüsünden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="f9b23-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="f9b23-106">Deyimdeki herhangi bir noktada `while` [Break](break.md) ifadesini kullanarak döngünün dışına kesebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9b23-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="f9b23-107">`while` [Continue](continue.md) deyimini kullanarak doğrudan ifadenin değerlendirmesine adım adım ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9b23-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="f9b23-108">İfade olarak değerlendirilirse `true` , yürütme döngüsünde ilk deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="f9b23-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="f9b23-109">Aksi halde, yürütme döngüden sonraki ilk ifadede devam eder.</span><span class="sxs-lookup"><span data-stu-id="f9b23-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="f9b23-110">Ayrıca `while` [goto](goto.md), [Return](return.md)veya [throw](throw.md) deyimleriyle bir döngüden çıkabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9b23-110">You can also exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="f9b23-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9b23-111">Example</span></span>

<span data-ttu-id="f9b23-112">Aşağıdaki örnek, ifadesinin kullanımını gösterir `while` .</span><span class="sxs-lookup"><span data-stu-id="f9b23-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="f9b23-113">Örnek kodu çalıştırmak için **Çalıştır** ' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="f9b23-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="f9b23-114">Bundan sonra kodu değiştirip yeniden çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f9b23-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](snippets/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="f9b23-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f9b23-115">C# language specification</span></span>

<span data-ttu-id="f9b23-116">Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [while ifadesinin](~/_csharplang/spec/statements.md#the-while-statement) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="f9b23-116">For more information, see [The while statement](~/_csharplang/spec/statements.md#the-while-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="f9b23-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f9b23-117">See also</span></span>

- [<span data-ttu-id="f9b23-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f9b23-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f9b23-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f9b23-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f9b23-120">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f9b23-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f9b23-121">do ekstresi</span><span class="sxs-lookup"><span data-stu-id="f9b23-121">do statement</span></span>](do.md)
