---
ms.openlocfilehash: b01424c63d6e7956127bf889c53422b60ba2f219
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598055"
---
### <a name="ca2013-do-not-use-referenceequals-with-value-types"></a><span data-ttu-id="ffd86-101">CA2013: ReferenceEquals metodunu değer türleriyle birlikte kullanmayın</span><span class="sxs-lookup"><span data-stu-id="ffd86-101">CA2013: Do not use ReferenceEquals with value types</span></span>

<span data-ttu-id="ffd86-102">.Net Code Analyzer Rule [CA2013](/visualstudio/code-quality/ca2013) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir.</span><span class="sxs-lookup"><span data-stu-id="ffd86-102">.NET code analyzer rule [CA2013](/visualstudio/code-quality/ca2013) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="ffd86-103"><xref:System.Object.ReferenceEquals(System.Object,System.Object)>Bir veya daha fazla değer türünü eşitlik için karşılaştırmak üzere kullanılan herhangi bir kod için derleme uyarısı üretir.</span><span class="sxs-lookup"><span data-stu-id="ffd86-103">It produces a build warning for any code where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ffd86-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="ffd86-104">Change description</span></span>

<span data-ttu-id="ffd86-105">.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../docs/fundamentals/productivity/code-analysis.md)içerir.</span><span class="sxs-lookup"><span data-stu-id="ffd86-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="ffd86-106">Bu kuralların bazıları varsayılan olarak [CA2013](/visualstudio/code-quality/ca2013)dahil olmak üzere etkindir.</span><span class="sxs-lookup"><span data-stu-id="ffd86-106">Several of these rules are enabled, by default, including [CA2013](/visualstudio/code-quality/ca2013).</span></span> <span data-ttu-id="ffd86-107">Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.</span><span class="sxs-lookup"><span data-stu-id="ffd86-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="ffd86-108">Rule CA2013 <xref:System.Object.ReferenceEquals(System.Object,System.Object)> , eşitlik için bir veya daha fazla değer türünü karşılaştırmak için kullanılan örnekleri bulur.</span><span class="sxs-lookup"><span data-stu-id="ffd86-108">Rule CA2013 finds instances where <xref:System.Object.ReferenceEquals(System.Object,System.Object)> is used to compare one or more value types for equality.</span></span> <span data-ttu-id="ffd86-109">Bu şekilde eşitlik için değer türlerini karşılaştırma, değerler karşılaştırılmadan önce paketlendikleri için yanlış sonuçlara yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="ffd86-109">Comparing value types for equality in this way can lead to incorrect results, because the values are boxed before they're compared.</span></span> <span data-ttu-id="ffd86-110"><xref:System.Object.ReferenceEquals(System.Object,System.Object)>`false`karşılaştırılan değerler bir değer türünün aynı örneğini temsil ediyorsa bile döndürülür.</span><span class="sxs-lookup"><span data-stu-id="ffd86-110"><xref:System.Object.ReferenceEquals(System.Object,System.Object)> will return `false` even if the compared values represent the same instance of a value type.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ffd86-111">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="ffd86-111">Version introduced</span></span>

<span data-ttu-id="ffd86-112">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="ffd86-112">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ffd86-113">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="ffd86-113">Recommended action</span></span>

- <span data-ttu-id="ffd86-114">Kodu, gibi uygun bir eşitlik işleci kullanacak şekilde değiştirin `==` .</span><span class="sxs-lookup"><span data-stu-id="ffd86-114">Change the code to use an appropriate equality operator, such as `==`.</span></span> <span data-ttu-id="ffd86-115">Bu uyarıyı gizmemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="ffd86-115">You should not suppress this warning.</span></span>

- <span data-ttu-id="ffd86-116">Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ffd86-116">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="ffd86-117">Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="ffd86-117">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="ffd86-118">Kategori</span><span class="sxs-lookup"><span data-stu-id="ffd86-118">Category</span></span>

<span data-ttu-id="ffd86-119">Kod analizi</span><span class="sxs-lookup"><span data-stu-id="ffd86-119">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ffd86-120">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="ffd86-120">Affected APIs</span></span>

- <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Object.ReferenceEquals(System.Object,System.Object)`

-->
