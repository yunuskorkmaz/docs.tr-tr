---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116359"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="24b16-101">Microsoft.VisualBasic.Devices ad alanında türleri kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="24b16-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="24b16-102"><xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> Ad alanındaki türler kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="24b16-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="24b16-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="24b16-103">Version introduced</span></span>

<span data-ttu-id="24b16-104">.NET Core 3.0 Önizleme 8</span><span class="sxs-lookup"><span data-stu-id="24b16-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="24b16-105">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="24b16-105">Change description</span></span>

<span data-ttu-id="24b16-106"><xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> Ad alanındaki türler bazı .NET Core 3.0 Önizleme sürümlerinde kullanılabilirdi.</span><span class="sxs-lookup"><span data-stu-id="24b16-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="24b16-107">.NET Core 3.0 Preview 9 ile başlayarak artık kullanılamazlar.</span><span class="sxs-lookup"><span data-stu-id="24b16-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="24b16-108">Türler, gereksiz derleme bağımlılıklarını veya sonraki sürümlerde değişiklikleri kırmayı önlemek için kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="24b16-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="24b16-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="24b16-109">Recommended action</span></span>

<span data-ttu-id="24b16-110">Kodunuz <xref:Microsoft.VisualBasic.Devices> türlerin ve üyelerinin kullanımına bağlıysa, .NET sınıf kitaplığında karşılık gelen bir türü veya üyeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="24b16-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="24b16-111">Örneğin, <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> sınıfa eşdeğer işlevsellik <xref:System.DateTime?displayProperty=nameWithType> ve <xref:System.Environment?displayProperty=nameWithType> türleri tarafından sağlanır ve <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> sınıfa eşdeğer işlevsellik <xref:System.IO.Ports?displayProperty=nameWithType> ad alanındaki türler tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="24b16-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="24b16-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="24b16-112">Category</span></span>

<span data-ttu-id="24b16-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24b16-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="24b16-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="24b16-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
