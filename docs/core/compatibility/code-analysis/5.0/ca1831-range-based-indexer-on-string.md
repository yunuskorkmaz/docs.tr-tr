---
title: 'Son değişiklik: CA1831: dize için Aralık tabanlı dizin oluşturucular yerine AsSpan kullanın'
description: Kod Analizi kuralı CA1831 'nin etkinleştirilmesi nedeniyle .NET 5,0 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 08/21/2020
ms.openlocfilehash: 850916b804ae29dba8d2bd05c6e4fb06fe667296
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437893"
---
# <a name="warning-ca1831-use-asspan-instead-of-range-based-indexers-for-string"></a><span data-ttu-id="73d59-103">Uyarı CA1831: dize için Aralık tabanlı dizin oluşturucular yerine AsSpan kullanın</span><span class="sxs-lookup"><span data-stu-id="73d59-103">Warning CA1831: Use AsSpan instead of Range-based indexers for string</span></span>

<span data-ttu-id="73d59-104">.Net Code Analyzer Rule [CA1831](/visualstudio/code-quality/ca1831) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="73d59-104">.NET code analyzer rule [CA1831](/visualstudio/code-quality/ca1831) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="73d59-105">Bir <xref:System.Range> dizede kullanılan bir dizin oluşturucunun kullanıldığı, ancak herhangi bir kopyanın istendiği herhangi bir kod için derleme uyarısı üretir.</span><span class="sxs-lookup"><span data-stu-id="73d59-105">It produces a build warning for any code where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span>

## <a name="change-description"></a><span data-ttu-id="73d59-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="73d59-106">Change description</span></span>

<span data-ttu-id="73d59-107">.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="73d59-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="73d59-108">Bu kuralların bazıları varsayılan olarak [CA1831](/visualstudio/code-quality/ca1831)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="73d59-108">Several of these rules are enabled, by default, including [CA1831](/visualstudio/code-quality/ca1831).</span></span> <span data-ttu-id="73d59-109">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="73d59-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="73d59-110">Rule CA1831 <xref:System.Range> , bir dize üzerinde bir-tabanlı dizin oluşturucunun kullanıldığı, ancak hiçbir kopyanın istendiği örnekleri bulur.</span><span class="sxs-lookup"><span data-stu-id="73d59-110">Rule CA1831 finds instances where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span> <span data-ttu-id="73d59-111"><xref:System.Range>-Tabanlı dizin oluşturucu örtük bir tür oluşturmak için doğrudan bir dize üzerinde kullanılıyorsa, dizenin istenen bölümünün gereksiz bir kopyası oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="73d59-111">If the <xref:System.Range>-based indexer is used directly on a string to produce an implicit cast, then an unnecessary copy of the requested portion of the string is created.</span></span> <span data-ttu-id="73d59-112">Örnek:</span><span class="sxs-lookup"><span data-stu-id="73d59-112">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

<span data-ttu-id="73d59-113">CA1831 <xref:System.Range> , bunun yerine dizenin bir *aralığında* tabanlı dizin oluşturucuyu kullanmayı önerir.</span><span class="sxs-lookup"><span data-stu-id="73d59-113">CA1831 suggests using the <xref:System.Range>-based indexer on a *span* of the string, instead.</span></span> <span data-ttu-id="73d59-114">Örnek:</span><span class="sxs-lookup"><span data-stu-id="73d59-114">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

## <a name="version-introduced"></a><span data-ttu-id="73d59-115">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="73d59-115">Version introduced</span></span>

<span data-ttu-id="73d59-116">5.0</span><span class="sxs-lookup"><span data-stu-id="73d59-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="73d59-117">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="73d59-117">Recommended action</span></span>

- <span data-ttu-id="73d59-118">Kodunuzu düzeltmek ve gereksiz ayırmaları önlemek için <xref:System.MemoryExtensions.AsSpan(System.String)> <xref:System.MemoryExtensions.AsMemory(System.String)> tabanlı dizin oluşturucuyu kullanmadan önce veya ' i çağırın <xref:System.Range> .</span><span class="sxs-lookup"><span data-stu-id="73d59-118">To correct your code and avoid unnecessary allocations, call <xref:System.MemoryExtensions.AsSpan(System.String)> or <xref:System.MemoryExtensions.AsMemory(System.String)> before using the <xref:System.Range>-based indexer.</span></span> <span data-ttu-id="73d59-119">Örnek:</span><span class="sxs-lookup"><span data-stu-id="73d59-119">For example:</span></span>

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- <span data-ttu-id="73d59-120">Kodunuzu değiştirmek istemiyorsanız, önem derecesini veya olarak ayarlayarak kuralı devre dışı bırakabilirsiniz `suggestion` `none` .</span><span class="sxs-lookup"><span data-stu-id="73d59-120">If you don't want to change your code, you can disable the rule by setting its severity to `suggestion` or `none`.</span></span> <span data-ttu-id="73d59-121">Daha fazla bilgi için bkz. [kod analizi kurallarını yapılandırma](../../../../fundamentals/code-analysis/configuration-options.md).</span><span class="sxs-lookup"><span data-stu-id="73d59-121">For more information, see [Configure code analysis rules](../../../../fundamentals/code-analysis/configuration-options.md).</span></span>

- <span data-ttu-id="73d59-122">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="73d59-122">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="73d59-123">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="73d59-123">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="73d59-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="73d59-124">Affected APIs</span></span>

- <xref:System.Range?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Range`

### Category

Code analysis

-->
