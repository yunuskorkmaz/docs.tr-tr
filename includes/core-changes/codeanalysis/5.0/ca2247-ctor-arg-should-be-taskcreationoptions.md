---
ms.openlocfilehash: 6bb3b11ef4e4cb6f6a039c97911b0acca862fe6f
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065186"
---
### <a name="ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a><span data-ttu-id="9a357-101">CA2247: TaskCompletionSource oluşturucusunun bağımsız değişkeni TaskCreationOptions değeri olmalıdır</span><span class="sxs-lookup"><span data-stu-id="9a357-101">CA2247: Argument to TaskCompletionSource constructor should be TaskCreationOptions value</span></span>

<span data-ttu-id="9a357-102">.Net Code Analyzer Rule [CA2247](/visualstudio/code-quality/ca2247) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="9a357-102">.NET code analyzer rule [CA2247](/visualstudio/code-quality/ca2247) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="9a357-103"><xref:System.Threading.Tasks.TaskCompletionSource%601>Türünde bir bağımsız değişken geçiren oluşturucuya yapılan çağrılar için bir derleme uyarısı oluşturur <xref:System.Threading.Tasks.TaskContinuationOptions> .</span><span class="sxs-lookup"><span data-stu-id="9a357-103">It produces a build warning for calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9a357-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="9a357-104">Change description</span></span>

<span data-ttu-id="9a357-105">.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../docs/fundamentals/productivity/code-analysis.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="9a357-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="9a357-106">Bu kuralların bazıları varsayılan olarak [CA2247](/visualstudio/code-quality/ca2247)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="9a357-106">Several of these rules are enabled, by default, including [CA2247](/visualstudio/code-quality/ca2247).</span></span> <span data-ttu-id="9a357-107">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="9a357-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="9a357-108">Rule CA2247, <xref:System.Threading.Tasks.TaskCompletionSource%601> türünde bir bağımsız değişken geçiren oluşturucuya yapılan çağrıları bulur <xref:System.Threading.Tasks.TaskContinuationOptions> .</span><span class="sxs-lookup"><span data-stu-id="9a357-108">Rule CA2247 finds calls to the <xref:System.Threading.Tasks.TaskCompletionSource%601> constructor that pass an argument of type <xref:System.Threading.Tasks.TaskContinuationOptions>.</span></span> <span data-ttu-id="9a357-109"><xref:System.Threading.Tasks.TaskCompletionSource%601>Türün bir değeri kabul eden bir oluşturucusu <xref:System.Threading.Tasks.TaskCreationOptions> ve öğesini kabul eden başka bir Oluşturucu vardır <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="9a357-109">The <xref:System.Threading.Tasks.TaskCompletionSource%601> type has a constructor that accepts a <xref:System.Threading.Tasks.TaskCreationOptions> value, and another constructor that accepts an <xref:System.Object>.</span></span> <span data-ttu-id="9a357-110">Yanlışlıkla bir değer yerine bir <xref:System.Threading.Tasks.TaskContinuationOptions> değer geçirirseniz <xref:System.Threading.Tasks.TaskCreationOptions> , parametresine sahip Oluşturucu <xref:System.Object> çalışma zamanında çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9a357-110">If you accidentally pass a <xref:System.Threading.Tasks.TaskContinuationOptions> value instead of a <xref:System.Threading.Tasks.TaskCreationOptions> value, the constructor with the <xref:System.Object> parameter is called at run time.</span></span> <span data-ttu-id="9a357-111">Kodunuz derleyip çalıştırılır, ancak amaçlanan davranışa sahip olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="9a357-111">Your code will compile and run but won't have the intended behavior.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9a357-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="9a357-112">Version introduced</span></span>

<span data-ttu-id="9a357-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="9a357-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9a357-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="9a357-114">Recommended action</span></span>

- <span data-ttu-id="9a357-115"><xref:System.Threading.Tasks.TaskContinuationOptions>Bağımsız değişkenini karşılık gelen değerle değiştirin <xref:System.Threading.Tasks.TaskCreationOptions> .</span><span class="sxs-lookup"><span data-stu-id="9a357-115">Replace the <xref:System.Threading.Tasks.TaskContinuationOptions> argument with the corresponding <xref:System.Threading.Tasks.TaskCreationOptions> value.</span></span> <span data-ttu-id="9a357-116">Kodunuzda bir hatayı neredeyse her zaman vurgudığından, bu uyarıyı göstermez.</span><span class="sxs-lookup"><span data-stu-id="9a357-116">Do not suppress this warning, since it almost always highlights a bug in your code.</span></span> <span data-ttu-id="9a357-117">Daha fazla bilgi için bkz. [CA2247](/visualstudio/code-quality/ca2247).</span><span class="sxs-lookup"><span data-stu-id="9a357-117">For more information, see [CA2247](/visualstudio/code-quality/ca2247).</span></span>

- <span data-ttu-id="9a357-118">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9a357-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="9a357-119">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="9a357-119">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="9a357-120">Kategori</span><span class="sxs-lookup"><span data-stu-id="9a357-120">Category</span></span>

<span data-ttu-id="9a357-121">Kod analizi</span><span class="sxs-lookup"><span data-stu-id="9a357-121">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9a357-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="9a357-122">Affected APIs</span></span>

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

#### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

-->
