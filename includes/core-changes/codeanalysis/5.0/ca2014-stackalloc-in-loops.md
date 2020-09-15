---
ms.openlocfilehash: a51160a8ab5a4b437e51db31def577f8d8f50182
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065185"
---
### <a name="ca2014-do-not-use-stackalloc-in-loops"></a><span data-ttu-id="c54b1-101">CA2014: Döngülerde stackalloc kullanmayın</span><span class="sxs-lookup"><span data-stu-id="c54b1-101">CA2014: Do not use stackalloc in loops</span></span>

<span data-ttu-id="c54b1-102">.Net Code Analyzer Rule [CA2014](/visualstudio/code-quality/ca2014) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="c54b1-102">.NET code analyzer rule [CA2014](/visualstudio/code-quality/ca2014) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="c54b1-103">Bir döngü içinde [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) ifadesinin kullanıldığı herhangi bir C# kodu için derleme uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c54b1-103">It produces a build warning for any C# code where a [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) expression is used inside a loop.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c54b1-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="c54b1-104">Change description</span></span>

<span data-ttu-id="c54b1-105">.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../docs/fundamentals/productivity/code-analysis.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="c54b1-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="c54b1-106">Bu kuralların bazıları varsayılan olarak [CA2014](/visualstudio/code-quality/ca2014)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="c54b1-106">Several of these rules are enabled, by default, including [CA2014](/visualstudio/code-quality/ca2014).</span></span> <span data-ttu-id="c54b1-107">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="c54b1-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="c54b1-108">Rule CA2014, bir [stackalloc ifadesinin](../../../../docs/csharp/language-reference/operators/stackalloc.md) bir döngü Içinde kullanıldığı C# kodunu arar.</span><span class="sxs-lookup"><span data-stu-id="c54b1-108">Rule CA2014 looks for C# code where a [stackalloc expression](../../../../docs/csharp/language-reference/operators/stackalloc.md) is used inside a loop.</span></span> <span data-ttu-id="c54b1-109">[stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) , geçerli yığın çerçevesindeki belleği ayırır.</span><span class="sxs-lookup"><span data-stu-id="c54b1-109">[stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) allocates memory from the current stack frame.</span></span> <span data-ttu-id="c54b1-110">Geçerli yöntem çağrısı döndürülünceye kadar bellek serbest bırakılana kadar, yığın taşlarına yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="c54b1-110">The memory isn't released until the current method call returns, which can lead to stack overflows.</span></span> <span data-ttu-id="c54b1-111">Yığın taşması özel durumlarını yakalayamayacak, yığın taşması durumunda uygulama sonlandırılacak.</span><span class="sxs-lookup"><span data-stu-id="c54b1-111">Because you can't catch stack overflow exceptions, the app will terminate in case of stack overflow.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c54b1-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c54b1-112">Version introduced</span></span>

<span data-ttu-id="c54b1-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="c54b1-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c54b1-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c54b1-114">Recommended action</span></span>

- <span data-ttu-id="c54b1-115">Döngüler içinde [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="c54b1-115">Avoid using [stackalloc](../../../../docs/csharp/language-reference/operators/stackalloc.md) inside loops.</span></span> <span data-ttu-id="c54b1-116">Bellek bloğunu döngü dışında ayırın ve döngü içinde yeniden kullanın.</span><span class="sxs-lookup"><span data-stu-id="c54b1-116">Allocate the memory block outside the loop and reuse it inside the loop.</span></span> <span data-ttu-id="c54b1-117">Daha fazla bilgi için bkz. [CA2014](/visualstudio/code-quality/ca2014).</span><span class="sxs-lookup"><span data-stu-id="c54b1-117">For more information, see [CA2014](/visualstudio/code-quality/ca2014).</span></span>

- <span data-ttu-id="c54b1-118">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c54b1-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="c54b1-119">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="c54b1-119">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="c54b1-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="c54b1-120">Category</span></span>

<span data-ttu-id="c54b1-121">Kod analizi</span><span class="sxs-lookup"><span data-stu-id="c54b1-121">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c54b1-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c54b1-122">Affected APIs</span></span>

<span data-ttu-id="c54b1-123">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="c54b1-123">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
