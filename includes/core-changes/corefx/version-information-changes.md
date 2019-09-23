---
ms.openlocfilehash: 5bed2d1d4eda4a4c577f05f614a71aa9180998a7
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182023"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="a5fa4-101">Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil</span><span class="sxs-lookup"><span data-stu-id="a5fa4-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="a5fa4-102">.NET Core sürümlerini döndüren API 'lerin birçoğu, artık dosya sürümü yerine ürün sürümünü döndürdü.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-102">Many of the APIs that return versions in .NET Core now returned the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a5fa4-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="a5fa4-103">Change description</span></span>

<span data-ttu-id="a5fa4-104">.NET Core 2,2 ve önceki sürümlerde,,, ve .net <xref:System.Environment.Version?displayProperty=nameWithType>Core <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>derlemeleri için dosya özellikleri iletişim kutusu gibi yöntemler dosya sürümünü yansıtır.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="a5fa4-105">.NET Core 3,0 ile başlayarak ürün sürümünü yansıtmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-105">Starting with .NET Core 3.0, they reflect the product version.</span></span> 

<span data-ttu-id="a5fa4-106">Aşağıdaki şekilde, **Windows Gezgini** dosya özellikleri iletişim kutusunda gösterildiği gibi .net Core 2,2 (solda) ve .net Core 3,0 (sağdaki) için *System. Runtime. dll* derlemesi için sürüm bilgileri arasındaki fark gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Ürün sürümü bilgilerinde fark](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="a5fa4-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="a5fa4-108">Version introduced</span></span>

<span data-ttu-id="a5fa4-109">3.0</span><span class="sxs-lookup"><span data-stu-id="a5fa4-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a5fa4-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="a5fa4-110">Recommended action</span></span>

<span data-ttu-id="a5fa4-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-111">None.</span></span> <span data-ttu-id="a5fa4-112">Bu değişiklik, sürüm algılamayı obtuse yerine sezgisel hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a5fa4-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="a5fa4-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="a5fa4-113">Category</span></span>

<span data-ttu-id="a5fa4-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="a5fa4-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a5fa4-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="a5fa4-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!-- 

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`


-->