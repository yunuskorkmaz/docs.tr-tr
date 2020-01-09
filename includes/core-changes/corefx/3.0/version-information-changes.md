---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344442"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="44a37-101">Sürümü şimdi rapor eden API 'Ler rapor ürünü ve dosya sürümü değil</span><span class="sxs-lookup"><span data-stu-id="44a37-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="44a37-102">.NET Core sürümlerini döndüren API 'lerin birçoğu, artık dosya sürümü yerine ürün sürümünü döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="44a37-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="44a37-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="44a37-103">Change description</span></span>

<span data-ttu-id="44a37-104">.NET Core 2,2 ve önceki sürümlerde, .NET Core derlemeleri için <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>ve dosya özellikleri iletişim kutusu gibi yöntemler dosya sürümünü yansıtır.</span><span class="sxs-lookup"><span data-stu-id="44a37-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="44a37-105">.NET Core 3,0 ile başlayarak ürün sürümünü yansıtmaktadır.</span><span class="sxs-lookup"><span data-stu-id="44a37-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="44a37-106">Aşağıdaki şekilde, **Windows Gezgini** dosya özellikleri iletişim kutusunda gösterildiği gibi .net Core 2,2 (solda) ve .net Core 3,0 (sağdaki) için *System. Runtime. dll* derlemesi için sürüm bilgileri arasındaki fark gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="44a37-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Ürün sürümü bilgilerinde fark](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="44a37-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="44a37-108">Version introduced</span></span>

<span data-ttu-id="44a37-109">3.0</span><span class="sxs-lookup"><span data-stu-id="44a37-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="44a37-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="44a37-110">Recommended action</span></span>

<span data-ttu-id="44a37-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="44a37-111">None.</span></span> <span data-ttu-id="44a37-112">Bu değişiklik, sürüm algılamayı obtuse yerine sezgisel hale getirir.</span><span class="sxs-lookup"><span data-stu-id="44a37-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="44a37-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="44a37-113">Category</span></span>

<span data-ttu-id="44a37-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="44a37-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="44a37-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="44a37-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
