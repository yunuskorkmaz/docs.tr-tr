---
ms.openlocfilehash: 4fc31f75e8f8cdd50abebd399d9749688e6faa5a
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065174"
---
### <a name="ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a><span data-ttu-id="87554-101">CA2015: MemoryManager’dan türetilen türler için sonlandırıcılar tanımlama\<T></span><span class="sxs-lookup"><span data-stu-id="87554-101">CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>

<span data-ttu-id="87554-102">.Net Code Analyzer Rule [CA2015](/visualstudio/code-quality/ca2015) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="87554-102">.NET code analyzer rule [CA2015](/visualstudio/code-quality/ca2015) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="87554-103">Sonlandırıcıyı tanımlayan herhangi bir tür için derleme uyarısı oluşturur <xref:System.Buffers.MemoryManager%601> .</span><span class="sxs-lookup"><span data-stu-id="87554-103">It produces a build warning for any types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span>

#### <a name="change-description"></a><span data-ttu-id="87554-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="87554-104">Change description</span></span>

<span data-ttu-id="87554-105">.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../docs/fundamentals/productivity/code-analysis.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="87554-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="87554-106">Bu kuralların bazıları varsayılan olarak [CA2015](/visualstudio/code-quality/ca2015)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="87554-106">Several of these rules are enabled, by default, including [CA2015](/visualstudio/code-quality/ca2015).</span></span> <span data-ttu-id="87554-107">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="87554-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="87554-108">Bir Sonlandırıcı tanımlatan türetilen kural CA2015 Flags türleri <xref:System.Buffers.MemoryManager%601> .</span><span class="sxs-lookup"><span data-stu-id="87554-108">Rule CA2015 flags types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span> <span data-ttu-id="87554-109">' Dan türetilen bir türe Sonlandırıcı eklemek <xref:System.Buffers.MemoryManager%601> , büyük olasılıkla bir hatanın göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="87554-109">Adding a finalizer to a type that derives from <xref:System.Buffers.MemoryManager%601> is likely an indication of a bug.</span></span> <span data-ttu-id="87554-110">Bir içinde elde edilen yerel bir kaynağın <xref:System.Span%601> temizlenmesinin yanı da hala tarafından kullanılıyor olması önerilir <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="87554-110">It suggests that a native resource that could have been obtained in a <xref:System.Span%601> is getting cleaned up, potentially while it's still in use by the <xref:System.Span%601>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="87554-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="87554-111">Version introduced</span></span>

<span data-ttu-id="87554-112">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="87554-112">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="87554-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="87554-113">Recommended action</span></span>

- <span data-ttu-id="87554-114">Sonlandırıcı tanımını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="87554-114">Remove the finalizer definition.</span></span> <span data-ttu-id="87554-115">Daha fazla bilgi için bkz. [CA2015](/visualstudio/code-quality/ca2015).</span><span class="sxs-lookup"><span data-stu-id="87554-115">For more information, see [CA2015](/visualstudio/code-quality/ca2015).</span></span>

- <span data-ttu-id="87554-116">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="87554-116">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="87554-117">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="87554-117">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="87554-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="87554-118">Category</span></span>

<span data-ttu-id="87554-119">Kod analizi</span><span class="sxs-lookup"><span data-stu-id="87554-119">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="87554-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="87554-120">Affected APIs</span></span>

<span data-ttu-id="87554-121">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="87554-121">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
