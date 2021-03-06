---
title: 'Son değişiklik: CA2013: ReferenceEquals değerini değer türleriyle kullanma'
description: Kod Analizi kuralı CA2013 'nin etkinleştirilmesi nedeniyle .NET 5 ' teki önemli değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: fc68d9a3af0d629dc39aba0091d32b1982d6f2c5
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257773"
---
# <a name="warning-ca2013-do-not-use-referenceequals-with-value-types"></a><span data-ttu-id="49b1d-103">Uyarı CA2013: ReferenceEquals değerini değer türleriyle kullanmayın</span><span class="sxs-lookup"><span data-stu-id="49b1d-103">Warning CA2013: Do not use ReferenceEquals with value types</span></span>

<span data-ttu-id="49b1d-104">.Net Code Analyzer Rule [CA2013](/visualstudio/code-quality/ca2013) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="49b1d-104">.NET code analyzer rule [CA2013](/visualstudio/code-quality/ca2013) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="49b1d-105"><xref:System.Object.ReferenceEquals(System.Object,System.Object)>Bir veya daha fazla değer türünü eşitlik için karşılaştırmak üzere kullanılan herhangi bir kod için derleme uyarısı üretir.</span><span class="sxs-lookup"><span data-stu-id="49b1d-105">It produces a build warning for any code where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span>

## <a name="change-description"></a><span data-ttu-id="49b1d-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="49b1d-106">Change description</span></span>

<span data-ttu-id="49b1d-107">.NET 5 ' den başlayarak .NET SDK [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="49b1d-107">Starting in .NET 5, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="49b1d-108">Bu kuralların bazıları varsayılan olarak [CA2013](/visualstudio/code-quality/ca2013)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="49b1d-108">Several of these rules are enabled, by default, including [CA2013](/visualstudio/code-quality/ca2013).</span></span> <span data-ttu-id="49b1d-109">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="49b1d-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="49b1d-110">Rule CA2013 <xref:System.Object.ReferenceEquals(System.Object,System.Object)> , eşitlik için bir veya daha fazla değer türünü karşılaştırmak için kullanılan örnekleri bulur.</span><span class="sxs-lookup"><span data-stu-id="49b1d-110">Rule CA2013 finds instances where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span> <span data-ttu-id="49b1d-111">Bu şekilde eşitlik için değer türlerini karşılaştırma, değerler karşılaştırılmadan önce paketlendikleri için yanlış sonuçlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="49b1d-111">Comparing value types for equality in this way can lead to incorrect results, because the values are boxed before they're compared.</span></span> <span data-ttu-id="49b1d-112"><xref:System.Object.ReferenceEquals(System.Object,System.Object)>`false`karşılaştırılan değerler bir değer türünün aynı örneğini temsil ediyorsa bile döndürülür.</span><span class="sxs-lookup"><span data-stu-id="49b1d-112"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> will return `false` even if the compared values represent the same instance of a value type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="49b1d-113">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="49b1d-113">Version introduced</span></span>

<span data-ttu-id="49b1d-114">5.0</span><span class="sxs-lookup"><span data-stu-id="49b1d-114">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="49b1d-115">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="49b1d-115">Recommended action</span></span>

- <span data-ttu-id="49b1d-116">Kodu, gibi uygun bir eşitlik işleci kullanacak şekilde değiştirin `==` .</span><span class="sxs-lookup"><span data-stu-id="49b1d-116">Change the code to use an appropriate equality operator, such as `==`.</span></span> <span data-ttu-id="49b1d-117">Bu uyarıyı gizmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="49b1d-117">You should not suppress this warning.</span></span>

- <span data-ttu-id="49b1d-118">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="49b1d-118">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="49b1d-119">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="49b1d-119">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="49b1d-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="49b1d-120">Affected APIs</span></span>

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

### Category

Code analysis

-->
