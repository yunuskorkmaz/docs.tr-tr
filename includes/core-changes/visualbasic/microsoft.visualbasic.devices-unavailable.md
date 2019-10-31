---
ms.openlocfilehash: 4c47b95e98aca727d9f0eda54a167a71fd53afb9
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198580"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="0cc80-101">Microsoft. VisualBasic. Devices ad alanındaki türler kullanılamıyor</span><span class="sxs-lookup"><span data-stu-id="0cc80-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="0cc80-102"><xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> ad alanındaki türler kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="0cc80-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0cc80-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0cc80-103">Version introduced</span></span>

<span data-ttu-id="0cc80-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="0cc80-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="0cc80-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="0cc80-105">Change description</span></span>

<span data-ttu-id="0cc80-106"><xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> ad alanındaki türler, bazı .NET Core 3,0 önizleme sürümlerinde bulunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0cc80-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="0cc80-107">.NET Core 3,0 Preview 9 ' dan itibaren artık kullanılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="0cc80-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="0cc80-108">Gereksiz bütünleştirilmiş kod bağımlılıklarından veya sonraki sürümlerde son değişikliklerden kaçınmak için türler kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0cc80-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0cc80-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0cc80-109">Recommended action</span></span>

<span data-ttu-id="0cc80-110">Kodunuz <xref:Microsoft.VisualBasic.Devices> türlerinin ve üyelerinin kullanımına bağımlıysa, .NET sınıf kitaplığı 'nda karşılık gelen bir türü veya üyeyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0cc80-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="0cc80-111">Örneğin, <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> sınıfına denk işlevsellik <xref:System.DateTime?displayProperty=nameWithType> ve <xref:System.Environment?displayProperty=nameWithType> türleri tarafından sağlanır ve <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> sınıfına denk işlevsellik <xref:System.IO.Ports?displayProperty=nameWithType> ad alanındaki türler tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="0cc80-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="0cc80-112">Kategori</span><span class="sxs-lookup"><span data-stu-id="0cc80-112">Category</span></span>

<span data-ttu-id="0cc80-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0cc80-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0cc80-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0cc80-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

