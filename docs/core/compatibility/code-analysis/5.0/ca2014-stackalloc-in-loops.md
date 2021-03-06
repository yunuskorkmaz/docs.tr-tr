---
title: 'Son değişiklik: CA2014: Döngülerde stackalloc kullanmayın'
description: Kod Analizi kuralı CA2014 'nin etkinleştirilmesi nedeniyle .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: ac17c8ee588576947e21618a55c0eea883aa37ad
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257784"
---
# <a name="warning-ca2014-do-not-use-stackalloc-in-loops"></a><span data-ttu-id="2e346-103">Uyarı CA2014: Döngülerde stackalloc kullanmayın</span><span class="sxs-lookup"><span data-stu-id="2e346-103">Warning CA2014: Do not use stackalloc in loops</span></span>

<span data-ttu-id="2e346-104">.Net Code Analyzer Rule [CA2014](/visualstudio/code-quality/ca2014) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="2e346-104">.NET code analyzer rule [CA2014](/visualstudio/code-quality/ca2014) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="2e346-105">Bir döngü içinde [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) ifadesinin kullanıldığı herhangi bir C# kodu için derleme uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2e346-105">It produces a build warning for any C# code where a [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) expression is used inside a loop.</span></span>

## <a name="change-description"></a><span data-ttu-id="2e346-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="2e346-106">Change description</span></span>

<span data-ttu-id="2e346-107">.NET 5 ' den başlayarak .NET SDK [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="2e346-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="2e346-108">Bu kuralların bazıları varsayılan olarak [CA2014](/visualstudio/code-quality/ca2014)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="2e346-108">Several of these rules are enabled, by default, including [CA2014](/visualstudio/code-quality/ca2014).</span></span> <span data-ttu-id="2e346-109">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="2e346-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="2e346-110">Rule CA2014, bir [stackalloc ifadesinin](../../../../csharp/language-reference/operators/stackalloc.md) bir döngü Içinde kullanıldığı C# kodunu arar.</span><span class="sxs-lookup"><span data-stu-id="2e346-110">Rule CA2014 looks for C# code where a [stackalloc expression](../../../../csharp/language-reference/operators/stackalloc.md) is used inside a loop.</span></span> <span data-ttu-id="2e346-111">[stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) , geçerli yığın çerçevesindeki belleği ayırır.</span><span class="sxs-lookup"><span data-stu-id="2e346-111">[stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) allocates memory from the current stack frame.</span></span> <span data-ttu-id="2e346-112">Geçerli yöntem çağrısı döndürülünceye kadar bellek serbest bırakılana kadar, yığın taşlarına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="2e346-112">The memory isn't released until the current method call returns, which can lead to stack overflows.</span></span> <span data-ttu-id="2e346-113">Yığın taşması özel durumlarını yakalayamayacak, yığın taşması durumunda uygulama sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="2e346-113">Because you can't catch stack overflow exceptions, the app will terminate in case of stack overflow.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="2e346-114">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="2e346-114">Version introduced</span></span>

<span data-ttu-id="2e346-115">5.0</span><span class="sxs-lookup"><span data-stu-id="2e346-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="2e346-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="2e346-116">Recommended action</span></span>

- <span data-ttu-id="2e346-117">Döngüler içinde [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="2e346-117">Avoid using [stackalloc](../../../../csharp/language-reference/operators/stackalloc.md) inside loops.</span></span> <span data-ttu-id="2e346-118">Bellek bloğunu döngü dışında ayırın ve döngü içinde yeniden kullanın.</span><span class="sxs-lookup"><span data-stu-id="2e346-118">Allocate the memory block outside the loop and reuse it inside the loop.</span></span> <span data-ttu-id="2e346-119">Daha fazla bilgi için bkz. [CA2014](/visualstudio/code-quality/ca2014).</span><span class="sxs-lookup"><span data-stu-id="2e346-119">For more information, see [CA2014](/visualstudio/code-quality/ca2014).</span></span>

- <span data-ttu-id="2e346-120">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2e346-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="2e346-121">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="2e346-121">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="2e346-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2e346-122">Affected APIs</span></span>

<span data-ttu-id="2e346-123">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="2e346-123">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
