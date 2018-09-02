---
title: while (C# Başvurusu)
ms.date: 05/28/2018
f1_keywords:
- while_CSharpKeyword
- while
helpviewer_keywords:
- while keyword [C#]
ms.assetid: 72a0765c-6852-4aca-b327-4a11cb7f5c59
ms.openlocfilehash: e3e9493b5371fbd6f53a779ba73743efc6d6e05b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43390030"
---
# <a name="while-c-reference"></a><span data-ttu-id="3475c-102">while (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3475c-102">while (C# Reference)</span></span>

<span data-ttu-id="3475c-103">`while` Deyimi, bir deyimi veya bir deyimler bloğunu belirtilen bir Boole ifadesi değerlendirilir sırada yürütür `true`.</span><span class="sxs-lookup"><span data-stu-id="3475c-103">The `while` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span> <span data-ttu-id="3475c-104">Bu ifade döngünün her yürütmesinden önce değerlendirilir çünkü bir `while` sıfır veya daha fazla kez döngü yürütür.</span><span class="sxs-lookup"><span data-stu-id="3475c-104">Because that expression is evaluated before each execution of the loop, a `while` loop executes zero or more times.</span></span> <span data-ttu-id="3475c-105">Bu farklıdır [yapmak](do.md) yürüten bir veya daha fazla kez döngü.</span><span class="sxs-lookup"><span data-stu-id="3475c-105">This differs from the [do](do.md) loop, which executes one or more times.</span></span>

<span data-ttu-id="3475c-106">Herhangi bir anda işaret içinde `while` deyim bloğunu kullanarak döngü dışında bozabilir [sonu](break.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="3475c-106">At any point within the `while` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="3475c-107">Değerlendirme için doğrudan geçebilirsiniz `while` kullanarak ifade [devam](continue.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="3475c-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="3475c-108">İfade değerlendirme sonucu `true`, yürütme Döngüdeki ilk deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="3475c-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="3475c-109">Aksi takdirde, yürütme döngüyü sonra ilk deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="3475c-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="3475c-110">Ayrıca çıkış bir `while` tarafından döngü [goto](goto.md), [dönüş](return.md), veya [throw](throw.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="3475c-110">You also can exit a `while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="3475c-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="3475c-111">Example</span></span>

<span data-ttu-id="3475c-112">Aşağıdaki örnek, kullanımını gösterir. `while` deyimi.</span><span class="sxs-lookup"><span data-stu-id="3475c-112">The following example shows the usage of the `while` statement.</span></span> <span data-ttu-id="3475c-113">Seçin **çalıştırma** örnek kodu çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="3475c-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="3475c-114">Bundan sonra bu kodu Değiştir ve yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="3475c-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[while loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="3475c-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3475c-115">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="3475c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3475c-116">See also</span></span>

- [<span data-ttu-id="3475c-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3475c-117">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="3475c-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3475c-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="3475c-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3475c-119">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="3475c-120">while Deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="3475c-120">while Statement (C++)</span></span>](/cpp/cpp/while-statement-cpp)  
- [<span data-ttu-id="3475c-121">Yineleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="3475c-121">Iteration Statements</span></span>](iteration-statements.md)  
- [<span data-ttu-id="3475c-122">do deyimi</span><span class="sxs-lookup"><span data-stu-id="3475c-122">do statement</span></span>](do.md)  
