---
ms.openlocfilehash: 5612ebce67946e22aaeeba861115ce4f8967e1f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344442"
---
### <a name="apis-that-report-version-now-report-product-and-not-file-version"></a><span data-ttu-id="defcb-101">Rapor sürümünü rapor eden API'ler artık ürünü rapor eder, dosya sürümünü bildirmez</span><span class="sxs-lookup"><span data-stu-id="defcb-101">APIs that report version now report product and not file version</span></span>

<span data-ttu-id="defcb-102">.NET Core'da sürümleri döndüren API'lerin çoğu artık dosya sürümü yerine ürün sürümünü döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="defcb-102">Many of the APIs that return versions in .NET Core now return the product version rather than the file version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="defcb-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="defcb-103">Change description</span></span>

<span data-ttu-id="defcb-104">.NET Core 2.2 ve önceki sürümlerde <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, , , ve .NET Core derlemeleri için dosya özellikleri iletişim kutusu gibi <xref:System.Environment.Version?displayProperty=nameWithType>yöntemler dosya sürümünü yansıtır.</span><span class="sxs-lookup"><span data-stu-id="defcb-104">In .NET Core 2.2 and previous versions, methods such as <xref:System.Environment.Version?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>, and the file properties dialog for .NET Core assemblies reflect the file version.</span></span> <span data-ttu-id="defcb-105">.NET Core 3.0 ile başlayarak ürün sürümünü yansıtırlar.</span><span class="sxs-lookup"><span data-stu-id="defcb-105">Starting with .NET Core 3.0, they reflect the product version.</span></span>

<span data-ttu-id="defcb-106">Aşağıdaki şekilde *System.Runtime.dll* assemblyi için .NET Core 2.2 (solda) ve .NET Core 3.0 (sağda) için windows **explorer** dosya özellikleri iletişim kutusunda görüntülenen sürüm bilgileri arasındaki farkı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="defcb-106">The following figure illustrates the difference in version information for the *System.Runtime.dll* assembly for .NET Core 2.2 (on the left) and .NET Core 3.0 (on the right) as displayed by the **Windows Explorer** file properties dialog.</span></span>

![Ürün sürüm bilgilerindeki fark](~/docs/images/core-changes/corefx/version-information-changes/file-details.png)

#### <a name="version-introduced"></a><span data-ttu-id="defcb-108">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="defcb-108">Version introduced</span></span>

<span data-ttu-id="defcb-109">3,0</span><span class="sxs-lookup"><span data-stu-id="defcb-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="defcb-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="defcb-110">Recommended action</span></span>

<span data-ttu-id="defcb-111">Yok.</span><span class="sxs-lookup"><span data-stu-id="defcb-111">None.</span></span> <span data-ttu-id="defcb-112">Bu değişiklik, sürüm algılamayı kalın kullanmaktan çok sezgisel hale getirmelidir.</span><span class="sxs-lookup"><span data-stu-id="defcb-112">This change should make version detection intuitive rather than obtuse.</span></span>

#### <a name="category"></a><span data-ttu-id="defcb-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="defcb-113">Category</span></span>

<span data-ttu-id="defcb-114">CoreFx</span><span class="sxs-lookup"><span data-stu-id="defcb-114">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="defcb-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="defcb-115">Affected APIs</span></span>

- <xref:System.Environment.Version?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType>

<!--

### Affected APIs

- `P:System.Environment.Version`
- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
