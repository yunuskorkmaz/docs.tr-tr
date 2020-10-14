---
ms.openlocfilehash: 80d13609f1b02ae0ac875b2028e745670bb8f503
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050578"
---
### <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a><span data-ttu-id="63033-101">FrameworkDescription 'un değeri .NET Core yerine .NET</span><span class="sxs-lookup"><span data-stu-id="63033-101">FrameworkDescription's value is .NET instead of .NET Core</span></span>

<span data-ttu-id="63033-102"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> Şimdi ".NET Core" yerine ".NET" döndürür.</span><span class="sxs-lookup"><span data-stu-id="63033-102"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> now returns ".NET" instead of ".NET Core".</span></span>

#### <a name="change-description"></a><span data-ttu-id="63033-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="63033-103">Change description</span></span>

<span data-ttu-id="63033-104">Önceki .NET sürümlerinde, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> Açıklama dizesinin parçası olarak ".NET Core" döndürür. Örneğin, `.NET Core 3.1.1` .</span><span class="sxs-lookup"><span data-stu-id="63033-104">In previous .NET versions, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET Core" as part of the description string, for example, `.NET Core 3.1.1`.</span></span>

<span data-ttu-id="63033-105">.NET 5,0 ' den başlayarak, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> Açıklama dizesinin parçası olarak ".net" döndürür. Örneğin, `.NET 5.0.0` .</span><span class="sxs-lookup"><span data-stu-id="63033-105">Starting in .NET 5.0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET" as part of the description string, for example, `.NET 5.0.0`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="63033-106">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="63033-106">Reason for change</span></span>

<span data-ttu-id="63033-107">.NET 5 ile, `netcoreapp` `net` kısa hedef çerçeve bilinen adıyla değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="63033-107">With .NET 5, `netcoreapp` is replaced by `net` as the short target-framework moniker.</span></span> <span data-ttu-id="63033-108">Tutarlılık için çerçevenin açıklaması da güncelleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="63033-108">For consistency, the framework's description has also been updated.</span></span> <span data-ttu-id="63033-109">Değişiklik, `FrameworkName` özelliğin dışında herhangi bir yerde kodlanmadığından, yüzeysel <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="63033-109">The change is cosmetic, as the `FrameworkName` isn't encoded anywhere else than in the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="63033-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="63033-110">Version introduced</span></span>

<span data-ttu-id="63033-111">5.0</span><span class="sxs-lookup"><span data-stu-id="63033-111">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="63033-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="63033-112">Recommended action</span></span>

<span data-ttu-id="63033-113">Tarafından döndürülen dizedeki ".NET Core" için arama yapan tüm kodları güncelleştirin <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> .</span><span class="sxs-lookup"><span data-stu-id="63033-113">Update any code that searches for ".NET Core" in the string returned by <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription>.</span></span>

#### <a name="category"></a><span data-ttu-id="63033-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="63033-114">Category</span></span>

<span data-ttu-id="63033-115">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="63033-115">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="63033-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="63033-116">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
