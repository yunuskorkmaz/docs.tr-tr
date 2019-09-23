---
ms.openlocfilehash: bb163d5a6eb3d926a44a83ea79572c3a497bbe8d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181708"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="28dbc-101">Microsoft. VisualBasic. Devices ad alanındaki türler kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="28dbc-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="28dbc-102"><xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> Ad alanındaki türler kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="28dbc-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="28dbc-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="28dbc-103">Version introduced</span></span>

<span data-ttu-id="28dbc-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="28dbc-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="28dbc-105">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="28dbc-105">Details</span></span>

<span data-ttu-id="28dbc-106"><xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> Ad alanındaki türler, bazı .NET Core 3,0 önizleme sürümlerinde mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="28dbc-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="28dbc-107">.NET Core 3,0 Preview 9 ' dan itibaren artık kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="28dbc-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="28dbc-108">Gereksiz bütünleştirilmiş kod bağımlılıklarından veya sonraki sürümlerde son değişikliklerden kaçınmak için türler kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="28dbc-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="28dbc-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="28dbc-109">Recommended action</span></span>

<span data-ttu-id="28dbc-110">Kodunuz <xref:Microsoft.VisualBasic.Devices> türlerin ve üyelerinin kullanımına bağımlıysa, .NET sınıf kitaplığı 'nda karşılık gelen bir türü veya üyeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28dbc-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="28dbc-111">Örneğin <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> , sınıfına denk işlevsellik <xref:System.Environment?displayProperty=nameWithType> <xref:System.DateTime?displayProperty=nameWithType> ve türleri tarafından sağlanır ve <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> sınıfa denk işlevsellik, <xref:System.IO.Ports?displayProperty=nameWithType> ad alanındaki türler tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="28dbc-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="28dbc-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="28dbc-112">Category</span></span>

<span data-ttu-id="28dbc-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="28dbc-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="28dbc-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="28dbc-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

