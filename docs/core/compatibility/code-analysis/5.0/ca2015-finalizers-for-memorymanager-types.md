---
title: "Son değişiklik: CA2015: MemoryManager 'dan türetilmiş türler için sonlandırıcılar tanımlama<T>"
description: Kod Analizi kuralı CA2015 'nin etkinleştirilmesi nedeniyle .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: 4333cec7657657f7e9ba864bcb9979609ad379e0
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257745"
---
# <a name="warning-ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a><span data-ttu-id="c35eb-103">Uyarı CA2015: MemoryManager 'dan türetilmiş türler için sonlandırıcılar tanımlama\<T></span><span class="sxs-lookup"><span data-stu-id="c35eb-103">Warning CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>

<span data-ttu-id="c35eb-104">.Net Code Analyzer Rule [CA2015](/visualstudio/code-quality/ca2015) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="c35eb-104">.NET code analyzer rule [CA2015](/visualstudio/code-quality/ca2015) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="c35eb-105">Sonlandırıcıyı tanımlayan herhangi bir tür için derleme uyarısı oluşturur <xref:System.Buffers.MemoryManager%601> .</span><span class="sxs-lookup"><span data-stu-id="c35eb-105">It produces a build warning for any types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span>

## <a name="change-description"></a><span data-ttu-id="c35eb-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="c35eb-106">Change description</span></span>

<span data-ttu-id="c35eb-107">.NET 5 ' den başlayarak .NET SDK [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="c35eb-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="c35eb-108">Bu kuralların bazıları varsayılan olarak [CA2015](/visualstudio/code-quality/ca2015)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="c35eb-108">Several of these rules are enabled, by default, including [CA2015](/visualstudio/code-quality/ca2015).</span></span> <span data-ttu-id="c35eb-109">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="c35eb-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="c35eb-110">Bir Sonlandırıcı tanımlatan türetilen kural CA2015 Flags türleri <xref:System.Buffers.MemoryManager%601> .</span><span class="sxs-lookup"><span data-stu-id="c35eb-110">Rule CA2015 flags types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span> <span data-ttu-id="c35eb-111">' Dan türetilen bir türe Sonlandırıcı eklemek <xref:System.Buffers.MemoryManager%601> , büyük olasılıkla bir hatanın göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="c35eb-111">Adding a finalizer to a type that derives from <xref:System.Buffers.MemoryManager%601> is likely an indication of a bug.</span></span> <span data-ttu-id="c35eb-112">Bir içinde elde edilen yerel bir kaynağın <xref:System.Span%601> temizlenmesinin yanı da hala tarafından kullanılıyor olması önerilir <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="c35eb-112">It suggests that a native resource that could have been obtained in a <xref:System.Span%601> is getting cleaned up, potentially while it's still in use by the <xref:System.Span%601>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c35eb-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c35eb-113">Version introduced</span></span>

<span data-ttu-id="c35eb-114">5.0</span><span class="sxs-lookup"><span data-stu-id="c35eb-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c35eb-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c35eb-115">Recommended action</span></span>

- <span data-ttu-id="c35eb-116">Sonlandırıcı tanımını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="c35eb-116">Remove the finalizer definition.</span></span> <span data-ttu-id="c35eb-117">Daha fazla bilgi için bkz. [CA2015](/visualstudio/code-quality/ca2015).</span><span class="sxs-lookup"><span data-stu-id="c35eb-117">For more information, see [CA2015](/visualstudio/code-quality/ca2015).</span></span>

- <span data-ttu-id="c35eb-118">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="c35eb-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="c35eb-119">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="c35eb-119">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c35eb-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c35eb-120">Affected APIs</span></span>

<span data-ttu-id="c35eb-121">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="c35eb-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
