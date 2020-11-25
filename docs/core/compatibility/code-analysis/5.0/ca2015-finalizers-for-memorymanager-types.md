---
title: "Son değişiklik: CA2015: MemoryManager 'dan türetilmiş türler için sonlandırıcılar tanımlama<T>"
description: Kod Analizi kuralı CA2015 'nin etkinleştirilmesi nedeniyle .NET 5,0 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: 5d0ba0546b5a72363559f23713c8af4bb4e26e48
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761325"
---
# <a name="warning-ca2015-do-not-define-finalizers-for-types-derived-from-memorymanagert"></a><span data-ttu-id="1c664-103">Uyarı CA2015: MemoryManager 'dan türetilmiş türler için sonlandırıcılar tanımlama\<T></span><span class="sxs-lookup"><span data-stu-id="1c664-103">Warning CA2015: Do not define finalizers for types derived from MemoryManager\<T></span></span>

<span data-ttu-id="1c664-104">.Net Code Analyzer Rule [CA2015](/visualstudio/code-quality/ca2015) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="1c664-104">.NET code analyzer rule [CA2015](/visualstudio/code-quality/ca2015) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="1c664-105">Sonlandırıcıyı tanımlayan herhangi bir tür için derleme uyarısı oluşturur <xref:System.Buffers.MemoryManager%601> .</span><span class="sxs-lookup"><span data-stu-id="1c664-105">It produces a build warning for any types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span>

## <a name="change-description"></a><span data-ttu-id="1c664-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="1c664-106">Change description</span></span>

<span data-ttu-id="1c664-107">.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="1c664-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="1c664-108">Bu kuralların bazıları varsayılan olarak [CA2015](/visualstudio/code-quality/ca2015)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="1c664-108">Several of these rules are enabled, by default, including [CA2015](/visualstudio/code-quality/ca2015).</span></span> <span data-ttu-id="1c664-109">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="1c664-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="1c664-110">Bir Sonlandırıcı tanımlatan türetilen kural CA2015 Flags türleri <xref:System.Buffers.MemoryManager%601> .</span><span class="sxs-lookup"><span data-stu-id="1c664-110">Rule CA2015 flags types that derive from <xref:System.Buffers.MemoryManager%601> that define a finalizer.</span></span> <span data-ttu-id="1c664-111">' Dan türetilen bir türe Sonlandırıcı eklemek <xref:System.Buffers.MemoryManager%601> , büyük olasılıkla bir hatanın göstergesidir.</span><span class="sxs-lookup"><span data-stu-id="1c664-111">Adding a finalizer to a type that derives from <xref:System.Buffers.MemoryManager%601> is likely an indication of a bug.</span></span> <span data-ttu-id="1c664-112">Bir içinde elde edilen yerel bir kaynağın <xref:System.Span%601> temizlenmesinin yanı da hala tarafından kullanılıyor olması önerilir <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="1c664-112">It suggests that a native resource that could have been obtained in a <xref:System.Span%601> is getting cleaned up, potentially while it's still in use by the <xref:System.Span%601>.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1c664-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="1c664-113">Version introduced</span></span>

<span data-ttu-id="1c664-114">5.0</span><span class="sxs-lookup"><span data-stu-id="1c664-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1c664-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1c664-115">Recommended action</span></span>

- <span data-ttu-id="1c664-116">Sonlandırıcı tanımını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1c664-116">Remove the finalizer definition.</span></span> <span data-ttu-id="1c664-117">Daha fazla bilgi için bkz. [CA2015](/visualstudio/code-quality/ca2015).</span><span class="sxs-lookup"><span data-stu-id="1c664-117">For more information, see [CA2015](/visualstudio/code-quality/ca2015).</span></span>

- <span data-ttu-id="1c664-118">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="1c664-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="1c664-119">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="1c664-119">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1c664-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1c664-120">Affected APIs</span></span>

<span data-ttu-id="1c664-121">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="1c664-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
