---
title: do (C# Başvurusu)
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 89c13f5b547c13052e229ff6eb3a39ae5babce41
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185843"
---
# <a name="do-c-reference"></a><span data-ttu-id="387e8-102">do (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="387e8-102">do (C# Reference)</span></span>

<span data-ttu-id="387e8-103">`do` Deyimi, bir deyimi veya bir deyimler bloğunu belirtilen bir Boole ifadesi değerlendirilir sırada yürütür `true`.</span><span class="sxs-lookup"><span data-stu-id="387e8-103">The `do` statement executes a statement or a block of statements while a specified boolean expression evaluates to `true`.</span></span> <span data-ttu-id="387e8-104">Bu ifade döngünün her yürütülmesi değerlendirilir çünkü bir `do-while` bir veya daha fazla kez döngü yürütür.</span><span class="sxs-lookup"><span data-stu-id="387e8-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="387e8-105">Bu farklıdır [sırada](while.md) döngü, sıfır veya daha fazla kez yürütülür.</span><span class="sxs-lookup"><span data-stu-id="387e8-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="387e8-106">Herhangi bir anda işaret içinde `do` deyim bloğunu kullanarak döngü dışında bozabilir [sonu](break.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="387e8-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="387e8-107">Değerlendirme için doğrudan geçebilirsiniz `while` kullanarak ifade [devam](continue.md) deyimi.</span><span class="sxs-lookup"><span data-stu-id="387e8-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="387e8-108">İfade değerlendirme sonucu `true`, yürütme Döngüdeki ilk deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="387e8-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="387e8-109">Aksi takdirde, yürütme döngüyü sonra ilk deyimde devam eder.</span><span class="sxs-lookup"><span data-stu-id="387e8-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="387e8-110">Ayrıca çıkış bir `do-while` tarafından döngü [goto](goto.md), [dönüş](return.md), veya [throw](throw.md) deyimleri.</span><span class="sxs-lookup"><span data-stu-id="387e8-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="387e8-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="387e8-111">Example</span></span>

<span data-ttu-id="387e8-112">Aşağıdaki örnek, kullanımını gösterir. `do` deyimi.</span><span class="sxs-lookup"><span data-stu-id="387e8-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="387e8-113">Seçin **çalıştırma** örnek kodu çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="387e8-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="387e8-114">Bundan sonra bu kodu Değiştir ve yeniden çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="387e8-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="387e8-115">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="387e8-115">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="387e8-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="387e8-116">See also</span></span>

- [<span data-ttu-id="387e8-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="387e8-117">C# Reference</span></span>](../index.md)  
- [<span data-ttu-id="387e8-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="387e8-118">C# Programming Guide</span></span>](../../programming-guide/index.md)  
- [<span data-ttu-id="387e8-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="387e8-119">C# Keywords</span></span>](index.md)  
- [<span data-ttu-id="387e8-120">do-while Deyimi (C++)</span><span class="sxs-lookup"><span data-stu-id="387e8-120">do-while Statement (C++)</span></span>](/cpp/cpp/do-while-statement-cpp)  
- [<span data-ttu-id="387e8-121">Yineleme Deyimleri</span><span class="sxs-lookup"><span data-stu-id="387e8-121">Iteration Statements</span></span>](iteration-statements.md)  
- [<span data-ttu-id="387e8-122">while deyimi</span><span class="sxs-lookup"><span data-stu-id="387e8-122">while statement</span></span>](while.md)  
