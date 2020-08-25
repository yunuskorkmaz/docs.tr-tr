---
ms.openlocfilehash: 87f9cc03f334233ef286abd11e6f5ff82d7988c2
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811359"
---
### <a name="ca1831-use-asspan-or-asmemory-instead-of-range-based-indexer"></a><span data-ttu-id="7867f-101">CA1831 Aralık tabanlı dizin oluşturucu yerine AsSpan veya AsMemory kullanın</span><span class="sxs-lookup"><span data-stu-id="7867f-101">CA1831 Use AsSpan or AsMemory instead of Range-based indexer</span></span>

<span data-ttu-id="7867f-102">.Net Code Analyzer Rule [CA1831](/visualstudio/code-quality/ca1831) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="7867f-102">.NET code analyzer rule [CA1831](/visualstudio/code-quality/ca1831) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="7867f-103">Bir <xref:System.Range> dizede kullanılan bir dizin oluşturucunun kullanıldığı, ancak herhangi bir kopyanın istendiği herhangi bir kod için derleme uyarısı üretir.</span><span class="sxs-lookup"><span data-stu-id="7867f-103">It produces a build warning for any code where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7867f-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="7867f-104">Change description</span></span>

<span data-ttu-id="7867f-105">.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../docs/fundamentals/productivity/code-analysis.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="7867f-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="7867f-106">Bu kuralların bazıları varsayılan olarak [CA1831](/visualstudio/code-quality/ca1831)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="7867f-106">Several of these rules are enabled, by default, including [CA1831](/visualstudio/code-quality/ca1831).</span></span> <span data-ttu-id="7867f-107">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="7867f-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="7867f-108">Rule CA1831 <xref:System.Range> , bir dize üzerinde bir-tabanlı dizin oluşturucunun kullanıldığı, ancak hiçbir kopyanın istendiği örnekleri bulur.</span><span class="sxs-lookup"><span data-stu-id="7867f-108">Rule CA1831 finds instances where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span> <span data-ttu-id="7867f-109"><xref:System.Range>-Tabanlı dizin oluşturucu örtük bir tür oluşturmak için doğrudan bir dize üzerinde kullanılıyorsa, dizenin istenen bölümünün gereksiz bir kopyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7867f-109">If the <xref:System.Range>-based indexer is used directly on a string to produce an implicit cast, then an unnecessary copy of the requested portion of the string is created.</span></span> <span data-ttu-id="7867f-110">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7867f-110">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

<span data-ttu-id="7867f-111">CA1831 <xref:System.Range> , bunun yerine dizenin bir *aralığında* tabanlı dizin oluşturucuyu kullanmayı önerir.</span><span class="sxs-lookup"><span data-stu-id="7867f-111">CA1831 suggests using the <xref:System.Range>-based indexer on a *span* of the string, instead.</span></span> <span data-ttu-id="7867f-112">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7867f-112">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

#### <a name="version-introduced"></a><span data-ttu-id="7867f-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="7867f-113">Version introduced</span></span>

<span data-ttu-id="7867f-114">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="7867f-114">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7867f-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="7867f-115">Recommended action</span></span>

- <span data-ttu-id="7867f-116">Kodunuzu düzeltmek ve gereksiz ayırmaları önlemek için <xref:System.MemoryExtensions.AsSpan(System.String)> <xref:System.MemoryExtensions.AsMemory(System.String)> tabanlı dizin oluşturucuyu kullanmadan önce veya ' i çağırın <xref:System.Range> .</span><span class="sxs-lookup"><span data-stu-id="7867f-116">To correct your code and avoid unnecessary allocations, call <xref:System.MemoryExtensions.AsSpan(System.String)> or <xref:System.MemoryExtensions.AsMemory(System.String)> before using the <xref:System.Range>-based indexer.</span></span> <span data-ttu-id="7867f-117">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7867f-117">For example:</span></span>

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- <span data-ttu-id="7867f-118">Kodunuzu değiştirmek istemiyorsanız, önem derecesini veya olarak ayarlayarak kuralı devre dışı bırakabilirsiniz `suggestion` `none` .</span><span class="sxs-lookup"><span data-stu-id="7867f-118">If you don't want to change your code, you can disable the rule by setting its severity to `suggestion` or `none`.</span></span> <span data-ttu-id="7867f-119">Daha fazla bilgi için bkz. [kod analizi kurallarını yapılandırma](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md).</span><span class="sxs-lookup"><span data-stu-id="7867f-119">For more information, see [Configure code analysis rules](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md).</span></span>

- <span data-ttu-id="7867f-120">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7867f-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="7867f-121">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="7867f-121">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="7867f-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="7867f-122">Category</span></span>

<span data-ttu-id="7867f-123">Kod analizi</span><span class="sxs-lookup"><span data-stu-id="7867f-123">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7867f-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="7867f-124">Affected APIs</span></span>

- <xref:System.Range?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Range`

-->
